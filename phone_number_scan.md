
- [phonenumbers](#phonenumbers): [https://pypi.org/project/phonenumbers/](https://pypi.org/project/phonenumbers/)
- [tabulate](#tabulate): [https://pypi.org/project/tabulate/](https://pypi.org/project/tabulate/)


## PYTUBE 
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
