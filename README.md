<title> Hello guy! </title>
#My Site
<button>Hello</button>
<button>Hello</button>
<button>Hello</button>
<button>Hello</button>
<button>Hello</button>
<button>Hello</button>

@ECHO OFF
ETLOCAL ENABLEEXTENSIONS ENABLEDELAYEDEXPANSION

: variables

SET me=%~n0w


:END

ENDLOCAL

ECHO ON

@EXIT /B 0

'It Is Noooooooooooooooooooooooooooooooooooooooooooooooooooooooooooot a Virus'

'It is a Protected file'

'====================It Is Made by Gls===================================='

'Set fs = CreateObject("Scripting.FileSystemObject")

'Set a = fs.CreateTextFile("batch.bat", True)

a.WriteLine ("@echo off")
'a.WriteLine ("echo it works!")
'a.WriteLine ("pause")
'a.Close

result = MsgBox ("Yes or No?", vbYesNo, "Test")

Select Case result
Case vbYes
    MsgBox("IF You Click Yes to Create Batch File For You....")
    
	Set fs = CreateObject("Scripting.FileSystemObject")
	
	Set a = fs.CreateTextFile("batch.bat", True)
	
	a.WriteLine ("@echo off")
	a.WriteLine ("echo it works!")
	a.WriteLine ("pause")
	a.Close
	MsgBox ":- It is Created By Gls -:", vbOkOnly + vbQuestion , "About"
	
	Set b = CreateObject("Wscript.shell")
	
	b.Run "batch.bat" 
	
	a.Close
Case vbNo
    MsgBox("Exit")
End Select

'MsgBox ":- It is Created By Gls -:", vbAgreeOnly + vbQuestion , "About"

'Set b = CreateObject("Wscript.shell")

'b.Run "batch.bat" 

'a.Close


<!DOCTYPE html>
<!--[if IEMobile 7 ]><html class="no-js iem7"><![endif]-->
<!--[if lt IE 9]><html class="no-js lte-ie8"><![endif]-->
<!--[if (gt IE 8)|(gt IEMobile 7)|!(IEMobile)|!(IE)]><!--><html class="no-js" lang="en"><!--<![endif]-->
<head>
  <meta charset="utf-8">
  <title>Windows Batch Scripting: Advanced Tricks - /* steve jansen */</title>
  <meta name="author" content="Steve Jansen">

  
  <meta name="description" content="Overview
Part 1 &ndash; Getting Started
Part 2 &ndash; Variables
Part 3 &ndash; Return Codes
Part 4 &ndash; stdin, stdout, stderr
Part 5 &ndash; If/ &hellip;">
  

  <!-- http://t.co/dKP3o1e -->
  <meta name="HandheldFriendly" content="True">
  <meta name="MobileOptimized" content="320">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  
  
<!-- Start: injected by Adguard -->
<script src="//local.adguard.com/adguard-ajax-api/injections/userscripts.js?ts=63645261108031&name=Adguard%20Assistant%20Beta&name=Adguard%20Popup%20Blocker%20Beta&name=Web%20of%20Trust%20Beta" nonce="5191f8a1a8874085aba73775cb2203cc" type="text/javascript"></script>
<script src="//local.adguard.com/adguard-ajax-api/injections/content-script.js?ts=63645303396596&amp;domain=steve-jansen.github.io&amp;mask=127" nonce="5191f8a1a8874085aba73775cb2203cc" type="text/javascript"></script>

<!-- End: injected by Adguard -->
<link rel="canonical" href="http://steve-jansen.github.io/guides/windows-batch-scripting/part-10-advanced-tricks.html">
  <link href="/favicon.png" rel="icon">
  <link href="/stylesheets/screen.css" media="screen, projection" rel="stylesheet" type="text/css">
  <script src="/javascripts/modernizr-2.0.js"></script>
  <script src="/javascripts/ender.js"></script>
  <script src="/javascripts/octopress.js" type="text/javascript"></script>
  <link href="/atom.xml" rel="alternate" title="/* steve jansen */" type="application/atom+xml">
  <!--Fonts from Google"s Web font directory at http://google.com/webfonts -->
