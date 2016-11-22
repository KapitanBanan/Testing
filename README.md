# Testing
AutoTest


using System;
using System.Text;
using System.Text.RegularExpressions;
using System.Threading;
using NUnit.Framework;
using OpenQA.Selenium;
using OpenQA.Selenium.Firefox;
using OpenQA.Selenium.Support.UI;
using OpenQA.Selenium.Chrome;

namespace SeleniumTests
{
    [TestFixture]
    public class Untitled2
    {
        private IWebDriver driver;
        private StringBuilder verificationErrors;
        private string baseURL;
        private bool acceptNextAlert = true;
        
        [SetUp]
        public void SetupTest()
        {
            driver = new ChromeDriver(@"C:\");
            baseURL = "https://tatarstan.hh.ru/";
            verificationErrors = new StringBuilder();
        }

        [TearDown]
        public void TeardownTest()
        {
            try
            {
                driver.Quit();
            }
            catch (Exception)
            {
                // Ignore errors if unable to close the browser
            }
            Assert.AreEqual("", verificationErrors.ToString());
        }

        [Test]
        public void TheEeeTest()
        {
            driver.Navigate().GoToUrl(baseURL + "/");
            driver.FindElement(By.Id("mailbox__login")).Clear();
            driver.FindElement(By.Id("mailbox__login")).SendKeys("grimjowsuper");
            driver.FindElement(By.Id("mailbox__password")).Clear();
            driver.FindElement(By.Id("mailbox__password")).SendKeys("spls50k8");
            driver.FindElement(By.Id("mailbox__auth__button")).Click();
            driver.FindElement(By.CssSelector("a.b-nav__link.js-shortcut > span.b-nav__item__text")).Click();
            driver.FindElement(By.XPath("//div[@id='f638cf771-ad3f-3621-679f-fce81183dfa']/div/div[3]/a/span")).Click();
            driver.FindElement(By.CssSelector("span.b-nav__item__text.b-nav__item__text_unread")).Click();
            driver.FindElement(By.Id("PH_logoutLink")).Click();
            driver.FindElement(By.Id("PH_logoutLink")).Click();
        }
        private bool IsElementPresent(By by)
        {
            try
            {
                driver.FindElement(by);
                return true;
            }
            catch (NoSuchElementException)
            {
                return false;
            }
        }

        private bool IsAlertPresent()
        {
            try
            {
                driver.SwitchTo().Alert();
                return true;
            }
            catch (NoAlertPresentException)
            {
                return false;
            }
        }

        private string CloseAlertAndGetItsText()
        {
            try
            {
                IAlert alert = driver.SwitchTo().Alert();
                string alertText = alert.Text;
                if (acceptNextAlert)
                {
                    alert.Accept();
                }
                else
                {
                    alert.Dismiss();
                }
                return alertText;
            }
            finally
            {
                acceptNextAlert = true;
            }
        }
    }
}
