###### html基本标签

```html
<!doctype html>
<html>
    <head>
        <title>
            HTML的基本标签
        </title>
    </head>
    <body>
        <!--段落标记-->
        <p>《黛玉葬花》是文学名著《红楼梦》中的经典片段。林黛玉最怜惜花，觉得花落以后埋在土里最干净，说明她对美有独特的见解。她写了葬花词，以花比喻自己，在《红楼梦》中是最美丽的诗歌之一。贾宝玉和林黛玉在葬花的时候有一段对话，成为《红楼梦》中一场情人之间解除误会的绝唱。</p>
        《黛玉葬花》是文学名著《红楼梦》中的经典片段。林黛玉最怜惜花，觉得花落以后埋在土里最干净，说明她对美有独特的见解。<p>kjsadnckjasncoanjaoncdoa</p>她写了葬花词，以花比喻自己，在《红楼梦》中是最美丽的诗歌之一。贾宝玉和林黛玉在葬花的时候有一段对话，成为《红楼梦》中一场情人之间解除误会的绝唱。《黛玉葬花》是文学名著《红楼梦》中的经典片段。林黛玉最怜惜花，觉得花落以后埋在土里最干净，说明她对美有独特的见解。她写了葬花词，以花比喻自己，在《红楼梦》中是最美丽的诗歌之一。贾宝玉和林黛玉在葬花的时候有一段对话，成为《红楼梦》中一场情人之间解除误会的绝唱。
        <!--换行标记，br标签是一个独立标记-->
    hello word
    hello<br>word

    <!--color和width都是hr的标签属性-->
    <hr color="red" width="50%">
    <hr color="blue" width="30%">


    <!--pre标签 预留格式-->
    <pre>
        pre标签中的内容保持不变
    </pre>

    </body>
</html>
```



###### 表格及背景颜色 背景图片



```html
<!DOCTYPE html>


<html>
    <head>
		<meta charset="utf-8" />
		<!--上面这行代码作用是告诉浏览器
		采用哪一种字符集打开当前页面
		不是设置当前页面的字符集-->
            <title>
                表格
            </title>
    </head> 
	
	//bgcolor 背景颜色
	//background 背景图片
    <body bgcolor="beige"  background="路径">
 
        <table border="1px" width="300px" height="150px"  align="center_vertical">
			<tr>
			    <th>第一列</th>
			    <th>第二列</th>
			    <th>第三列</th>
			</tr>
            <tr>
				
				
                <td>a</td>
                <td>b</td>
                <td>c</td>
            </tr>
			
			<!--行合并：rowspan
				列合并：colspan
				row合并时 删除单元格删除下面的
				
				th标签也是单元格标签
				自带加粗居中-->
            <tr>
                <td colspan="2">de</td>
                
                <td rowspan="2">fz</td>
            </tr>

            <tr>
                <td>x</td>
                <td>y</td>
             
               
            </tr>
            
        </table>
        <table border="3px" width="%60">
            <tr>
                <td>a</td>
                <td>b</td>
                <td>c</td>
            </tr>
            <tr>
                <td>d</td>
                <td>e</td>
                <td>f</td>
            </tr>

            <tr>
                <td>x</td>
                <td>y</td>
                <td>z</td>
               
            </tr>
            
        </table>
		
    </body>
</html>
```

###### 超链接





```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>超链接  热链接</title>
	</head>
	
	<body>
		<!-- href: hot references
		href属性后面一定是一个资源地址
		路径可以是绝对路径/相对路径/网络资源中的路径/本地路径-->
		<a href="https://www.baidu.com/">百度2</a>
		<a href="表格2.html">表格</a>
		<a href="图片.html"><img src="bg.jpg" width="120px" ></a>
		<a href="表格2.html" target="_blank">表格</a>
		超链接的target属性
		_blank新标签页
		_self当前标签页
		_parent父窗口
		_top顶级窗口
	</body>
</html>

```





