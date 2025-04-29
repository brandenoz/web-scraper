<p align="center">
 <img src="https://github.com/user-attachments/assets/784c1a3e-f470-4234-ac8f-d98ff29eff9c" alt="Python Logo" width=20%/>
 </p>

 <h1>Website Scraper</h1>
 This Python website scraper will collect all the assets from a website including images, links, and link text.   
 
 <h2>Code</h2>
 
```python
# Get request module from url library.
from urllib import request
# This one has handy tools for scraping a web page.
from bs4 import BeautifulSoup
# Sample page for practice.
page_url = 'https://freeeasy.ai/scrape_sample.html' # https://freeeasy.ai/scrape_sample.html

# Open that page.
raw_page = request.urlopen(page_url)
# Make a BeautifulSoup object from the html page.
soup = BeautifulSoup(raw_page, 'html5lib')
# Isolate the main content block.
content = soup.article
# Create an empty list to hold a dictionary for each item.
links_list = []

# Loop through all the links in the article.
for link in content.find_all('a'):
    # Try to get the href, image url, and text.
    try:
        url = link.get('href')
        img = link.img.get('src')
        text = link.span.text
        links_list.append({'url' : url, 'img': img, 'text': text})
    # If the row is missing anything...
    except AttributeError:
        #... skip it, don't blow up.
        pass

# Option 2: Print each item nicely (from ChatGPT).
print("\nReadable Output:\n")
for i, item in enumerate(links_list, start=1):
    print(f"Link {i}:")
    print(f"  Text : {item['text']}")
    print(f"  URL  : {item['url']}")
    print(f"  Image: {item['img']}\n")

"""# Save to a text file (ChatGPT). 
with open("output.txt", "w", encoding="utf-8") as file:
    for i, item in enumerate(links_list, start=1):
        file.write(f"Link {i}:\n")
        file.write(f"  Text : {item['text']}\n")
        file.write(f"  URL  : {item['url']}\n")
        file.write(f"  Image: {item['img']}\n\n")

print("✅ Output saved to 'output.txt'")"""
```
 
 <h2>Example Website to "Scrape"</h2>

- It should be noted that in this case, "scraping" just means taking all of the public assets of a web page rather than stealing. It is just taking them in a extremely time-saving way and outputing it into a neat txt file for you using Python.
- This example is from "Python Essentials for Dummies" by John C. Shovic, PhD and Alan Simpson.
- Here is the example website from the book to try the scraping code on: (https://freeeasy.ai/scrape_sample.html)

![image](https://github.com/user-attachments/assets/d908d96b-a522-40b5-ad00-9e3d037aade2)

- The code up until line 28 just gathers the website page's assets. Lines 30-36 print them for you in the IDE terminal, I'm using VS Code.

![image](https://github.com/user-attachments/assets/5f3a6cb7-8b7d-4c20-a968-fce3232cf814)

- Lines 38-46 are 'turned-off' using the triple quotes before and after, see: """. Once removed, they take the assets of the webpage and output the as a txt file named "output.txt". I have them turned off with triple quotes because if you run the code mmultiple times, you would have multiple files getting named "output.txt". If you using this method to scrape content from an actual website, you would simple change the website URL on line 6 and the name of the output file (if using that part) on line 39.
- See "output.txt" below: 

![image](https://github.com/user-attachments/assets/9cb08eb3-31f0-4a75-8965-575cc19f1361)

- To see other projects click here: https://github.com/brandenoz. 
