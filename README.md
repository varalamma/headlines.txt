# headlines.txt
import requests
from bs4 import BeautifulSoup

# Step 1: Fetch HTML from a news site
url = 'https://www.bbc.com/news' 
response = requests.get(url)
soup = BeautifulSoup(response.text, 'html.parser')

# Step 2: Parse headlines (look for <h2> tags)
headlines = []
for tag in soup.find_all('h2'):
    text = tag.get_text(strip=True)
    if text:  # Avoid empty tags
        headlines.append(text)

# Step 3: Save headlines to a .txt file
with open('headlines.txt', 'w', encoding='utf-8') as file:
    for line in headlines:
        file.write(line + '\n')

print(" Headlines saved to 'headlines.txt'")
