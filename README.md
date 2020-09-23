<div align="center">

## Building Applets


</div>

### Description

Like applications, applets are created from classes. However, applets do not have a main method as an entry point, but instead, have several methods to control specific aspects of applet execution.

This lesson converts an application from Lesson 2 (Building Applications) to an applet and describes the structure and elements of an applet.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Monica Pawlan \(Copyright Sun Microsystems Inc\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/monica-pawlan-copyright-sun-microsystems-inc.md)
**Level**          |Beginner
**User Rating**    |5.0 (30 globes from 6 users)
**Compatibility**  |Java \(JDK 1\.1\)
**Category**       |[Complete Applications](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/complete-applications__2-64.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/monica-pawlan-copyright-sun-microsystems-inc-building-applets__2-1833/archive/master.zip)





### Source Code


<ul>
 <li><a href="#convert"><font face="Verdana">Application to Applet</font></a>
 <li><a href="#run"><font face="Verdana">Run the Applet</font></a>
 <li><a href="#struct"><font face="Verdana">Applet Structure and Elements</font></a>
 <li><a href="#package"><font face="Verdana">Packages</font></a>
 <li><a href="#more"><font face="Verdana">More Information</font></a></li>
</ul>
<font face="Verdana, Arial, Helvetica, sans-serif">
<hr>
<a name="convert"></a></font>
<h3><font face="Verdana">Application to Applet</font></h3>
<font face="Verdana">The following code is the <a href="http://www.planet-source-code.com/vb/tutorial/java/samples/SimpleApplet.java">applet</a>
equivalent to the <code>LessonTwoB</code> application from Lesson 2. The figure
below shows how the running applet looks. The structure and elements of the
applet code are discussed after the section on how to run the applet just below.</font>
<p><font face="Verdana"><img src="http://www.planet-source-code.com/vb/tutorial/java/images/applet.gif" width="212" height="193"></font><font face="Verdana, Arial, Helvetica, sans-serif">
<p>&nbsp;</font>
<pre><font face="Verdana">import java.applet.Applet;
import java.awt.Graphics;
import java.awt.Color;
public class SimpleApplet extends Applet{
 String text = &quot;I'm a simple applet&quot;;
 public void init() {
    text = &quot;I'm a simple applet&quot;;
    setBackground(Color.cyan);
 }
 public void start() {
    System.out.println(&quot;starting...&quot;);
 }
 public void stop() {
    System.out.println(&quot;stopping...&quot;);
 }
 public void destroy() {
    System.out.println(&quot;preparing to unload...&quot;);
 }
 public void paint(Graphics g){
    System.out.println(&quot;Paint&quot;);
    g.setColor(Color.blue);
    g.drawRect(0, 0,
          getSize().width -1,
          getSize().height -1);
    g.setColor(Color.red);
    g.drawString(text, 15, 25);
 }
}
</font></pre>
<font face="Verdana">The <code>SimpleApplet</code> class is declared <code>public</code>
so the program that runs the applet (a browser or <code>appletviewer</code>),
which is not local to the program can access it. <a name="run"></a></font>
<h3><font face="Verdana">Run the Applet</font></h3>
<font face="Verdana">To see the applet in action, you need an <code>HTML</code>
file with the Applet tag as follows:</font>
<p><code><font face="Verdana">&lt;HTML&gt;<br>
&lt;BODY&gt;<br>
&lt;APPLET CODE=SimpleApplet.class WIDTH=200 HEIGHT=100&gt;<br>
&lt;/APPLET&gt;<br>
&lt;/BODY&gt;<br>
&lt;/HTML&gt;<br>
</font></code>
<p><font face="Verdana">The easiest way to run the applet is with appletviewer
shown below where <code>simpleApplet.html</code> is a file that contains the
above HTML code:</font><font face="Verdana, Arial, Helvetica, sans-serif">
<p>&nbsp;</font>
<pre><font face="Verdana">  appletviewer simpleApplet.html
</font></pre>
<font face="Verdana, Arial, Helvetica, sans-serif">
<blockquote>
 <hr>
