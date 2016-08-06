## angular-filemanager API docs [multiple file support]

#### 上市 (URL: fileManagerConfig.listUrl, Method: POST)

**JSON请求内容**
```json
{
    "action": "list",
    "path": "/public_html"
}
```
**JSON响应**
```json
{ "result": [ 
    {
        "name": "magento",
        "rights": "drwxr-xr-x",
        "size": "4096",
        "date": "2016-03-03 15:31:40",
        "type": "dir"
    }, {
        "name": "index.php",
        "rights": "-rw-r--r--",
        "size": "549923",
        "date": "2016-03-03 15:31:40",
        "type": "file"
    }
]}
```
--------------------
#### 重命名 (URL: fileManagerConfig.renameUrl, Method: POST)
**JSON请求内容**
```json
{
    "action": "rename",
    "item": "/public_html/index.php",
    "newItemPath": "/public_html/index2.php"
}
```
**JSON响应**
```json
{ "result": { "success": true, "error": null } }
```
--------------------
#### 移动 (URL: fileManagerConfig.moveUrl, Method: POST)
**JSON请求内容**
```json
{
    "action": "move",
    "items": ["/public_html/libs", "/public_html/config.php"],
    "newPath": "/public_html/includes"
}
```
**JSON响应**
```json
{ "result": { "success": true, "error": null } }
```
--------------------
#### 复制(URL: fileManagerConfig.copyUrl, Method: POST)
**JSON请求内容**
```json
{
    "action": "copy",
    "items": ["/public_html/index.php", "/public_html/config.php"],
    "newPath": "/includes",
    "singleFilename": "renamed.php" <-- (only present in single selection copy)
}
```
**JSON响应**
```json
{ "result": { "success": true, "error": null } }
```
--------------------
#### 删除 (URL: fileManagerConfig.removeUrl, Method: POST)
**JSON请求内容**
```json
{
    "action": "remove",
    "items": ["/public_html/index.php"],
}
```
**JSON响应**
```json
{ "result": { "success": true, "error": null } }
```
--------------------
#### 编辑文件 (URL: fileManagerConfig.editUrl, Method: POST)
**JSON请求内容**
```json
{
    "action": "edit",
    "item": "/public_html/index.php",
    "content": "<?php echo random(); ?>"
}
```
**JSON响应**
```json
{ "result": { "success": true, "error": null } }
```
--------------------
#### 获取文件的内容 (URL: fileManagerConfig.getContentUrl, Method: POST)
**JSON请求内容**
```json
{
    "action": "getContent",
    "item": "/public_html/index.php"
}
```
**JSON响应**
```json
{ "result": "<?php echo random(); ?>" }
```
--------------------
#### 创建文件夹 (URL: fileManagerConfig.createFolderUrl, Method: POST)
**JSON请求内容**
```json
{
    "action": "createFolder",
    "newPath": "/public_html/new-folder"
}
```
**JSON响应**
```json
{ "result": { "success": true, "error": null } }
```
--------------------
#### 设置权限 (URL: fileManagerConfig.permissionsUrl, Method: POST)
**JSON请求内容**
```json
{
    "action": "changePermissions",
    "items": ["/public_html/root", "/public_html/index.php"],
    "perms": "653",
    "permsCode": "rw-r-x-wx",
    "recursive": true
}
```
**JSON响应**
```json
{ "result": { "success": true, "error": null } }
```
--------------------
#### 压缩文件 (URL: fileManagerConfig.compressUrl, Method: POST)
**JSON请求内容**
```json
{
    "action": "compress",
    "items": ["/public_html/photos", "/public_html/docs"],
    "destination": "/public_html/backups",
    "compressedFilename": "random-files.zip"
}}
```
**JSON响应**
```json
{ "result": { "success": true, "error": null } }
```
--------------------
#### 提取文件 (URL: fileManagerConfig.extractUrl, Method: POST)
**JSON请求内容**
```json
{
    "action": "extract",
    "destination": "/public_html/extracted-files",
    "item": "/public_html/compressed.zip"
}
```
**JSON响应**
```json
{ "result": { "success": true, "error": null } }
```
--------------------
#### 上传文件 (URL: fileManagerConfig.uploadUrl, Method: POST, Content-Type: multipart/form-data)

**HTTP POST请求负载**
```
------WebKitFormBoundaryqBnbHc6RKfXVAf9j
Content-Disposition: form-data; name="destination"
/

------WebKitFormBoundaryqBnbHc6RKfXVAf9j
Content-Disposition: form-data; name="file-0"; filename="github.txt"
Content-Type: text/plain
```
**JSON响应**
```json
{ "result": { "success": true, "error": null } }
```
无限上传文件的项目，每个项目将被列为file-0，file-1，等。


例如，您可以检索使用PHP文件：
```php
$destination = $_POST['destination'];
$_FILES['file-0'] or foreach($_FILES)
```
--------------------
#### 下载/预览文件 (URL: fileManagerConfig.downloadMultipleUrl, Method: GET)
**Http query params**
```
[fileManagerConfig.downloadFileUrl]?action=download&path=/public_html/image.jpg
```
**响应**
```
-File content
```
--------------------
#### 下载的倍数文件在jpg/zip (URL: fileManagerConfig.downloadFileUrl, Method: GET)
**JSON Request content**
```json
{
    "action": "downloadMultiple",
    "items": ["/public_html/image1.jpg", "/public_html/image2.jpg"],
    "toFilename": "multiple-items.zip"
}}
```
**响应**
```
-File content
```
--------------------
##### 错误/异常
任何后端的误差应与HTTP代码错误500.

顺便说一句，你也可以报告错误200响应使用JSON结构
```json
{ "result": {
    "success": false,
    "error": "Access denied to remove file"
}}
```
