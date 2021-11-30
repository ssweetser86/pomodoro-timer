<div class="scrollable-container" ng-transclude=""> <div markdown="fileTab.file.contents || fileTab.file.markdown" language="fileTab.file.language" class="markdown collapsed"><h1>Pomodoro Timer</h1><p>The Pomodoro Technique is a time management method developed by Francesco Cirillo in the late 1980s.<br>
The technique uses a timer to break down work into intervals, traditionally 25 minutes in length, separated by short breaks. Each interval is known as a pomodoro, from the Italian word for 'tomato', after the tomato-shaped kitchen timer that Cirillo used as a university student.</p>
<p>You will implement a Pomodoro timer that follows these steps (simplified from the original technique):</p>
<ol>
<li>Set the focus duration (default to 25 minutes, no less than 5 or more than 60).</li>
<li>Set the break duration (default to 5 minutes, no less than 1 or more than 15).</li>
<li>When the user clicks the "play" button, the timer starts.</li>
<li>When the focus time expires, an alarm plays and then the break timer starts.</li>
<li>When the break time expires, the alarm plays again and then the focus timer starts.</li>
</ol>
<p>This application uses <a href="https://getbootstrap.com/" target="_blank" rel="noopener">Bootstrap 4</a> for styling and <a href="https://useiconic.com/open" target="_blank" rel="noopener">Open-Iconic icons</a> for icons.</p>
<p>This project is designed to test your ability to work with rendering and state management using React. Before taking on this module, you should be comfortable with the following:</p>
<ul>
<li>Installing packages via NPM.</li>
<li>Running tests from the command line.</li>
<li>Writing React function components.</li>
<li>Using hooks like <code>useState()</code></li>
<li>Debugging React code through console output</li>
</ul>
<h2>Project setup</h2><p>Follow the instructions below to get this project up and running on your own machine:</p>
<ul>
<li>Sync this challenge with your computer so that you can work on the project locally.</li>
<li>Run <code>npm install</code>.</li>
</ul>
<p>To run the tests, you can run the following command:</p>
<div class="language-tabset"><div class="language-tab language-bash"><pre><code class="lang-bash">npm test
</code></pre>
</div></div><p>You can run the application using the following command.</p>
<div class="language-tabset"><div class="language-tab language-bash"><pre><code class="lang-bash">npm start
</code></pre>
</div></div><h2>Initial Screen</h2><p>The initial screen lets the user set the length of the focus and break and break sessions.</p>

<p><zoomable-image zoom-disabled="expandable &amp;&amp; !expanded" class="enabled" style="height: 400.404px;"><!----><span class="zoomable-image-controls" ng-if="$ctrl.enabled" style=""> <button class="btn-default btn-sm icon-expand" ng-click="$ctrl.expandOrContract($event)" tooltip="Make this image as large as possible" type="button"></button> <button class="btn-default btn-sm icon-minus" ng-click="$ctrl.zoomOut($event)" ng-disabled="$ctrl.zoomOutDisabled" tooltip="Zoom Out" type="button" disabled="disabled"></button> <button class="btn-default btn-sm" ng-class="{ active: $ctrl.is100 }" ng-click="$ctrl.zoom100($event)" tooltip="Zoom 1:1 pixels" type="button"> 1:1 </button> <button class="btn-default btn-sm icon-plus" ng-click="$ctrl.zoomIn($event)" ng-disabled="$ctrl.zoomInDisabled" tooltip="Zoom In" type="button"></button> </span><!----> <div class="zoomable-image-scrollbox" ng-transclude="" ng-dblclick="$ctrl.autoZoom($event)" tooltip="You can zoom into this image using the controls, or double-clicking on it" tooltip-position="top" scroll-on-drag="$ctrl.enabled &amp;&amp; $ctrl.zoomed" tabindex="0"><img src="https://res.cloudinary.com/strive/image/upload/w_1000,h_1000,c_limit/06ddc6bb0f6b5add9db441447000e59c-o-initial-screen.png" alt="Initial Screen" style="width: 544.268px; height: 398.404px; max-width: none;"></div></zoomable-image></p>
<p>The "stop" button is disabled on the initial screen because the user has not yet started the timer.</p>
<p>When the user clicks the "play" button, the timer will always start a new focus session.</p>
<h2>Active Session Screen</h2><p>After the user clicks the "play" button, the buttons to change the focus and break duration are disabled, and the session timer appears.</p>

