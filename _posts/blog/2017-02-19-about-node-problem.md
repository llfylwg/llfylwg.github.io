---
layout: post
title: Node.js中fs.renameSync问题
category: blog
description: 如何解决？
---

## 如何解决报错呢？

在上传文件时，会遇到文件重命名问题


**错误代码如下**

    fs:js return bingding rename(pathMoudule._makeLong()),
    error: cross-device link not permitted`

代码如下：

    function upload(response,request){
		    console.log("Request handler 'upload' was called");
		    var form = new formidable.IncomingForm();
		    form.uploadDir='tmp';  //(加上这一行代码可以解决)
		    console.log('about to parse');
		    form.parse(request,function(error,fields,files){
		    console.log('parsing done');
		    fs.renameSync(files.upload.path,"./tmp/test.png");
		    response.writeHead(200,{"Content-Type":"text/html"});
		    response.write("receive img<br/>");
		    response.write("<img src='/show' />");
		    response.end();
   			})  
    }


加上了`form.uploadDir="tmp"`可以解决上传出错的问题，原因大概是因为跨盘操作文件没有权限。增加个临时目录tmp就可以了！