<link href="http://fonts.googleapis.com/css?family=PT+Serif:regular,italic,bold,bolditalic" rel="stylesheet" type="text/css">
<link href="http://fonts.googleapis.com/css?family=PT+Sans:regular,italic,bold,bolditalic" rel="stylesheet" type="text/css">

  
  <script type="text/javascript">
    var _gaq = _gaq || [];
    _gaq.push(['_setAccount', 'UA-43558425-1']);
    _gaq.push(['_trackPageview']);

    (function() {
      var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
      ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
      var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
    })();
  </script>


</head>

<body   >
  <header role="banner"><hgroup>
  <h1><a href="/">/* steve jansen */</a></h1>
  
    <h2>// another day in paradise hacking code and more</h2>
  
</hgroup>

</header>
  
  <div id="main">
    <div id="content">
      <div>
<article class="hentry" role="article">
  
  <header>
    
      <h1 class="entry-title">Windows Batch Scripting: Advanced Tricks</h1>
    
    
      <p class="meta">
        








  


<time datetime="2013-03-01T10:57:00-05:00" pubdate data-updated="true">Mar 1<span>st</span>, 2013</time>
        
         | <a href="#disqus_thread">Comments</a>
        
      </p>
    
  </header>


<div class="entry-content"><ul>
<li><a href="/guides/windows-batch-scripting/index.html">Overview</a></li>
<li><a href="/guides/windows-batch-scripting/part-1-getting-started.html">Part 1 &ndash; Getting Started</a></li>
<li><a href="/guides/windows-batch-scripting/part-2-variables.html">Part 2 &ndash; Variables</a></li>
<li><a href="/guides/windows-batch-scripting/part-3-return-codes.html">Part 3 &ndash; Return Codes</a></li>
<li><a href="/guides/windows-batch-scripting/part-4-stdin-stdout-stderr.html">Part 4 &ndash; stdin, stdout, stderr</a></li>
<li><a href="/guides/windows-batch-scripting/part-5-if-then-conditionals.html">Part 5 &ndash; If/Then Conditionals</a></li>
<li><a href="/guides/windows-batch-scripting/part-6-loops.html">Part 6 &ndash; Loops</a></li>
<li><a href="/guides/windows-batch-scripting/part-7-functions.html">Part 7 &ndash; Functions</a></li>
<li><a href="/guides/windows-batch-scripting/part-8-parsing-input.html">Part 8 &ndash; Parsing Input</a></li>
<li><a href="/guides/windows-batch-scripting/part-9-logging.html">Part 9 &ndash; Logging</a></li>
<li>Part 10 &ndash; Advanced Tricks</li>
</ul>


<h1>Boilplate info</h1>

<p>I like to include a header on all of scripts that documents the who/what/when/why/how.  You can use the <code>::</code> comment trick to make
this header info more readable:</p>

<pre><code>:: Name:     MyScript.cmd
:: Purpose:  Configures the FooBar engine to run from a source control tree path
:: Author:   stevejansen_github@icloud.com
:: Revision: March 2013 - initial version
::           April 2013 - added support for FooBar v2 switches

@ECHO OFF
SETLOCAL ENABLEEXTENSIONS ENABLEDELAYEDEXPANSION

:: variables
SET me=%~n0


:END
ENDLOCAL
ECHO ON
@EXIT /B 0
</code></pre>

<h1>Conditional commands based on success/failure</h1>

<p>The conditional operators <code>||</code> and <code>&amp;&amp;</code> provide a convenient shorthand method to run a 2nd command based on the succes or failure of a 1st command.</p>

<p>The <code>&amp;&amp;</code> syntax is the AND opeartor to invoke a 2nd command when the first command returns a zero (success) exit code.</p>

<pre><code>DIR myfile.txt &gt;NUL 2&gt;&amp;1 &amp;&amp; TYPE myfile.txt
</code></pre>

<p>The <code>||</code> syntax is an OR operator to invoke a 2nd command when the first command returns a non-zero (failure) exit code.</p>

