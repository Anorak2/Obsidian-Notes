## Quickly share files with python
	python -m http.server 8000
## Converting Music files in a Dir
- `for f in *.flac; do ffmpeg -i "$f" "${f%.flac}.mp3"; done`

## Serial into Pi5
- `screen /dev/ttyUSB0 1500000`

# Gpg general form
- `gpg --batch --output out.zip.gpg --symmetric --cipher-algo AES256 in.zip`

##  Pi5
http://www.orangepi.org/orangepiwiki/index.php/Orange_Pi_5
- `sudo screen /dev/tty0 1500000`
![[Pasted image 20251113174903.png]]

**generate ssh keypair -> send to keepassxc**
	`ssh-keygen -o -f keepassxc -C johndoe@example`

**GPG**
```
gpg --cipher-algo AES256 --output test.gpg --symmetric test.out
```
```
gpg --output test.out -d test.gpg 
```

## Zip
```
zip out.zip dir
```
```
zip --encrypt out.zip dir
```


[[Debugging Dnsmasq]]



