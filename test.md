const { Builder, By, Key, until } = require('selenium-webdriver');

async function clickLinkByText() {
    let driver = await new Builder().forBrowser('chrome').build();
    try {
        await driver.get('https://outsourcing.ankhora.co.uk/');

        // CLICK ON (SEND)
        await driver.findElement(By.linkText('Send')).click();
    
        await new Promise(resolve => setTimeout(resolve, 1000));
        

        // FIRST NAME FIELD
        await driver.findElement(By.id('wpforms-551-field_0')).sendKeys('name');
        await new Promise(resolve => setTimeout(resolve, 1000));

        // MIDDLE NAME FIELD
        await driver.findElement(By.id('wpforms-551-field_0-middle')).sendKeys('name');
        await new Promise(resolve => setTimeout(resolve, 1000));

        // LAST NAME FIELD
        await driver.findElement(By.id('wpforms-551-field_0-last')).sendKeys('name');
        await new Promise(resolve => setTimeout(resolve, 1000));

        // EMAIL FIELD
        await driver.findElement(By.id('wpforms-551-field_1')).sendKeys('pass@gmail.com');
        await new Promise(resolve => setTimeout(resolve, 1000));

        // PLACE OF WORK FIELD
        await driver.findElement(By.id('wpforms-551-field_4')).sendKeys('My Work place');
        await new Promise(resolve => setTimeout(resolve, 1000));

        // SPECIALITY FIELD
        await driver.findElement(By.id('wpforms-551-field_6')).sendKeys('Qa');
        await new Promise(resolve => setTimeout(resolve, 1000));

        // PHONE NUMBER FIELD
        await driver.findElement(By.id('wpforms-551-field_7')).sendKeys('8987787');
        await new Promise(resolve => setTimeout(resolve, 2000));

         // YOUR MESSAGE FIELD
         await driver.findElement(By.id('wpforms-551-field_2')).sendKeys('Hello!');
         await new Promise(resolve => setTimeout(resolve, 2000));

         //SUBMIT BUTTON
         await driver.findElement(By.id('wpforms-submit-551')).click();
         await new Promise(resolve => setTimeout(resolve, 2000));
       
         //FINAL

         await driver.findElement(By.linkText('Send')).click();


         await driver.wait(until.elementLocated(By.xpath("//*[contains(text(), 'Thanks for contacting us! We will be in touch with you shortly.')]")), 10000);

         await new Promise(resolve => setTimeout(resolve, 2000));
          
        console.log("Тест успешно выполнен");

    } catch (error) {
        console.error("Произошла ошибка:", error);
    } finally {
        await driver.quit();
    }
}

clickLinkByText();