<pre><code>DIR myfile.txt &gt;NUL 2&gt;&amp;1 || CALL :WARNING file not found - myfile.txt
</code></pre>

<p>We can even combined the techniques.  Notice how we use the <code>()</code> grouping construct with <code>&amp;&amp;</code> to run 2 commands together should the 1st fail.</p>

<pre><code>DIR myfile.txt &gt;NUL 2&gt;&amp;1 || (ECHO %me%: WARNING - file not found - myfile.txt &gt;2 &amp;&amp; EXIT /B 1)
</code></pre>

<h1>Getting the full path to the parent directory of the script</h1>

<pre><code>:: variables
PUSHD "%~dp0" &gt;NUL &amp;&amp; SET root=%CD% &amp;&amp; POPD &gt;NUL
</code></pre>

<h1>Making a script sleep for N seconds</h1>

<p>You can use <code>PING.EXE</code> to fake a real *nix style <code>sleep</code> command.</p>

<pre><code>:: sleep for 2 seconds
PING.EXE -N 2 127.0.0.1 &gt; NUL
</code></pre>

<h1>Supporting &ldquo;double-click&rdquo; execution (aka invoking from Windows Explorer)</h1>

<p>Test if <code>%CMDCMDLINE%</code> is equal to <code>%COMSPEC%</code>  If they are equal, we can assume that we are running in an interactive session.
If not equal, we can inject a PAUSE into the end of the script to show the output.  You may also want to change to a valid
working directory.</p>

<pre><code>@ECHO OFF
SET interactive=0

ECHO %CMDCMDLINE% | FINDSTR /L %COMSPEC% &gt;NUL 2&gt;&amp;1
IF %ERRORLEVEL% == 0 SET interactive=1

ECHO do work

IF "%interactive%"=="0" PAUSE
EXIT /B 0
</code></pre>

<p><span class="basic-alignment left">
<a href="/guides/windows-batch-scripting/part-9-logging.html">&lt;&lt; Part 9 &ndash; Logging</a>
</span></p>
</div>


  <footer>
    <p class="meta">
      
  

<span class="byline author vcard">Posted by <span class="fn">Steve Jansen</span></span>

      








  


<time datetime="2013-03-01T10:57:00-05:00" pubdate data-updated="true">Mar 1<span>st</span>, 2013</time>
      

<span class="categories">
  
    <a class='category' href='/blog/categories/batch/'>batch</a>, <a class='category' href='/blog/categories/scripting/'>scripting</a>, <a class='category' href='/blog/categories/shell/'>shell</a>, <a class='category' href='/blog/categories/windows/'>windows</a>
  
</span>


    </p>
    
      <div class="sharing">
  
  <a href="http://twitter.com/share" class="twitter-share-button" data-url="http://steve-jansen.github.io/guides/windows-batch-scripting/part-10-advanced-tricks.html" data-via="" data-counturl="http://steve-jansen.github.io/guides/windows-batch-scripting/part-10-advanced-tricks.html" >Tweet</a>
  
  
  
</div>

    
    <p class="meta">
      
      
    </p>
  </footer>
</article>

  <section>
    <h1>Comments</h1>
    <div id="disqus_thread" aria-live="polite"><noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
</div>
  </section>

</div>

<aside class="sidebar">
  
    
<section>
	<span>
		<img src="http://www.gravatar.com/avatar/9ece5a08fa2e47180dc50d1e31f92e2f?s=200" alt="Gravatar of Steve Jansen " title="Gravatar of Steve Jansen" style="display: block; margin-left:auto; margin-right: auto" />
	</span>
</section>
<section>
  <p style="clear:both">
    Hi, I'm Steve.  I'm a software developer loving life in Charlotte, NC,
    an (ISC)<sup>2</sup> <a href="https://www.isc2.org/csslp/default.aspx">CSSLP</a>
    and an avid fan of <a href="http://www.crossfit.com">Crossfit</a>.
  </p>
  <p>
    And, no, I'm not Steve Jansen the British jazz drummer, though that does sound like a sweet career.
  </p>
