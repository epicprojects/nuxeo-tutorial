# Develop With Nuxeo (Tutorial)
Do you want to develop Nuxeo Platform with you favorite IDE IntelliJ? 

I’d like to share with you the IntelliJ configuration for Nuxeo. After reading this, you’ll understand how to:

1. Getting the Nuxeo Source Code
2. Import Nuxeo Source Code into IntelliJ
3. Configure Nuxeo Code Style 
4. Compiling and Building Nuxeo Server with IntelliJ
5. Installing Web UI bundle to Nuxeo Server



<h3>Prerequisite</h3>

Before getting started, you need to ensure your computer has installed the following software:

1. IntelliJ IDEA CE (Latest)
2. JDK 8 (Oracle's JDK or OpenJDK recommended)
3. Apache Maven 3.1.1+ (3.2+ recommended)
4. Apache Ant 1.7.1+
5. Git
6. NodeJS 0.10.32 and (npm, yo, grunt, grunt-cli, gulp, bower) *don't forget to install these are very important*
7. Python 2.7



<h2>1. Getting the Nuxeo Source Code</h2>

Clone the Nuxeo 'master' branch to some folder using git GUI or Command line
```ruby
https://github.com/nuxeo/nuxeo.git
```
In the cloned source code folder find 'clone.py' and execute following command
```py
python clone.py master -a
```

<h2>2. Import Nuxeo Source Code into IntelliJ</h2>
Before importing Nuxeo source code, you need to configure the VM options for importer to increase the importation capacity.
Open IntelliJ, a welcome menu will be shown. On the right bottom of menu, click <b> Configure > Preferences. </b>
Then search <b>VM options for importer</b> in <i>Build Toold > Maven > Importing</i> and set it to:



```py
-Xmx4g -Xms1g
```

![](http://omershafiq.com/nuxeo-tutorial/vm-options-for-importer.png)

Now import Nuxeo source code as Maven project. In the default welcome menu, choose <b>Import Project</b>, then find the Nuxeo root folder and select the POM file in <i><b>$NX_HOME/pom.xml</b></i>. Afterwards, set up the Maven import options as the following screenshot:

![](http://omershafiq.com/nuxeo-tutorial/import-project-from-maven.png)

Later, you will need to:

1. Choose Maven profiles: <b>default</b>
2. Choose Project SDK: <b> use JDK 8 </b> (in next steps)
3. Edit name to create a new IntelliJ project: <b> default (or anything you like) </b> (in next steps)


![](http://omershafiq.com/nuxeo-tutorial/maven_profile.png)

When the configuration is finished. IntelliJ will create a project for you, the entire process (Maven import) will take a some minutes, You have to be patient about that. And final view will be something like this:

![](http://omershafiq.com/nuxeo-tutorial/20170209-final-view.png)

<h2>3. Configure Nuxeo Code Style </h2>

Get the Eclipse code formatter plugin (https://plugins.jetbrains.com/plugin/6546-eclipse-code-formatter) from <b> Preferences > Plugins > Install JetBrains Plugin > Search "Eclipse code formatter" </b> and install it. It will improve the performance of IntelliJ. You can customize the VM options by <b>Click Help > Edit Custom VM Options…. </b> If there’s no existing configuration file, IntelliJ will help you to create one. Then edit the content with your preferred values:

```py
-Xmx4g -Xms1g
```

![](http://omershafiq.com/nuxeo-tutorial/20170209-eclipse-code-formatter.png)

<h2>4. Compiling and Building Nuxeo Server with IntelliJ</h2>

To compile and run nuxeo project you need to create a configration. In my case of Mac OS you can use (https://plugins.jetbrains.com/plugin/4230-bashsupport) and in case of Windows you can use (https://plugins.jetbrains.com/plugin/265-batch-scripts-support). You can install the required plugin from <b> Preferences > Plugins > Install JetBrains Plugin > Search plugin name </b>. 

You can create a <b>run.sh/run.bat</b> (bash or batch script) in <b>$NX_HOME/Scripts</b> and add following command to it.

For Mac OS
```py
/YOUR_PATH_TO_NUXEO/nuxeo/nuxeo-distribution/nuxeo-server-tomcat/target/nuxeo-server-tomcat-9.2-SNAPSHOT/bin/Start\ Nuxeo.command
```

For Windows
```py
"C:\YOUR_PATH_TO_NUXEO\nuxeo\nuxeo-distribution\nuxeo-server-tomcat\target\nuxeo-server-tomcat-9.2-SNAPSHOT\bin\Start Nuxeo.bat"
```

After that you have to create a run configuration which should look like this:

In before launch section you need to add <b>"Make"</b> (Which will compile all the sources) and also create a <b>"Run Maven Goal"</b> with following parameters:

```py
clean -DskipTests=true install -Paddons,distrib
```

![](http://omershafiq.com/nuxeo-tutorial/run_config.png)



*Most common mistake is either not having right <b>Maven (I am using 3.3.9)</b> version installed or not having all required <b>NPM components (npm, yo, grunt, grunt-cli, gulp, bower) or missing any other prerequisites</b>


and run the project after making configrations and if everything goes well you should see the <b>Nuxeo Server GUI</b>:

![](http://omershafiq.com/nuxeo-tutorial/server-gui.png)

if you go to browser and open following link you should see that nuxeo server is up and running.

```py
http://localhost:8080/nuxeo
```

![](http://omershafiq.com/nuxeo-tutorial/install-web-ui.png)


<h2>5. Installing Web UI bundle to Nuxeo Server</h2>

<b>!!! IMPORTANT !!!</b>
Before installing component you need to stop the Nuxeo Server!

Nuxeo Web UI component can be downloaded from following link https://connect.nuxeo.com/nuxeo/site/marketplace/package/nuxeo-web-ui
Now using following command install <b>Nuxeo Web UI Comoponent</b>

```py
/YOUR_PATH_TO_NUXEO/nuxeo/nuxeo-distribution/nuxeo-server-tomcat/target/nuxeo-server-tomcat-9.2-SNAPSHOT/bin/nuxeoctl mp-install <download-path>/nuxeo-web-ui-0.10.0.zip
```

If while installing the component it askes you to <i>"Do you want to relax the constraint (yes/no)?"</i> Answer with <b>Yes</b>

Now start the server using following command or run your 'run.bat/run.sh' script.

For Mac OS
```py
/YOUR_PATH_TO_NUXEO/nuxeo/nuxeo-distribution/nuxeo-server-tomcat/target/nuxeo-server-tomcat-9.2-SNAPSHOT/bin/Start\ Nuxeo.command
```

For Windows
```py
"C:\YOUR_PATH_TO_NUXEO\nuxeo\nuxeo-distribution\nuxeo-server-tomcat\target\nuxeo-server-tomcat-9.2-SNAPSHOT\bin\Start Nuxeo.bat"
```

and if everything works fine you should see fully functional nuxeo server with a UI interface on http://localhost:8080/nuxeo.
You can login to the dashboard using following credentials.

<b>Username:</b> Administrator
<b>Password:</b> Administrator

![](http://omershafiq.com/nuxeo-tutorial/login.png)

![](http://omershafiq.com/nuxeo-tutorial/nuxeo-dashboard.png)




