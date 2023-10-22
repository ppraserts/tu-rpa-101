### ตรวจสอบ Version Python ที่ติดตั้งในเครื่อง
```
python -V

# output: 
# Python 3.10.11
```

### ตรวจสอบ Package Python ที่ติดตั้งในเครื่อง
```
pip list

# output:
# Package           Version
# ----------------- -------
...
```

### การสั่งให้ python ทำงาน
- สร้าง File "lab1.py" และเพิ่ม Code ด้านล่างดังนี้
```
print("Hello RPA!!!")
```
- Run python
```
py lab1.py

# output: 
# Hello RPA!!!
```

### ตัวแปรใน Python
- แบบที่ 1
```
first_name = 'Elon'
last_name = 'Musk'
print(f"Hi, {first_name} {last_name}")

# output:
# Hi, Elon Musk
```

- แบบที่ 2
```
num1 = 500
num2 = 300
num3 = num1 + num2
print(f"{num1} + {num2} = {num3}")

# output:
# 500 + 300 = 800
```

### เงื่อนไขการตัดสินใจใน Python
```
score = 80
if score >= 50 and score <= 100:
    print("Pass")
elif score >= 0 and score <= 49:
    print("Fail")
else:
    print("Score invalid")

# output:
# Pass
```

### การทำซ้ำใน Python
- แบบที่ 1
```
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# output:
apple
banana
cherry
```

- แบบที่ 2
```
count = 1
while count <= 5:
    print(count)
    count += 1

# output:
1
2
3
4
5
```