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

<p>Now that we&rsquo;ve learned about commenting, let&rsquo;s take a deep dive into documenting a Python code base. In this section, you&rsquo;ll learn about docstrings and how to use them for documentation. This section is further divided into the following sub-sections:</p>
<ol>
<li><strong><a href="#docstrings-background">Docstrings Background</a>:</strong> A background on how docstrings work internally within Python</li>
<li><strong><a href="#docstring-types">Docstring Types</a>:</strong> The various docstring &ldquo;types&rdquo; (function, class, class method, <a href="https://realpython.com/python-modules-packages/">module, package</a>, and script)</li>
<li><strong><a href="#docstring-formats">Docstring Formats</a>:</strong> The different docstring &ldquo;formats&rdquo; (Google, NumPy/SciPy, reStructuredText, and Epytext)</li>
</ol>
<section class="section3" id="docstrings-background"><h3>Docstrings Background<a class="headerlink" href="#docstrings-background" title="Permanent link"></a></h3>
<p>Documenting your Python code is all centered on docstrings. These are built-in strings that, when configured correctly, can help your users and yourself with your project&rsquo;s documentation. Along with docstrings, Python also has the built-in function <code>help()</code> that prints out the objects docstring to the console. Here&rsquo;s a quick example:</p>
<div class="highlight python repl"><span class="repl-toggle" title="Toggle REPL prompts and output">&gt;&gt;&gt;</span><pre><span></span><code><span class="gp">&gt;&gt;&gt; </span><span class="n">help</span><span class="p">(</span><span class="nb">str</span><span class="p">)</span>
<span class="go">Help on class str in module builtins:</span>