<p><zoomable-image zoom-disabled="expandable &amp;&amp; !expanded" class="enabled" style="height: 323.824px;"><!----><span class="zoomable-image-controls" ng-if="$ctrl.enabled" style=""> <button class="btn-default btn-sm icon-expand" ng-click="$ctrl.expandOrContract($event)" tooltip="Make this image as large as possible" type="button"></button> <button class="btn-default btn-sm icon-minus" ng-click="$ctrl.zoomOut($event)" ng-disabled="$ctrl.zoomOutDisabled" tooltip="Zoom Out" type="button" disabled="disabled"></button> <button class="btn-default btn-sm" ng-class="{ active: $ctrl.is100 }" ng-click="$ctrl.zoom100($event)" tooltip="Zoom 1:1 pixels" type="button"> 1:1 </button> <button class="btn-default btn-sm icon-plus" ng-click="$ctrl.zoomIn($event)" ng-disabled="$ctrl.zoomInDisabled" tooltip="Zoom In" type="button"></button> </span><!----> <div class="zoomable-image-scrollbox" ng-transclude="" ng-dblclick="$ctrl.autoZoom($event)" tooltip="You can zoom into this image using the controls, or double-clicking on it" tooltip-position="top" scroll-on-drag="$ctrl.enabled &amp;&amp; $ctrl.zoomed" tabindex="0"><img src="https://res.cloudinary.com/strive/image/upload/w_1000,h_1000,c_limit/517bceae35a5acf63fb3d20cb04733cf-ro-active-sesson.png" alt="Active Session Screen" style="width: 543.622px; height: 321.824px; max-width: none;"></div></zoomable-image></p>
<p>The session timer shows the type of session, either "Focusing" or "On Break", the total duration of the session, the time remaining, and a progress bar showing how much of the session is complete.</p>
<blockquote>
<p><strong>Hint</strong>: In React, if you want to hide/show something, use conditional rendering rather than CSS styles. In general, conditional rendering is preferred. The tests in this project require the use of conditional rendering to show/hide the session timer.</p>
</blockquote>
<h2>Paused Session Screen</h2><p>If the user clicks the "pause" button, "paused" appears below the time remaining.</p>

<p><zoomable-image zoom-disabled="expandable &amp;&amp; !expanded" class="enabled" style="height: 330.935px;"><!----><span class="zoomable-image-controls" ng-if="$ctrl.enabled" style=""> <button class="btn-default btn-sm icon-expand" ng-click="$ctrl.expandOrContract($event)" tooltip="Make this image as large as possible" type="button"></button> <button class="btn-default btn-sm icon-minus" ng-click="$ctrl.zoomOut($event)" ng-disabled="$ctrl.zoomOutDisabled" tooltip="Zoom Out" type="button" disabled="disabled"></button> <button class="btn-default btn-sm" ng-class="{ active: $ctrl.is100 }" ng-click="$ctrl.zoom100($event)" tooltip="Zoom 1:1 pixels" type="button"> 1:1 </button> <button class="btn-default btn-sm icon-plus" ng-click="$ctrl.zoomIn($event)" ng-disabled="$ctrl.zoomInDisabled" tooltip="Zoom In" type="button"></button> </span><!----> <div class="zoomable-image-scrollbox" ng-transclude="" ng-dblclick="$ctrl.autoZoom($event)" tooltip="You can zoom into this image using the controls, or double-clicking on it" tooltip-position="top" scroll-on-drag="$ctrl.enabled &amp;&amp; $ctrl.zoomed" tabindex="0"><img src="https://res.cloudinary.com/strive/image/upload/w_1000,h_1000,c_limit/e179e707512486a110fbdb155a7897b4-o-paused-session.png" alt="Paused Session Screen" style="width: 543.694px; height: 328.935px; max-width: none;"></div></zoomable-image></p>
<p>The session timer shows the type of session, either "Focusing" or "On Break", the total duration of the session, the time remaining, and a progress bar showing how much of the session is complete.</p>
<h2>Stopping a session</h2><p>Stopping a session returns the application to the initial screen and the user is able to change the focus and break duration.</p>
<p>Clicking the "play" button will always start a new focus session.</p>
<h2>Specific instruction</h2><ol>
<li>The code has various TODO items that should help you build the project as expected. With that said, feel free to make the changes you feel are necessary to accomplish the tasks.</li>
<li>Break up the code into at least two additional components that have a single responsibility.</li>
<li>The user cannot change the duration of the focus or break during a focus or break session.</li>
<li>Display durations as <code>mm:ss</code>. i.e. 05:00 for 5 minutes or 18:45 for eighteen minutes and forty-five seconds.</li>
<li>The tests use the <code>data-testid="..."</code> attributes on elements. Removing these will break one or more tests.</li>
</ol>
<h2>Using <code>setInterval</code> in React</h2><p>Using <code>setInterval</code> with React functional components requires a custom hook.</p>
<p>We have provided a custom <code>useInterval</code> hook in <code>src/utils/useInterval/index.js</code> for you to use. The <code>useInterval</code> hook is already setup to start and stop with the play/pause buttons</p>
<p>You may not have learned about hooks yet, but don't worry, this function works exactly like <code>setInterval</code> except you don't need to use <code>clearInterval</code> to stop it.</p>
<p>As it is currently configured, the <code>useInterval</code> will execute the code in the callback every second, unless <code>isTimerRunning</code> is set to false.</p>
<p>This should be sufficient to implement the pomodoro timer.</p>
<h2>Playing Audio alarm</h2><p>Use the following code to play an alarm when the time expires. You can upload your own sound or use the one provided in the link below.</p>
<div class="language-tabset"><div class="language-tab language-javascript"><pre><code class="lang-javascript"><span class="hljs-keyword">new</span> Audio(<span class="hljs-string">`https://bigsoundbank.com/UPLOAD/mp3/1482.mp3`</span>).play();
</code></pre>
</div></div><h2>classNames function</h2><p><code>import classNames from "../utils/class-names";</code></p>
<p>Use this function to dynamically assign the className property of react components.</p>
<p>Usage:</p>
<div class="language-tabset"><div class="language-tab language-jsx"><pre><code class="lang-jsx">&lt;span
  className={classNames({
    oi: <span class="hljs-literal">true</span>,
    <span class="hljs-string">"oi-media-play"</span>: currentState.isPaused,
    <span class="hljs-string">"oi-media-pause"</span>: !currentState.isPaused,
  })}
