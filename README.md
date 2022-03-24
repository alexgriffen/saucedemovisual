## saucedemo

This code is provided on an "AS-IS” basis without warranty of any kind, either express or implied, including without limitation any implied warranties of condition, uninterrupted use, merchantability, fitness for a particular purpose, or non-infringement. Your tests and testing environments may require you to modify this framework. Issues regarding this framework should be submitted through GitHub. For questions regarding Sauce Labs integration, please see the Sauce Labs documentation at https://wiki.saucelabs.com/. This framework is not maintained by Sauce Labs Support. For the most part, this example assumes you're using a Mac.

### Environment Setup

1. Global Dependencies
    * This project assumes you have a valid value for $JAVA_HOME set in your environment - [here's an article](https://www.baeldung.com/java-home-on-windows-7-8-10-mac-os-x-linux) that can help if needed
    * [Install Maven](https://maven.apache.org/install.html)
    * Or Install Maven with [Homebrew](http://brew.sh/)
    ```
    $ brew install maven
    ```
2. Sauce and Sauce Visual Credentials
    * In the terminal export your Sauce Labs Credentials as environmental variables:
      * to save yourself some time in the future, save these values in ~/.bash_profile (and run $ source ~/.bash_profile when you start up your IDE) or better yet ~/.zshrc 
    ```
    $ export SAUCE_USERNAME=<your Sauce Labs username>
    $ export SAUCE_ACCESS_KEY=<your Sauce Labs access key>
    $ export SCREENER_API_KEY=<your Screener.io api key>
    $ export BUILD_TAG=$(python -c 'import datetime; print datetime.datetime.now()')
    ```
   NOTE: BUILD_TAG in this case sets the system date/time as the Build variable's value - it's not strictly required, but it's nice to help keep track of individual builds
3. Project Dependencies
	* Check that Packages are available
	```
	$ cd saucedemovisual
	$ mvn test-compile
	```
	* You may also want to run the command below to check for outdated dependencies. Please be sure to verify and review updates before editing your pom.xml file. The updated packages may or may not be compatible with your code.
	```
	$ mvn versions:display-dependency-updates
	```
### Running Tests

1. Kick tests off with ```$ mvn test```
2. Run ```export BUILD_TAG=$(python -c 'import datetime; print datetime.datetime.now()')``` again to reset the system date/time value in BUILD_TAG (or reload your ```~/.bash_profile``` or ```~/.zshrc``` file)
3. After you've run the first set of tests, go into Screener and accept the snapshots, creating the Baselines for each snapshot.
4. After the Baselines are set, go into src/test/java/com.swaglabs/Tests/LoginValidUser.java, and look for the blocks of commented sneaky javascript. Uncomment those blocks, and re-run the tests.
5. Those blocks of javascript will cause your next test to fail, and provide you with some great examples of how Visual works.

[Sauce Labs Dashboard](https://saucelabs.com/beta/dashboard)

### Advice/Troubleshooting
1. It may be useful to use a Java IDE such as IntelliJ or Eclipse to help troubleshoot potential issues. 
2. There may be additional latency when using a remote webdriver to run tests on Sauce Labs. Timeouts or Waits may need to be increased.
    * [Selenium tips regarding explicit waits](https://wiki.saucelabs.com/display/DOCS/Best+Practice%3A+Use+Explicit+Waits)

### Resources
##### [Sauce Labs Documentation](https://wiki.saucelabs.com/)

##### [SeleniumHQ Documentation](http://www.seleniumhq.org/docs/)

##### [TestNg Documentation](http://testng.org/javadocs/index.html)

##### [Java Documentation](https://docs.oracle.com/javase/7/docs/api/)

##### Stack Overflow:
* [Related Stack Overflow Threads](http://stackoverflow.com/questions/27355003/advise-on-hierarchy-for-element-locators-in-selenium-webdriver)
