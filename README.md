# software_testing_selenuim

Selenium hands on tutorial
1.	Get control of webpage using webdriver
2.	with help of webdrivers API, function, method : findElement
3.	Then use locator techniques mentioned below, to identify and reach the UI element with help of webdrivers API, function, method : findElement

Locator Techniques
way you establish communication with UI elements on the website
1.	ID
2.	ClassName
3.	Name
4.	TagName
5.	Link
6.	PartialLink
7.	Xpath
8.	CSS

Xpath is the Xml path
Two types:
1.	Absolute – begins from root not=de and traverses node to node till it reaches the end. Starts with / 
2.	Relative – doesn’t have to start with root node . starts with //
customization of xpath 
syntax:
//tagname[@attribrute='value']
Functions supported by xpath : starts-with, contains and text
1.	sytanx for xpath start-with 
 //tagname[starts-with(@attribute,'value')]

2.	sytanx for xpath contains
 //tagname[contains(@attribute,'value')]


3.		 sytanx for xpath text
		 //tagname[text() ='Put your search text here')]

Logical operators support : ‘And’ ‘or’


	
//condition 1: here both conditions are true so print list =1
		List <WebElement> myList = driver.findElements(By.xpath("//input[@type='submit' and @name='btnLogin']"));
	   System.out.println("Size of the list is " + myList.size());
		
	    //condition 2 : here only one condition is true so prints list = 0
	    List <WebElement> myList = driver.findElements(By.xpath("//input[@type='submit' and @name='btnReset']"));
	    System.out.println("Size of the list is " + myList.size());	
	    
		//condition 3 : 
		here because it is or prints list = 2 because either submit or btnReset
	    List <WebElement> myList = driver.findElements(By.xpath("//input[@type='submit' or @name='btnReset']"));
	    System.out.println("Size of the list is " + myList.size());	
		

For tag name instead of input you can put *  - the * represents a regular expression

CSS Selectors  

•	Tag and ID
•	Tag and class
•	Tag and attribute
•	Tag class and attribute





List did not work


Alert handling
Use switchto() function

Three types:

1.	Simple alerts – eg. Pop up with just “ok” option

 driver.findElement(By.xpath("//*[@id=\"alertButton\"]")).click();
	    driver.switchTo().alert().accept();

2.	Confirmation alert: Alerts/Pop up with two options : “ok” and “cancel” . eg amazon cart payment option

driver.findElement(By.xpath("//*[@id=\"confirmButton\"]")).click();
	   	 //driver.switchTo().alert().accept();
	 driver.switchTo().alert().dismiss();

3.	Prompt alert: Alerts/ Pop up which asks you to enter some info and “ok” button.


//for demoqa.com THIS LAST POP UP NOT WORKING 
		driver.findElement(By.xpath("//*[@id=\"promtButton\"]")).click();
		driver.switchTo().alert().sendKeys("abc");
	    //driver.switchTo().alert().accept();
		
		/*for guru99 opens website, types in 12345 in prompt and clicks submit button. then clicks on ok of pop 
		then clicks on ok of pop up to delete customer.*/
		
	     //driver.findElement(By.xpath("//input[@name='cusid']")).sendKeys("12345");
	      
	      
	              //driver.findElement(By.xpath("/html/body/form/table/tbody/tr[3]/td[2]/input[1]")).click();
	     // driver.findElement(By.xpath("//input[@name='submit']")).click();
	     // driver.switchTo().alert().accept();




Guru 99:
How to handle Alert in Selenium WebDriver
Alert interface provides the below few methods which are widely used in Selenium Webdriver.
1) void dismiss() // To click on the ‘Cancel’ button of the alert.
driver.switchTo().alert().dismiss();
2) void accept() // To click on the ‘OK’ button of the alert.
driver.switchTo().alert().accept();
3) String getText() // To capture the alert message.
driver.switchTo().alert().getText();
4) void sendKeys(String stringToSend) // To send some data to alert box.
driver.switchTo().alert().sendKeys("Text");


