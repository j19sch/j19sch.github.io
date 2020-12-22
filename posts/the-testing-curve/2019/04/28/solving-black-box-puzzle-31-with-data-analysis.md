<html><body><p><a href="https://twitter.com/workroomprds">James Lyndsay</a> has created a number of amazing <a href="http://blackboxpuzzles.workroomprds.com/">Black Box Puzzles</a>: tiny applications that challenge you to figure out what they do. (You can support him in creating more of these at <a href="https://www.patreon.com/workroomprds">his Patreon page</a>.) Two of these Puzzles, <a href="http://blackboxpuzzles.workroomprds.com/puzzle29/">29</a> and <a href="http://blackboxpuzzles.workroomprds.com/puzzle31/">31</a>, not only have a GUI to explore, but also an API.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>And that gave me an idea. If you explore these Puzzles through their GUI, you start from the inputs. You try out different inputs in the hope of discovering a pattern in the outputs. And then that pattern feeds back into your exploration.<br>With an API, however - and because of the nature of Puzzle 31 - it becomes easy to get the outputs for all possible combinations of inputs. Which means you can start your exploration from the outputs instead of the inputs.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Before I tell you how and what I did, three important remarks.<br>First of all, I will be spoiling the solution to the Puzzle in this blog post. So this is the right moment to go and solve <a href="http://blackboxpuzzles.workroomprds.com/puzzle31/">Puzzle 31</a> for yourself first. Or at least go play a bit with it, so you have an idea what the inputs and outputs are.<br>Secondly, I had already solved the Puzzle through the GUI a few months ago. So it was more of a "Can I find the solution this way as well?" than a "Can I find the solution?" thing.<br>Finally, the code and the spreadsheet I created (linked throughout, also available on GitHub <a href="https://github.com/j19sch/blackbox-puzzle-31">here</a>), are not very clean. I thought about tidying them up, but my two reasons for not doing so are (1) laziness; (2) the way they are now gives a more honest picture of what I did.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2><strong>Getting all the combinations for Puzzle 31</strong></h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>The API of Puzzle 31 is described <a href="http://blackboxpuzzles.workroomprds.com:8002/puzzle31">here</a>. You can actually use it from your browser by adding the query parameters for all the buttons like this: <a href="http://blackboxpuzzles.workroomprds.com:8002/puzzle31?buttonA1=up&amp;buttonA2=up&amp;buttonA3=up&amp;buttonB1=up&amp;buttonB2=up&amp;buttonB3=up&amp;buttonC1=up&amp;buttonC2=up&amp;buttonC3=up">http://blackboxpuzzles.workroomprds.com:8002/puzzle31?buttonA1=up&amp;buttonA2=up&amp;buttonA3=up&amp;buttonB1=up&amp;buttonB2=up&amp;buttonB3=up&amp;buttonC1=up&amp;buttonC2=up&amp;buttonC3=up</a>, which will return <code>{"lamp1":"on","lamp2":"off","lamp3":"off","lamp4":"off"}</code>.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>With that figured out, the next question was how to iterate over all the possible inputs in the API requests. Turns out that the Python library <code>itertools</code> has a <code><a href="https://docs.python.org/3.7/library/itertools.html#itertools.product">product</a></code><a href="https://docs.python.org/3.7/library/itertools.html#itertools.product"> </a> function, which does exactly that: <code>product(('up', 'down'), repeat=9)</code>.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Sending API requests with Python is something I have done before (yay requests library!). The same for writing data to a csv file. So I ended up writing <a href="https://github.com/j19sch/blackbox-puzzle-31/blob/master/get_it_all.py">this Python script</a>, which got me <a href="https://github.com/j19sch/blackbox-puzzle-31/blob/master/puzzle31.csv">this csv file</a>.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>In hindsight I would make one change to the script. The values "down"/"up" and "on"/"off" make data analysis harder than it should be. So later on I created <a href="https://github.com/j19sch/blackbox-puzzle-31/blob/master/puzzle31-binary.csv">a different csv file</a> replacing down"/"up" and "on"/"off" with 0/1.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2><strong>Data analysis with a spreadsheet</strong></h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Before trying to tackle the analysis with Python (see the next section), I went at it with a spreadsheet. I have done some data analysis and manipulation with spreadsheets in the past, so I figured that with some filters, some formulas, some conditional formatting, and perhaps a pivot table, I should be able to solve the Puzzle.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>You can find that spreadsheet <a href="https://github.com/j19sch/blackbox-puzzle-31/blob/master/puzzle31.ods">here</a>. Normally I would use Excel, but I got curious if I could get it done with LibreOffice Calc instead. Turns out that yes.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>Solving lamp 1</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>First thing I did was checking how many input combinations would turn each of the lamps on/off. For lamp 1 there are only 2 combinations that turn it on. For all other 510 combinations, it is off. Lamp 2 is on for 337 combinations, off for 175. And lamp 3 and 4 have the same ratio: 169 combinations for on and 343 combinations for off.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>These results suggest that although we have four lamps, there might be just three types of behavior. Or just three behaviors. So I checked if lamp 3 and 4 do the same thing, but that's not the case. For 91 input combinations both are on, for 2 x 78 one is off and the other on, for 265 combinations both are off.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Ok, back to lamp 1, because with just 2 input combinations that switch it on, it should be easy to look at those two combinations and figure out how it works.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":477} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp1-spreadsheet.png" alt="" class="wp-image-477"><figcaption>(Screenshot made after I added conditional formatting to solve lamp 3 and 4.)</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>And there it is: lamp 1 switches on when all buttons are either up or when all of them are down. So that's lamp 1 solved.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>Solving lamp 3 and 4</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>With lamps 2, 3 and 4 having so many combinations resulting in the lamps being either on or off, I added a column to the spreadsheet counting the number of "down" buttons for each input combination. This told me that switching lamp 2 requires at least two "down" buttons. Switching on lamp 3 or 4 required at least 3 "down" buttons. (So lamp 3 and 4 are still very similar.)</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Another thing I did was adding conditional formatting similar to the GUI of the puzzle. "Down" buttons turn blue and "on" lights turn red. This made it a lot easier for me to spot patterns while looking at the data.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>I decided to look further into lamp 3 and lamp 4 first. Looking at the input combinations with the minimal number of three "down" buttons that switch the lamps on, shows a clear pattern:</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":453} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp3-1.png" alt="" class="wp-image-453"><figcaption>Lamp 3: buttons with the same number.</figcaption></figure>
<!-- /wp:image -->

