# Online Book Store 1.0 – Authenticated RCE 


## Usage

modify 
```
url = "<target-url>"
```
with the valid url

add the admin username and password at 

 ```
login_data = {
    "username": "admin",
    "password": "admin",
    "login": "1"
}
```

## Typical Web Shell Usage

* Access the uploaded PHP file directly via its URL
* Append `?cmd=<command>` to execute system commands
* Can be upgraded to a reverse shell for stable access

---


