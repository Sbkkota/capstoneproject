package utils;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.*;

public class Ecomercesite {

@Test(priority = 1)
public void testRegisterLoginSearchAddToCartCheckout() {
    extentTest = extent.createTest("End-to-End Test");

    // Register
    homePage.navigateToRegisterPage();
    registerPage.register("testuserk", "password123");

    // Login
    homePage.navigateToLoginPage();
    loginPage.login("testuserk", "password123");

    // Search and add to cart
    homePage.searchProduct("Samsung galaxy s6");
    productPage.addToCart();

    // View cart and checkout
    cartPage.viewCart();
    cartPage.proceedToCheckout("John Doe", "USA", "New York", "1234567890", "June", "2025");

    // Confirmation
    checkoutPage.verifyOrderConfirmation();

    ScreenshotUtil.captureScreenshot(driver, "E2E_Success");
}
}
