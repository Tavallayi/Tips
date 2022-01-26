Get 10 first lines of stream
``` powershell
Get-Content D:\example.txt | Select -First 10
```
Skip 10 first lines of stream
``` powershell
Get-Content D:\example.txt | Select -Skip 10
```
Get lines 4 to 10 from stream
``` powershell
Get-Content D:\example.txt | Select -Skip 4 -First 6
```

Get 10 first lines of file
``` powershell
Get-Content -First 10 D:\example.txt
```
Get 10 last lines of file
``` powershell
Get-Content -Tail 10 D:\example.txt
```
Get lines 4 to 9 from file
```
Get-Content -First 10  .\example.txt | select -skip 4  -First 5
```


https://stackoverflow.com/a/36507532

https://shellgeek.com/powershell-get-content-get-top-lines-of-the-file/
2022-01-26
