# Nuxeo Tutorial
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
6. NodeJS 0.10.32, npm, yo, grunt-cli, gulp, bower
7. Python 2.7



<h2>Getting the Nuxeo Source Code</h2>

Clone the Nuxeo 'master' branch to some folder using git GUI or Command line
```ruby
https://github.com/nuxeo/nuxeo.git
```
In the cloned source code folder find 'clone.py' and execute following command
```py
python clone.py master -a
```

<h2>Import Nuxeo Source Code into IntelliJ</h2>
Before importing Nuxeo source code, you need to configure the VM options for importer to increase the importation capacity.
Open IntelliJ, a welcome menu will be shown. On the right bottom of menu, click <b> Configure > Preferences. </b>
Then search <b>VM options for importer</b> in <i>Build Toold > Maven > Importing</i> and set it to:


```py
-Xms1g -Xmx4g
```
