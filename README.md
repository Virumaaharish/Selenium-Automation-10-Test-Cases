# Selenium Automation – 10 Test Cases

A collection of 10 beginner-friendly Selenium WebDriver automation test cases written in Python. The examples cover website login, JavaScript alerts, mouse actions, drag-and-drop, and explicit waits.

## Table of Contents

1. [Open Online Shopping Website](#tc-1-open-online-shopping-website)
2. [Alert Accept](#tc-2-alert-accept)
3. [Alert Dismiss](#tc-3-alert-dismiss)
4. [Prompt Alert](#tc-4-prompt-alert)
5. [Mouse Hover](#tc-5-mouse-hover)
6. [Double Click](#tc-6-double-click)
7. [Drag and Drop](#tc-7-drag-and-drop)
8. [Explicit Wait](#tc-8-explicit-wait)
9. [Clickable Wait](#tc-9-clickable-wait)
10. [Alert Wait](#tc-10-alert-wait)

## Requirements

- Python 3
- Google Chrome
- Selenium Python package

Install Selenium:

```bash
python -m pip install selenium
```

Selenium Manager can manage the compatible ChromeDriver for current Selenium versions.

---

## TC-1: Open Online Shopping Website

**Test case:** Customer opens the online shopping website and logs in.

**Website:** [SauceDemo](https://www.saucedemo.com/inventory.html)

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("https://www.saucedemo.com/inventory.html")
driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")
driver.find_element(By.ID, "login-button").click()
time.sleep(10)
driver.quit()
```

**Expected result:** The user logs in and the inventory page is displayed.
<img width="808" height="668" alt="image" src="https://github.com/user-attachments/assets/5a6eeca5-6e8a-46c4-b02b-a40bc0ca9810" />

---

## TC-2: Alert Accept

**Test case:** Customer clicks the alert button and accepts the confirmation popup.

**Website:** [TutorialsPoint Alerts](https://www.tutorialspoint.com/selenium/practice/alerts.php)

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("https://www.tutorialspoint.com/selenium/practice/alerts.php")
driver.find_element(By.XPATH, "//button[@onclick='myDesk()']").click()

alert = driver.switch_to.alert
time.sleep(5)
alert.accept()
time.sleep(10)
driver.quit()
```

**Expected result:** The alert is accepted and closed.
<img width="870" height="657" alt="image" src="https://github.com/user-attachments/assets/47b6b6bb-b3ab-43c3-89f2-cae87decbe92" />

---

## TC-3: Alert Dismiss

**Test case:** Customer clicks the alert button but chooses Cancel/dismiss.

**Website:** [TutorialsPoint Alerts](https://www.tutorialspoint.com/selenium/practice/alerts.php)

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("https://www.tutorialspoint.com/selenium/practice/alerts.php")
driver.find_element(By.XPATH, "//button[@onclick='myDesk()']").click()

alert = driver.switch_to.alert
time.sleep(5)
alert.dismiss()
time.sleep(10)
driver.quit()
```

**Expected result:** The alert is dismissed.
<img width="870" height="673" alt="image" src="https://github.com/user-attachments/assets/cf8a9524-4fda-4d36-99b0-e9581487d778" />

---

## TC-4: Prompt Alert

**Test case:** Customer enters a name or other information in a prompt popup.

**Website:** [TutorialsPoint Alerts](https://www.tutorialspoint.com/selenium/practice/alerts.php)

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get("https://www.tutorialspoint.com/selenium/practice/alerts.php")
driver.find_element(By.XPATH, "//button[@onclick='myPromp()']").click()
time.sleep(1)

alert = driver.switch_to.alert
alert.send_keys("DK")
time.sleep(10)
alert.accept()
time.sleep(2)
driver.quit()
```

**Expected result:** The text `DK` is entered into the prompt and the prompt is accepted.
<img width="849" height="680" alt="image" src="https://github.com/user-attachments/assets/748de2b6-4702-4c6e-a3f0-11ed8567f764" />

---

## TC-5: Mouse Hover

**Test case:** Customer moves the mouse over a menu item to trigger its hover behavior.

**Website:** [DemoQA Menu](https://demoqa.com/menu/)

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains

driver = webdriver.Chrome()
driver.get("https://demoqa.com/menu/")
time.sleep(5)

menu = driver.find_element(By.XPATH, "//a[text()='Main Item 2']")
actions = ActionChains(driver)
time.sleep(2)

actions.move_to_element(menu).perform()
time.sleep(3)
driver.quit()
```

**Expected result:** The pointer hovers over `Main Item 2` and its hover behavior is triggered.
<img width="870" height="663" alt="image" src="https://github.com/user-attachments/assets/ab14e8ae-5a1c-4dd3-95fc-200742dabcec" />

---

## TC-6: Double Click

**Test case:** Customer double-clicks a button.

**Website:** [DemoQA Buttons](https://demoqa.com/buttons)

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains

driver = webdriver.Chrome()
driver.get("https://demoqa.com/buttons")
time.sleep(10)

button = driver.find_element(By.ID, "doubleClickBtn")
ActionChains(driver).double_click(button).perform()

time.sleep(10)
driver.quit()
```

**Expected result:** The double-click action is performed on the button.
<img width="870" height="783" alt="image" src="https://github.com/user-attachments/assets/c4f16d51-e733-4f0d-8a09-47f3d31d540b" />

---

## TC-7: Drag and Drop

**Test case:** Customer drags an item into a target area.

**Website:** [DemoQA Droppable](https://demoqa.com/droppable)

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains

driver = webdriver.Chrome()
driver.get("https://demoqa.com/droppable")
driver.maximize_window()

time.sleep(2)

source = driver.find_element(By.ID, "draggable")
target = driver.find_element(By.ID, "droppable")

time.sleep(3)
actions = ActionChains(driver)
actions.click_and_hold(source)
actions.move_to_element(target)
actions.release()
actions.perform()

time.sleep(3)
driver.quit()
```

**Expected result:** The draggable item is moved to the droppable target.
<img width="819" height="568" alt="image" src="https://github.com/user-attachments/assets/cdf81493-7865-43f4-806e-41b58e05c8d1" />

---

## TC-8: Explicit Wait

**Test case:** Customer logs in and waits until a product becomes visible.

**Website:** [SauceDemo](https://www.saucedemo.com/)

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()
driver.get("https://www.saucedemo.com/")

driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")
driver.find_element(By.ID, "login-button").click()

wait = WebDriverWait(driver, 10)
product = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//div[text()='Sauce Labs Backpack']")
    )
)
product.click()

time.sleep(10)
driver.quit()
```

**Expected result:** Selenium waits up to 10 seconds for the product element to become visible, then clicks it.
<img width="732" height="685" alt="image" src="https://github.com/user-attachments/assets/8ea15c1d-8e3c-4fd0-ae89-bb4643163ab4" />

---

## TC-9: Clickable Wait

**Test case:** Customer proceeds through checkout and waits until the Finish button is clickable.

**Website:** [SauceDemo](https://www.saucedemo.com/)

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()
driver.get("https://www.saucedemo.com/")

driver.find_element(By.ID, "user-name").send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")
driver.find_element(By.ID, "login-button").click()

driver.find_element(By.ID, "add-to-cart-sauce-labs-backpack").click()
driver.find_element(By.CLASS_NAME, "shopping_cart_link").click()
driver.find_element(By.ID, "checkout").click()

time.sleep(5)

driver.find_element(By.ID, "first-name").send_keys("DK")
driver.find_element(By.ID, "last-name").send_keys("Test")
driver.find_element(By.ID, "postal-code").send_keys("600001")

driver.find_element(By.ID, "continue").click()

wait = WebDriverWait(driver, 10)
finish_button = wait.until(
    EC.element_to_be_clickable((By.ID, "finish"))
)
finish_button.click()

time.sleep(2)
driver.quit()
```

**Expected result:** Selenium waits until the Finish button is clickable, then clicks it to complete the checkout flow.
<img width="870" height="568" alt="image" src="https://github.com/user-attachments/assets/752c0b58-7849-4f45-b363-4ef3d566fff9" />

---

## TC-10: Alert Wait

**Test case:** Customer triggers an alert and waits until the alert popup is present.

**Website:** [TutorialsPoint Alerts](https://www.tutorialspoint.com/selenium/practice/alerts.php)

```python
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()
driver.get("https://www.tutorialspoint.com/selenium/practice/alerts.php")

driver.find_element(By.XPATH, "//button[@onclick='myMessage()']").click()

wait = WebDriverWait(driver, 10)
alert = wait.until(EC.alert_is_present())

time.sleep(5)
alert.accept()
time.sleep(5)
driver.quit()
```

**Expected result:** Selenium waits up to 10 seconds for the alert to appear and then accepts it.
<img width="870" height="617" alt="image" src="https://github.com/user-attachments/assets/6efca728-a3bc-41d1-8715-bbee27ac396a" />

---

## Concepts Covered

- Opening websites and locating elements with Selenium
- Locators: `By.ID`, `By.XPATH`, and `By.CLASS_NAME`
- Handling JavaScript alerts with `accept()`, `dismiss()`, and `send_keys()`
- Mouse interactions using `ActionChains`
- Drag-and-drop interactions
- Explicit waits using `WebDriverWait` and `expected_conditions`
- Waiting for visibility, clickability, and alert presence
