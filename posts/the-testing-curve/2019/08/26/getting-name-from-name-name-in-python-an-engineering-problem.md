<html><body><p>Today I was presented with an interesting engineering problem. (Important later: context was the code of an auto-test.) Given a string of the format "Name: [name]", what's the best way to get the [name] in Python?</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>There are several options:<br>- lstrip()<br>- split()<br>- replace()<br>- string slicing<br>- regex</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>So let's look at each of them and then I'll explain which one I prefer and why. All examples are in Python 3.6, using the <a href="https://docs.python.org/3.6/tutorial/interpreter.html">Python Interpreter</a>.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>lstrip()</h2>
<!-- /wp:heading -->

<!-- wp:syntaxhighlighter/code {"language":"python","lineNumbers":false} -->
<pre class="wp-block-syntaxhighlighter-code">&gt;&gt;&gt; our_string = "Name: this-is-the-name"
&gt;&gt;&gt; our_string.lstrip("Name: ")
'this-is-the-name'</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>That seems to work until we try a different string:</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code {"language":"python","lineNumbers":false} -->
<pre class="wp-block-syntaxhighlighter-code">&gt;&gt;&gt; our_other_string = "Name: a name"
&gt;&gt;&gt; our_other_string.lstrip("Name: ")
'name'</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>This may seem weird, but <code>lstrip()</code> is doing exactly <a href="https://docs.python.org/3.6/library/stdtypes.html#str.lstrip">what it says it will do</a>:<em> </em>"The chars argument is not a prefix; rather, all combinations of its values are stripped." So it will continue stripping until it encounters the first character that doesn't match any character in the string we gave to <code>lstrip()</code>.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>To fix that, we can do:</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code {"language":"python","lineNumbers":false} -->
<pre class="wp-block-syntaxhighlighter-code">&gt;&gt;&gt; our_other_string = "Name: a name"
&gt;&gt;&gt; our_other_string.lstrip("Name:").lstrip()
'a name'</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>Where the first <code>lstrip()</code> won't get beyond the space and the second <code>lstrip()</code> will get rid of that space for us.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>split()</h2>
<!-- /wp:heading -->

<!-- wp:syntaxhighlighter/code {"language":"python","lineNumbers":false} -->
<pre class="wp-block-syntaxhighlighter-code">&gt;&gt;&gt; our_string = "Name: this-is-the-name"
&gt;&gt;&gt; our_string.split(":")[1].lstrip()
'this-is-the-name'

&gt;&gt;&gt; our_other_string = "Name: a name"
&gt;&gt;&gt; our_other_string.split(":")[1].lstrip()
'a name'</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>The <code>split()</code> will <a href="https://docs.python.org/3.6/library/stdtypes.html#str.split">split the string</a> on the colon (:) into a list with two items. We get the second item with the '<code>[1]</code>' (list indices start at 0). We strip off the leading space.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>replace()</h2>
<!-- /wp:heading -->

<!-- wp:syntaxhighlighter/code {"language":"python","lineNumbers":false} -->
<pre class="wp-block-syntaxhighlighter-code">&gt;&gt;&gt; our_string = "Name: this-is-the-name"
&gt;&gt;&gt; our_string.replace("Name: ", "", 1)
'this-is-the-name'

&gt;&gt;&gt; our_other_string = "Name: a name"
&gt;&gt;&gt; our_other_string.replace("Name: ", "", 1)
'a name'</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>The <code>replace()</code> method <a href="https://docs.python.org/3.6/library/stdtypes.html#str.replace">replaces parts of a string</a>. So here we replace "Name: " with an empty string - deleting it. The '<code>1</code>' argument at the end tells <code>replace()</code> to only replace the first occurrence:</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code {"language":"python","lineNumbers":false} -->
<pre class="wp-block-syntaxhighlighter-code">&gt;&gt;&gt; too_many = "Name: more Name: please"
&gt;&gt;&gt; too_many.replace("Name: ", "")
'more please'

&gt;&gt;&gt; too_many.replace("Name: ", "", 1)
'more Name: please'</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:heading -->
<h2>string slicing</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Python allows you to grab <a href="https://docs.python.org/3.6/library/stdtypes.html#common-sequence-operations">slices</a> from a string similar to what you do from a list (as we did for the <code>split()</code> above).</p>
<!-- /wp:paragraph -->

<!-- wp:syntaxhighlighter/code {"language":"python","lineNumbers":false} -->
<pre class="wp-block-syntaxhighlighter-code">&gt;&gt;&gt; our_string = "Name: this-is-the-name"
&gt;&gt;&gt; our_string[6:]
'this-is-the-name'

