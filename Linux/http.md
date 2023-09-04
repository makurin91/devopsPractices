### Curl

* `curl --head example.com`
* `curl -X POST -d "param1=value1&param2=value2" https://example.com/api` By default curl send GET requests but with -X
  can use POST, PUT etc..
* `curl -X POST -F "file=@path/to/file.ext" https://example.com/upload`
* `curl -X POST -H "Content-Type: application/json" -d '{"param1": "value1", "param2": "value2"}' https://example.com/api`




### Wget

* `wget --server-response --spider example.com`
* `wget https://example.com/file.ext`
* `wget -b https://example.com/file.ext` download in background
* `wget -r https://example.com` recursive download of the entire site
* `wget -r -nH --cut-dirs=1 https://example.com` loading while maintaining the original directory structure
* `wget -r -A "*.jpg,*.png" https://example.com/images` Boot skipping certain extensions
* `wget --proxy=on https://example.com` downloading through a specific proxy