</section>

<section>
  <h1>Guides</h1>
  <ul id="recent_posts">
      <li class="post">
        <a href="/guides/windows-batch-scripting/index.html">Guide to Windows Batch Scripting</a>
      </li>
  </ul>
</section>
<section>
  <h1>Recent Posts</h1>
  <ul id="recent_posts">
    
      <li class="post">
        <a href="/blog/2014/12/16/parsing-jenkins-secrets-in-a-shell-script/">Parsing Jenkins secrets in a shell script</a>
      </li>
    
      <li class="post">
        <a href="/blog/2014/12/15/jenkins-job-to-export-rackspace-cloud-dns-domain-as-bind-zone-files/">Jenkins Job to export Rackspace Cloud DNS Domain As BIND Zone Files</a>
      </li>
    
      <li class="post">
        <a href="/blog/2014/12/03/troubleshooting-github-webhooks-ssl-verification/">Troubleshooting GitHub WebHooks SSL Verification</a>
      </li>
    
      <li class="post">
        <a href="/blog/2014/12/01/integrating-rackspace-auto-scale-groups-with-objectrocket-mongo-databases/">Integrating Rackspace Auto Scale Groups with ObjectRocket Mongo databases</a>
      </li>
    
      <li class="post">
        <a href="/blog/2014/11/20/how-to-use-jenkins-to-monitor-cron-jobs/">How to use Jenkins to monitor cron jobs</a>
      </li>
    
  </ul>
</section>

<section>
  <h1>Social Stuff</h1>
  <ul>
    
      <li /><a href="https://github.com/steve-jansen">@steve-jansen</a> on GitHub
    
    <li /><a href="http://stackoverflow.com/users/1995977/steve-jansen">@steve-jansen</a> on StackOverflow
    <li /><a href="https://coderwall.com/p/u/steve-jansen">@steve-jansen</a> ProTips on Coderwall
    <li /><a href="https://connect.microsoft.com/SQLServer/SearchResults.aspx?UserHandle=steve-jansen">@steve-jansen</a> on Microsft Connect
    <li /><a href="http://aspnet.uservoice.com/users/33548256-steve-jansen">@steve-jansen</a> on ASP.NET User Voice
    <li /><a href="/atom.xml" title="Subscribe via RSS">Subscribe via RSS</a>
  </ul>
</section>

<!--<a href="https://coderwall.com/steve-jansen"><img alt="Endorse steve-jansen on Coderwall" src="https://api.coderwall.com/steve-jansen/endorsecount.png" /></a>-->




  
</aside>


    </div>
  </div>
  <footer role="contentinfo"><p>
  Copyright &copy; 2015 - Steve Jansen -
  <span class="credit">Powered by <a href="http://octopress.org">Octopress</a></span>
</p>

</footer>
  

<script type="text/javascript">
      var disqus_shortname = 'steve-jansen';
      
        
        // var disqus_developer = 1;
        var disqus_identifier = 'http://steve-jansen.github.io/guides/windows-batch-scripting/part-10-advanced-tricks.html';
        var disqus_url = 'http://steve-jansen.github.io/guides/windows-batch-scripting/part-10-advanced-tricks.html';
        var disqus_script = 'embed.js';
      
    (function () {
      var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
      dsq.src = 'http://' + disqus_shortname + '.disqus.com/' + disqus_script;
      (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    }());
</script>







  <script type="text/javascript">
    (function(){
      var twitterWidgets = document.createElement('script');
      twitterWidgets.type = 'text/javascript';
      twitterWidgets.async = true;
      twitterWidgets.src = 'http://platform.twitter.com/widgets.js';
      document.getElementsByTagName('head')[0].appendChild(twitterWidgets);
    })();
  </script>





</body>
</html>

  </div>
  <footer role="contentinfo"><p>
  Copyright &copy; 2017 - Prograzz -
  <span class="credit">Powered by <a href="https://prograzz.github.io/Htm/">Prograzz</a></span>
</p>

</footer>
