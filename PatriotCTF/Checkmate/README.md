# **Checkmate**
**Difficulty**: Medium

**Describtion**: Get your adrenaline pumping as you navigate the thrilling world of Crypto Web for Capture the Flag.

Minor brute force is allowed, but you should not need over 4000 tries.

*Flag format: PCTF{}*

[http://chal.pctf.competitivecyber.club:9096/](https://)

# **Solution**
At first look, I had only this webpage, running only Javascript and no interactions with back-end things. ![](https://hackmd.io/_uploads/rkqH5haC2.jpg)

When I submit "name" and "password", only some alert functions pop up, so I had look at the source code. Just focus on these Javascript code:
```
<script>

function checkName(name){

    var check  = name.split("").reverse().join("");
    return check === "uyjnimda" ? !0 : !1;
}

function checkLength(pwd){
     return (password.length % 6 === 0 )? !0:!1;
    }
function checkValidity(password){
    const arr = Array.from(password).map(ok);
    function ok(e){
        if (e.charCodeAt(0)<= 122 && e.charCodeAt(0) >=97 ){
        return e.charCodeAt(0);
    }}

    let sum = 0;
    for (let i = 0; i < arr.length; i+=6){
        var add = arr[i] & arr[i + 2]; 
        var or = arr[i + 1] | arr[i + 4]; 
        var xor = arr[i + 3] ^ arr[i + 5];
        if (add === 0x60   && or === 0x61   && xor === 0x6) sum += add + or - xor; 
    }
   return  sum === 0xbb ? !0 : !1;
}
// /check.php 
var btn = document.getElementsByClassName('btn-1')[0];
btn.addEventListener('click',(e)=>{
    e.preventDefault();

    var nam = document.getElementById('name').value;
    if(!(checkName(nam))){         
         alert('Incorrect Name! 😥😥')
    }
    else{
           alert('Correct Name! 🙂🙂')
    }

    var pwd = document.getElementById('password').value;
    if(!checkValidity(pwd) && !checkLength(pwd)){
            alert('Incorrect Password! 😥😥')
    }
    else{
           alert('Correct Password! 🙂🙂')
    }
});


</script>
```

So we knew "name" value should be "adminjyu" (but this wasn't important). Noticing in the **checkLength** and **checkValidity** function, we had to find the password satisfy these conditions and there were plenty of them. And the challenge mentioned some kind of brute force so I went for it. And also, the page source reavealed where I could get the flag - at the ***/check.php*** path.

Here is my payloads: 
```
import string
import requests
import sys

url = "http://chal.pctf.competitivecyber.club:9096/check.php"
session = requests.Session()

string_printable = string.ascii_lowercase + '_'
string_char = list()
for x in string_printable:
    string_char.append(x)



key_and = dict()
key_or = dict()
key_xor = dict()

for char in string_char:
    for x in string_char:
        if (ord(char) & ord(x)) == 96:
            key_and.setdefault(char,[]).append(x)
        if (ord(char) | ord(x)) == 97:
            key_or.setdefault(char,[]).append(x)
        if (ord(char) ^ ord(x)) == 6:
            key_xor.setdefault(char,[]).append(x)

#print(f"{key_xor} '\n'  {key_and} '\n'  {key_or}")

pwd = ''
cnt = 0
for char_1, value_list_1 in key_and.items():
    for value_1 in value_list_1:
        for char_2, value_list_2 in key_or.items():
            for value_2 in value_list_2:
                for char_3, value_list_3 in key_xor.items():
                    for value_3 in value_list_3:
                        pwd = char_1 + char_2 + value_1 + char_3 + value_2 + value_3
                        print(f"Trying with password: {pwd}")

                        response = session.post(url, data = {"password" : pwd})
                        content = response.text
                        cnt += 1
                        if "incorrect" in content:
                            print("Error")
                        else:    
                            print(content)
                            print(f'The correct password is: {pwd}')
                            print(f"We have tried {cnt} times")
                            sys.exit()

print(f"We have tried {cnt} times")


#password = sadsau
#flag:PCTF{Y0u_Ch3k3d_1t_N1c3lY_149}
```