/&gt;
</code></pre>
</div></div><p>if currentState.isPaused === true, the className will be "oi oi-media-play" otherwise it will be "oi oi-media-pause"</p>
<p><code>classNames</code> takes a map of a class name to a boolean value. If the boolean value is <code>true</code>, the class name is included, otherwise it is excluded.</p>
<p>returns: A space delimited string of the class names which have a value of <code>true</code>.</p>
<h2>minutesToDuration function</h2><p><strong>minutesToDuration</strong> formats a number of minutes as 'mm:00'. For example,</p>
<div class="language-tabset"><div class="language-tab language-javascript"><pre><code class="lang-javascript"><span class="hljs-keyword">import</span> { minutesToDuration } <span class="hljs-keyword">from</span> <span class="hljs-string">"../utils/duration"</span>;
minutesToDuration(<span class="hljs-number">3</span>); <span class="hljs-comment">// '03:00'</span>
minutesToDuration(<span class="hljs-number">45</span>); <span class="hljs-comment">// '45:00'</span>
</code></pre>
</div></div><h2>secondsToDuration function</h2><p><strong>secondsToDuration</strong> formats a number of seconds as 'mm:ss'. For example,</p>
<div class="language-tabset"><div class="language-tab language-javascript"><pre><code class="lang-javascript"><span class="hljs-keyword">import</span> { secondsToDuration } <span class="hljs-keyword">from</span> <span class="hljs-string">"../utils/duration"</span>;
secondsToDuration(<span class="hljs-number">305</span>); <span class="hljs-comment">// '05:05'</span>
secondsToDuration(<span class="hljs-number">930</span>); <span class="hljs-comment">// '15:30'</span>
</code></pre>
</div></div><h2>Debugging</h2><p>If you have a failing test, but the application appears to be working correctly when you view it in the browser, try the following debugging steps:</p>
<ol>
<li>In <a href="./src/pomodoro/Pomodoro.js" target="_blank" rel="noopener">./src/pomodoro/Pomodoro.js</a>, find <code>isTimerRunning ? 1000 : null</code> and temporarily change it to <code>isTimerRunning ? 100 : null</code>.<ul>
<li>This will make the timer run 10 times faster, making it easier to debug.</li>
</ul>
</li>
<li>Start the app and open it in the browser.</li>
<li>Set the focus and break times to the minimum values.</li>
<li>Click the play button to start the pomodoro timer.</li>
<li>Observe the application going through <em>multiple</em> focus/break sessions. Let it run through at least two transitions from "Focusing" to "On break" and back to "Focusing", just like a real user.<ul>
<li>Check the values displayed in session title, session sub-title, and progress bar.</li>
<li>At this point you will likely see the problem.</li>
</ul>
</li>
<li>In <a href="./src/pomodoro/Pomodoro.js" target="_blank" rel="noopener">./src/pomodoro/Pomodoro.js</a>, change <code>isTimerRunning ? 100 : null</code> back to <code>isTimerRunning ? 1000 : null</code> so the timer runs at normal speed.</li>
</ol>
<p><strong>Note:</strong> In addition to needing to pass the tests and requirements in the instructions here, please review the Rubric Requirements for the human-graded part of this project in your Thinkful curriculum page.</p>
<h2>Tests failing unexpectedly on your local machine?</h2><p>If you've completed the assignment but the tests are still failing on your local machine, then try re-creating the project dependencies, as follows:</p>
<ol>
<li>Delete the <code>package-lock.json</code> file.</li>
<li>Delete the <code>node_modules</code> directory.</li>
<li>Run <code>npm install</code>.</li>
<li>Then try running the tests again.</li>
</ol>
</div> </div>