Frames and window handling
Frames : use switchto() function 
              /*
* first you need to reach the frame since the text filed in inside the              frame 
		 * then find the text field and write "java". 
		 */
	    driver.switchTo().frame(driver.findElement(By.className("demo-frame")));
	   
 driver.findElement(By.xpath("//*[@id=\"tags\"]")).sendKeys("java");
	  
//driver.findElement(By.id("tags")).sendKeys("java");

Windows:

Guru99
How to handle Selenium Pop-up window using Webdriver
In Selenium web driver there are methods through which we can handle multiple windows.
Driver.getWindowHandles();
To handle all opened windows by web driver, we can use “Driver.getWindowHandles()” and then we can switch window from one window to another in a web application. Its return type is Iterator<String>.
Driver.getWindowHandle();
When the site opens, we need to handle the main window by driver.getWindowHandle(). This will handle the current window that uniquely identifies it within this driver instance. Its return type is String.







Actions class Keyboard and Mouse Events

Mousehover


//create new object act_object
		Actions act_object = new Actions(driver);
		
		//use the object
		act_object.moveToElement(driver.findElement(By.xpath("//*[@id=\"global-nav\"]/nav/div/ul[2]/li[2]/a"))).perform();
		//act_object.moveToElement(driver.findElement(By.xpath("//a[@contains(text(),'Contribute')]"))).perform();
	
		act_object.moveToElement(driver.findElement(By.linkText("Documentation"))).perform();
		act_object.click().perform();

Page up and down with keys class

//create new object act_object
		Actions act_object = new Actions(driver);
		
		//use the object and keys class
		act_object.keyDown(Keys.PAGE_DOWN).perform();
        //YOU CAN ALSO USE BELOW sendKeys OPTION ALSO
		//act_object.sendKeys(Keys.PAGE_DOWN).perform();
        
        Thread.sleep(10000);
        act_object.sendKeys(Keys.PAGE_UP).perform();



Shift Key to type all caps is UserID

HOver the mouse over the "UserID" field.
Click on the "UserID" field
Press down and hold the "Shift" button.
Type "HCL TECH" in caps in the "UserID" field

//create new object act_object
		Actions act_object = new Actions(driver);
		
		//use the object
		//act_object.moveToElement(driver.findElement(By.xpath("//*[@id=\"global-nav\"]/nav/div/ul[2]/li[2]/a"))).perform();
		//step 1 : mouse hover
		//act_object.moveToElement(driver.findElement(By.xpath("//input[@name='uid']"))).perform();
		//optionally find by name 
		//act_object.moveToElement(driver.findElement(By.name("uid"))).perform();
		
		//step 2: mouse click
		//act_object.click().perform();
		
		//step 3 : press down and hold shift key and type hcltech in userid field
		//.keyDown(Keys.SHIFT).sendKeys("hcl tech").perform();
	
		//OPTION 2 : instead of breaking up as above perform a series of actions
		act_object.moveToElement(driver.findElement(By.name("uid"))).click().keyDown(Keys.SHIFT).sendKeys("hcl tech").perform();


composite key actions : eg control “a”. 

//create new object act_object
		Actions act_object = new Actions(driver);
		
		//use the object
		
		//hovermouse over "UserID", click it, hold shifte key down and type hcl tech in UserID field
		act_object.moveToElement(driver.findElement(By.name("uid"))).click().keyDown(Keys.SHIFT).sendKeys("hcl tech").perform();
		
		// after above, press control key and a to select the text "hcl tech"
		act_object.keyDown(Keys.CONTROL).sendKeys("a").perform();
	
	//this is used when there is a sequence of commands. But not always needed sinve the 
		//perform command will call the "build" command explicitly.
		act_object.build().perform();

drag and drop 
http://demo.guru99.com/test/drag_drop.html

