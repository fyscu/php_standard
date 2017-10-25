### 什么是 composer

没有什么比 **[composer中文网](http://docs.phpcomposer.com/00-intro.html)** 更值得去看一遍了。

如果你想深入研究`composer`的话，还是推荐先看一下上面的网站。

本文的重点是摘要部分实战中用得比较多的**知识点**, 以及一些最佳实践。

### Getting Start

- 安装`composer`

	这里当然不会叫你如何安装`composer`，**[composer安装指南](http://docs.phpcomposer.com/00-intro.html#Installation-*nix)**已经介绍得很清楚了。
	
	这里是要补充一些可能的问题。
	
	1.下载composer.phar以后，没有composer命令怎么办？
	
	答案就是自己做软链
	> ln -s /path/of/composer.phar /usr/bin/composer
	
	2.使用国内的源
	
	这个怎么说呢，如果你用过`apt-get` `yum` `npm`之类，就很能理解什么是国内源了。
	
	> composer config -g repo.packagist composer https://packagist.laravel-china.org
	
### 既然是简介本文就到此结束，更细节的部分将在下一节呈现。