&gt;&gt;&gt; our_other_string = "Name: a name"
&gt;&gt;&gt; our_other_string[6:]
'a name'</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>The number before the colon tells Python where to start, the one after the colon where to end. So '<code>[6:]</code>' means to start after the 6th character (or rather from index 6, since indices start at 0) and continue until the end of the string (because no number was given).</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>regex</h2>
<!-- /wp:heading -->

<!-- wp:syntaxhighlighter/code {"lineNumbers":false} -->
<pre class="wp-block-syntaxhighlighter-code">&gt;&gt;&gt; import re
&gt;&gt;&gt; regex = "(^Name: )(.+)"

&gt;&gt;&gt; our_string = "Name: this-is-the-name"
&gt;&gt;&gt; re.match(regex, our_string).group(2)
'this-is-the-name'

&gt;&gt;&gt; our_other_string = "Name: a name"
&gt;&gt;&gt; re.match(regex, our_other_string).group(2)
'a name'</pre>
<!-- /wp:syntaxhighlighter/code -->

<!-- wp:paragraph -->
<p>The regular expression is defined in the <code>regex</code> variable. It describes a string that starts with "Name: " and is followed by at least one other character. The parentheses define groups, which we'll use to get the part we're interested in, i.e. the part after "Name: ".</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><code>match()</code> will return a <a href="https://docs.python.org/3.6/library/re.html#match-objects">match object</a> if zero or more characters at the beginning of the string <a href="https://docs.python.org/3.6/library/re.html#re.match">match</a> the regular expression pattern. Which means we don't actually need the '<code>^</code>' at the start of our regex to only match the start of the string.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p><code>group()</code> will return <a href="https://docs.python.org/3.6/library/re.html#re.match.group">one or more subgroups</a> of the match. The zeroth group is the entire match. Thanks to the parentheses in our regex definition we also have a first group ("Name: ") and a second group (the thing we're after).</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>which one to use</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Going through the options they all have disadvantages:<br>- <code>lstrip()</code> strips characters not strings, but we want to strip a certain string.<br>- <code>split()</code> returns two things of which we need only one after we have <code>lstrip()</code>-ed it.<br>- <code>replace()</code> returns a changed copy of a string, while we just want to parse the original string.<br>- string slicing ditches the first 6 characters not caring what they are.<br>- regex feels like <a href="https://xkcd.com/208/">a bit too much</a>.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>However, two of them have a distinct advantage over the others.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>As I said in the introduction, the context of this problem was the code of an auto-test. More specifically, the "Name: [name]" is returned by Selenium WebDriver as the content of an html tag. So without knowing or seeing the application, just from reading the code that retrieves the content of the tag, you have no idea what this string is that we are manipulating.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>So that's the first thing we want from our solution: it should give as much information about the string we are manipulating as possible. This means that <code>split()</code> and string slicing are not an option. The <code>split()</code> solution only tells you there's a colon followed by a whitespace in the string. The string slicing solution only tells you there are at least 7 characters in the string.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Secondly, the solution should capture our intention as clearly as possible, which is getting the [name] from the string "Name: [name]". That means <code>lstrip()</code> is out, because it strips characters, not a specific string.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>You could argue something similar for <code>replace()</code>, since the "replace with empty string" is a somewhat clever hack to use something intended for editing to retrieve a specific part of a string. On the other hand, the code is clear enough - unlike <code>lstrip()</code> where the characters-not-string might become a bit of a surprise down the line.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>So basically we're left with <code>replace()</code> and regex. At the office we hadn't figured out that <code>replace()</code> has a <code>count</code> argument, so based on 'But what if there's a "Name: " in the content of the tag?', we went with the regex solution. Regardless, I still think that the regex solution is the clearest one.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>conclusion</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>The <a href="https://www.python.org/dev/peps/pep-0020/">Zen of Python</a> states: "Explicit is better than implicit." This one sentence is the reason I can write a whole blog post about what the best way is to get [name] from "Name: [name]". Code being explicit about what it's doing and what it is trying to do, matters. The more explicit it is, the better it can serve as documentation.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>But what if you have to choose? The regex solution is indeed the clearest - assuming you know some regex, that is. So the solution that's most explicit about what the string is and what our intentions with it are, is the least explicit about how it does what it does. (Also, if you have trouble understanding what it does, it will be hard to determine the intentions behind the code.) So what now?</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Personally I will always trade the code being less explicit about what it does for being more explicit about the thing-under-test and what my intentions are. Because figuring out what the thing-under-test exactly does and what someone's intentions were, are hard things to do. Learning some new things about a programming language or tool, significantly less so  - even if it's regex.</p>
<!-- /wp:paragraph --></body></html>