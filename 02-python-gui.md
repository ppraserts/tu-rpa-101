### ติดตั้ง Library สำหรับ pyautogui
```
pip install pyautogui
```
```
pip list

# output: 
# Package      Version
# ------------ -------
# PyAutoGUI    0.9.54
```

### เตรียมไฟล์ lab2
- สร้าง File "lab2.py"

### การหา Position
```
import pyautogui as pg

print(pg.position())
```

```
py lab2.py

# output:
# Point(x=14, y=1048)
```

### การคลิก Mouse
```
import pyautogui as pg

pg.click(22, 1053)
```

```
# เปิดเว็บ https://cpstest.click/en
# คลิก 5 ครั้ง
pg.click(734, 633, 5)
# pg.click(734, 633, 5, interval=1)
```

### การเลื่อน Mouse
```
import pyautogui as pg

pg.moveTo(22, 1053)
# หน่วงการเลื่อน Mouse
# pg.moveTo(22, 1053, 3)
```

### การScroll Mouse
```
import pyautogui as pg

# เลื่อนขึ้น
pg.scroll(1000)

# เลื่อนลง
# pg.scroll(-1000)
```

### การ Click ขวา Mouse 
```
import pyautogui as pg

pg.rightClick()
```

### การพิมพ์
```
import pyautogui as pg

pg.typewrite("Hello World")

# หน่วงเวลาในการพิมพ์
# pg.typewrite("Hello World", interval=0.5)

# สั่งให้ Enter
# pg.typewrite(['enter'])
# pg.press('enter')
# pg.press('enter', 5, interval=1)
```
```
import pyautogui as pg
import pyperclip

# สำหรับภาษาไทย
keyword = "สวัสดีจ้า"
pyperclip.copy(keyword)
pg.hotkey('ctrl','v')
```

### Screenshot
```
import pyautogui as pg

pg.screenshot('screen.png')
```

### Usecase
```
1 เปิด Open Webbrowser และไปที่เว็บ Google
2 พิมพ์ค้นหาในช่อง Search
3 กด Enter เพื่อเริ่มการค้นหา
4 Screenshot ผลการค้นหา
```
```
import webbrowser
import pyautogui as pg
import time
import pyperclip


# 1 เปิด Open Webbrowser และไปที่เว็บ Google
url = 'https://www.google.com'
webbrowser.open(url)
time.sleep(3)

# 2 พิมพ์ค้นหาในช่อง Search
keyword = 'Robotic Process Automation'
pg.write(keyword, interval=0.25)

# keyword = 'หนังเรื่องสัปเหร่อ'
# pyperclip.copy(keyword)
# time.sleep(0.5)
# pg.hotkey('ctrl', 'v')
# time.sleep(1)

# 3 กด Enter เพื่อเริ่มการค้นหา
pg.press("enter")
time.sleep(3)

# 4 Screenshot ผลการค้นหา
pg.screenshot("screenshot.png")
```

```
import webbrowser
import pyautogui as pg
import time
import pyperclip

def search(keyword, eng = False):
    # 1 เปิด Open Webbrowser และไปที่เว็บ Google
    url = 'https://www.google.com'
    webbrowser.open(url)
    time.sleep(3)

    # 2 พิมพ์ค้นหาในช่อง 
    if eng == True:
        #keyword = 'Robotic Process Automation'
        pg.write(keyword, interval=0.25)
    else:
        # keyword = 'หนังเรื่องสัปเหร่อ'
        pyperclip.copy(keyword)
        time.sleep(0.5)
        pg.hotkey('ctrl', 'v')
        time.sleep(1)

    # 3 กด Enter เพื่อเริ่มการค้นหา
    pg.press("enter")
    time.sleep(3)

    # 4 Screenshot ผลการค้นหา
    pg.screenshot("screenshot.png")

search('หนังเรื่องสัปเหร่อ')
search('Robotic Process Automation', True)
```

Reference: https://pyautogui.readthedocs.io/en/latest/ 
