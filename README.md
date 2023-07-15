# QA-Assignment-Sonali
package assignments;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.junit.AfterClass;
import org.junit.BeforeClass;
import org.junit.Test;

public class LoginTest {

    private static WebDriver driver;

    @BeforeClass
    public static void setUp() {
        // Set up Chrome WebDriver
    	System.setProperty("webdriver.chrome.driver",
				"E:\\Selenium\\New folder\\chromedriver.exe");
        ChromeOptions options = new ChromeOptions();
        options.addArguments("--headless"); // Run in headless mode (without UI)
        driver = new ChromeDriver(options);
        driver.get("https://www.facebook.com"); // Replace with your login page URL
    }

    @Test
    public void testSuccessfulLogin() {
        String username = "valid_username";
        String password = "valid_password";

        login(username, password);

        // Add assertions to validate successful login and access to the system
    }

    private void login(String username, String password) {
		// TODO Auto-generated method stub
		
	}

	@Test
    public void testInvalidCredentials() {
        String username = "invalid_username";
        String password = "invalid_password";

        login(username, password);

        // Add assertions to validate error message for invalid credentials
    }

    @Test
    public void testRetainFieldsAfterFailedLogin() {
        String username = "invalid_username";
        String password = "invalid_password";

        WebElement usernameField = driver.findElement(By.id("username"));
        WebElement passwordField = driver.findElement(By.id("password"));

        usernameField.sendKeys(username);
        passwordField.sendKeys(password);
        driver.findElement(By.id("login_button")).click();

        // Add assertions to validate that username and password fields retain their values
    }

    @Test
    public void testLoginButtonDisabled() {
        // Add assertions to validate that the login button is disabled when fields are empty
    }

    @Test
    public void testLoginButtonEnabled() {
        String username = "valid_username";
        String password = "valid_password";

        WebElement usernameField = driver.findElement(By.id("username"));
        WebElement passwordField = driver.findElement(By.id("password"));

        usernameField.sendKeys(username);
        passwordField.sendKeys(password);

        // Add assertions to validate that the login button is enabled when fields have valid input
    }

    @Test
    public void testPasswordRecoveryRedirect() {
        driver.findElement(By.linkText("Forgot Password")).click();

        // Add assertions to validate the redirection to the password recovery page
    }

    @Test
    public void testPasswordRecoveryFunctionality() {
        String email = "user@example.com";

        driver.findElement(By.linkText("Forgot Password")).click();

        WebElement emailField = driver.findElement(By.id("email"));
        WebElement recoverButton = driver.findElement(By.id("recover_button"));

        emailField.sendKeys(email);
        recoverButton.click();

        // Add assertions to validate the success message for password recovery

        // Simulate password recovery process
        // Retrieve recovery instructions and reset the password

        // Add assertions to validate successful password reset and redirection to the login page

        // Log in with the new password
    }

    @AfterClass
    public static void tearDown() 
    {
        driver.quit();
    }
}

