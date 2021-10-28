# Sprint1-
# Import libraries
import requests
import urllib.request
import time
from bs4 import BeautifulSoup

url = 'https://covid19.ca.gov/state-dashboard/'
url = 'https://covid.cdc.gov/covid-data-tracker/#datatracker-home'


response = requests.get(url)

soup = BeautifulSoup(response.text, "html.parser")

# To download the whole data set, let's do a for loop through all a tags
line_count = 1 #variable to track what line you are on
for one_a_tag in soup.findAll('Vaccines Administered'):  #'a' tags are for links
    if line_count >= 1: #code for text files starts at line 36
        link = one_a_tag['href']
        download_url = 'https://covid19.ca.gov/state-dashboard/' + link
        urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:])
        time.sleep(1) #pause the code for a sec
    #add 1 for next line
    line_count +=1
for one_a_tag in soup.findAll('Cases'):  #'a' tags are for links
    if line_count >= 1: #code for text files starts at line 36
        link = one_a_tag['href']
        download_url = 'https://covid19.ca.gov/state-dashboard/' + link
        urllib.request.urlretrieve(download_url,'./'+link[link.find('/turnstile_')+1:])
        time.sleep(1) #pause the code for a sec
    #add 1 for next line
    line_count +=1
    for one_a_tag in soup.findAll('Deaths'):  # 'a' tags are for links
        if line_count >= 1:  # code for text files starts at line 36
            link = one_a_tag['href']
            download_url = 'https://covid19.ca.gov/state-dashboard/' + link
            urllib.request.urlretrieve(download_url, './' + link[link.find('/turnstile_') + 1:])
            time.sleep(1)  # pause the code for a sec
        # add 1 for next line
        line_count += 1
        for one_a_tag in soup.findAll('Tests'):  # 'a' tags are for links
            if line_count >= 1:  # code for text files starts at line 36
                link = one_a_tag['href']
                download_url = 'https://covid19.ca.gov/state-dashboard/' + link
                urllib.request.urlretrieve(download_url, './' + link[link.find('/turnstile_') + 1:])
                time.sleep(1)  # pause the code for a sec
            # add 1 for next line
            line_count += 1
