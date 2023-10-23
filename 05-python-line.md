### ติดตั้ง Library สำหรับ Line
```
pip install requests
```
```
pip list

# output: 
# Package      Version
# ------------ -------
# requests           2.31.0
```

### เตรียมไฟล์ lab5
- สร้าง File "lab5.py"

### เตรียม Line Token ตามเอกสาร
### ทดลองส่งข้อความธรรมดา
```
import requests

url = 'https://notify-api.line.me/api/notify'
token = '<your token>'
headers = {
    'content-type': 'application/x-www-form-urlencoded',
    'Authorization': 'Bearer ' + token
}

msg = 'Hello Line'
data = {
    'message': msg
}
response = requests.post(url, headers=headers, data=data)
print(response.content)
```

### ทดลองส่ง Sticker
- https://developers.line.biz/en/docs/messaging-api/sticker-list/#sticker-definitions
```
import requests

url = 'https://notify-api.line.me/api/notify'
token = '<your token>'
headers = {
    'content-type': 'application/x-www-form-urlencoded',
    'Authorization': 'Bearer ' + token
}

msg = "Hello with Sticker"
data = {
    'message': msg,
    'stickerPackageId': 446,   # Sample package ID
    'stickerId': 1988        # Sample sticker ID
}
response = requests.post(url, headers=headers, data=data)
print(response.content)
```

### ทดลองส่งรูปภาพจาก URL
```
import requests

url = 'https://notify-api.line.me/api/notify'
token = '<your token>'
headers = {
    'content-type': 'application/x-www-form-urlencoded',
    'Authorization': 'Bearer ' + token
}

msg = "Hello with Image"
image_url = "https://s.isanook.com/wo/0/ud/4/20927/d21.jpg?ip/resize/w850/q80/jpg"
data = {
    'message': msg,
    'imageThumbnail': image_url,
    'imageFullsize': image_url
}
response = requests.post(url, headers=headers, data=data)
print(response.content)
```

