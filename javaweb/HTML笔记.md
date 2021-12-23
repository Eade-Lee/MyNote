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



###### 表格



```html
<!DOCTYPE html>


<html>
    <head>
            <title>
                表格
            </title>
    </head>
    <body>
 
        <table border="1px" width="300px" height="150px"  align="center_vertical">
			<tr>
			    <th>a</th>
			    <th>b</th>
			    <th>c</th>
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