###### 列表

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>列表</title>
	</head>
	<body>
		<!--type="1/A/a/I" 顺序类型-->
		<!--有序列表:<ol>  
		-->
		<ol type="1/A/a/I">
			<li>中国
				<ol>
					<li>北京</li>
					<li>天津</li>
					<li>上海</li>
				</ol>
			</li>
			<li>美国</li>
			<li>日本</li>
		</ol>
		
		<!--无序列表:<ul>
		type="disc/circle/square" 前面小标志的形状
		-->
		<ul type="disc/circle/square">
			<li>中国
				<ul>
					<li>北京</li>
					<li>天津</li>
					<li>上海</li>
				</ul>
			</li>
			<li>美国</li>
			<li>日本</li>
		</ul>
		
		
	</body>
</html>

```

###### 表单

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>表单</title>
	</head>
	<!-- 
	1.用户填写表单，提交数据给服务器，
	所以表单是专门用来收集用户数据的。 
	2.表单标签 <form>
	3.一个页面可以有多个表单
	4.表单提交给服务器 form中的action属性用来指定地址
	
	-->
	<body>
		<form action="https://www.baidu.com/">
			<input type="submit" value="百度" />
		</form>
		
		
		<form action="http://localhost:8080/jd/login">
			用户名<input type="text"/><br />
			密码<input type="password" /><br />
			<input type="submit"value="登录" />
		
		</form>
		<br />
		
		<form action="http://localhost:8080/jd/login">
		<table border="1px">
			<tr>
				<td>用户名</td>  
				<td><input type="text" name="username" value="123" maxlength=""/></td>
			</tr>
			<tr>
				<td>密码</td>
				<td><input type="password" name="pwd" /></td>
			</tr>
			<tr align="center">
				<td colspan="2">
					<input type="submit" value="登录" />
					&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
					<input type="reset" value="清空" />
				
				</td>
				
			</tr>
		</table>
		</form>
		
		<br>
		<form action="http://localhost:8080/jd/login" method="post">
			<input type="radio" name="gender" value="1" />男
			<input type="radio" name="gender" value="0"  checked/>女
			<input type="checkbox" name="interest" value="smoke"/>抽烟
			<input type="checkbox" name="interest" value="drink"/>喝酒
			<input type="checkbox" name="interest" value="firehair" checked/>烫头
			<br />
			
			<select name="grade" multiple="multiple" size="2">
				<option value="gz">高中</option>
				<option value="dz">大专</option>
				<option value="bk" selected>本科</option>
				<option value="ss">硕士</option>
			</select>
			
			<textarea  rows="10" cols="60" name="introduce"></textarea>
			<input type="submit" value="注册" />
		</form>
	</body>
	<!--
（1）action属性等同于超链接的href属性，填写请求的url
（2）input标签属于输入域标签，input标签的type属性是text，表示文本框，是password，表示密码框
（3）input标签的type是submit表示提交按钮，该按钮可以提交表单，所谓表单的提交是发送请求url，并携带数据给服务器。
（4）所有按钮的value属性都是用来设置按钮上显示的文本内容 
		maxlength属性限制输入长度
（5）发送请求并提交数据时，数据格式遵循HTTP协议，所有浏览器都会采用这种格式：url?name=value&name=value&name=value...，其中name是input标签的name属性，value是input标签的value属性
（6）文本框和密码框的value不需要开发人员指定，用户填写的数据就是value。 指定则自动显示在文本框中
（7）submit按钮放到form标签外面无法提交表单
（8）普通按钮不具备提交表单的能力。
（9）radio单选按钮  name一样则单选 checked属性表示默认选中
（10）checkbox 复选框
（11）<select name="grade" multiple="multiple" size="2">
				<option value="gz">高中</option>
				<option value="dz">大专</option>
				<option value="bk" selected>本科</option>
				<option value="ss">硕士</option>
			</select>
			下拉列表
			multiple 多选属性 
			size显示的条数
（12）textarea文本域 没有value值 文本框中的内容即value
（13）form表单method属性：
提交方式有两种
get:提交后信息会显示在地址栏处
post:提交后会隐藏信息

 -->

</html>

```





