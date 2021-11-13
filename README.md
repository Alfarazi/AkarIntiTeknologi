# AkarIntiTeknologi

package qaautomation.AkarIntiTeknologi;

import java.time.Duration;
import java.util.Set;

import org.apache.commons.collections4.IteratorUtils;
import org.apache.commons.io.input.WindowsLineEndingInputStream;
import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WindowType;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.SendKeysAction;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.Test;

import com.mifmif.common.regex.util.Iterator;

import io.github.bonigarcia.wdm.WebDriverManager;

public class TestAkarInti {
	
	ThreadLocal<WebDriver> driver = new ThreadLocal<WebDriver>();
	ThreadLocal<WebDriverWait> explicitWait = new ThreadLocal<WebDriverWait>();
	
	@Test
	public void setUp() throws InterruptedException{
		WebDriverManager.chromedriver().setup();
		driver.set(new ChromeDriver());
		driver.get().manage().window().maximize();//maximize window
		driver.get().manage().deleteAllCookies();//delete all cookies
		driver.get().get("https://ultimateqa.com/automation/");
		explicitWait.set(new WebDriverWait(driver.get(), Duration.ofSeconds(3000)));
		
		driver.get().findElement(By.xpath("//a[normalize-space()='Fake Pricing Page']")).click();
		Thread.sleep(3000);
		
		driver.get().findElement(By.xpath("//a[normalize-space()='Facebook']")).click();
		Thread.sleep(3000);
		
		driver.get().navigate().back();
		System.out.println(driver.get().getTitle());
		Thread.sleep(3000);
		
//		driver.get().findElement(By.xpath("//input[@placeholder='Search …']")).sendKeys("QA test");
//		driver.get().findElement(By.xpath("//input[@placeholder='Search …']")).sendKeys(Keys.ENTER);
//		Thread.sleep(3000);
		
		driver.get().quit();
       
    

	}

}
