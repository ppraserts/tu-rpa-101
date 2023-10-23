### ติดตั้ง Library สำหรับ Selenium
```
pip install selenium
```
```
pip list

# output: 
# Package      Version
# ------------ -------
# selenium           4.14.0
```

### เตรียมไฟล์ lab4
- สร้าง File "lab4.py"
- https://googlechromelabs.github.io/chrome-for-testing/

### Work with selenium
```
import time
import pandas as pd
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

driver = webdriver.Chrome()

driver.get('https://www.google.com/')

# input_search = driver.find_element(By.XPATH, '//*[@name="q"]')
# input_search.send_keys("ละครพรหมลิขิต")
# input_search.send_keys(Keys.ENTER)

# button_view_all = driver.find_element(By.XPATH,'//*[contains(@class, "CHn7Qb") and contains(@class, "pYouzb")]')
# button_view_all.click()

# all_title = driver.find_elements(By.XPATH, '//*[contains(@class, "LC20lb") and contains(@class, "MBeuO") and contains(@class, "DKV0Md")]')

# drama_title = []
# for title in all_title:
#     print(title.text)
#     drama_title.append(title.text)

# data = {
#     'Title': drama_title,
# }

# df = pd.DataFrame(data)
# df.to_excel('drama_list.xlsx', index=False, engine='openpyxl')

time.sleep(10)
driver.quit()
```
Reference: https://selenium-python.readthedocs.io/installation.html
