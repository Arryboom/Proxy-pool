Proxy Pool
==========
包含http(s)/socks的极简代理池服务。
注：大佬就不用看了，你们分分钟撸一个自己的^_^

> python3.6  
> windows 


### 说明

* 为什么叫极简？

	你可能已经搜过关于代理池，大多用到了数据库储存，打分，提前验证什么的，定时刷新（嗯..这个功能我用一种相比更简单的方式也加上了），复杂、不那么简单，动手做的过程中慢慢发现了问题。。。
		
	免费代理根本不需要用数据库做保存，也不需要验证好了放数据库，需要的时候拿。免费代理就像丢盔弃甲的残兵败将，有力气的还能挥两下钝剑，也就那两下，上一秒活着，下一秒就死了，又或者这一秒躺着像个死人，下一秒又爬起来走两步，
	
	**极低的质量和极低的稳定性**根本**不值得**提前做验证使用数据库当宝一样保存起来。
		
	这个代理池的核心部分也就100来行，即便是初学者，也能快速开始使用。建议你先从爬代理的两个py开始看。
		

* 啥功能?

	通过requests get方法获取一个socks代理 
	
	```requests.get('localhost:5000/getsocks/').text```
	
	<img src="https://github.com/Shaw-lib/Proxy-pool/raw/master/getsocks.png" width="20%" height="20%">
		
	通过requests get方法获取一个http(s)代理 
	
	```requests.get('localhost:5000/gethttps/').text```
	
	<img src="https://github.com/Shaw-lib/Proxy-pool/raw/master/gethttps.png" width="20%" height="20%">
		
	通过requests get方法开启自动刷新服务，10分钟/次 
	
	```requests.get('localhost:5000/refresh/').text```
	
	<img src="https://github.com/Shaw-lib/Proxy-pool/raw/master/show.gif" width="20%" height="20%">
		
	不用等待refresh的返回值，请求发送了就可以了，可以在命令行看到状态，这就是gevent的作用。
	
	如果10分钟没到你想再刷新一次，嗯，可以的。
	
	 **注：** GatherProxy.com的服务器很脆弱，经常崩掉，请爱护它 0.0

--------------

### 那么，开始吧

* 准备

	1.建议使用虚拟环境
	
	```virtualenv proxypool```
	  
	```cd proxypool/Scripts```
	  
	```activate```
	  
	2.需要的第三方库，直接复制下面这条命令就好
	
	```pip install requests lxml beautifulsoup4 flask gevent ```
	
	3.开启服务
	
	```python app.py ```
	
	4.打开浏览器试验一下
	
	```localhost:5000/```
	
	<img src="https://github.com/Shaw-lib/Proxy-pool/raw/master/localhost.png" width="20%" height="20%">

服务部署完了！

* PLUS

	**Tips:** test.py是一个使用代理池服务的小爬虫案例，有点麻烦只是，你需要在爬虫项目中通过requests获得一个随机的代理，我不能保证这个代理就能用，毕竟免费的，所以我们直接给爬虫用，不行就换一个。


------------


**欢迎交流:**

	QQ:584927688
	
	微信:18271693418(这个手机号拒接一切陌生电话=.=)
	
	也可以直接issues，我每天都会来。