</font><font face="Verdana"><strong>Note:</strong> To run an applet written with
Java<font size="-2"><sup>TM</sup></font> 2 APIs in a browser, the browser must
be enabled for the Java 2 Platform. If your browser is not enabled for the Java
2 Platform, you have to use appletviewer to run the applet or install <a href="http://java.sun.com/products/plugin/index.html" target="_blank">Java
Plug-in</a>. Java Plug-in lets you run applets on web pages under the 1.2
version of the Java VM instead of the web browser's default Java VM.</font><font face="Verdana, Arial, Helvetica, sans-serif">
<hr>
</blockquote>
<a name="struct"></a></font>
<h3><font face="Verdana">Applet Structure and Elements</font></h3>
<font face="Verdana">The Java API <code>Applet</code> class provides what you
need to design the appearance and manage the behavior of an applet. This class
provides a graphical user interface (GUI) component called a <code>Panel</code>
and a number of methods. To create an applet, you extend (or subclass) the <code>Applet</code>
class and implement the appearance and behavior you want.</font>
<p><font face="Verdana">The applet's appearance is created by drawing onto the <code>Panel</code>
or by attaching other GUI components such as push buttons, scrollbars, or text
areas to the <code>Panel</code>. The applet's behavior is defined by
implementing the methods.</font>
<h4><font face="Verdana">Extending a Class</font></h4>
<font face="Verdana"><img align="left" src="http://www.planet-source-code.com/vb/tutorial/java/images/hierarchy.gif">
Most classes of any complexity extend other classes. To extend another class
means to write a new class that can use the fields and methods defined in the
class being extended. The class being extended is the parent class, and the
class doing the extending is the child class. Another way to say this is the
child class inherits the fields and methods of its parent or chain of parents.
Child classes either call or override inherited methods. This is called single
inheritance.</font>
<p><font face="Verdana">The <code>SimpleApplet</code> class extends <code>Applet</code>
class, which extends the <code>Panel</code> class, which extends the <code>Container</code>
class. The <code>Container</code> class extends <code>Object</code>, which is
the parent of all Java API classes.</font>
<p><font face="Verdana">The <code>Applet</code> class provides the <code>init</code>,
<code>start</code>, <code>stop</code>, <code>destroy</code>, and <code>paint</code>
methods you saw in the example applet. The <code>SimpleApplet</code> class
overrides these methods to do what the <code>SimpleApplet</code> class needs
them to do. The <code>Applet</code> class provides no functionality for these
methods.</font>
<p><font face="Verdana">However, the <code>Applet</code> class does provide
functionality for the <code>setBackground</code> method,which is called in the <code>init</code>
method. The call to <code>setBackground</code> is an example of calling a method
inherited from a parent class in contrast to overriding a method inherited from
a parent class.</font>
<p><font face="Verdana">You might wonder why the Java language provides methods
without implementations. It is to provide conventions for everyone to use for
consistency across Java APIs. If everyone wrote their own method to start an
applet, for example, but gave it a different name such as <code>begin</code> or <code>go</code>,
the applet code would not be interoperable with other programs and browsers, or
portable across multiple platforms. For example, Netscape and Internet Explorer
know how to look for the <code>init</code> and <code>start</code> methods.</font>
<h4><font face="Verdana">Behavior</font></h4>
<font face="Verdana">An applet is controlled by the software that runs it.
Usually, the underlying software is a browser, but it can also be <code>appletviewer</code>
as you saw in the example. The underlying software controls the applet by
calling the methods the applet inherits from the <code>Applet</code> class.</font>
<p><font face="Verdana"><strong><code>The init Method:</code></strong> The <code>init</code>
method is called when the applet is first created and loaded by the underlying
software. This method performs one-time operations the applet needs for its
operation such as creating the user interface or setting the font. In the
example, the <code>init</code> method initializes the text string and sets the
background color.</font>
<p><font face="Verdana"><strong><code>The start Method:</code></strong> The <code>start</code>
method is called when the applet is visited such as when the end user goes to a
web page with an applet on it. The example prints a string to the console to
tell you the applet is starting. In a more complex applet, the <code>start</code>
method would do things required at the start of the applet such as begin
animation or play sounds.</font>
<p><font face="Verdana">After the <code>start</code> method executes, the event
thread calls the <code>paint</code> method to draw to the applet's <code>Panel</code>.
A thread is a single sequential flow of control within the applet, and every
applet can run in multiple threads. <code>Applet</code> drawing methods are
always called from a dedicated drawing and event-handling thread.</font>
<p><font face="Verdana"><strong>The <code>stop and destroy Methods:</code></strong>
The <code>stop</code> method stops the applet when the applet is no longer on
the screen such as when the end user goes to another web page. The example
prints a string to the console to tell you the applet is stopping. In a more
complex applet, this method should do things like stop animation or sounds.</font>
<p><font face="Verdana">The <code>destroy</code> method is called when the
browser exits. Your applet should implement this method to do final cleanup such
as stop live threads.</font>
<h4><font face="Verdana">Appearance</font></h4>
<font face="Verdana">The <code>Panel</code> provided in the <code>Applet</code>
class inherits a <code>paint</code> method from its parent <code>Container</code>
class. To draw something onto the Applet's <code>Panel</code>, you implement the
<code>paint</code> method to do the drawing.</font>
<p><font face="Verdana">The <code>Graphics</code> object passed to the <code>paint</code>
method defines a <i>graphics context</i> for drawing on the <code>Panel</code>.
The <code>Graphics</code> object has methods for graphical operations such as
setting drawing colors, and drawing graphics, images, and text.</font>
<p><font face="Verdana">The <code>paint</code> method for the <code>SimpleApplet</code>
draws the <i>I'm a simple applet</i> string in red inside a blue rectangle.</font>
<pre><font face="Verdana">  public void paint(Graphics g){
    System.out.println(&quot;Paint&quot;);
//Set drawing color to blue
    g.setColor(Color.blue);
//Specify the x, y, width and height for a rectangle
    g.drawRect(0, 0,
          getSize().width -1,
          getSize().height -1);
//Set drawing color to red
    g.setColor(Color.red);
//Draw the text string at the (15, 25) x-y location
    g.drawString(text, 15, 25);
  }