<!-- wp:image {"id":454} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp4-1.png" alt="" class="wp-image-454"><figcaption>Lamp 4: buttons with the same letter.</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Lamp 3 switches on if three buttons with the same number are down; lamp 4 if three buttons with the same letter are down.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Of course, the question remains if that's all there is to lamps 3 and 4. I did a quick visual spot check for lamp 4 with more than three buttons in the down state. That was more of a formality, though, since I knew from solving the Puzzle through the GUI, that I had the correct solution.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>What I should have done however, was add a formula to the spreadsheet calculating the state of lamps 1, 3 and 4 based on the inputs. Then add another formula comparing those states to the actual states and check if I got al off them correctly. So I added these for lamp 4 in the <a href="https://github.com/j19sch/blackbox-puzzle-31/blob/master/puzzle31.ods">spreadsheet</a> in sheet "puzzle31_binary".</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>Solving lamp 2</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Taking a similar approach as with lamp 3 and 4, I looked at all input combinations with only 2 "down" buttons that switched lamp 2 on. That suggested a pattern related to the middle buttons of the outer rows and columns. However that pattern didn't seem to hold up when also looking at the inputs with 3 "down" buttons. So I needed something more.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>I decided to turn to pivot tables (pun intended). That didn't gain me anything, though. I have only very rarely used pivot tables in Excel and now in LibreOffice Calc I failed to make a pivot table do anything useful. Back to using filters to make sense of lamp 2.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>To make that a little easier, I copied all inputs that result in lamp 2 switching on to a new sheet. Filtering the input combinations on 2 or 3 "down" buttons and counting how often each button was "down", showed a pattern. The count would be either 5, 6 or 15. And only the ones with count 15 play a role in the combinations with 2 "down" buttons. So I filter further, keeping only the combinations in which the inputs with count 15 are "up". And I am left with two input combinations: A1-B2-C3 and A3-B2-C1.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>On a hunch I decided to go back to the first filter result, while filtering out the two input combinations I just found. (Hence the "man filter" column in the sheet.) Looking at the counts, that leaves me with only two groups of inputs: the one with a count of 4 and with a count of 15. So it seems that hunch was a good one.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Then I look at all the input combinations in which button A2 is "down". If there are only two "down" buttons, these are either B1 or B3. And when there are three, either B1 or B3 are "down" as well.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":479} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp2-a2-spreadsheet.png" alt="" class="wp-image-479"></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Performing the same steps with B1, shows the same pattern, but with A2 and C2. Which means there are two types of input that switch lamp 2 on: (1) inputs of the pattern A2-B1|B3, and (2) inputs of the pattern A1-B2-C3.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>And that solves lamp 2: where lamp 3 and 4 are about the straight lines, lamp 2 covers the diagonals.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2><strong>Data analysis with pandas and seaborn</strong></h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>For the data analysis in Python I created a <a href="https://jupyter.org/">Jupyter notebook</a> - been wanting to look into these - which you can find <a href="https://github.com/j19sch/blackbox-puzzle-31/blob/master/puzzle31.ipynb">here</a> (rendered very nicely  by GitHub, btw). For analysis I used the <a href="https://pandas.pydata.org/">pandas</a> library, for visualization <a href="https://seaborn.pydata.org/">seaborn</a>.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>Visualizing a single input combination</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>After using pandas' dataframes to replicate some of the steps with the spreadsheet, I decided to "mis-use" seaborn's heatmap to visualize the two input combinations in which lamp 1 is on. That allowed me to figure out how to create a heatmap, and how it would be displayed in the notebook.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":460} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp1-heatmap1.png" alt="" class="wp-image-460"><figcaption>All buttons in the "up" state.</figcaption></figure>
<!-- /wp:image -->

