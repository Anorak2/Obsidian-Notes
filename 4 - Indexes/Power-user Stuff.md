## Quickly share files with python
	python -m http.server 8000
## Converting Music files in a Dir
- `for f in *.flac; do ffmpeg -i "$f" "${f%.flac}.mp3"; done`

## Serial into Pi5
- `screen /dev/ttyUSB0 1500000`

[[Debugging Dnsmasq]]