</font></pre>
<font face="Verdana, Arial, Helvetica, sans-serif"><a name="package"></a></font>
<h3><font face="Verdana">Packages</font></h3>
<font face="Verdana">The applet code also has three <code>import</code>
statements at the top. Applications of any size and all applets use <code>import</code>
statements to access ready-made Java API classes in <i>packages</i>. This is
true whether the Java API classes come in the Java platform download, from a
third-party, or are classes you write yourself and store in a directory separate
from the program. At compile time, a program uses <code>import</code> statements
to locate and reference compiled Java API classes stored in packages elsewhere
on the local or networked system. A compiled class in one package can have the
same name as a compiled class in another package. The package name
differentiates the two classes.</font>
<p><font face="Verdana">The examples in Lessons 1 and 2 did not need a package
declaration to call the <code>System.out.println</code> Java API class because
the <code>System</code> class is in the <code>java.lang</code> package that is
included by default. You never need an <code>import java.lang.*</code> statement
to use the compiled classes in that package. <a name="more"></a></font>
<h3><font face="Verdana">More Information</font></h3>
<font face="Verdana">You can find more information on applets in the <a href="http://java.sun.com/docs/books/tutorial/applet/" target="_blank">Writing
Applets</a> trail in <a href="http://java.sun.com/docs/books/tutorial/" target="_blank">The
Java Tutorial</a>.<br>
</font>
<hr>
<!--BEGIN READER SURVEY-->
<font size="2">
<p><font face="verdana,arial"><b>Reprinted with permission from the <a href="http://developer.java.sun.com/developer/" target="_blank">Java
Developer Connection(SM)</a><br>
Copyright <a href="http://www.sun.com" target="_blank">Sun Microsystems Inc</a>.</b></font></p>
</font>

