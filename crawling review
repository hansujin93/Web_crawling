from bs4 import BeautifulSoup
from selenium import webdriver
from time import sleep

def write_file(file_name, mode, content):
    with open(file=file_name, mode=mode, encoding='utf-8') as f:
        f.writelines(content)

def web_crawling() :
    browser = webdriver.Chrome()
    browser.implicitly_wait(5)
    browser.get('https://play.google.com/store/apps/details?id=com.perfectcorp.amb&hl=en_US&showAllReviews=true')
    last_height = browser.execute_script("return document.body.scrollHeight")
    new_height = last_height + 1
    # i = 0
    while last_height != new_height:
        browser.execute_script("window.scrollTo(0, document.body.scrollHeight);")
        sleep(5)
        new_height = browser.execute_script("return document.body.scrollHeight")
        print(last_height, new_height)
        last_height = new_height
        # i += 1
    html = browser.page_source
    return html

html =  web_crawling()
soup = BeautifulSoup(html, 'html.parser')
body_script = soup.find('div', {'class' : 'W4P4ne'})
for script in body_script.findAll('span', {'jsname' : 'bN97Pc'}) :
    print(script.string)
    try :
        write_file('sujin.txt', 'a', f'{script.string}\n')
    except :
        pass

