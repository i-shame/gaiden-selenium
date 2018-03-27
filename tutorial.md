# Selenium Tutorial

> Selenium is an open-source and a portable automated software testing tool for testing web applications. It has capabilities to operate across different browsers and operating systems. Selenium is not just a single tool but a set of tools that helps testers to automate web-based applications more efficiently.

Let us now understand each one of the tools available in the Selenium suite and their usage.

| Tool | Description  |
| :---: | :---|
| Selenium **IDE** | Selenium **I**ntegrated **D**evelopment **E**nvironment (IDE) is a **Firefox** plugin that lets testers to record their actions as they follow the workflow that they need to test. |
| Selenium **RC** |   Selenium **R**emote **C**ontrol (RC) was the flagship testing framework that allowed more than simple **browser actions** and **linear execution**. It makes use of the full power of programming languages such as **Java**, **C#**, **PHP**, **Python**, **Ruby** and **PERL** to create more complex tests. |
| Selenium **WebDriver** |    Selenium **WebDriver** is the successor to Selenium RC which sends commands directly to the browser and retrieves results. |
| Selenium **Grid** |    Selenium **Grid** is a tool used to **run parallel tests across different machines and different browsers simultaneously** which results in minimized execution time. |

## Selenium - IDE

- The Selenium-IDE (Integrated Development Environment) is an easy-to-use Firefox plug-in to develop Selenium test cases. It provides a Graphical User Interface for recording user actions using Firefox which is used to learn and use Selenium, but it can only be used with Firefox browser as other browsers are not supported.
- Launch Firefox and navigate to the following URL - [http://seleniumhq.org/download/](http://seleniumhq.org/download/ "http://seleniumhq.org/download/"). Under the Selenium IDE section, click on the link then Install [Selenium IDE – Add-ons for Firefox](https://addons.mozilla.org/en-US/firefox/addon/selenium-ide/ "https://addons.mozilla.org/en-US/firefox/addon/selenium-ide/")
![2018-03-27_10-50-25](images\2018-03-27_10-50-25.png)

The Selenium IDE can now be accessed by navigating
![2018-03-27_10-52-58](images\2018-03-27_10-52-58.png)

## Selenium - Environment Setup

In order to **develop Selenium RC or WebDriver scripts**, users have to ensure that they have the **initial configuration** done. Setting up the environment involves the following steps.

- **Download and Install Java**: We need to have JDK (Java Development Kit) installed in order to work with Selenium WebDriver/Selenium. Let download, install and config JAVA_HOME  [jdk8-downloads](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html "http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html")
- **Download and Configure Eclipse**: Navigate to [Eclipse IDE for Java EE Developers](https://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/oxygen3 "https://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/oxygen3") and download the appropriate file based on your OS architecture
- **Download and Configure Selenium RC, Selenium WebDriver**: Navigate to the [selenium downloads of all the Selenium components](http://selenium-release.storage.googleapis.com/index.html "http://selenium-release.storage.googleapis.com/index.html") and download latest releases file based on your OS architecture
![2018-03-27_11-16-16](images\2018-03-27_11-16-16.png)

## Selenium - Remote Control 

	Since Selenium 3.x, Selenium RC is Officially Dead – Long Live WebDriver

[selenium-3-now-officially-available](https://www.joecolantonio.com/2016/10/13/selenium-3-now-officially-available/ "https://www.joecolantonio.com/2016/10/13/selenium-3-now-officially-available/")

[selenium-30-release-testers-say-buh-bye-selenium-rc](https://techbeacon.com/selenium-30-release-testers-say-buh-bye-selenium-rc "https://techbeacon.com/selenium-30-release-testers-say-buh-bye-selenium-rc")

- Selenium **R**emote **C**ontrol (RC) was the main Selenium project that sustained for a long time before Selenium **WebDriver**(Selenium **2.0**) came into existence. **Selenium RC** is **hardly in use**, as **WebDriver** offers **more powerful features**. 

## Selenium - Webdriver

**WebDriver** is a tool for automating testing web applications. It is popularly known as **Selenium 2.0**. **WebDriver** uses a different underlying framework, while Selenium RC uses JavaScript Selenium-Core embedded within the browser which has got some limitations. **WebDriver** interacts directly with the browser without any intermediary, unlike Selenium RC that depends on a server. It is used in the following context −

- **Multi-browser testing** including improved functionality for browsers which is not well-supported by Selenium RC (Selenium 1.0).
- Handling multiple **frames**, multiple **browser windows**, **popups**, and **alerts**.
- Complex page **navigation**.
- Advanced user navigation such as **drag-and-drop**.
- **AJAX-based** UI elements.

![Selenium Webdriver Architecture](images\selenium_ide_92.jpg)
###Scripting using WebDriver

The way to write a sample script using WebDriver

- Download the driver based on the type of your OS, unzip the exe file and place it in a folder which has to be referred
![2018-03-27_14-33-33](images\2018-03-27_14-33-33.png)
- Add reference to all the JAR's of Selenium WebDriver Library folder to **Configure Build Path**
![2018-03-27_14-15-04](images\2018-03-27_14-15-04.png)
- Now it is time for coding. Let's execute the following code by clicking **Run** (**Ctrl+F11**). The output of the above script would be printed in Console.

```
package sel;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;

public class WebDriverDemo {
	public static void main(String[] args) {
		System.setProperty("webdriver.gecko.driver", "C:\\lab\\dev\\drivers\\geckodriver.exe");
		WebDriver driver = new FirefoxDriver();
		// Puts an Implicit wait, Will wait for 10 seconds before throwing exception
		driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);

		// Launch website
		driver.navigate().to("http://www.calc-site.com/");

		// Maximize the browser
		driver.manage().window().maximize();

		// Enter value in the calc_display
		driver.findElement(By.id("calc_display")).sendKeys("12*34");

		// Click on button equal
		driver.findElement(By.xpath("//*[@id='calculator']/div[2]/table/tbody/tr[5]/td[3]/input")).click();

		// Get the Result Text based on its xpath
		String result = driver.findElement(By.xpath("//*[@id='calc_display']")).getAttribute("value");

		// Print a Log In message to the screen
		System.out.println(" The Result is " + result);

		// Close the Browser.
		driver.close();
	}
}

```

### Most Used Commands

*The following table lists some of the most frequently used commands in WebDriver along with their syntax.*

Command  | Description 
--- | --- 
driver.get("URL") | To navigate to an application.
element.sendKeys("inputtext") | Enter some text into an input box.
element.clear() | Clear the contents from the input box.
select.deselectAll() | Deselect all OPTIONs from the first SELECT on the page.
select.selectByVisibleText("some text") | Select the OPTION with the input specified by the user.
driver.switchTo().window("windowName") | Move the focus from one window to another.
driver.switchTo().frame("frameName") | Swing from frame to frame.
driver.switchTo().alert() | Helps in handling alerts.
driver.navigate().to("URL") | Navigate to the URL.
driver.navigate().forward() | To navigate forward.
driver.navigate().back() | To navigate back.
driver.close() | Closes the current browser associated with the driver.
driver.quit() | Quits the driver and closes all the associated window of that driver.
driver.refresh() | Refreshes the current page. 

### Locating Elements
*The following table lists all the Java syntax for locating elements in Selenium WebDriver.*

Syntax | Description
--- | ---
driver.findElement(By.id (<element ID>)) | Locates an element using the ID attribute
driver.findElement(By.name (<element name>)) | Locates an element using the Name attribute
driver.findElement(By.className (<element class>)) | Locates an element using the Class attribute
driver.findElement(By.tagName (<htmltagname>)) | Locates an element using the HTML tag
driver.findElement(By.linkText (<linktext>)) | Locates a link using link text
driver.findElement(By.partialLinkText (<linktext>)) | Locates a link using the link's partial text
driver.findElement(By.cssSelector (<css selector>)) | Locates an element using the CSS selector
driver.findElement(By.xpath (<xpath>)) | Locates an element using XPath query

### User Interactions
*Listed below are the different kinds of actions against those GUI objects −*

- [Text Box Interaction](https://www.tutorialspoint.com//selenium/selenium_textbox.htm)
- [Radio Button Selection](https://www.tutorialspoint.com//selenium/selenium_radio_button.htm)
- [Check Box Selection](https://www.tutorialspoint.com//selenium/selenium_check_box.htm)
- [Drop Down Item Selection](https://www.tutorialspoint.com//selenium/selenium_drop_down.htm)
- [Synchronization](https://www.tutorialspoint.com//selenium/selenium_synchronization.htm)
- [Drag &amp; Drop](https://www.tutorialspoint.com//selenium/selenium_drag_drop.htm)
- [Keyboard Actions](https://www.tutorialspoint.com//selenium/selenium_keyboard_actions.htm)
- [Mouse Actions](https://www.tutorialspoint.com//selenium/selenium_mouse_actions.htm)
- [Multi Select](https://www.tutorialspoint.com//selenium/selenium_multi_select.htm)
- [Find All Links](https://www.tutorialspoint.com//selenium/selenium_find_all_links.htm)

### Test design techniques
*There are various components involved in designing the tests*

- [Page Object Model](https://www.tutorialspoint.com//selenium/selenium_page_object_model.htm)
- [Parameterizing using Excel](https://www.tutorialspoint.com//selenium/selenium_parameterizing_using_excel.htm)
- [Log4j Logging](https://www.tutorialspoint.com//selenium/selenium_log4j_logging.htm)
- [Exception Handling](https://www.tutorialspoint.com//selenium/selenium_exception_handling.htm)
- [Multi Browser Testing](https://www.tutorialspoint.com//selenium/selenium_multi_browser_testing.htm)
- [Capture Screenshots](https://www.tutorialspoint.com//selenium/selenium_capture_screenshots.htm)
- [Capture Videos](https://www.tutorialspoint.com//selenium/selenium_capture_video.htm)

## Selenium - TestNG

*TestNG is a powerful testing framework, an enhanced version of JUnit which was in use for a long time before TestNG came into existence. NG stands for 'Next Generation'.*

- **Installing TestNG for Eclipse** : Launch Eclipse and select 'Install New Software'. Enter the URL as '**http://beust.com/eclipse**' and install **TestNG** 
![2018-03-27_15-27-09.png](images\2018-03-27_15-27-09.png)

### Scripting Using TestNG

- Launch Eclipse and create a 'New Java Project' with 'TestNG' Library 
![2018-03-27_15-43-10](images\2018-03-27_15-43-10.png)
- Then, time for coding. Let's execute the following code by right click on the created XML and select "Run As" >> "TestNG Suite"

`testng.FirstTest.java`

```
package testng;

import static org.testng.Assert.assertEquals;

import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;

public class FirstTest {
	WebDriver driver;

	@Test
	public void f() {
		// Enter value in the calc_display
		driver.findElement(By.id("calc_display")).sendKeys("12*34");
		// Click on button equal
		driver.findElement(By.xpath("//*[@id='calculator']/div[2]/table/tbody/tr[5]/td[3]/input")).click();
		// Get the Result Text based on its xpath
		String result = driver.findElement(By.xpath("//*[@id='calc_display']")).getAttribute("value");

		assertEquals(result, "408");
	}

	@BeforeTest
	public void beforeTest() {
		System.setProperty("webdriver.gecko.driver", "C:\\lab\\dev\\drivers\\geckodriver.exe");
		driver = new FirefoxDriver();
		// Puts an Implicit wait, Will wait for 10 seconds before throwing exception
		driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
		// Launch website
		driver.navigate().to("http://www.calc-site.com/");
		driver.manage().window().maximize();
	}

	@AfterTest
	public void afterTest() {
		// Close the Browser.
		driver.close();
	}

}
```

`test.xml`

```
<?xml version="1.0" encoding="UTF-8"?>
<suite name="Suite" parallel="false">
  <test name="Test">
    <classes>
      <class name="testng.FirstTest"/>
    </classes>
  </test>
</suite>
```

- The result of TestNG can also be seen in a this tab

![2018-03-27_15-52-53](images\2018-03-27_15-52-53.png)

### Annotations in TestNG
*Following are some of the benefits of using annotations. More about TestNG can be found [here](https://www.tutorialspoint.com/testng/index.htm)*

Annotation   | Description 
:--- | :--- 
@BeforeSuite | The annotated method will be run only once before all the tests in this suite have run.
@AfterSuite | The annotated method will be run only once after all the tests in this suite have run.
@BeforeClass | The annotated method will be run only once before the first test method in the current class is invoked.
@AfterClass | The annotated method will be run only once after all the test methods in the current class have run.
@BeforeTest | The annotated method will be run before any test method belonging to the classes inside the <test> tag is run.
@AfterTest | The annotated method will be run after all the test methods belonging to the classes inside the <test> tag have run.
@BeforeGroups | The list of groups that this configuration method will run before. This method is guaranteed to run shortly before the first test method that belongs to any of these groups is invoked.
@AfterGroups | The list of groups that this configuration method will run after. This method is guaranteed to run shortly after the last test method that belongs to any of these groups is invoked.
@BeforeMethod | The annotated method will be run before each test method.
@AfterMethod | The annotated method will be run after each test method.
@DataProvider | Marks a method as supplying data for a test method. The annotated method must return an Object[ ][ ] where each Object[ ] can be assigned the parameter list of the test method. The @Test method that wants to receive data from this DataProvider needs to use a dataProvider name equals to the name of this annotation.
@Factory | Marks a method as a factory that returns objects that will be used by TestNG as Test classes. The method must return Object[ ].
@Listeners | Defines listeners on a test class.
@Parameters | Describes how to pass parameters to a @Test method.
@Test | Marks a class or a method as part of the test.

## Selenium - Grid

*Selenium Grid is a tool that distributes the tests across multiple physical or virtual machines so that we can execute scripts in parallel (simultaneously)*

Selenium Grid has a Hub and a Node.

- **Hub** − The hub can also be understood as a server which acts as the central point where the tests would be triggered. A Selenium Grid has only one Hub and it is launched on a single machine once.
- **Node** − Nodes are the Selenium instances that are attached to the Hub which execute the tests. There can be one or more nodes in a grid which can be of any OS and can contain any of the Selenium supported browsers.

![Grid Architecture](images\selenium_ide_121.jpg)

### Working with Grid
`updating...`