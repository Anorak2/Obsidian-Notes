
## General Use 
 **Converting Music files in a Dir**
- `for f in *.flac; do ffmpeg -i "$f" "${f%.flac}.mp3"; done`

**Zip**
```
zip out.zip dir
```
```
zip --encrypt out.zip dir
```
#### Gpg 
- `gpg --batch --output out.zip.gpg --symmetric --cipher-algo AES256 in.zip`

```
gpg --cipher-algo AES256 --output test.gpg --symmetric test.out
```
```
gpg --output test.out -d test.gpg 
```

**Quickly share files with python**
	python -m http.server 8000


[[Debugging Dnsmasq]
## Networking
- `ping -c 5 ip
- `traceroute

`mtr -zb hostname
- shows the route in real time with autonomous systems numbers

DNS:
- `dig`
- `nslookup`
