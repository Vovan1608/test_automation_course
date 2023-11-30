Create a maven project and add the appropriate dependencies.
Create a test class and add the code from the example.
Refactor the code, fix bugs in the existing ones and add new test methods to test
"Signin":

1. check the locators, make changes to optimize the locators. If necessary, add new
   locators
2. add test methods for testing positive and negative scenarios to the test class
3. refactor existing parameterized test methods depending on the logic of test
   construction and perform additional parameterized tests

```java
import io.github.bonigarcia.wdm.WebDriverManager;
import org.junit.jupiter.api.*;
import org.junit.jupiter.params.ParameterizedTest;
import org.junit.jupiter.params.provider.CsvSource;
import org.openqa.selenium.support.FindBy;
import org.openqa.selenium.Dimension;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.PageFactory;
import static org.hamcrest.CoreMatchers.is;
import static org.hamcrest.MatcherAssert.assertThat;
import java.util.concurrent.TimeUnit;

public class TestSamples3 {
    private final String incorrectEmailMessage = "Please check if the email is written correctly";
    private final String incorrectPasswordMessage = "Bad email or password";
    @FindBy(css = "app-header:nth-child(1) .ubs-header-sing-in-img")
    private WebElement signInButton;
    @FindBy(css = ".ng-star-inserted > h1")
    private WebElement welcomeText;
    @FindBy(css = "h2:nth-child(2)")
    private WebElement signInDetailsText;
    @FindBy(xpath = "//label[@for='email']")
    private WebElement emailLabel;
    @FindBy(id = "email")
    private WebElement emailInput;
    @FindBy(xpath = "//label[@for='password']")
    private WebElement passwordLabel;
    @FindBy(id = "password")
    private WebElement passwordInput;
    @FindBy(css = ".ubsStyle")
    private WebElement signInSubmitButton;
    @FindBy(css=".mat-simple-snackbar > span")
    private WebElement result;
    @FindBy(css = ".alert-general-error")
    private WebElement errorMessage;
    @FindBy(xpath = "//div[@id='pass-err-msg']/app-error/div")
    private WebElement errorPasswordLessEightChar;
    @FindBy(xpath = "//div[@class='alert-general-error ng-star-inserted']")
    private WebElement errorPassword;
    @FindBy(xpath = "//*[@id='email-err-msg']/app-error/div")
    private WebElement errorEmail;
    @FindBy(xpath = ".//img[@alt='close button']")
    private WebElement closeButton;
    private static WebDriver driver;
    @BeforeAll
    public static void setUp() {
        WebDriverManager.chromedriver().setup();

        driver = new ChromeDriver();
        driver.get("https://www.greencity.social/");
        driver.manage().window().setSize(new Dimension(1264, 798));
    }

    @BeforeEach
    public void initPageElements() {
        PageFactory.initElements(driver, this);
    }

    @AfterAll
    public static void tearDown() {
        driver.quit();
    }

    @Test
    public void verifyTitle() {
        String titleName = "GreenCity";
        assertThat(driver.getTitle(), is(titleName));
    }

    @ParameterizedTest
    @CsvSource({
            "samplestest@greencity.com, weyt3$Guew^",
            "sadgmplestest@greencity.com, weyt3$Guew^",
            "test@multiline.dp.ua, eyt3$Guew^"
    })
    public void signIn(String email, String password) {
        signInButton.click();
        assertThat(welcomeText.getText(), is("Welcome back!"));
        assertThat(signInDetailsText.getText(), is("Please enter your details to sign in."));
        assertThat(emailLabel.getText(), is("Email"));
        assertThat(passwordLabel.getText(), is("Password"));
        emailInput.sendKeys(email);
        assertThat(emailInput.getAttribute("value"), is(email));
        passwordInput.sendKeys(password);
        assertThat(passwordInput.getAttribute("value"), is(password));
        signInSubmitButton.click();
        closeButton.click();
    }

    @ParameterizedTest
    @CsvSource({
            "samplestestgreencitycom, weyt3$Guew^",
            "samplestestgreencity.com, weyt3$Guew^",
            "samplestest@greencitycom, weyt3$Guew^",
            "@samplestestgreencity.com, weyt3$Guew^",
            "samplestestgreencity.com@, weyt3$Guew^"
    })
    public void signInNotValidEmail(String email, String password) {
        signInButton.click();
        emailInput.sendKeys(email);
        passwordInput.sendKeys(password);
        assertThat(errorEmail.getText().trim(), is(incorrectEmailMessage));
        signInSubmitButton.click();
        closeButton.click();
    }

    @Test
    public void passwordHasLessThanEightChar() {
        String incorrectMessageWhenPasswordHasLessThanEightChar = "Password must be at least 8 characters long without spaces";
        signInButton.click();
        emailInput.sendKeys("samplestest@greencity.com");
        passwordInput.sendKeys("pasword");
        signInSubmitButton.click();
        assertThat(errorPasswordLessEightChar.getText().trim(), is(incorrectMessageWhenPasswordHasLessThanEightChar));
        closeButton.click();
    }

    @ParameterizedTest
    @CsvSource({
            "samplestest@greencity.com, weytuewfghj",
            "samplestest@greencity.com, weyt$Guew^",
            "samplestest@greencity.com, weyt3Guew",
            "samplestest@greencity.com, weyt3$uew^"
    })
    public void sifnInNotValidPassword (String email, String password) {
        signInButton.click();
        emailInput.sendKeys(email);
        passwordInput.sendKeys(password);
        signInSubmitButton.click();
        driver.manage().timeouts().implicitlyWait(5, TimeUnit.SECONDS);
        assertThat(errorPassword.getText().trim(), is(incorrectPasswordMessage));
        closeButton.click();
    }
}
```
