# **Karter**
**Difficulty**: Medium

**Description**: In 2021, Flipkart added a new director. Your task is to find:

* his last name (UPPERCASE)
* his Director Identification Number
* And the URL of the primary source from where you found his name (URL format: scheme://subdomain.rootdomain.tld) paths excluded

*Flag Format: PCTF{LASTNAME_IdentificationNumber_URL}*

*Example: PCTF{SMITH_123456_https://www.google.com}*

# Solution
So at first look, I had no clues where to start with since I tried some Google searchs with "Flipkart" keyword. 

Then I searched Director Identification Number and I found this https://www.mca.gov.in/mcafoportal/viewCompanyMasterData.do

And in the "lookup" for Company name, I searched for "Flipkart" and I got several companies. When viewing every company, I could see the date of their directors appointed. Finally I got one being appointed in 2021. 

Flag: PCTF{Collins}
