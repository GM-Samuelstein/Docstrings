<h1 align="center">Documenting Python Code: A Complete Guide</h1>

Welcome to your complete guide to documenting Python code. Whether you’re documenting a small script or a large project, whether you’re a beginner or a seasoned Pythonista, this guide will cover everything you need to know.

<h2 id="content">Content</h2>

<ol>
<li><a href="#01">Why Documenting Your Code Is So Important.</a></li>
<li><a href="#02">Commenting vs Documenting Code.</a></li>
<li><a href="#03">Documenting Your Python Code Base Using Docstrings.</a></li>
<li><a href="#04">Documenting Your Python Projects.</a></li>
</ol>

<p>Feel free to read through this tutorial from beginning to end or jump to a section you’re interested in. It was designed to work both ways.</p>

<h2 id="01">Why Documenting Your Code Is So Important.</h2>
<h6><a href="#content">Back to Contents.</h6>

<p>Hopefully, if you&rsquo;re reading this tutorial, you already know the importance of documenting your code. But if not, then let me quote something Guido mentioned to me at a recent <a href="https://realpython.com/pycon-guide/">PyCon</a>:</p>
<blockquote>
<p>&ldquo;Code is more often read than written.&rdquo;</p>
<p>&mdash; <em>Guido van Rossum</em></p>
</blockquote>
<p>When you write code, you write it for two primary audiences: your users and your developers (including yourself). Both audiences are equally important. If you&rsquo;re like me, you&rsquo;ve probably opened up old codebases and wondered to yourself, &ldquo;What in the world was I thinking?&rdquo; If you&rsquo;re having a problem reading your own code, imagine what your users or other developers are experiencing when they&rsquo;re trying to use or contribute to your code.</p>
<p>Conversely, I&rsquo;m sure you&rsquo;ve run into a situation where you wanted to do something in Python and found what looks like a great library that can get the job done. However, when you start using the library, you look for examples, write-ups, or even official documentation on how to do something specific and can&rsquo;t immediately find the solution.</p>
<p>After searching, you come to realize that the documentation is lacking or even worse, missing entirely. This is a frustrating feeling that deters you from using the library, no matter how great or efficient the code is. Daniele Procida summarized this situation best:</p>
<blockquote>
<p>&ldquo;It doesn&rsquo;t matter how good your software is, because <strong>if the documentation is not good enough, people will not use it.</strong>&ldquo;</p>
<p>&mdash; <em><a href="https://www.divio.com/en/blog/documentation/">Daniele Procida</a></em></p>
</blockquote>
<p>In this guide, you&rsquo;ll learn from the ground up how to properly document your Python code from the smallest of scripts to the largest of <a href="https://realpython.com/intermediate-python-project-ideas/">Python projects</a> to help prevent your users from ever feeling too frustrated to use or contribute to your project.</p>
<h6><a href="#content">Back to Contents.</h6>

<h2 id ="02">Commenting vs Documenting Code.</h2>
<h6><a href="#content">Back to Contents.</h6>

<p>Before we can go into how to document your Python code, we need to distinguish documenting from commenting.</p>
<p>In general, commenting is describing your code to/for developers. The intended main audience is the maintainers and developers of the Python code. In conjunction with well-written code, comments help to guide the reader to better understand your code and its purpose and design:</p>
<blockquote>
<p>&ldquo;Code tells you how; Comments tell you why.&rdquo;</p>
<p>&mdash; <em><a href="https://blog.codinghorror.com/code-tells-you-how-comments-tell-you-why/">Jeff Atwood</a> (aka Coding Horror)</em></p>
</blockquote>
<p>Documenting code is describing its use and functionality to your users. While it may be helpful in the development process, the main intended audience is the users. The following section describes how and when to comment your code.</p>
<section class="section3" id="basics-of-commenting-code"><h3>Basics of Commenting Code<a class="headerlink" href="#basics-of-commenting-code" title="Permanent link"></a></h3>
<p>Comments are created in Python using the pound sign (<code>#</code>) and should be brief statements no longer than a few sentences. Here&rsquo;s a simple example:</p>
<div class="highlight python"><pre><span></span><code><span class="k">def</span> <span class="nf">hello_world</span><span class="p">():</span>
    <span class="c1"># A simple comment preceding a simple print statement</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Hello World&quot;</span><span class="p">)</span>
</code></pre></div>
<p>According to <a href="http://pep8.org/#maximum-line-length">PEP 8</a>, comments should have a maximum length of 72 characters. This is true even if your project changes the max line length to be greater than the recommended 80 characters. If a comment is going to be greater than the comment char limit, using multiple lines for the comment is appropriate:</p>
<div class="highlight python"><pre><span></span><code><span class="k">def</span> <span class="nf">hello_long_world</span><span class="p">():</span>
    <span class="c1"># A very long statement that just goes on and on and on and on and</span>
    <span class="c1"># never ends until after it&#39;s reached the 80 char limit</span>
    <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;Hellooooooooooooooooooooooooooooooooooooooooooooooooooooooo World&quot;</span><span class="p">)</span>
