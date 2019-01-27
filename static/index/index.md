
#### html嵌入markdown格式
markdown用于在html文件中解析mark down格式
地址为`https://github.com/showdownjs/showdown`
用法可参考github的readme文件， 简单的举例如下：
```
<html>
	<head>
		<script src="static/js/showdown.min.js"></script>
	</head>
	<body>
		<div id="markdown" style="border: black 1px solid;border-radius:10%;position: absolute; top: 2%; bottom:2%; left:20%; right:20%; padding: 20px; border-radius: 5px; padding-right:260px;overflow:auto;background:white">
		</div>
	</body>
	<script>
		var xhr = new XMLHttpRequest();  
		xhr.open("get","static/index/index.md");      
		xhr.send();
		xhr.onreadystatechange = function(){ 
			if(xhr.readyState === 4 && xhr.status === 200){ 
				var converter = new showdown.Converter();
				converter.setOption('tasklists', true); 
				var html = converter.makeHtml(xhr.responseText);
				$("#markdown").html(html);   
			}
		}
	</script>
</html>
```