String url = "https://demo.guru99.com/test/drag_drop.html";
		WebDriver driver;
		System.setProperty("webdriver.chrome.driver","C:\\Users\\eshani.shah\\OneDrive - HCL Technologies Ltd\\Documents\\selenium\\chromedriver_win32\\chromedriver.exe");
	    
		driver = new ChromeDriver();
		// to maximize the window when the website opens use before getting web site
		driver.manage().window().maximize();  
		driver.get(url);
		
		WebElement source_WE = driver.findElement(By.xpath("//*[@id=\"fourth\"]/a"));
		WebElement destination_WE = driver.findElement(By.xpath("//*[@id=\"amt7\"]/li"));
		
		//create new object act_object
		Actions act_object = new Actions(driver);
		
		//use the object to drag and drop the amount 5000 on the debit side in amount
		act_object.dragAndDrop(source_WE,destination_WE).perform();
		


Web Driver Wait
Selenium Wait:
•	Implicit Wait : for every web element on the page
•	Explicit Wait  : associated with/for a specific web element only. 
•	Fluent Wait: form of explicit wait and define a pulling interval to check for status.
https://www.selenium.dev/downloads/


JavaScript Executor
JavaScript Executor is an interface provided by selenium that gives a mechanism to execute JavaScript through Selenium WebDriver.
It provides 2 methods to run Java Scripts

- executeScript : This function will execute a synchronour piece of JavaScript in the context of the currently selected frame or eindow in Selenium. Used More often
- executeAsyncScript :this method executes JS in the context of the currently selected frame or window in selenium. The script used in this method runs in the body of an anonymous function (a function without a name). User can also pass complicated arguments to it.
•	Different locator techniques such as id, name, xpath, linkText, partialLinkText, className, tagName are used to locate elemen and perform operations on them
•	In some scenarios, the above mentioned techniques do not work
•	In such cases we take the help of JavaScriptExecutor to perform the desired task

JavaScript Log in Demo

public class LoginDemo {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		String url = "http://demo.guru99.com/V4/";
		WebDriver driver;
		System.setProperty("webdriver.chrome.driver","C:\\Users\\eshani.shah\\OneDrive - HCL Technologies Ltd\\Documents\\selenium\\chromedriver_win32\\chromedriver.exe");
	    
		driver = new ChromeDriver();
		// to maximize the window when the website opens use before getting web site
		driver.manage().window().maximize();  
		driver.get(url);
	
		//using locator techniques
		/*driver.findElement(By.name("uid")).sendKeys("mngr88613");
		driver.findElement(By.name("password")).sendKeys("YzubadA");
		driver.findElement(By.name("btnLogin")).click();*/
	
		//JavaScript executor
		//important to end the JavaScript code with semicolon and enclose in double quotes
		JavascriptExecutor js = (JavascriptExecutor) driver;
		
		WebElement name_WE = driver.findElement(By.name("uid"));
		js.executeScript("arguments[0].value='mngr88613';",name_WE);
	
		
		WebElement password_WE = driver.findElement(By.name("password"));
		js.executeScript("arguments[0].value='YzubadA';",password_WE);
	
	
		WebElement button_WE = driver.findElement(By.name("btnLogin"));
		js.executeScript("arguments[0].click();",button_WE);
		
		
	}

}

JavaScript using ID
public static void main(String[] args) {
		// TODO Auto-generated method stub
		String url = "https://www.seleniumeasy.com/";
		WebDriver driver;
		System.setProperty("webdriver.chrome.driver","C:\\Users\\eshani.shah\\OneDrive - HCL Technologies Ltd\\Documents\\selenium\\chromedriver_win32\\chromedriver.exe");
	    
		driver = new ChromeDriver();
		// to maximize the window when the website opens use before getting web site
		driver.manage().window().maximize();  
		driver.get(url);
	
		//using locator techniques
		/*driver.findElement(By.name("uid")).sendKeys("mngr88613");
		driver.findElement(By.name("password")).sendKeys("YzubadA");
		driver.findElement(By.name("btnLogin")).click();*/
	
		//JavaScript executor
		//important to end the JavaScript code with semicolon and enclose in double quotes
		JavascriptExecutor js = (JavascriptExecutor) driver;
		
		
		js.executeScript("document.getElementById('edit-search-block-form--2').value='JavaScript';");
		
		WebElement search_WE = driver.findElement(By.className("icon glyphicon glyphicon-search"));
		// below click is no
		js.executeScript("arguments[0].click();",search_WE);
		
		
	}

}

