The Object Log is basically an OrderedCollection of instances of ObjectLogEntry.

You view the Object Log from your web-browser with the WAObjectLog component:
<img src='http://gemstonesoup.files.wordpress.com/2011/11/objectlog.png'>
Clicking on the <b>priority</b> link will take you to an inspector on the ObjectLogEntry instance.<br>
<br>
<h3>Enable ObjectLog Component</h3>
To enable the WAObjectLog component evaluate the following expression:<br>
<pre><code>WAAdmin <br>
	register: WAObjectLog <br>
	asApplicationAt: WAObjectLog entryPointName<br>
	user: 'admin' password: 'tool'.<br>
</code></pre>
Note that the username/password is admin/tool. If you enable the Object Log in a production application, you should choose a unique username and/or password.