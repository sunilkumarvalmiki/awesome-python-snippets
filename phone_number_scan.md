### Method 1 :

- [phonenumbers](#phonenumbers): [https://pypi.org/project/phonenumbers/](https://pypi.org/project/phonenumbers/)
- [tabulate](#tabulate): [https://pypi.org/project/tabulate/](https://pypi.org/project/tabulate/)


- Install Phonenumbers Library :
```py

pip install phonenumbers

```

- Install tabulate Library :
```py

pip install tabulate

```

```py

# importing libraries
import phonenumbers
from phonenumbers import carrier
from phonenumbers import geocoder
from tabulate import tabulate

# function
def number_scanner(phone_number):
    number = phonenumbers.parse(phone_number)
    description = geocoder.description_for_number(number, "en")
    supplier = carrier.name_for_number(number, "en")
    info = [["Country", "Supplier"],
            [description, supplier]]
    data = str(tabulate(info, headers="firstrow", tablefmt="github"))
    return data
    
if __name__ == "__main__":
    number = input("enter number: ")
    print(number_scanner(number))

```
---

### Method 2 : 

- [BeautifulSoup(bs4)](https://pypi.org/project/beautifulsoup4/)
- [mechanize](https://pypi.org/project/mechanize/)

- Install BeautifulSoup Library :
```py

pip install bs4

```

- Install Mechanize Library :
```py

pip install mechanize

```

```py

# import libraries
from bs4 import BeautifulSoup
import mechanize

mc = mechanize.Browser()
mc.set_handle_robots(False)
 
url = 'https://www.findandtrace.com/trace-mobile-number-location'
mc.open(url)

mc.select_form(name='trace')
mc['mobilenumber'] = '9912291202' # Enter a mobile number
res = mc.submit().read()

soup = BeautifulSoup(res,'html.parser')
tbl = soup.find_all('table',class_='shop_table')
#print(tbl)
 
 
data = tbl[0].find('tfoot')
c=0
for i in data:
    c+=1
    if c in (1,4,6,8):
        continue
    th = i.find('th')
    td = i.find('td')
    print(th.text,td.text)
 
 
data = tbl[1].find('tfoot')
c=0
for i in data:
    c+=1
    if c in (2,20,22,26): 
        th = i.find('th')
        td = i.find('td')
        print(th.text,td.text)

```