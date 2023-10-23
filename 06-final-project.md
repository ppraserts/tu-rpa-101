### Usecase
```
Discover:
ห้างทองแม่มะลิ ในทุกๆ วันพนักงานจะต้องทำการตรวจสอบราคาทองกับสมาคมค้าทองคำแห่งประเทศไทย เพื่อตรวจสอบราคาซื้อขาย และทำการบันทึกยอดในทุกๆ ช่วงที่ราคาทองมีการปรับตัวขึ้นหรือลง ผลกระทบคือ
- พนักงานไม่สามารถเข้ามา Monitor ราคาทองได้ตลอดเวลา
- เมื่อราคามีการปรับตัวขึ้น หรือลงทำให้ห้างทองแม่มะลิ เกิดความเสียหายเนื่องจากไม่ทราบราคา ณ ปัจจุบัน

Capture & Assess:
- พนักงานเปิดหน้าเว็บสมาคมค้าทองคำ: https://www.goldtraders.or.th/ ทุกๆ ครึ่งวัน
- ตรวจสอบราคาทองคำรูปพรรณ และทองคำแท่ง
- บันทึกราคาทองคำลงกระดาษรายงาน
- แจ้งพนักงานภายในห้างทองทราบราคาปัจจุบัน

Design:
- สร้าง Unattended RPA
    - เตรียมเครื่อง PC เชื่อมต่อ Internet ตลอดเวลา
    - เครื่องเป็นระบบปฎิบัติการ Windows 10 ติดตั้ง Python + Chrome Browser
    - ตั้ง Schduler ให้ Run ทุกๆ 1 ชม
- ออกแบบ WorkFlow ใหม่ดังนี้
    - เปิดเว็บสมาคมค้าทองคำแห่งประเทศไทย https://www.goldtraders.or.th/
    - ตรวจสอบราคาทองคำรูปพรรณ และทองคำแท่ง
    - ส่งไลน์แจ้งเตือนราคาทองคำรูปพรรณ และทองคำแท่ง ให้กับพนักงานทุกคน
    - บันทึกราคาทองลงในรูปแบบ Excel
```
```
import time
import requests
import pandas as pd
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

### เปิดเว็บสมาคมค้าทองคำแห่งประเทศไทย https://www.goldtraders.or.th/
url = 'https://www.goldtraders.or.th/' 
driver = webdriver.Chrome()
driver.get(url)

# ### ตรวจสอบราคาทองคำรูปพรรณ และทองคำแท่ง
# # อัพเดต
# gold_update_xpath = '//*[@id="DetailPlace_uc_goldprices1_lblAsTime"]/b/font'
# gold_update_lbl = driver.find_element(By.XPATH, gold_update_xpath)

# # ทองคำแท่ง 96.5%
# gold_bl_sell_xpath = '//*[@id="DetailPlace_uc_goldprices1_lblBLSell"]/b/font'
# gold_bl_buy_xpath = '//*[@id="DetailPlace_uc_goldprices1_lblBLBuy"]/b/font'

# gold_bl_sell_lbl = driver.find_element(By.XPATH, gold_bl_sell_xpath)
# gold_bl_buy_lbl = driver.find_element(By.XPATH, gold_bl_buy_xpath)

# # ทองรูปพรรณ 96.5%
# gold_om_sell_xpath = '//*[@id="DetailPlace_uc_goldprices1_lblOMSell"]/b/font'
# gold_om_buy_xpath = '//*[@id="DetailPlace_uc_goldprices1_lblOMBuy"]/b/font'

# gold_om_sell_lbl = driver.find_element(By.XPATH, gold_om_sell_xpath)
# gold_om_buy_lbl = driver.find_element(By.XPATH, gold_om_buy_xpath)

# output_message = f"""อัพเดต: {gold_update_lbl.text}
# ทองคำแท่ง 96.5%
# ขายออก: {gold_bl_sell_lbl.text}
# รับซื้อ: {gold_bl_buy_lbl.text}
# ทองรูปพรรณ 96.5%:
# ขายออก: {gold_om_sell_lbl.text}
# รับซื้อ: {gold_om_buy_lbl.text}"""

# print(output_message)

# ### ส่งไลน์แจ้งเตือนราคาทองคำรูปพรรณ และทองคำแท่ง ให้กับพนักงานทุกคน
# url = 'https://notify-api.line.me/api/notify'
# token = '<your token>'
# headers = {
#     'content-type': 'application/x-www-form-urlencoded',
#     'Authorization': 'Bearer ' + token
# }

# msg = output_message
# data = {
#     'message': msg
# }
# response = requests.post(url, headers=headers, data=data)
# print(response.content)

# ### บันทึกราคาทองลงในรูปแบบ Excel
# file_name = "gold_price_list.xlsx"
# sheet_name = "Sheet1"
# df = pd.read_excel(file_name, sheet_name=sheet_name, engine='openpyxl')
# df_new = [gold_update_lbl.text, gold_bl_sell_lbl.text, gold_bl_buy_lbl.text, gold_om_sell_lbl.text, gold_om_buy_lbl.text]

# df.loc[len(df)] = df_new
# df.to_excel(file_name, sheet_name=sheet_name, index=False, engine='openpyxl')

time.sleep(10)
driver.quit()
```

