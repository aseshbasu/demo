# This is for test only

import requests
key=input("Enter the keyword you are looking for: ") 
link = "https://www.theguardian.com/uk-news/2019/apr/11/julian-assange-arrested-at-ecuadorian-embassy-wikileaks"
page = requests.get(link)
from bs4 import BeautifulSoup
soup = BeautifulSoup(page.content, 'html.parser')

flag=0

for i in range (0, 10):
    x=soup.find_all('p')[i].get_text()
    if(x.find(key)!=-1):
        flag=1

if(flag==0):
    print("Sorry, your keyword was not found.")
if (flag==1):
    print("Your keyword: ", key," , was found in ", link)
