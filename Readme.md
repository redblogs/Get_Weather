项目要求：输入一个城市名称，把对应城市的天气信息打印出来展示给客户。

项目思路：

之所以能知道一个城市现在的天气,是因为用了中国天气网(www.weather.com.cn)提供的天气查询接口,例如访问www.weather.com.cn/data/cityinfo/101010100.html就能看见北京现在的天气,这段看上去有点像python字典类的文字是一种称作json格式的数据。而我们程序要做的事情就是按照用户输入城市的名称，去天气网的接口请求对应的天气信息，再将结果展示给客户。

1.在这个程序中,需要用到两个新模块：urllib2
	
	1.urllib2用来发送网络请求,获取数据
	
	2.json用来解析获得数据

2.深入剖息：我们请求北京天气时用了"101010100"这样的数字,这是天气网设定的城市代码,然而令人蛋疼的是,天气网并没有直接给出城市所有城市代码的对应关系,而是给了下面三个接口：

	a.http://m.weather.com.cn/data5/city.xml	获取所有省/直辖市的编号，如“01|北京，02|上海，03|天津”

	b.http://m.weather.com.cn/data5/city省编号.xml	获取二级地区编号,如江苏是city19.xml

	c.http://m.weather.com.cn/data5/city二级编号.xml	获取三级编号,如南京是city1901.xml

3.实现过程:

	1.利用cityFirstCode.py脚本中的程序获取一级地区编号,保存在字典中.字典以城市为key,地区编号为value存放

	2.以用户输入的城市名称,找到一级域名后,在获取二级地区编号,在获取三级地区编号,最终拼接为完整的天气信息链接

	3.整理分析最终的天气信息网页提取出所需要的网页信息并显示打印出来