</code></pre></div>
<p>Commenting your code serves <a href="https://en.wikipedia.org/wiki/Comment_(computer_programming)#Uses">multiple purposes, including</a>:</p>
<ul>
<li>
<p><strong>Planning and Reviewing:</strong> When you are developing new portions of your code, it may be appropriate to first use comments as a way of planning or outlining that section of code. Remember to remove these comments once the actual coding has been implemented and reviewed/tested:</p>
<div class="highlight python"><pre><span></span><code><span class="c1"># First step</span>
<span class="c1"># Second step</span>
<span class="c1"># Third step</span>
</code></pre></div>
</li>
<li>
<p><strong>Code Description:</strong> Comments can be used to explain the intent of specific sections of code:</p>
<div class="highlight python"><pre><span></span><code><span class="c1"># Attempt a connection based on previous settings. If unsuccessful,</span>
<span class="c1"># prompt user for new settings.</span>
</code></pre></div>
</li>
<li>
<p><strong>Algorithmic Description:</strong> When algorithms are used, especially complicated ones, it can be useful to explain how the algorithm works or how it&rsquo;s implemented within your code. It may also be appropriate to describe why a specific algorithm was selected over another.</p>
<div class="highlight python"><pre><span></span><code><span class="c1"># Using quick sort for performance gains</span>
</code></pre></div>
</li>
<li>
<p><strong>Tagging:</strong> The use of tagging can be used to label specific sections of code where known issues or areas of improvement are located. Some examples are: <code>BUG</code>, <code>FIXME</code>, and <code>TODO</code>.</p>
<div class="highlight python"><pre><span></span><code><span class="c1"># TODO: Add condition for when val is None</span>
</code></pre></div>
</li>
</ul>
<p>Comments to your code should be kept brief and focused. Avoid using long comments when possible. Additionally, you should use the following four essential rules as <a href="https://blog.codinghorror.com/when-good-comments-go-bad/">suggested by Jeff Atwood</a>:</p>
<ol>
<li>
<p>Keep comments as close to the code being described as possible. Comments that aren&rsquo;t near their describing code are frustrating to the reader and easily missed when updates are made.</p>
</li>
<li>
<p>Don&rsquo;t use complex formatting (such as tables or ASCII figures). Complex formatting leads to distracting content and can be difficult to maintain over time.</p>
</li>
<li>
<p>Don&rsquo;t include redundant information. Assume the reader of the code has a basic understanding of programming principles and language syntax.</p>
</li>
<li>
<p>Design your code to comment itself. The easiest way to understand code is by reading it. When you design your code using clear, easy-to-understand concepts, the reader will be able to quickly conceptualize your intent.</p>
</li>
</ol>
<p>Remember that comments are designed for the reader, including yourself, to help guide them in understanding the purpose and design of the software.</p>
</section><section class="section3" id="commenting-code-via-type-hinting-python-35"><h3>Commenting Code via Type Hinting (Python 3.5+)<a class="headerlink" href="#commenting-code-via-type-hinting-python-35" title="Permanent link"></a></h3>
<p>Type hinting was added to Python 3.5 and is an additional form to help the readers of your code. In fact, it takes Jeff&rsquo;s fourth suggestion from above to the next level. It allows the developer to design and explain portions of their code without commenting. Here&rsquo;s a quick example:</p>
<div class="highlight python"><pre><span></span><code><span class="k">def</span> <span class="nf">hello_name</span><span class="p">(</span><span class="n">name</span><span class="p">:</span> <span class="nb">str</span><span class="p">)</span> <span class="o">-&gt;</span> <span class="nb">str</span><span class="p">:</span>
    <span class="k">return</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;Hello </span><span class="si">{</span><span class="n">name</span><span class="si">}</span><span class="s2">&quot;</span><span class="p">)</span>
</code></pre></div>
<p>From examining the type hinting, you can immediately tell that the function expects the input <code>name</code> to be of a type <code>str</code>, or <a href="https://realpython.com/python-strings/">string</a>. You can also tell that the expected output of the function will be of a type <code>str</code>, or string, as well. While type hinting helps reduce comments, take into consideration that doing so may also make extra work when you are creating or updating your project documentation.</p>
<p>You can learn more about type hinting and type checking from <a href="https://www.youtube.com/watch?v=2xWhaALHTvU">this video created by Dan Bader</a>.</p>

<h6><a href="#content">Back to Contents.</h6>

<h2 id ="03">Documenting Your Python Code Base Using Docstrings.</h2>
<h6><a href="#content">Back to Contents.</h6>

<h6><a href="#content">Back to Contents.</h6>

<h2 id ="04">Documenting Your Python Projects.</h2>
<h6><a href="#content">Back to Contents.</h6>

<h6><a href="#content">Back to Contents.</h6>