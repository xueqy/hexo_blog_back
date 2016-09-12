---
title: Android v7包下Toolbar和ActionBarActivity实现后退导航效果
permalink: Android v7包下Toolbar和ActionBarActivity实现后退导航效果
comments: true
date: 2016-09-12 22:00:00
toc: true
tags:
   - Android
description: Android v7包下Toolbar和ActionBarActivity实现后退导航效果。
---

&emsp;&emsp;Android v7包下Toolbar和ActionBarActivity实现后退导航效果
<!-- more -->
### Android v7包下Toolbar和ActionBarActivity实现后退导航效果

android.support.v7包下的ToolBar和ActionBarActivity，均自带后退导航按钮，只是要手动开启，让它显示出来。
先来看看ToolBar，页面前台代码：
<android.support.v7.widget.Toolbar
            android:id="@+id/toolbar"
            android:layout_width="match_parent"
            android:layout_height="?attr/actionBarSize"
            android:background="?attr/colorPrimary"
            app:popupTheme="@style/AppTheme.PopupOverlay" />
如果要让后退按钮显示出来，需要在后台添加如下的代码

        getSupportActionBar().setDisplayHomeAsUpEnabled(true);
当然添加这行代码后仅仅是出现一个后退的箭头而已，点击后并没反应，需要继续添加监听事件才行，默认添加的按钮id是固定的，android.R.id.home，在onOptionsItemSelected中再添加如下的监听事件
```
　　　case android.R.id.home:
              finish();
              break;
```
        
其实这样并不是真正意义上的返回上一个页面，而是将这个页面销毁，从而显示上一个页面，也就是跳转之前的页面。

那么ActionBarActivity如何设置呢，看下面：

首先在要返回的页面A中设置该页面为要返回的页面
　　　　setHomeButtonEnabled
然后在清单文件中设置页面B的parentActivityName为页面A即可，但是这个属性在API 16之后才可，之前的话要用meta-data才可
```
<meta-data android:name="android.support.PARENT_ACTIVITY"
                android:value=".MainActivity"></meta-data>
```
要在页面B中显示后退按钮，也要添加代码

        ActionBar actionBar=getSupportActionBar();
        actionBar.setDisplayHomeAsUpEnabled(true);    
这样在页面B的标题栏左上角就公显示一个后退箭头，点击后就会自动返回页面A，并不需要添加额外的监听事件。

总结：看起来ActionBarActivity自带的后退导航要比ToolBar的更方便，但是到目前为止，google已不建议使用ActionBarActivity，现在在AS中新建Activity继承的是AppCompatActivity，至于为什么我这个初学者并不知道，我也尝试实现ToolBar的自动后退效果，但是虽然ToolBar也有对应的setHomeButtonEnabled方法和setDisplayHomeAsUpEnabled，但是并不起作用，google后找到的都是说的要添加监听事件，并没有发现有说可以实现类似ActionBarActivity的效果，最后放弃。