JavaScript Navigate and scroll

public class NavigateAndScroll {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		String url = "http://demo.guru99.com/V4/";
		WebDriver driver;
		System.setProperty("webdriver.chrome.driver","C:\\Users\\eshani.shah\\OneDrive - HCL Technologies Ltd\\Documents\\selenium\\chromedriver_win32\\chromedriver.exe");
	    
		driver = new ChromeDriver();
		// to maximize the window when the website opens use before getting web site
		driver.manage().window().maximize();  
		driver.get(url);
	
		//using locator techniques
		/*driver.findElement(By.name("uid")).sendKeys("mngr88613");
		driver.findElement(By.name("password")).sendKeys("YzubadA");
		driver.findElement(By.name("btnLogin")).click();*/
	
		//JavaScript executor
		//important to end the JavaScript code with semicolon and enclose in double quotes
		JavascriptExecutor js = (JavascriptExecutor) driver;
		
		WebElement name_WE = driver.findElement(By.name("uid"));
		js.executeScript("arguments[0].value='mngr88613';",name_WE);
	
		
		WebElement password_WE = driver.findElement(By.name("password"));
		js.executeScript("arguments[0].value='YzubadA';",password_WE);
	
	    //click on log in button using JS
		/*WebElement button_WE = driver.findElement(By.name("btnLogin"));
		js.executeScript("arguments[0].click();",button_WE);*/
		
		js.executeScript("window.location = 'https://www.selenium.dev/'");
		js.executeScript("window.scrollBy(0, 1500);");
		
		
		
	}

}
MODAL not alert
package JavaScriptDemo;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;


public class JavaScriptID2 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		String url = "https://formy-project.herokuapp.com/modal";
		WebDriver driver;
		System.setProperty("webdriver.chrome.driver","C:\\Users\\eshani.shah\\OneDrive - HCL Technologies Ltd\\Documents\\selenium\\chromedriver_win32\\chromedriver.exe");
	    
		driver = new ChromeDriver();
		// to maximize the window when the website opens use before getting web site
		driver.manage().window().maximize();  
		driver.get(url);
	
		
		JavascriptExecutor js = (JavascriptExecutor) driver;
		
		//js.executeScript("document.getElementById('close-button').value='JavaScript';");
		//js.executeScript("document.getElementById('close-button');");
		
		//locator and switchtoAlert will not work here since it is modal button.
		//need to use JavaScript Executor
		
		WebElement modal_WE = driver.findElement(By.id("modal-button"));
		js.executeScript("arguments[0].click();",modal_WE);
		
		WebElement close_WE = driver.findElement(By.id("close-button"));
		// below click is not working
		js.executeScript("arguments[0].click();",close_WE);
		
		
	}

}


Capturing screenshots and generating reports

Test Report: Captures execution status. Which tests passed , which failed, capture screen shots and keep as logs
Create a separate function and call it from anywhere using the captureScreen class.  
Since it is a static method 
Make object in the function,
Create file (using java files) capture the screen first then creat e afile which points to the screenshot 
import org.openqa.selenium.chrome.ChromeDriver;

public class captureScreen {