<!-- wp:image {"id":461} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp1-heatmap2.png" alt="" class="wp-image-461"><figcaption>All buttons in the "down" state.</figcaption></figure>
<!-- /wp:image -->

<!-- wp:heading {"level":3} -->
<h3>Lamp state heatmap - attempt 1</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Now that I had an idea of how to create heatmaps, I decided to create one of all the input combinations that result in lamp 3 switching on.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":462} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp3on-heatmap.png" alt="" class="wp-image-462"><figcaption>Input combinations that result in lamp 3 being on.</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Obviously that didn't do me any good. To be honest, I couldn't quite believe my eyes, so I verified the result using the spreadsheet. It checked out. Thinking about it I realized that the input combinations could be sorted into three groups. And each group could be defined as: three buttons with the same number that are "down", combined with all possible combinations for the other buttons.  So basically all the noise drowns out any signal.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>Lamp state heatmap - attempt 2</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>I realized I had to filter the data in some way, so I decided to reduce the dataset to input combinations that resulted in only one of the lamps being switched on.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":463} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp1only-heatmap.png" alt="" class="wp-image-463"><figcaption>lamp 1 only - all on or all off</figcaption></figure>
<!-- /wp:image -->

<!-- wp:image {"id":464} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp2only-heatmap.png" alt="" class="wp-image-464"><figcaption>lamp 2 only - diagonals</figcaption></figure>
<!-- /wp:image -->

