# PHP

## Windows下配置PHP环境

### PHP自身设置

>- 下载需要的php版本
>- 解压到需要放置的目录
>- 复制粘贴php.ini-deployment并改成php.ini
>- 打开并设置extension_dir = <指向扩展库目录的路径> - extension_dir 需要指向存放 PHP 扩展库文件的目录。可以是绝对路径（如 "C:\PHP\ext"）或相对路径（如 ".\ext"）。在 php.ini 文件中要加载的扩展库都必须在 extension_dir 所指定的目录之中。
>- 打开要激活的extension = xxxxx.dll - 对每个需要激活的扩展，都需要一行相应的 "extension=" 语句来说明 PHP 启动时加载 extension_dir 目录下的哪些扩展。 

### 将Apache和php关联

>- 确保Apache成功安装,我的php在E:/PHP/php下,Apache2.4,PHP7.0
>- 找到Apache下的conf下的httpd.conf文件，找到#LoadModule，在后面加入“LoadModule php7_module E:\PHP\php\php7apache2_4.dll”,其中E:PHP/pho为php的位置，php7apache2_4.为要加载的类库(在php下面找对应的名字)
>- 在下一行加入AddHandler application/x-httpd-php .php或者<FilesMatch \.php$>SetHandler application/x-httpd-php </FilesMatch>，后者可以保证.php.txt类似文件不被处理
>- 在下一行加入PHPIniDir E:/PHP/php		
>- 测试，在htdocs下新建一个index.php ，内容为<?php phpinfo()  ?>，浏览器中输入loclahost/index.php，如果现实php配置，则成功
	Note：
		修改DirectoryIndex index.html index.php可以使index.php默认打开，先后顺序决定那个优先打开
### MySql和php关联:
>- 找到php.ini并打开,找到如下;extension=php_mysqli.dll，将它们前面的;去掉即可
>- 测试

## 缓存

>- php的缓存机制
		1. output_buffering(ob类的函数)			
		2. 程序缓存(flush)
		3. 相关的配置
			①.display_errors 
			②.error_reporting 
			③.output_buffering 	
>- 服务器缓存
>- 浏览器缓存

## 静态化

>- 使用ob来实现伪静态化:
	缺点:
		①实时性不好，延迟
		②请求某个页面时使用php动态连接

>-真静态化
	概念：在添加和修改的时候，实时生成静态页面（不用ob）
	好处：减少服务器对数据响应的负荷，加载不用调用数据库，便于搜索引擎
	缺陷：数据量过大，造成真静态的html页面过多，磁盘占用过多

>- 伪静态化
	1.php程序中用正则表达式提取参数
		以前访问一个页面使用.xxx?id=1&lang=zh,现在用.xxx/1.zh.html(使用正则表达式提取参数)，即动态网址静态化
	2.Apache的rewrite
		流程：
			①Apache的配置文件中开启rewrite模块
			②配置<Directory >节点下的 AllowOverride All
			③配置.htaccess文件
				RewriteEngine On   //$i i为正则表达式的第几个匹配项，正则表达式的反向匹配(\d)\1
				RewiteRule news-id(\d)\.html  news.xxx?id=$i
				RewiteRule 正则表达式         对应的请求
				RewiteRule 正则表达式		  对应的请求
				#在外层加上<IfModule rewrite_module></IfModule>表示如果启用了rewrite模块
			④也可以把这些rewrite规则写在<Directory>节点中

## 静态化的原则

	1.网站实时性要求高，不要使用静态化
	2.网站访问量小，没必要使用静态化
	3.数据项目不多，但是访问频率很高，建议使用真静态化（如新浪新闻频道）
	4.数据项目海量，使用真静态会生成海量的html，建议使用伪静态
	5.在大型网站中，静态化技术是综合使用的
	6.推荐使用伪静态和缓存技术来加速网站访问速度

## PHP发送http请求

>- fopen
>- file_get_contents
>- fsockopen
>- 使用curl库
>- 第三方类库HttpClient

## php的单引行双引号

>- 当外面是双引号时，里面用单引号;当外面是单引号时，里面使用双引号
>- PHP中，双引号会搜索引号内的内容是不是变量，有则输出其值，没有则输出原有内容;单引号则直接输出里面的字符
