

 #                                      Web Scraping using Python

                To scrape the Content from the University of Michigan website using Requests library




1.import requests                                                           


2.URL = "https://www.si.umich.edu/people/"                                 

3.page = requests.get(URL)

4.page                                                                  
    
5.page.status_code

1. -imports the requests library.
2. -URL of the webpage you want to scrape
4. -gets the raw HTML(hypertext markup language) content of the webpage

A 403 Forbidden error means that the server has refused to allow access to a particular resource, 
#often due to permission restrictions


              To scrape the Content from the University of Michigan website using BeautifulSoup 
 
 




from bs4 import BeautifulSoup                           #Imports the package 
import requests                    



URL = "https://www.si.umich.edu/people/"
page = requests.get(URL)                                # Using the requests library to grab the content of the page, 
                                                        #this line assigns the response (and its content) to the page variable.

soup = BeautifulSoup(page.content,'html.parser')       # this passes the HTML of the page into the BeautifulSoup class
                                                      # We can grab the page source using the content attribute.
                                                    


print(soup.prettify())                                  #For easier viewing



# In[ ]:





# In[ ]:





  To scrape the Content from the University of Michigan website using both BeautifulSoup and a Headless Browser (e.g. Selenium)
 


pip install selenium

pip install webdriver-manager

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager

from bs4 import BeautifulSoup
import time


9.driver = webdriver.Chrome(service=Service(ChromeDriverManager().install())) 

url = "https://www.si.umich.edu/people/"
driver.get(url)


12. time.sleep(1) 


13. soup = BeautifulSoup(driver.page_source, 'html.parser')


14. print(soup.prettify()) 


15. driver.quit() 

print(soup.text)

9.  Sets up the Chrome driver
12. Waits for dynamic content to load
13. Gets the page source after JavaScript has been executed
14. Prints the formatted HTML
15. Closes the driver














                           Finding an item 

1.soup.title

title= soup.find('title')

print(title.text)



2.soup.span

span = soup.find("span")

print(span.text)

soup.p

soup.h2.text

soup.div



                        To find the first div tag

3.div= soup.find('div') 

print(div.text)

soup.head


4.head = soup.find("head")

print(head.text)






                                 Finding all of a particular element

1. To find all the div tags

soup.find_all('div')




2. head_element = soup.find_all("head")

print(head_element)



3. title_element = soup.find_all("title")

print(title_element)



4. soup.find_all("span")





5. soup.find_all('p')




6. soup.find_all('h2')





                    Finding element by class

 To find particular div tags

class_element = soup.find('div', class_='body wysiwyg-content')  
print(class_element.text)



2. class_element2 = soup.find('div', class_='page-crumbs')

class_element2.text



3. class_element1 = soup.find('header', class_="header")
                          
class_element1.text.strip()                    





                           Finding element by id



id_element = soup.find('div', id_= 'main')

print(id_element)





                            Finding a list


1. span_title = soup.find(["span","title"])

print(span_title)




2. span_title = soup.find_all(["span","title"])

print(span_title)