<!-- wp:image {"id":465} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp3only-heatmap.png" alt="" class="wp-image-465"><figcaption>lamp 3 only - verticals</figcaption></figure>
<!-- /wp:image -->

<!-- wp:image {"id":466} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp4only-heatmap.png" alt="" class="wp-image-466"><figcaption>lamp 4 only - horizontals</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>You could say that the lamp 2 heatmap suggests a diagonal pattern, lamp 3 a vertical one, and lamp 4 a horizontal pattern. However, it's not really clear cut. If I hadn't known the solution, I'm not sure what I would have concluded from these heatmaps.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>lamp state heatmap - interlude</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>By now I had figured out I needed to find a way to analyse the correlation between different inputs - instead of throwing all inputs and outputs on one big pile.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>After some googling I found that I could use pandas' <a href="https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.size.html">size()</a> on the result of a <a href="https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.groupby.html#pandas.DataFrame.groupby">DataFrame.groupby()</a> to get more insight into these correlations. As you can see below, if I group by A1-A2-A3, I can see how often each unique combination of values of A1-A2-A3, occur in a dataset.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>So I took the dataset that only switches lamp 4 on and grouped by A1-A2-A3, A1-B1-C1 and A1-B2-C3. The first two you can see below. The third one you can find in the <a href="https://github.com/j19sch/blackbox-puzzle-31/blob/master/puzzle31.ipynb">notebook</a>; it's very similar to the second one.</p>
<!-- /wp:paragraph -->

<!-- wp:code -->
<pre class="wp-block-code"><code>A1  A2  A3               A1  B1  C1
0   0   0     6          0   0   1     5
        1     2              1   0     3
    1   0     1                  1     2
        1     1          1   0   0     5
1   0   0     2                  1     7
        1     2              1   0     2
    1   0     1
        1     9</code></pre>
<!-- /wp:code -->

<!-- wp:paragraph -->
<p>I noticed two things. Firstly, the A1-A2-A3 result seems to adhere to some logic, while the A1-B1-C1 looks more random. Secondly, the A1-A2-A3 grouping contains input combinations in which all three buttons are "down" or "up". The other grouping does not.</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>lamp state heatmap - correlation</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Feeling I was on the right track, I started browsing the pandas documentation and there I found the solution: the <a href="https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.corr.html">DataFrame.corr()</a> method. It does exactly what I need it to do. You feed it all the input combinations that result in for example lamp 4 switching on and it calculates the correlation between the inputs.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>The result is a table, where a positive number indicates a positive linear correlation (highest is 1), zero indicates no correlation, and a negative number indicates a negative linear correlation (lowest is -1).<br>Since we are looking for a positive correlation (buttons being either up or down together resulting in lamp 4 switching on), this table allows us to solve lamp 4. Anything with a positive number is part of the pattern for lamp 4.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":469} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp4-corr-table.png" alt="" class="wp-image-469"></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>And the pattern is even clearer in a heatmap:</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":470} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp4-corr-heatmap.png" alt="" class="wp-image-470"><figcaption>lamp 4 input correlation heatmap</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Since I was curious, I did the same for the dataset of input combinations in which only lamp 4 and none of the others are switched on. Interestingly, although the pattern is still visible, it is less clear. We need the full dataset with what I previously called "noise" to properly calculate the correlations.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":471} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp4only-corr-heatmap.png" alt="" class="wp-image-471"><figcaption>lamp 4 only input correlation heatmap</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Now let's look at the other three heatmaps. The one for lamp 3 shows a clear pattern similar to lamp 4.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":473} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp3-corr-heatmap.png" alt="" class="wp-image-473"><figcaption>lamp 3 input correlation heatmap</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>The correlation heatmap of lamp 1 shows a clear pattern, although it does look a bit weird because of the logic behind its behavior: all buttons either up or down.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":474} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp1-corr-heatmap.png" alt="" class="wp-image-474"><figcaption>lamp 1 input correlation heatmap</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>Finally, the heatmap of lamp 2 does show a clear enough pattern (focus on the positive versus negative numbers), but it doesn't jump out as much as with lamps 3 or 4.</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":475} -->
<figure class="wp-block-image"><img src="/2019/04/puzzle31-lamp2-corr-heatmap.png" alt="" class="wp-image-475"><figcaption>lamp 2 input correlation heatmap</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>I can think of two reasons for the pattern not to jump out as clearly.<br>First of all, there are two patterns in the data: diagonals of two "down" buttons and diagonals of three "down" buttons. Add to that all the different states the rest of the buttons can be in and you get a lot of noise.<br>Secondly, some of the correlations of the two "down" buttons pattern cancel each other out. You can see that in this heatmap showing the correlation between input combinations with max two "down" buttons switching lamp 2 on:</p>
<!-- /wp:paragraph -->