	public static void main(String[] args) throws Exception {
		// TODO Auto-generated method stub
		String url = "https://www.selenium.dev/";
		String filePath = "C:\\Users\\eshani.shah\\OneDrive - HCL Technologies Ltd\\Documents\\selenium\\ScreenshotsSelenium\\Screenshot1.png";
		
		WebDriver driver;
		System.setProperty("webdriver.chrome.driver","C:\\Users\\eshani.shah\\OneDrive - HCL Technologies Ltd\\Documents\\selenium\\chromedriver_win32\\chromedriver.exe");
	    
		driver = new ChromeDriver();
		// to maximize the window when the website opens use before getting web site
		driver.manage().window().maximize();  
		driver.get(url);
		
		captureScreen.captureScreenshot(driver, filePath);
	}

	public static void captureScreenshot(WebDriver driver, String filePath) throws Exception {
	
		//create object 
		TakesScreenshot screenShot = (TakesScreenshot) driver;
		
		//Create file (using java files) capture the screen first then create a file which points to the screenshot 
		File sourceFile = screenShot.getScreenshotAs(OutputType.FILE);
		File destinationFile = new File(filePath);
		
		FileUtils.copyFile(sourceFile, destinationFile);
		
	}
	
	
}



Auto IT – tool how to install, use and how it helps us
https://tus.io/demo.html
used above website for demo.

Selenium is web based and if you need to operate windows operations like uploading resume to website etc. selenium cannot do it by itself. Need to use Auto IT along with selenium for that
Selenium provides excellent integration capability with tools like
AutoIT  which can cater to these kind of scenarios.
Code written in Auto IT can be embedded inside selenium which handled these kind of windows based control
Auto IT is a freeware
Download, install and start using it.
It is a scripting language designed for automating windows GUI applications
It uses a combination of simulated keystroked, mouse movement and window/control manipulation in order to automate tasks in a way not possible or reliable with other languages
Auto IT is just another automation tool like selenium but unlike selenium it is used for desktop automation rather than web automation
It is a powerful tool and it just does not automate desktop windows, buttons and form, it automates mouse movements and keystrokes too

Two things to install
•	AutoIT Editor and 
•	AutoIT Element Identifier
Easy to learn
simulates key strokes
simulates mouse events
scripts can be compiled into standalone executable which can be embedded in selenium
Handles many types of windows control
AutoIT Editor
 

AutoIT Element Identifier
 
 
1.	Focuses on the element you need to work on
2.	Gives the path of file you want to upload
3.	Clicks on the “open” button to upload the file
Use the finder tool to drag and drop on the element you want to focus on. Then use the element identifier tool to give you details for “title” “controlID etc.
Then save the file you created in the AutoIT editor
Then right click on the file and compile it , either 64 bit or if you have 32 bit, then use 84 bit.
Then go back to eclipse and embed this file as shown in code. 
package FileUploadDemo;

import java.io.IOException;

import org.openqa.selenium.By;
import org.openqa.selenium.JavascriptExecutor;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;

public class FileUploadDemo {

	public static void main(String[] args) throws IOException {
		// TODO Auto-generated method stub

		String url = "https://tus.io/demo.html";
		WebDriver driver;
		System.setProperty("webdriver.chrome.driver","C:\\Users\\eshani.shah\\OneDrive - HCL Technologies Ltd\\Documents\\selenium\\chromedriver_win32\\chromedriver.exe");
		
		driver = new ChromeDriver();
		// to maximize the window when the website opens use before getting web site
		driver.manage().window().maximize();  
		driver.get(url);
	
		//this code does not work so use the actions class
	    //driver.findElement(By.id("js-file-input")).click();
		JavascriptExecutor js = (JavascriptExecutor) driver;
		js.executeScript("window.location = 'https://tus.io/demo.html'");
		js.executeScript("window.scrollBy(0, 650);");
	    
		//ACTIONS CLASS USED HERE
		 
		Actions action = new Actions(driver);
		//hover mouse over "choosefile", click it, 
				action.moveToElement(driver.findElement(By.id("js-file-input"))).perform();
				action.click().perform();
				
				//embed AutoIt file here
				//give the path of the saved and compiled executable file written in AutoIT here after exec
				Runtime.getRuntime().exec("");
	}

----------------------------------------------------------------------


