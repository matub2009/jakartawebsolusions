# jakartawebsolusions
automationpractice
package transisi;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.Select;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.testng.Assert;
import org.testng.annotations.Test;

public class signup {
	WebDriver driver;
	
  @Test
  public void loadDriver() throws InterruptedException {
	  System.setProperty("webdriver.gecko.driver", "D:\\Software\\Otomasi\\jar file\\geckodriver.exe");
	  driver = new FirefoxDriver();
	  driver.get("http://automationpractice.com");
	  WebDriverWait wait = new WebDriverWait(driver, 30);
	  
	//Click on Sign in
	  driver.findElement(By.xpath("/html/body/div/div[1]/header/div[2]/div/div/nav/div[1]/a")).click();
		
	//Enter email address
	  driver.findElement(By.id("email_create")).sendKeys("asd@yopmail.com");
	  driver.findElement(By.xpath("/html/body/div/div[2]/div/div[3]/div/div/div[1]/form/div/div[3]/button/span")).click();
	  
	//input radio button
	  Thread.sleep(200);
	  wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//*[@id='uniform-id_gender1']")));
	  driver.findElement(By.xpath("//*[@id='uniform-id_gender1']")).click();
	  driver.findElement(By.id("customer_firstname")).sendKeys("saya");
	  driver.findElement(By.id("customer_lastname")).sendKeys("aja");
	  driver.findElement(By.id("passwd")).sendKeys("qwert");
	  
	//Using Select class for selecting value from dropdown
	  Thread.sleep(2000);
	//wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//*[@id='days']")));
	  Select dropdown = new Select(driver.findElement(By.id("days")));
	  dropdown.selectByValue("1");
	  
	  Thread.sleep(2000);
	//wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//*[@id='months']")));
	  Select dropdown1 = new Select(driver.findElement(By.id("months")));
	  dropdown1.selectByValue("9");
	  
	  Thread.sleep(2000);
	//wait.until(ExpectedConditions.visibilityOfElementLocated(By.xpath("//*[@id='years']")));
	  Select dropdown2 = new Select(driver.findElement(By.id("years")));
	  dropdown2.selectByValue("1985");
	  
	//input
	  driver.findElement(By.id("firstname")).sendKeys("saya");
	  driver.findElement(By.id("lastname")).sendKeys("aja");
	  driver.findElement(By.id("company")).sendKeys("anginribut");
	  driver.findElement(By.id("address1")).sendKeys("3801 Chalk Butte Rd, Cut Bank, MT 59427, United States");
	  driver.findElement(By.id("address2")).sendKeys("buntu");
	  driver.findElement(By.id("city")).sendKeys("hrg");
	  Thread.sleep(200);
	  
	  Select dropdown3 = new Select(driver.findElement(By.id("id_state")));
	  dropdown3.selectByValue("3");
	  
	  driver.findElement(By.id("postcode")).sendKeys("12240");
	  
	  Select dropdown4 = new Select(driver.findElement(By.id("id_country")));
	  dropdown4.selectByValue("21");
	  
	  driver.findElement(By.id("other")).sendKeys("(347) 466-74321");
	  driver.findElement(By.id("phone")).sendKeys("(347) 466-7432");
	  driver.findElement(By.id("phone_mobile")).sendKeys("(347) 466-74321");
	  driver.findElement(By.id("alias")).sendKeys("Gangbuntu");
	  Thread.sleep(200);
	  
	  driver.findElement(By.xpath("/html/body/div/div[2]/div/div[3]/div/div/form/div[4]/button/span")).click();
	  
	  wait.until(ExpectedConditions.visibilityOfAllElementsLocatedBy(By.xpath("/html/body/div/div[2]/div/div[3]/div/h1")));
	  String actual = driver.findElement(By.xpath("/html/body/div/div[2]/div/div[3]/div/h1")).getText();
	  System.out.println(actual);
	  Assert.assertEquals(actual, "My account");
	  
  }
}
