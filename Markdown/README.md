# Markdown基础语法学习


# #一级标题

## ##二级标题

### ###三级标题

#### ####以此类推，总共六级标题，建议在井号后加一个空格

####无序列表 -,*,+ 开头都可以,也需要一个空格哦
- 无序列表 - 
* 无序列表 *
+ 无序列表 +

####有序列表 1.2.... 需要加空格
1. 有序列表1
2. 有序列表2
3. 有序列表3

####嵌套列表 要缩进4个空格
- 列表1
    1. 列表2
        1. 列表3
    2. 列表2
        * 列表4
        * 列表4
- 列表1

####引用 > 
> 这是引用内容

####引用中的引用 >>前面需要一个空格
> 这是引用
 >> 这才是引用中的引用

####字体
我要 **\*\*加粗\*\***  *\*斜体\**  ~~~~删除线~~~~

####如何加代码 tab 或者4个空格
	<!--lang: javascript-->
	var a = 1;
	print("hello world");
    print("4 space or tab");


####文字超级链接 [超链接文字]\(网址 "鼠标移上去的提示"\)
[yimiaodaren](https://github.com/yimiaodaren "yimiaodaren")

####图片 ![如果无法显示图像，浏览器将显示替代文本alt]\(图片网址,也可以是相对路径 "鼠标移上去的提示"\)
![yimiaodaren](https://avatars3.githubusercontent.com/u/5618443?v=3&s=460 "yimiaodaren")

####索引超链：Reference方式 网址可以用\[1\]来代替,然后需要申明\[1\]:网址 提示语
[yimiaodaren][1]
[1]:https://github.com/yimiaodaren "yimiaodaren"

####自动链接 <网址>
<https://github.com/yimiaodaren>

####表格
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned |   $16 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |






sublime text 3 插件 OmniMarkupPreviewer 报404解决办法
http://blog.csdn.net/gsying1474/article/details/53642097