# StorageX

## Installable

```bash
pip install storagex 
```

## CommandLine

### Upload file

```bash
-->rainx@JingdeMacBook-Pro:~/dev/storagex$ storagex upload /tmp/sz000001 
2017-09-08 23:21:45.570764 [storagex] total file size is 0
2017-09-08 23:21:45.571984 [storagex] seq 0 size is 0
2017-09-08 23:21:47.833424 [storagex] meta is : {"piece_width": 1024, "protocol_version": 1.0, "pieces": [], "piece_height": 768, "filename": "sz000001"}
2017-09-08 23:21:47.833511 [storagex] meta key is : http://f.hiphotos.baidu.com/image/pic/item/1b4c510fd9f9d72a455d3a22df2a2834349bbbd7.jpg 
Completely uploaded! YOUR DOWNLOAD KEY IS : http://f.hiphotos.baidu.com/image/pic/item/1b4c510fd9f9d72a455d3a22df2a2834349bbbd7.jpg
```

### Download File

```bash
-->rainx@JingdeMacBook-Pro:~/dev/storagex [master]$ storagex download http://f.hiphotos.baidu.com/image/pic/item/1b4c510fd9f9d72a455d3a22df2a2834349bbbd7.jpg /tmp/sz000001.backup
{"piece_width": 1024, "protocol_version": 1.0, "pieces": [], "piece_height": 768, "filename": "sz000001"}
donwload done! the file is /tmp/sz000001.backup
```

### API

### Upload file

```python
from storagex.storage import Storage

storage = Storage(width=600, height=600) 
# width and height will decide the chunk size ,one chunk size will be `width * height * 3 - 4`
key, meta_info = storage.upload(file_name)
```
### Download file

```python
from storagex.storage import Storage

storage = Storage()
storage.download_file(meta_info_key, file_name)
```