<!-- wp:image {"id":491,"width":547,"height":466} -->
<figure class="wp-block-image is-resized"><img src="/2019/04/puzzle31-lamp2-2downs-corr-heatmap-cropped-1.png" alt="" class="wp-image-491" width="547" height="466"><figcaption>lamp 2 input correlation heatmap - two "down" inputs (matplotlib render)</figcaption></figure>
<!-- /wp:image -->

<!-- wp:paragraph -->
<p>I don't think this heatmap is a really valid way of using correlation coefficients because of the limited dataset, but it still tells us something about the behavior of lamp 2.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>And that wraps that up: Puzzle 31 solved with Python data analysis.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2><strong>Closing thoughts</strong></h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Since I wasn't familiar with all the tools I was using, solving the Puzzle this way took a long time - literally hours. I'd be faster next time, of course, but finding the solution through exploring the GUI can be done in 5-10 minutes.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>I had a lot of fun trying to figure out how to get these tools to do what I wanted. So a big thank you to all the great people who built these tools.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>I still have a lot to learn on how to do data analysis well. For instance, when seeing the positive numbers in the correlation tables, I was like: "Puzzle solved!" It was only when writing this blog post, I dove a little deeper into what those numbers actually mean.<br></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Do not underestimate the power of spreadsheets. As Felienne Hermans says in her talk "<a href="https://www.youtube.com/watch?v=UJxXgugvXmE">How to teach programming and other things?</a>" (great talk, go watch when you're done here) at <a href="https://youtu.be/UJxXgugvXmE?t=325">5:25</a>: </p>
<!-- /wp:paragraph -->

<!-- wp:quote -->
<blockquote class="wp-block-quote"><p>Excel is an amazing programming language that empowers 'normal people' to do programming in a variety of different domains in finance. And this became the motto of my PhD dissertation: "Spreadsheets are code." Spreadsheets are a valid means of programming.</p><p></p></blockquote>
<!-- /wp:quote -->

<!-- wp:paragraph -->
<p>In that light it was interesting to notice how a Jupyter notebook is basically a spreadsheet on steroids.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Something that wasn't as fun as I had hoped, was solving the Puzzle with Python. I didn't have the expected eureka-feeling when I saw how the correlation heatmaps provided the solution. Ok, it was the end of a tiring day and I knew the solution beforehand, but still.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Writing this blog post made me realize how my decisions while doing the data analysis were informed by me already knowing the solution. To give one very basic example: I knew that putting buttons in their "down" state made the lamps switch on. So from the start the focus of my data analysis was: "What input combinations make the lights switch on?"</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>So if I hadn't known the GUI and the solution, I think we could have seen a clearer difference between my data analysis approaches and a GUI approach. Instead of having the mental representation of 9 buttons in a 3x3 grid and 4 lamps, I would only have the data. 512 combinations of 9 binary inputs and 4 binary outputs. I would have found the patterns in the data and then... I'm not sure actually. Look at the GUI to see what the thing is that the data relates to?</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>I guess there's only one way to find out: next time James Lyndsay releases a Black Box Puzzle with an API, I am going API-first.</p>
<!-- /wp:paragraph --></body></html>