<span class="go">class str(object)</span>
<span class="go"> |  str(object=&#39;&#39;) -&gt; str</span>
<span class="go"> |  str(bytes_or_buffer[, encoding[, errors]]) -&gt; str</span>
<span class="go"> |</span>
<span class="go"> |  Create a new string object from the given object. If encoding or</span>
<span class="go"> |  errors are specified, then the object must expose a data buffer</span>
<span class="go"> |  that will be decoded using the given encoding and error handler.</span>
<span class="go"> |  Otherwise, returns the result of object.__str__() (if defined)</span>
<span class="go"> |  or repr(object).</span>
<span class="go"> |  encoding defaults to sys.getdefaultencoding().</span>
<span class="go"> |  errors defaults to &#39;strict&#39;.</span>
<span class="go"> # Truncated for readability</span>
</code></pre></div>
<p>How is this output generated?  Since everything in Python is an object, you can examine the directory of the object using the <code>dir()</code> command. Let&rsquo;s do that and see what find:</p>
<div class="highlight python repl"><span class="repl-toggle" title="Toggle REPL prompts and output">&gt;&gt;&gt;</span><pre><span></span><code><span class="gp">&gt;&gt;&gt; </span><span class="nb">dir</span><span class="p">(</span><span class="nb">str</span><span class="p">)</span>
<span class="go">[&#39;__add__&#39;, ..., &#39;__doc__&#39;, ..., &#39;zfill&#39;] # Truncated for readability</span>
</code></pre></div>
<p>Within that directory output, there&rsquo;s an interesting property, <code>__doc__</code>. If you examine that property, you&rsquo;ll discover this:</p>
<div class="highlight python repl"><span class="repl-toggle" title="Toggle REPL prompts and output">&gt;&gt;&gt;</span><pre><span></span><code><span class="gp">&gt;&gt;&gt; </span><span class="nb">print</span><span class="p">(</span><span class="nb">str</span><span class="o">.</span><span class="vm">__doc__</span><span class="p">)</span>
<span class="go">str(object=&#39;&#39;) -&gt; str</span>
<span class="go">str(bytes_or_buffer[, encoding[, errors]]) -&gt; str</span>

<span class="go">Create a new string object from the given object. If encoding or</span>
<span class="go">errors are specified, then the object must expose a data buffer</span>
<span class="go">that will be decoded using the given encoding and error handler.</span>
<span class="go">Otherwise, returns the result of object.__str__() (if defined)</span>
<span class="go">or repr(object).</span>
<span class="go">encoding defaults to sys.getdefaultencoding().</span>
<span class="go">errors defaults to &#39;strict&#39;.</span>
</code></pre></div>
<p>Voilà! You&rsquo;ve found where docstrings are stored within the object. This means that you can directly manipulate that property. However, there are restrictions for builtins:</p>
<div class="highlight python repl"><span class="repl-toggle" title="Toggle REPL prompts and output">&gt;&gt;&gt;</span><pre><span></span><code><span class="gp">&gt;&gt;&gt; </span><span class="nb">str</span><span class="o">.</span><span class="vm">__doc__</span> <span class="o">=</span> <span class="s2">&quot;I&#39;m a little string doc! Short and stout; here is my input and print me for my out&quot;</span>
<span class="gt">Traceback (most recent call last):</span>
  File <span class="nb">&quot;&lt;stdin&gt;&quot;</span>, line <span class="m">1</span>, in <span class="n">&lt;module&gt;</span>
<span class="gr">TypeError</span>: <span class="n">can&#39;t set attributes of built-in/extension type &#39;str&#39;</span>
</code></pre></div>
<p>Any other custom object can be manipulated:</p>
<div class="highlight python"><pre><span></span><code><span class="k">def</span> <span class="nf">say_hello</span><span class="p">(</span><span class="n">name</span><span class="p">):</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;Hello </span><span class="si">{</span><span class="n">name</span><span class="si">}</span><span class="s2">, is it me you&#39;re looking for?&quot;</span><span class="p">)</span>

<span class="n">say_hello</span><span class="o">.</span><span class="vm">__doc__</span> <span class="o">=</span> <span class="s2">&quot;A simple function that says hello... Richie style&quot;</span>
</code></pre></div>
<div class="highlight python repl"><span class="repl-toggle" title="Toggle REPL prompts and output">&gt;&gt;&gt;</span><pre><span></span><code><span class="gp">&gt;&gt;&gt; </span><span class="n">help</span><span class="p">(</span><span class="n">say_hello</span><span class="p">)</span>
<span class="go">Help on function say_hello in module __main__:</span>

<span class="go">say_hello(name)</span>
<span class="go">    A simple function that says hello... Richie style</span>
</code></pre></div>
<p>Python has one more feature that simplifies docstring creation. Instead of directly manipulating the <code>__doc__</code> property, the strategic placement of the string literal directly below the object will automatically set the <code>__doc__</code> value. Here&rsquo;s what happens with the same example as above:</p>
<div class="highlight python"><pre><span></span><code><span class="k">def</span> <span class="nf">say_hello</span><span class="p">(</span><span class="n">name</span><span class="p">):</span>
    <span class="sd">&quot;&quot;&quot;A simple function that says hello... Richie style&quot;&quot;&quot;</span>
    <span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;Hello </span><span class="si">{</span><span class="n">name</span><span class="si">}</span><span class="s2">, is it me you&#39;re looking for?&quot;</span><span class="p">)</span>
</code></pre></div>
<div class="highlight python repl"><span class="repl-toggle" title="Toggle REPL prompts and output">&gt;&gt;&gt;</span><pre><span></span><code><span class="gp">&gt;&gt;&gt; </span><span class="n">help</span><span class="p">(</span><span class="n">say_hello</span><span class="p">)</span>
<span class="go">Help on function say_hello in module __main__:</span>

<span class="go">say_hello(name)</span>
<span class="go">    A simple function that says hello... Richie style</span>
</code></pre></div>
<p>There you go! Now you understand the background of docstrings. Now it&rsquo;s time to learn about the different types of docstrings and what information they should contain.</p>
</section><section class="section3" id="docstring-types"><h3>Docstring Types<a class="headerlink" href="#docstring-types" title="Permanent link"></a></h3>
<p>Docstring conventions are described within <a href="https://www.python.org/dev/peps/pep-0257/">PEP 257</a>. Their purpose is to provide your users with a brief overview of the object. They should be kept concise enough to be easy to maintain but still be elaborate enough for new users to understand their purpose and how to use the documented object.</p>
<p>In all cases, the docstrings should use the triple-double quote (<code>"""</code>) string format. This should be done whether the docstring is multi-lined or not. At a bare minimum, a docstring should be a quick summary of whatever is it you&rsquo;re describing and should be contained within a single line:</p>
<div class="highlight python"><pre><span></span><code><span class="sd">&quot;&quot;&quot;This is a quick summary line used as a description of the object.&quot;&quot;&quot;</span>
</code></pre></div>
<p>Multi-lined docstrings are used to further elaborate on the object beyond the summary. All multi-lined docstrings have the following parts:</p>
<ul>
<li>A one-line summary line</li>
<li>A blank line proceeding the summary</li>
<li>Any further elaboration for the docstring</li>
<li>Another blank line</li>
</ul>
    
<div class="highlight python"><pre><span></span><code><span class="sd">&quot;&quot;&quot;This is the summary line.</span>
<br />
<span class="sd">This is the further elaboration of the docstring. Within this section,</span>
<span class="sd">you can elaborate further on details as appropriate for the situation.</span>
<span class="sd">Notice that the summary and the elaboration is separated by a blank new</span>
<span class="sd">line.</span>
<span class="sd">&quot;&quot;&quot;</span>
<br />
<span class="c1"># Notice the blank line above. Code should continue on this line.</span>
</code></pre></div>
<p>All docstrings should have the same max character length as comments (72 characters). Docstrings can be further broken up into three major categories:</p>
<ul>
<li><strong>Class Docstrings:</strong> Class and class methods</li>
<li><strong>Package and Module Docstrings:</strong> Package, modules, and functions</li>
<li><strong>Script Docstrings:</strong> Script and functions</li>
</ul>
<section class="section4" id="class-docstrings"><h4>Class Docstrings<a class="headerlink" href="#class-docstrings" title="Permanent link"></a></h4>
<p>Class Docstrings are created for the class itself, as well as any class methods. The docstrings are placed immediately following the class or class method indented by one level:</p>

<pre><code>
class SimpleClass:
    """Class docstrings go here."""

    def say_hello(self, name: str):
        """Class method docstrings go here."""

        print(f'Hello {name}')

</code></pre>

<p>Class docstrings should contain the following information:</p>
<ul>
<li>A brief summary of its purpose and behavior</li>
<li>Any public methods, along with a brief description</li>
<li>Any class properties (attributes)</li>
<li>Anything related to the <a href="https://realpython.com/python-interface/">interface</a> for subclassers, if the class is intended to be subclassed </li>
</ul>
<p>The <a href="https://realpython.com/python-class-constructor/">class constructor</a> parameters should be documented within the <code>__init__</code> class method docstring. Individual methods should be documented using their individual docstrings. Class method docstrings should contain the following:</p>
<ul>
<li>A brief description of what the method is and what it&rsquo;s used for</li>
<li>Any arguments (both required and optional) that are passed including keyword arguments</li>
<li>Label any arguments that are considered optional or have a default value</li>
<li>Any side effects that occur when executing the method</li>
<li>Any exceptions that are raised</li>
<li>Any restrictions on when the method can be called</li>
</ul>
<p>Let&rsquo;s take a simple example of a data class that represents an Animal. This class will contain a few class properties, instance properties, a <code>__init__</code>, and a single <a href="https://realpython.com/instance-class-and-static-methods-demystified/">instance method</a>:</p>
<div class="highlight python"><pre><span></span><code><span class="k">class</span> <span class="nc">Animal</span><span class="p">:</span>
    <span class="sd">&quot;&quot;&quot;</span>
<span class="sd">    A class used to represent an Animal</span>

<span class="sd">    ...</span>

<span class="sd">    Attributes</span>
<span class="sd">    ----------</span>
<span class="sd">    says_str : str</span>
<span class="sd">        a formatted string to print out what the animal says</span>
<span class="sd">    name : str</span>
<span class="sd">        the name of the animal</span>
<span class="sd">    sound : str</span>
<span class="sd">        the sound that the animal makes</span>
<span class="sd">    num_legs : int</span>
<span class="sd">        the number of legs the animal has (default 4)</span>

<span class="sd">    Methods</span>
<span class="sd">    -------</span>
<span class="sd">    says(sound=None)</span>
<span class="sd">        Prints the animals name and what sound it makes</span>
<span class="sd">    &quot;&quot;&quot;</span>

   <span class="n">says_str</span> <span class="o">=</span> <span class="s2">&quot;A </span><span class="si">{name}</span><span class="s2"> says </span><span class="si">{sound}</span><span class="s2">&quot;</span>

   <span class="k">def</span> <span class="fm">__init__</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">name</span><span class="p">,</span> <span class="n">sound</span><span class="p">,</span> <span class="n">num_legs</span><span class="o">=</span><span class="mi">4</span><span class="p">):</span>
        <span class="sd">&quot;&quot;&quot;</span>
<span class="sd">        Parameters</span>
<span class="sd">        ----------</span>
<span class="sd">        name : str</span>
<span class="sd">            The name of the animal</span>
<span class="sd">        sound : str</span>
<span class="sd">            The sound the animal makes</span>
<span class="sd">        num_legs : int, optional</span>
<span class="sd">            The number of legs the animal (default is 4)</span>
<span class="sd">        &quot;&quot;&quot;</span>

<span class="bp">self</span><span class="o">.</span><span class="n">name</span> <span class="o">=</span> <span class="n">name</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">sound</span> <span class="o">=</span> <span class="n">sound</span>
        <span class="bp">self</span><span class="o">.</span><span class="n">num_legs</span> <span class="o">=</span> <span class="n">num_legs</span>

<span class="k">def</span> <span class="nf">says</span><span class="p">(</span><span class="bp">self</span><span class="p">,</span> <span class="n">sound</span><span class="o">=</span><span class="kc">None</span><span class="p">):</span>
        <span class="sd">&quot;&quot;&quot;Prints what the animals name is and what sound it makes.</span>

<span class="sd">        If the argument `sound` isn&#39;t passed in, the default Animal</span>
<span class="sd">        sound is used.</span>

<span class="sd">        Parameters</span>
<span class="sd">        ----------</span>
<span class="sd">        sound : str, optional</span>
<span class="sd">            The sound the animal makes (default is None)</span>

<span class="sd">        Raises</span>
<span class="sd">        ------</span>
<span class="sd">        NotImplementedError</span>
<span class="sd">            If no sound is set for the animal or passed in as a</span>
<span class="sd">            parameter.</span>
<span class="sd">        &quot;&quot;&quot;</span>

<span class="k">if</span> <span class="bp">self</span><span class="o">.</span><span class="n">sound</span> <span class="ow">is</span> <span class="kc">None</span> <span class="ow">and</span> <span class="n">sound</span> <span class="ow">is</span> <span class="kc">None</span><span class="p">:</span>
            <span class="k">raise</span> <span class="ne">NotImplementedError</span><span class="p">(</span><span class="s2">&quot;Silent Animals are not supported!&quot;</span><span class="p">)</span>

<span class="n">out_sound</span> <span class="o">=</span> <span class="bp">self</span><span class="o">.</span><span class="n">sound</span> <span class="k">if</span> <span class="n">sound</span> <span class="ow">is</span> <span class="kc">None</span> <span class="k">else</span> <span class="n">sound</span>
        <span class="nb">print</span><span class="p">(</span><span class="bp">self</span><span class="o">.</span><span class="n">says_str</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">name</span><span class="o">=</span><span class="bp">self</span><span class="o">.</span><span class="n">name</span><span class="p">,</span> <span class="n">sound</span><span class="o">=</span><span class="n">out_sound</span><span class="p">))</span>
</code></pre></div>
</section><section class="section4" id="package-and-module-docstrings"><h4>Package and Module Docstrings<a class="headerlink" href="#package-and-module-docstrings" title="Permanent link"></a></h4>
<p>Package docstrings should be placed at the top of the package&rsquo;s <code>__init__.py</code> file. This docstring should list the modules and sub-packages that are exported by the package.</p>
<p>Module docstrings are similar to class docstrings. Instead of classes and class methods being documented, it&rsquo;s now the module and any functions found within. Module docstrings are placed at the top of the file even before any imports. Module docstrings should include the following:</p>
<ul>
<li>A brief description of the module and its purpose</li>
<li>A list of any classes, exception, functions, and any other objects exported by the module</li>
</ul>
<p>The docstring for a module function should include the same items as a class method:</p>
<ul>
<li>A brief description of what the function is and what it&rsquo;s used for</li>
<li>Any arguments (both required and optional) that are passed including keyword arguments</li>
<li>Label any arguments that are considered optional</li>
<li>Any side effects that occur when executing the function</li>
<li>Any exceptions that are raised</li>
<li>Any restrictions on when the function can be called</li>
</ul>
</section><section class="section4" id="script-docstrings"><h4>Script Docstrings<a class="headerlink" href="#script-docstrings" title="Permanent link"></a></h4>
<p>Scripts are considered to be single file executables run from the console. Docstrings for scripts are placed at the top of the file and should be documented well enough for users to be able to have a sufficient understanding of how to use the script. It should be usable for its &ldquo;usage&rdquo; message, when the user incorrectly passes in a parameter or uses the <code>-h</code> option.</p>
<p>If you use <a href="https://realpython.com/command-line-interfaces-python-argparse/"><code>argparse</code></a>, then you can omit parameter-specific documentation, assuming it&rsquo;s correctly been documented within the <code>help</code> parameter of the <code>argparser.parser.add_argument</code> function. It is recommended to use the <code>__doc__</code> for the <code>description</code> parameter within <code>argparse.ArgumentParser</code>&rsquo;s constructor. Check out our tutorial on <a href="https://realpython.com/comparing-python-command-line-parsing-libraries-argparse-docopt-click/">Command-Line Parsing Libraries</a> for more details on how to use <code>argparse</code> and other common command line parsers.</p>
<p>Finally, any custom or third-party imports should be listed within the docstrings to allow users to know which packages may be required for running the script. Here&rsquo;s an example of a script that is used to simply print out the column headers of a spreadsheet:</p>
<div class="highlight python"><pre><span></span><code><span class="sd">&quot;&quot;&quot;Spreadsheet Column Printer</span>

<span class="sd">This script allows the user to print to the console all columns in the</span>
<span class="sd">spreadsheet. It is assumed that the first row of the spreadsheet is the</span>
<span class="sd">location of the columns.</span>

<span class="sd">This tool accepts comma separated value files (.csv) as well as excel</span>
<span class="sd">(.xls, .xlsx) files.</span>

<span class="sd">This script requires that `pandas` be installed within the Python</span>
<span class="sd">environment you are running this script in.</span>

<span class="sd">This file can also be imported as a module and contains the following</span>
<span class="sd">functions:</span>

<span class="sd">    * get_spreadsheet_cols - returns the column headers of the file</span>
<span class="sd">    * main - the main function of the script</span>
<span class="sd">&quot;&quot;&quot;</span>

<span class="kn">import</span> <span class="nn">argparse</span>

<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>


<span class="k">def</span> <span class="nf">get_spreadsheet_cols</span><span class="p">(</span><span class="n">file_loc</span><span class="p">,</span> <span class="n">print_cols</span><span class="o">=</span><span class="kc">False</span><span class="p">):</span>
    <span class="sd">&quot;&quot;&quot;Gets and prints the spreadsheet&#39;s header columns</span>

<span class="sd">    Parameters</span>
<span class="sd">    ----------</span>
<span class="sd">    file_loc : str</span>
<span class="sd">        The file location of the spreadsheet</span>
<span class="sd">    print_cols : bool, optional</span>
<span class="sd">        A flag used to print the columns to the console (default is</span>
<span class="sd">        False)</span>

<span class="sd">    Returns</span>
<span class="sd">    -------</span>
<span class="sd">    list</span>
<span class="sd">        a list of strings used that are the header columns</span>
<span class="sd">    &quot;&quot;&quot;</span>

<span class="n">file_data</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_excel</span><span class="p">(</span><span class="n">file_loc</span><span class="p">)</span>
    <span class="n">col_headers</span> <span class="o">=</span> <span class="nb">list</span><span class="p">(</span><span class="n">file_data</span><span class="o">.</span><span class="n">columns</span><span class="o">.</span><span class="n">values</span><span class="p">)</span>

<span class="k">if</span> <span class="n">print_cols</span><span class="p">:</span>
        <span class="nb">print</span><span class="p">(</span><span class="s2">&quot;</span><span class="se">\n</span><span class="s2">&quot;</span><span class="o">.</span><span class="n">join</span><span class="p">(</span><span class="n">col_headers</span><span class="p">))</span>

<span class="k">return</span> <span class="n">col_headers</span>


<span class="k">def</span> <span class="nf">main</span><span class="p">():</span>
    <span class="n">parser</span> <span class="o">=</span> <span class="n">argparse</span><span class="o">.</span><span class="n">ArgumentParser</span><span class="p">(</span><span class="n">description</span><span class="o">=</span><span class="vm">__doc__</span><span class="p">)</span>
    <span class="n">parser</span><span class="o">.</span><span class="n">add_argument</span><span class="p">(</span>
        <span class="s1">&#39;input_file&#39;</span><span class="p">,</span>
        <span class="nb">type</span><span class="o">=</span><span class="nb">str</span><span class="p">,</span>
        <span class="n">help</span><span class="o">=</span><span class="s2">&quot;The spreadsheet file to pring the columns of&quot;</span>
    <span class="p">)</span>
    <span class="n">args</span> <span class="o">=</span> <span class="n">parser</span><span class="o">.</span><span class="n">parse_args</span><span class="p">()</span>
    <span class="n">get_spreadsheet_cols</span><span class="p">(</span><span class="n">args</span><span class="o">.</span><span class="n">input_file</span><span class="p">,</span> <span class="n">print_cols</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>


<span class="k">if</span> <span class="vm">__name__</span> <span class="o">==</span> <span class="s2">&quot;__main__&quot;</span><span class="p">:</span>
    <span class="n">main</span><span class="p">()</span>
</code></pre></div>
</section></section><section class="section3" id="docstring-formats"><h3>Docstring Formats<a class="headerlink" href="#docstring-formats" title="Permanent link"></a></h3>
<p>You may have noticed that, throughout the examples given in this tutorial, there has been specific formatting with common elements: <code>Arguments</code>, <code>Returns</code>, and <code>Attributes</code>. There are specific docstrings formats that can be used to help docstring parsers and users have a familiar and known format. The formatting used within the examples in this tutorial are NumPy/SciPy-style docstrings. Some of the most common formats are the following:</p>
<div class="table-responsive">
<table class="table table-hover">
<thead>
<tr>
<th>Formatting Type</th>
<th>Description</th>
<th class="text-center">Supported by Sphynx</th>
<th class="text-center">Formal Specification</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://github.com/google/styleguide/blob/gh-pages/pyguide.md#38-comments-and-docstrings">Google docstrings</a></td>
<td>Google&rsquo;s recommended form of documentation</td>
<td class="text-center">Yes</td>
<td class="text-center">No</td>
</tr>
<tr>
<td><a href="http://docutils.sourceforge.net/rst.html">reStructuredText</a></td>
<td>Official Python documentation standard; Not beginner friendly but feature rich</td>
<td class="text-center">Yes</td>
<td class="text-center">Yes</td>
</tr>
<tr>
<td><a href="https://numpydoc.readthedocs.io/en/latest/format.html">NumPy/SciPy docstrings</a></td>
<td>NumPy&rsquo;s combination of reStructuredText and Google Docstrings</td>
<td class="text-center">Yes</td>
<td class="text-center">Yes</td>
</tr>
<tr>
<td><a href="http://epydoc.sourceforge.net/epytext.html">Epytext</a></td>
<td>A Python adaptation of Epydoc; Great for Java developers</td>
<td class="text-center">Not officially</td>
<td class="text-center">Yes</td>
</tr>
</tbody>
</table>
</div>
<p>The selection of the docstring format is up to you, but you should stick with the same format throughout your document/project. The following are examples of each type to give you an idea of how each documentation format looks.</p>
<section class="section4" id="google-docstrings-example"><h4>Google Docstrings Example<a class="headerlink" href="#google-docstrings-example" title="Permanent link"></a></h4>
<div class="highlight python"><pre><span></span><code><span class="sd">&quot;&quot;&quot;Gets and prints the spreadsheet&#39;s header columns</span>

<span class="sd">Args:</span>
<span class="sd">    file_loc (str): The file location of the spreadsheet</span>
<span class="sd">    print_cols (bool): A flag used to print the columns to the console</span>
<span class="sd">        (default is False)</span>

<span class="sd">Returns:</span>
<span class="sd">    list: a list of strings representing the header columns</span>
<span class="sd">&quot;&quot;&quot;</span>
</code></pre></div>
</section><section class="section4" id="restructuredtext-example"><h4>reStructuredText Example<a class="headerlink" href="#restructuredtext-example" title="Permanent link"></a></h4>
<div class="highlight python"><pre><span></span><code><span class="sd">&quot;&quot;&quot;Gets and prints the spreadsheet&#39;s header columns</span>

<span class="sd">:param file_loc: The file location of the spreadsheet</span>
<span class="sd">:type file_loc: str</span>
<span class="sd">:param print_cols: A flag used to print the columns to the console</span>
<span class="sd">    (default is False)</span>
<span class="sd">:type print_cols: bool</span>
<span class="sd">:returns: a list of strings representing the header columns</span>
<span class="sd">:rtype: list</span>
<span class="sd">&quot;&quot;&quot;</span>
</code></pre></div>
</section><section class="section4" id="numpyscipy-docstrings-example"><h4>NumPy/SciPy Docstrings Example<a class="headerlink" href="#numpyscipy-docstrings-example" title="Permanent link"></a></h4>
<div class="highlight python"><pre><span></span><code><span class="sd">&quot;&quot;&quot;Gets and prints the spreadsheet&#39;s header columns</span>

<span class="sd">Parameters</span>
<span class="sd">----------</span>
<span class="sd">file_loc : str</span>
<span class="sd">    The file location of the spreadsheet</span>
<span class="sd">print_cols : bool, optional</span>
<span class="sd">    A flag used to print the columns to the console (default is False)</span>

<span class="sd">Returns</span>
<span class="sd">-------</span>
<span class="sd">list</span>
<span class="sd">    a list of strings representing the header columns</span>
<span class="sd">&quot;&quot;&quot;</span>
</code></pre></div>
</section><section class="section4" id="epytext-example"><h4>Epytext Example<a class="headerlink" href="#epytext-example" title="Permanent link"></a></h4>
<div class="highlight python"><pre><span></span><code><span class="sd">&quot;&quot;&quot;Gets and prints the spreadsheet&#39;s header columns</span>

<span class="sd">@type file_loc: str</span>
<span class="sd">@param file_loc: The file location of the spreadsheet</span>
<span class="sd">@type print_cols: bool</span>
<span class="sd">@param print_cols: A flag used to print the columns to the console</span>
<span class="sd">    (default is False)</span>
<span class="sd">@rtype: list</span>
<span class="sd">@returns: a list of strings representing the header columns</span>
<span class="sd">&quot;&quot;&quot;</span>
</code></pre></div>
</section>

<h6><a href="#content">Back to Contents.</h6>

<h2 id ="04">Documenting Your Python Projects.</h2>
<h6><a href="#content">Back to Contents.</h6>

<p>Python projects come in all sorts of shapes, sizes, and purposes. The way you document your project should suit your specific situation. Keep in mind who the users of your project are going to be and adapt to their needs. Depending on the project type, certain aspects of documentation are recommended. The general <a href="https://realpython.com/python-application-layouts/">layout</a> of the project and its documentation should be as follows:</p>
<div class="highlight"><pre><span></span><code>project_root/
│
├── project/  # Project source code
├── docs/
├── README
├── HOW_TO_CONTRIBUTE
├── CODE_OF_CONDUCT
├── examples.py
</code></pre></div>
<p>Projects can be generally subdivided into three major types: Private, Shared, and Public/Open Source.</p>
<section class="section3" id="private-projects"><h3>Private Projects<a class="headerlink" href="#private-projects" title="Permanent link"></a></h3>
<p>Private projects are projects intended for personal use only and generally aren&rsquo;t shared with other users or developers. Documentation can be pretty light on these types of projects. There are some recommended parts to add as needed:</p>
<ul>
<li><strong>Readme:</strong> A brief summary of the project and its purpose. Include any special requirements for installation or operating the project.</li>
<li><strong><code>examples.py</code>:</strong> A Python script file that gives simple examples of how to use the project.</li>
</ul>
<p>Remember, even though private projects are intended for you personally, you are also considered a user. Think about anything that may be confusing to you down the road and make sure to capture those in either comments, docstrings, or the readme.</p>
</section>

<section class="section3" id="shared-projects"><h3>Shared Projects<a class="headerlink" href="#shared-projects" title="Permanent link"></a></h3>
<p>Shared projects are projects in which you collaborate with a few other people in the development and/or use of the project. The &ldquo;customer&rdquo; or user of the project continues to be yourself and those limited few that use the project as well.</p>
<p>Documentation should be a little more rigorous than it needs to be for a private project, mainly to help onboard new members to the project or alert contributors/users of new changes to the project. Some of the recommended parts to add to the project are the following:</p>
<ul>
<li><strong>Readme:</strong> A brief summary of the project and its purpose. Include any special requirements for installing or operating the project. Additionally, add any major changes since the previous version.</li>
<li><strong><code>examples.py</code>:</strong> A Python script file that gives simple examples of how to use the projects.</li>
<li><strong>How to Contribute:</strong> This should include how new contributors to the project can start contributing.</li>
</ul>
</section><section class="section3" id="public-and-open-source-projects"><h3>Public and Open Source Projects<a class="headerlink" href="#public-and-open-source-projects" title="Permanent link"></a></h3>
<p>Public and Open Source projects are projects that are intended to be shared with a large group of users and can involve large development teams. These projects should place as high of a priority on project documentation as the actual development of the project itself. Some of the recommended parts to add to the project are the following:</p>
<ul>
<li>
<p><strong>Readme:</strong> A brief summary of the project and its purpose. Include any special requirements for installing or operating the projects. Additionally, add any major changes since the previous version. Finally, add links to further documentation, bug reporting, and any other important information for the project. Dan Bader has put together <a href="https://dbader.org/blog/write-a-great-readme-for-your-github-project">a great tutorial</a> on what all should be included in your readme.</p>
</li>
<li>
<p><strong>How to Contribute:</strong> This should include how new contributors to the project can help. This includes developing new features, fixing known issues, adding documentation, adding new tests, or reporting issues.</p>
</li>
<li>
<p><strong>Code of Conduct:</strong> Defines how other contributors should treat each other when developing or using your software. This also states what will happen if this code is broken. If you&rsquo;re using Github, a Code of Conduct <a href="https://help.github.com/articles/adding-a-code-of-conduct-to-your-project/">template</a> can be generated with recommended wording. For Open Source projects especially, consider adding this.</p>
</li>
<li>
<p><strong>License:</strong> A plaintext file that describes the license your project is using. For Open Source projects especially, consider adding this.</p>
</li>
<li>
<p><strong>docs:</strong> A folder that contains further documentation. The next section describes more fully what should be included and how to organize the contents of this folder.</p>
</li>
</ul>
<section class="section4" id="the-four-main-sections-of-the-docs-folder"><h4>The Four Main Sections of the <code>docs</code> Folder<a class="headerlink" href="#the-four-main-sections-of-the-docs-folder" title="Permanent link"></a></h4>
<p>Daniele Procida gave a wonderful <a href="https://www.youtube.com/watch?v=azf6yzuJt54">PyCon 2017 talk</a> and subsequent <a href="https://www.divio.com/en/blog/documentation/">blog post</a> about documenting Python projects. He mentions that all projects should have the following four major sections to help you focus your work:</p>
<ul>
<li><strong>Tutorials</strong>: Lessons that take the reader by the hand through a series of steps to complete a project (or meaningful exercise). Geared towards the user&rsquo;s learning.</li>
<li><strong>How-To Guides</strong>: Guides that take the reader through the steps required to solve a common problem (problem-oriented recipes).</li>
<li><strong>References</strong>: Explanations that clarify and illuminate a particular topic. Geared towards understanding.</li>
<li><strong>Explanations</strong>: Technical descriptions of the machinery and how to operate it (key classes, functions, APIs, and so forth). Think Encyclopedia article.</li>
</ul>
<p>The following table shows how all of these sections relates to each other as well as their overall purpose:</p>
<div class="table-responsive">
<table class="table table-hover">
<thead>
<tr>
<th class="text-right"></th>
<th class="text-center">Most Useful When We&rsquo;re Studying</th>
<th class="text-center">Most Useful When We&rsquo;re Coding</th>
</tr>
</thead>
<tbody>
<tr>
<td class="text-right"><strong>Practical Step</strong></td>
<td class="text-center"><em>Tutorials</em></td>
<td class="text-center"><em>How-To Guides</em></td>
</tr>
<tr>
<td class="text-right"><strong>Theoretical Knowledge</strong></td>
<td class="text-center"><em>Explanation</em></td>
<td class="text-center"><em>Reference</em></td>
</tr>
</tbody>
</table>
</div>
<p>In the end, you want to make sure that your users have access to the answers to any questions they may have. By organizing your project in this manner, you&rsquo;ll be able to answer those questions easily and in a format they&rsquo;ll be able to navigate quickly.</p>
</section></section><section class="section3" id="documentation-tools-and-resources"><h3>Documentation Tools and Resources<a class="headerlink" href="#documentation-tools-and-resources" title="Permanent link"></a></h3>
<p>Documenting your code, especially large projects, can be daunting. Thankfully there are some tools out and references to get you started:</p>
<div class="table-responsive">
<table class="table table-hover">
<thead>
<tr>
<th>Tool</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="http://www.sphinx-doc.org/en/stable/">Sphinx</a></td>
<td>A collection of tools to auto-generate documentation in multiple formats</td>
</tr>
<tr>
<td><a href="http://epydoc.sourceforge.net/">Epydoc</a></td>
<td>A tool for generating API documentation for Python modules based on their docstrings</td>
</tr>
<tr>
<td><a href="https://readthedocs.org/">Read The Docs</a></td>
<td>Automatic building, versioning, and hosting of your docs for you</td>
</tr>
<tr>
<td><a href="https://www.doxygen.nl/manual/docblocks.html">Doxygen</a></td>
<td>A tool for generating documentation that supports Python as well as multiple other languages</td>
</tr>
<tr>
<td><a href="https://www.mkdocs.org/">MkDocs</a></td>
<td>A static site generator to help build project documentation using the Markdown language. Check out <a href="https://realpython.com/python-project-documentation-with-mkdocs/">Build Your Python Project Documentation With MkDocs</a> to learn more.</td>
</tr>
<tr>
<td><a href="https://pycco-docs.github.io/pycco/">pycco</a></td>
<td>A &ldquo;quick and dirty&rdquo; documentation generator that displays code and documentation side by side. Check out <a href="https://realpython.com/generating-code-documentation-with-pycco/">our tutorial on how to use it for more info</a>.</td>
</tr>
<tr>
<td><a href="https://docs.python.org/3/library/doctest.html"><code>doctest</code></a></td>
<td>A standard-library module for running usage examples as automated tests. Check out <a href="https://realpython.com/python-doctest/">Python&rsquo;s doctest: Document and Test Your Code at Once</a></td>
</tr>
</tbody>
</table>
</div>
<p>Along with these tools, there are some additional tutorials, videos, and articles that can be useful when you are documenting your project:</p>
<ol>
<li><a href="https://www.youtube.com/watch?v=0ROZRNZkPS8">Carol Willing - Practical Sphinx - PyCon 2018</a></li>
<li><a href="https://www.youtube.com/watch?v=bQSR1UpUdFQ">Daniele Procida - Documentation-driven development - Lessons from the Django Project - PyCon 2016</a></li>
<li><a href="https://www.youtube.com/watch?v=hM4I58TA72g">Eric Holscher - Documenting your project with Sphinx &amp; Read the Docs - PyCon 2016</a></li>
<li><a href="https://youtu.be/SUt3wT43AeM?t=6299">Titus Brown, Luiz Irber - Creating, building, testing, and documenting a Python project: a hands-on HOWTO - PyCon 2016</a></li>
<li><a href="http://docutils.sourceforge.net/rst.html">reStructuredText Official Documentation</a></li>
<li><a href="http://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html">Sphinx&rsquo;s reStructuredText Primer</a></li>
</ol>
<p>Sometimes, the best way to learn is to mimic others. Here are some great examples of projects that use documentation well:</p>
<ul>
<li><strong>Django:</strong> <a href="https://docs.djangoproject.com/en/2.0/">Docs</a> (<a href="https://github.com/django/django/tree/master/docs">Source</a>)</li>
<li><strong>Requests:</strong> <a href="https://requests.readthedocs.io/en/master/">Docs</a> (<a href="https://github.com/requests/requests/tree/master/docs">Source</a>)</li>
<li><strong>Click:</strong> <a href="http://click.pocoo.org/dev/">Docs</a> (<a href="https://github.com/pallets/click/tree/master/docs">Source</a>)</li>
<li><strong>Pandas:</strong> <a href="http://pandas.pydata.org/pandas-docs/stable/">Docs</a> (<a href="https://github.com/pandas-dev/pandas/tree/master/doc">Source</a>)</li>
</ul>
</section></section>

<h6><a href="#content">Back to Contents.</h6>
