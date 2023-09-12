
# **Scavenger Hunt**
**Difficulty**: Beginner 

**Description**: Can you find all the hidden pieces of the flag?

*Flag format: PCTF{}*

[http://chal.pctf.competitivecyber.club:5999/](https://)

# Solution
When viewing the source code of the page, we can see the first two parts of the flag

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>Scavenger Hunt</title>
  </head>
  <body style="background-color:#f7e172;">
    <main>
        <h1 style="text-align:center">There are 5 flags hidden on this webpage, find them all to solve the scavenger hunt!</h1> 
		<h1 style="text-align:center">Flag 1/5 - PCTF{Hunt</h1> 
    </main>
  </body>
  <script src="script1.js" type="text/javascript"></script> 
  <script src="script2.js" type="text/javascript"></script> 
</html>
<!-- Flag 2/5 - 3r5_4n -->
```

*Flag 1/5 - "PCTF{Hunt"*

*Flag 2/5 - "3r5_4n"*

Then, I noticed two Javascript files and when examining those, I found another two pieces

*Flag 4/5 - "R5_e49"*

*Flag 5/5 - "e4a541}"*

So where could be the final piece of the flag? I tried some common paths such as robots.txt, admin.php,... And I found the last piece in robots.txt

*Flag 3/5 - D_g4tH3*

Flag: PCTF{Hunt3r5_4nD_g4tH3R5_e49e4a541}
