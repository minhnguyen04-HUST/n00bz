# **Satellite Killer**
**Difficulty**: Easy

**Description**: Most satellites get to live out a relatively peaceful existence in space until their orbit eventually decays and they fall back to Earth.

Most.

Back in the 80's, one poor satellite met a premature end at the hands of an ASM-135.

I would like you to find the date that the second-to-last piece of its debris fell back down to Earth (Or more realistically, its decay date).

In addition, please give me its object ID/International Code.

*Flag format: PCTF{OBJECTID_YEAR-MONTH-DAY}*

*For example, for a piece of debris from the Falcon 9, the flag would look like this: PCTF{2023-028BG_2023-3-15}*

# Solution

Through some basic Google searches, I could identify the name of the satellite was Solwind. When reading about Solwind, I found out that the last debris deorbited 8 May 2004. But the challenge required the deorbited day of the second-to-last debris, so I tried another tools. I used this page to have a look on every 285 debris of the satellite: [https://in-the-sky.org/search.php](https://)

![](https://github.com/minhnguyen04-HUST/n00bz/blob/main/PatriotCTF/Satellite%20Killer/image.jpg)

So I knew the last one fell down to Earth in 2004, I tried some closed to 2004 and I got the one with **NORAD_ID**: 16085 right. 

*FLAG: PCTF{1979-017AN_2022_12_6}*
