

 #                                      Web Scraping using Python

                To scrape the Content from the University of Michigan website using Requests library

 In[1]:


import requests                                                                        #imports the requests library.


URL = "https://www.si.umich.edu/people/"                                                #URL of the webpage you want to scrape
page = requests.get(URL)
page                                                                                    #gets the raw HTML(hypertext markup language) content of the webpage

    
                         
                                                   


 In[2]:


page.status_code


 In[3]:


# A 403 Forbidden error means that the server has refused to allow access to a particular resource, 
#often due to permission restrictions


#              To scrape the Content from the University of Michigan website using BeautifulSoup 
# 
# 

# In[4]:


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





#  To scrape the Content from the University of Michigan website using both BeautifulSoup and a Headless Browser (e.g. Selenium)
# 

# In[5]:


pip install selenium


# In[6]:


pip install webdriver-manager


# In[7]:


from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager

from bs4 import BeautifulSoup
import time


driver = webdriver.Chrome(service=Service(ChromeDriverManager().install())) # This sets up the Chrome driver

url = "https://www.si.umich.edu/people/"
driver.get(url)


time.sleep(1)  # this Waits for dynamic content to load


soup = BeautifulSoup(driver.page_source, 'html.parser')# To get the page source after JavaScript has been executed


print(soup.prettify()) # To print the formatted HTML


driver.quit() # To close the driver


# In[ ]:





# In[8]:


print(soup.text)


# In[ ]:





# In[ ]:





# In[ ]:





#                                Finding an item 

# In[11]:


soup.title


# In[16]:


title= soup.find('title')

print(title.text)


# In[17]:


soup.span


# In[18]:


span = soup.find("span")

print(span.text)


# In[19]:


soup.p


# In[20]:


soup.h2.text


# In[21]:


soup.div


# In[23]:


div= soup.find('div')  # to find the first div tag

print(div.text)


# In[ ]:





# In[24]:


soup.head


# In[25]:


head = soup.find("head")

print(head.text)


# In[ ]:





# In[ ]:





#                    Finding all of a particular element

# In[26]:


soup.find_all('div') # to find all the div tags


# In[27]:


head_element = soup.find_all("head")

print(head_element)


# In[28]:


title_element = soup.find_all("title")

print(title_element)


# In[29]:


soup.find_all("span")


# In[30]:


soup.find_all('p')


# In[31]:


soup.find_all('h2')


# In[ ]:





#                     Finding element by class

# In[ ]:





# In[32]:


class_element = soup.find('div', class_='body wysiwyg-content')   # to find particular div tags

print(class_element.text)


# In[33]:


class_element2 = soup.find('div', class_='page-crumbs')

class_element2.text


# In[34]:


class_element1 = soup.find('header', class_="header")
                          
class_element1.text.strip()                    


# In[ ]:





# In[ ]:





#                             Finding element by id

# In[35]:


id_element = soup.find('div', id_= 'main')

print(id_element)


# In[ ]:





# In[ ]:





#                      Finding a list

# In[36]:


span_title = soup.find(["span","title"])

print(span_title)


# In[ ]:





# In[125]:


span_title = soup.find_all(["span","title"])

print(span_title)


# In[ ]:




