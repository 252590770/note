# 前端笔记

![nihao](https://github.com/252590770/-/blob/master/images/kai-fa-yi-lai.png)

### 前端开发阶段需要依赖的东西

__http-server__ 是在本地架起一个网页服务器,方便开发者预览效果   
__browser-sync__ 除了具有http-server的功能外,还能同时调试不同的网页




### 使用angular 去开发前端
* [node下载引用包](#a)
* [在html中引用Angular](#a)
* [创建一个模块用于管理数据](#a)
* [创建一个控制器,和页面交互(暴露)数据](#a)
* [完成控制器对视图的数据暴露操作](#a)
* [设置controller](#a)
* [数据绑定](#a)





```
@Override
protected void onDestroy() {
    EventBus.getDefault().unregister(this);
    super.onDestroy();
}
``` 