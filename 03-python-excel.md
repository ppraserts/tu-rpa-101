### ติดตั้ง Library สำหรับ pd
```
pip install pandas
pip install openpyxl
```
```
pip list

# output: 
# Package      Version
# ------------ -------
# pandas          2.1.1
# openpyxl        3.1.2
```

### เตรียมไฟล์ lab3
- สร้าง File "lab3.py"

### เตรียมไฟล์ Excel
- Download file excel 'product_list.xlsx' มาไว้ใน Folder

### การอ่านไฟล์ Excel
```
import pandas as pd

df = pd.read_excel('product_list.xlsx')
print(df)

# output:
#    Unnamed: 0 ProductId                                            Product  Price  Stock
# 0           1      P001  NOTEBOOK (โน้ตบุ๊ค) HP 15-FD0026TU (NATURAL SI...  23990     10
# 1           2      P002  NOTEBOOK (โน้ตบุ๊ค) HP 15S-FQ5189TU (SPRUCE BLUE)  14990      5
# 2           3      P003  NOTEBOOK (โน้ตบุ๊ค) ASUS VIVOBOOK 16 X1605ZA-M...  19990      8
# 3           4      P004  NOTEBOOK (โน้ตบุ๊ค) DELL VOSTRO 3430-VN3430RHX...  25990      6
# 4           5      P005  NOTEBOOK (โน้ตบุ๊ค) LENOVO IDEAPAD 3 15IAU7-82...  13590      4

# ดึงเฉพาะ Column นั้นๆ
# print(df['Product'])
```

### การเพิ่ม Row ใหม่
```
import pandas as pd

df = pd.read_excel('product_list.xlsx')
df.loc[len(df.index)] = [6, 'P006', 'NOTEBOOK (โน้ตบุ๊ค) GIGABYTE AORUS 15X AKF-D3TH754SH (BLACK)', 69990, 10]

# บันทึกเป็นไฟล์ใหม่
# df.to_excel('product_list_new.xlsx', index=False)
```

### การแก้ไขข้อมูลบาง Column
```
import pandas as pd

df = pd.read_excel('product_list.xlsx')

# Update the price for product with productid 2
df.loc[df['ProductId'] == 'P001', 'Stock'] = 9

# บันทึกเป็นไฟล์ใหม่
df.to_excel('product_list_new.xlsx', index=False)
```

Reference: https://pandas.pydata.org/docs/user_guide/index.html#user-guide
