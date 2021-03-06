# 前端笔记

![nihao](https://github.com/252590770/-/blob/master/images/kai-fa-yi-lai.png)

### 前端开发阶段需要依赖的东西

__http-server__ 是在本地架起一个网页服务器,方便开发者预览效果   
__browser-sync__ 除了具有http-server的功能外,还能同时调试不同的网页

### 安卓运行时权限


	compile 'com.yanzhenjie:permission:2.0.0-rc4'
  
	   AndPermission.with(this)
			.permission(new String[]{Manifest.permission.INTERNET,
				Manifest.permission.ACCESS_COARSE_LOCATION,
				Manifest.permission.ACCESS_FINE_LOCATION,
				Manifest.permission.WRITE_EXTERNAL_STORAGE})
                   .onGranted(new Action() {
                        @Override
                       public void onAction(List<String> permissions) {

                        try {
                            ToastUtil.show(context, "请输入密码");
                            if(getStringOK()) {
                                login();
                            }
                        }catch (Exception E)
                        {
                            E.printStackTrace();
                        }
                    }
                })
                .start();
		




### 获取安卓签名
		public static String sHA1(Context context){
			try {
			    PackageInfo info = context.getPackageManager().getPackageInfo(
				    context.getPackageName(), PackageManager.GET_SIGNATURES);
			    byte[] cert = info.signatures[0].toByteArray();
			    MessageDigest md = MessageDigest.getInstance("SHA1");
			    byte[] publicKey = md.digest(cert);
			    StringBuffer hexString = new StringBuffer();
			    for (int i = 0; i < publicKey.length; i++) {
				String appendString = Integer.toHexString(0xFF & publicKey[i])
					.toUpperCase(Locale.US);
				if (appendString.length() == 1)
				    hexString.append("0");
				hexString.append(appendString);
				hexString.append(":");
			    }
			    String result = hexString.toString();
			    return result.substring(0, result.length()-1);
			} catch (PackageManager.NameNotFoundException e) {
			    e.printStackTrace();
			} catch (NoSuchAlgorithmException e) {
			    e.printStackTrace();
			}
			return null;
		    }

### listview 自动刷新加载（RefreshRelativelayout  ）
         
          dependencies {
   			 compile 'com.mbg.refreshrelativelayout:library:1.3.2'
			}	 
			
	  E:\gyworkspace\YingQu
	 


### LocalService  退出登录后闪退解决方法

	protected Integer doInBackground(Integer... integers) {

		 if (mSocket != null) {
                      
			//这里加上判断		      
                        if(SPTool.getUserInfo(context)!=null){
                            mSocket.sendLogin(SPTool.getUserInfo(context).body.comm_no + "", 0x02);
                        }

                  } else {
                        break;
                  }


	//主页退出方法加上
	 case R.id.ll_nav_close:

                LocalService.myService.onDestroy();


### 安卓WebView 隐藏放大缩小控制条

	WebSettings webSettings = equitwebView_web.getSettings();
	webSettings.setDisplayZoomControls(false);
		  

### 安卓调用系统声音

	Uri uri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
	Ringtone rt = RingtoneManager.getRingtone(getApplicationContext(), uri);
	rt.play();

### Android webview  返回事件 




            case R.id.backf:
			
			
	     if ( equitwebView_web.canGoBack()) {
	         //后退
		quitwebView_web.goBack();
		break;
	     }

		finish();
			
			
		break;
		
		------
		
		@Override
	public boolean onKeyDown(int keyCode, KeyEvent event) {

		if (keyCode == KeyEvent.KEYCODE_BACK/* && equitwebView_web.canGoBack()*/) {

			if ( equitwebView_web.canGoBack()) {
				//后退
				equitwebView_web.goBack();

			}else {
				return super.onKeyDown(keyCode, event);
			}
			return true;
		}

		return super.onKeyDown(keyCode, event);
	}




### 接口文档模板 

[接口文档模板   docx](https://github.com/252590770/-/blob/master/demo/API接口模板/接口模板.docx)
    
[接口文档模板   xlsx](https://github.com/252590770/-/blob/master/demo/API接口模板/接口模板.xlsx)


###  spring-boot  Windows服务器上当做服务来运行的       

```  
 可以使用winsw     
 可以参考下这篇文章哦 https://blog.csdn.net/qq_28566071/article/details/80882503 
```  

### 安卓服务 

[安卓服务   源码](https://github.com/252590770/-/blob/master/demo/TelCar.zip)

### 安卓动态申请权限  

[安卓动态申请权限   源码](https://github.com/252590770/-/blob/master/demo/安卓动态申请权限.zip)


### 使用VUE 去开发前端   
   
   vue day2 使用vue发送ajax请求

### 使用angular 去开发前端

#### PowerShell 命令行工具    https://github.com/zce

[todomvc 源码](https://github.com/252590770/-/blob/master/demo/todomvc.zip)

* [node下载引用包](#a)

```
 npm install angular --save
``` 

* [在html中引用Angular](#a)

* [Angular2 中文网站](https://www.angular.cn/)    

```
<script src="node_modules/angular/angular.js"></script>

```

* [创建一个模块用于管理数据](#a)
```

后面的[]写入引用的模块,这里没有引用别的angular模块,所以不填
 var app = angular.module('app', []);
```
* [创建一个控制器,和页面交互(暴露)数据](#a)
* [完成控制器对视图的数据暴露操作](#a)
* [设置controller](#a)
* [数据绑定](#a)
```
// 4 创建一个控制器用于和界面交互（暴露）数据
  app.controller('TodoController', ['$scope', function($scope) {

    // 5 完成控制器中对视图的数据暴露操作
    $scope.todos = [
      { id: Math.random(), text: 'JavaScript', completed: false },
      { id: Math.random(), text: 'HTML', completed: false },
      { id: Math.random(), text: 'CSS', completed: true },
    ];
    $scope.input = '';

    // 8 暴露行为
    $scope.actions = {};
    $scope.actions.add = function() {
    	// 获取文本框中的值，加入数组中，由于数据列表是自动同步的
    	if(!$scope.input){
    		// 如果文本框没有输入
    		return false;
    	}

    	$scope.todos.push({ id: Math.random(), text: $scope.input, completed: false });

    	$scope.input = '';
    };

  }]);
```

[todomvc 源码](https://github.com/252590770/-/blob/master/demo/todomvc.zip)

-----------

电影展示的例子(Ajax请求,跨域, bootstrap 算是一个项目骨架)

* 在当前的目录下才能做Ajax请求,别的目录只能用跨域

##### 熟悉前端开发后需要看   视频介绍:怎么构建一个项目骨架   前端  >>13. 主流框架\06 流行框架第6天 2016-02-17\videos\上午02-项目骨架.avi

[电影展示 moviecat   源码](https://github.com/252590770/-/blob/master/demo/moviecat.zip)    
[电影展示 moviecat视频中的demo   源码](https://github.com/252590770/-/blob/master/demo/moviecat视频中的demo.zip)


-----------



###  [SeaJS](#a)是JavaScript的模块化开发及加载机制 

*  (13. 主流框架\07 流行框架第7天 02-19\2016-02-19\videos\下午04-SEAJS载入模块.avi)


------------------------






## 混合开发


WebApp:就是在浏览器中运行的web应用   
NativeApp:用android和Object-C等原生语言开发的应用   
HybridApp:就是外面是原生的壳，里面是webapp应用，兼具2者的优势   

### 快速开发快捷键  Emmet语法:http://docs.emmet.io/cheat-sheet/


3.1移动端开发有哪些框架那？

* 混合开发框架
	** Ionic (当前很火) 基于angular   
	** Html5+
	** AppCan
	** Framework7

	
* 类似于原生开发的框架	
	** React Native  (未来很火)

	
	
	
	
	
###	Ionic 官网地址  

    IONIC 是目前最有潜力的一款 HTML5 手机应用开发框架。通过 SASS 构建应用程序，它提供了很多 UI 组件来帮助开发者开发强大的应用。 它使用 JavaScript MVVM 框架和 AngularJS 来增强应用。提供数据的双向绑定，使用它成为 Web 和移动开发者的共同选择。Ionic是一个专注于用WEB开发技术，基于HTML5创建类似于手机平台原生应用的一个开发框架。Ionic框架的目的是从 web的角度开发手机应用，基于PhoneGap的编译平台，可以实现编译成各个平台的应用程序。


* Ionic官网 http://ionicframework.com/  

* Ionic中文网 http://www.ionic.wang/  





* [*重要 阮一峰  ECMAScript 6 入门   文档](http://es6.ruanyifeng.com/)   

* [*重要 Angular2 中文网站 ](https://www.angular.cn/) 

-- 和angular 1  不一样  1 是模块化的思想    angular 2 是组件化的了




# 网站

### 8uFTP  

8UFTP分为8UFTP客户端工具和 8UFTP智能扩展服务端工具，涵盖其它FTP工具所有的功能。不占内存，体积小，多线程，支持在线解压缩。界面友好，操作简单，可以管理多个ftp站点，使用拖拉即可完成文件或文件夹的上传下载。智能升级检查，免费升级。建议同时安装8UFTP客户端和8UFTP智能扩展服务端工具。