###### file控件及hidden控件



```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>表单</title>
	</head>
	<!-- 
	1.用户填写表单，提交数据给服务器，
	所以表单是专门用来收集用户数据的。 
	2.表单标签 <form>
	3.一个页面可以有多个表单
	4.表单提交给服务器 form中的action属性用来指定地址
	
	-->
	<body>
		<form action="https://www.baidu.com/">
			<input type="submit" value="百度" />
		</form>
		
		
		<form action="http://localhost:8080/jd/login">
			用户名<input type="text"/><br />
			密码<input type="password" /><br />
			<input type="submit"value="登录" />
		
		</form>
		<br />
		
		<form action="http://localhost:8080/jd/login">
		<table border="1px">
			<tr>
				<td>用户名</td>  
				<td><input type="text" name="username" value="123"/></td>
			</tr>
			<tr>
				<td>密码</td>
				<td><input type="password" name="pwd" /></td>
			</tr>
			<tr align="center">
				<td colspan="2">
								<input type="hidden" name="userid" value="111" />
					<input type="submit" value="登录" />
					&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
					<input type="reset" value="清空" />
				
				</td>
				
			</tr>
		</table>
		</form>
		
		<br>
		<form action="http://localhost:8080/jd/login" method="get">
			<input type="radio" name="gender" value="1" />男
			<input type="radio" name="gender" value="0"  checked/>女
			<input type="checkbox" name="interest" value="smoke"/>抽烟
			<input type="checkbox" name="interest" value="drink"/>喝酒
			<input type="checkbox" name="interest" value="firehair" checked/>烫头
			<br />
			
			<select name="grade" multiple="multiple" size="2">
				<option value="gz">高中</option>
				<option value="dz">大专</option>
				<option value="bk" selected>本科</option>
				<option value="ss">硕士</option>
			</select>
			
			<textarea  rows="10" cols="60" name="introduce"></textarea>
			<input type="submit" value="注册" />
		</form>
	</body>
	<!--
（1）action属性等同于超链接的href属性，填写请求的url
（2）input标签属于输入域标签，input标签的type属性是text，表示文本框，是password，表示密码框
（3）input标签的type是submit表示提交按钮，该按钮可以提交表单，所谓表单的提交是发送请求url，并携带数据给服务器。
（4）所有按钮的value属性都是用来设置按钮上显示的文本内容
（5）发送请求并提交数据时，数据格式遵循HTTP协议，所有浏览器都会采用这种格式：url?name=value&name=value&name=value...，其中name是input标签的name属性，value是input标签的value属性
（6）文本框和密码框的value不需要开发人员指定，用户填写的数据就是value。 指定则自动显示在文本框中
（7）submit按钮放到form标签外面无法提交表单
（8）普通按钮不具备提交表单的能力。
（9）radio单选按钮  name一样则单选 checked属性表示默认选中
（10）checkbox 复选框
（11）<select name="grade" multiple="multiple" size="2">
				<option value="gz">高中</option>
				<option value="dz">大专</option>
				<option value="bk" selected>本科</option>
				<option value="ss">硕士</option>
			</select>
			下拉列表
			multiple 多选属性 
			size显示的条数
（12）textarea文本域 没有value值 文本框中的内容即value
（13）form表单method属性：
提交方式有两种
get:提交后信息会显示在地址栏处
post:提交后会隐藏信息

 -->

</html>

```

###### 

###### 属性readonly与disabled





![image-20211223143928052](https://raw.githubusercontent.com/Eade-Lee/MyNote/master/img/202112231439258.png)

![image-20211223143131119](https://raw.githubusercontent.com/Eade-Lee/MyNote/master/img/202112231431004.png)



