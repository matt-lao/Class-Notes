## IP + Port
- IP - identifier of machine
- Port - identifier of application
	- 80 - default HTTP
	- 433 - default HTTPS

## How to Setup Server in VSCode
```PowerShell
cd ./directory-of-site/
npm install -g static-server
static-server -p 8000
```

## Curl
```PowerShell
curl http://localhost:8000/index.html
# use -v to show request header
```

## Static Server Review
Example: https://stthomas.edu/cisc/375.html

Client Side:
- Connect to server
	- stthomas.edu -> server -> resolves to DNS
- Connect to port
	- https -> 403
	- Denotes application on server you want to connect to
- Issue GET request
	- What content you want
	- cisc/375.html

Server Side:
- Read file with path equal to request
- Respond with content (internals) of the file
	- Html text NOT html file