# Run automation tests with using TestNG On LambdaTest

![image](https://user-images.githubusercontent.com/70570645/171934563-4806efd2-1154-494c-a01d-1def95657383.png)


<p align="center">
  <a href="https://www.lambdatest.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=Java-TestNG-Selenium" target="_bank">Blog</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=Java-TestNG-Selenium" target="_bank">Docs</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=Java-TestNG-Selenium" target="_bank">Learning Hub</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/newsletter/?utm_source=github&utm_medium=repo&utm_campaign=Java-TestNG-Selenium" target="_bank">Newsletter</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.lambdatest.com/certification/?utm_source=github&utm_medium=repo&utm_campaign=Java-TestNG-Selenium" target="_bank">Certifications</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.youtube.com/c/LambdaTest" target="_bank">YouTube</a>
</p>
&emsp;
&emsp;
&emsp;

# Pre-requisites:

Before you can start performing Java automation testing with Selenium, you would need to:

Install the latest Java development environment i.e. JDK 1.6 or higher. We recommend using the latest version.

Download the latest Selenium Client and its WebDriver bindings from the official website. Latest versions of Selenium Client and WebDriver are ideal for running your automation script on LambdaTest Selenium cloud grid.

Install Maven which supports JUnit framework out of the box. Maven can be downloaded and installed following the steps from the official website. Maven can also be installed easily on Linux/MacOS using Homebrew package manager.

# Cloning Repo and Installing Dependencies:

Step 1: Clone the LambdaTest’s Java-TestNG-Selenium repository and navigate to the code directory as shown below:

git clone https://github.com/lambdatestsupport/GamesGlobalAutomationTesting

cd GamesGlobalAutomationTesting

You can also run the command below to check for outdated dependencies.

mvn versions:display-dependency-updates

# Setting Up Your Authentication:

Make sure you have your LambdaTest credentials with you to run test automation scripts. You can get these credentials from the LambdaTest Automation Dashboard or by your LambdaTest Profile.

Step 2: Set LambdaTest Username and Access Key in environment variables.

# For Linux/macOS:

export LT_USERNAME="YOUR_USERNAME" 
export LT_ACCESS_KEY="YOUR ACCESS KEY"

# For Windows:

set LT_USERNAME="YOUR_USERNAME" 
set LT_ACCESS_KEY="YOUR ACCESS KEY"

To run the Tests:

mvn test -D suite=parallel.xml

mvn test

# Run Parallel Tests:

Here is an xml file location `src/test/java/parallel.xml` which would help you to run parallel test on different devices and browser at the same time.
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd">
<suite thread-count="100" name="Mobile" parallel="tests">

    <test name="AndroidAppTest">
        <parameter name="version" value="11" />
        <parameter name="platform" value="Android" />
        <parameter name="device" value="Galaxy Note20 Ultra 5G" />
        <classes>
            <class name="GameApp" />
        </classes>
    </test><!-- Test -->

    <test name="IOSAppTest">
        <parameter name="version" value="16" />
        <parameter name="platform" value="ios" />
        <parameter name="device" value="iPhone 14" />
        <classes>
            <class name="GameApp" />
        </classes>
    </test><!-- Test -->

    <test thread-count="20" parallel="classes" name="WindowTest">
        <classes>
            <class name="WindowsTest"/>
        </classes>
    </test><!-- Test -->
    <test thread-count="20" parallel="classes" name="WindowTest1">
        <parameter name="platform" value="Windows"/>
        <parameter name="browser" value="Chrome"/>
        <classes>
            <class name="WindowsAndMacOS"/>
        </classes>
    </test> <!-- Test -->
    <test thread-count="20" parallel="classes" name="MacTest">
        <parameter name="platform" value="macOS Sonoma"/>
        <parameter name="browser" value="safari"/>
        <classes>
            <class name="WindowsAndMacOS"/>
        </classes>
    </test> <!-- Test -->
</suite>

