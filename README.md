# 前端笔记

![nihao](https://github.com/252590770/-/blob/master/images/kai-fa-yi-lai.png)

### 前端开发阶段需要依赖的东西

__http-server__ 是在本地架起一个网页服务器,方便开发者预览效果   
__browser-sync__ 除了具有http-server的功能外,还能同时调试不同的网页




### 使用angular 去开发前端

#### PowerShell 命令行工具    https://github.com/zce

[todomvc 源码](https://github.com/252590770/-/blob/master/demo/todomvc.zip)

* [node下载引用包](#a)

```
 npm install angular --save
``` 

* [在html中引用Angular](#a)

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



