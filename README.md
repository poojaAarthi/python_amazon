### mobile_oneplus### 

from selenium import webdriver
from selenium.webdriver.support.ui import Select
import time
import pandas as pd
import os
import  xlsxwriter

driv=(r"C:\Users\Merit\Downloads\chromedriver_win32 (1)\chromedriver.exe")
driver = webdriver.Chrome(executable_path=driv)
driver.get("https://www.amazon.in/s?k=offers+today+low+price&crid=2EN671FD3KPKN&sprefix=offer%2Caps%2C300&ref=nb_sb_ss_ts-doa-p_1_5")
driver.find_element_by_xpath("//a[contains(text(),'Mobiles')]").click()
driver.find_element_by_xpath("//body/div[@id='a-page']/div[2]/div[2]/div[1]/div[1]/section[1]/div[1]/div[1]/div[2]/div[2]/div[1]/ol[1]/li[1]/a[1]/img[1]").click()
a=driver.find_elements_by_xpath("//span[contains(text(),'OnePlus')]")

l=[]
for i in a:
    l.append(i.text.split("\n"))
print(l,end=" ")

b=driver.find_elements_by_xpath("//span[@class='a-price-whole']")
l2=[]
for j in b:
    l2.append(j.text.split("\n"))
print(l2,end=" ")

df=pd.DataFrame(list(zip(l,l2)),columns=["Product Name","Original Price"])
writer = pd.ExcelWriter('Amaz_mobile_oneplus.xlsx', engine='xlsxwriter')
df.to_excel(writer, sheet_name="Amazon_mobile", index=False)
writer.save()



--------sunglass page --------


#######sunglass##########

from selenium import webdriver
from selenium.webdriver.support.ui import Select
import time
import pandas as pd
import os
import  xlsxwriter

driv=(r"C:\Users\Merit\Downloads\chromedriver_win32 (1)\chromedriver.exe")
driver = webdriver.Chrome(executable_path=driv)
driver.get("https://www.amazon.in/s?k=offer+sunglass&rh=n%3A1968401031&ref=nb_sb_noss")
##Brand name

a=driver.find_elements_by_xpath("//h5[@class='s-line-clamp-1']")
l1=[]
for i in a:
    l1.append(i.text.split("\n"))
print(l1,end=" ")
##Product name
b=driver.find_elements_by_xpath("//h2[@class='a-size-mini a-spacing-none a-color-base s-line-clamp-2']")
l2=[]
for j in b:
    l2.append(j.text.split("\n"))
print(l2,end=" ")
##  MRP
c=driver.find_elements_by_xpath("//div[@class='a-row a-size-base a-color-base']//following::span[contains(@class,'a-price a-text-price')]")
l3=[]
for k in c:
    l3.append(k.text.split("\n"))
print(l3,end=" ")
## Discount price
d=driver.find_elements_by_xpath("//h2[@class='a-size-mini a-spacing-none a-color-base s-line-clamp-2']//following::span[@class='a-price']")
l4=[]
for m in d:
    l4.append(m.text.split("\n"))
print(l4,end=" ")

df=pd.DataFrame(list(zip(l1,l2,l3,l4)),columns=["Brand Name","Product Name","MRP","Discount Price"])
writer = pd.ExcelWriter('sun_glass2.xlsx', engine='xlsxwriter')
df.to_excel(writer, sheet_name="cooling_glass", index=False)
writer.save()


output - mobile_oneplus
[Amaz_mobile_oneplus.xlsx](https://github.com/poojaAarthi/python_amazon/files/7072198/Amaz_mobile_oneplus.xlsx)

output - sunglass
[sun_glass2.xlsx](https://github.com/poojaAarthi/python_amazon/files/7072200/sun_glass2.xlsx)









