---
title: Android UI design
date: 2022-09-19 13:16:26
tags: Android | UI
---

记录了一些开发过程中整理的UI设计方案，持续更新...


## 关联`toolbar`和`drawerLayout`

```java
ActionBarDrawerToggle(Activity activity, DrawerLayout drawerLayout,Toolbar toolbar, @StringRes int openDrawerContentDescRes,@StringRes int closeDrawerContentDescRes) 
```

`BottomNavigationView`

```java
navigation.setOnNavigationItemSelectedListener();/*设置点击事件*/
```

`FloatingActionButton` & `SnackBar`


浮动菜单设置点击事件

```java
setOnClickListener();
/*Snackbar弹出和响应*/
snackbar.make(v,String,int time)
    .setAction(String,OnClickListener())
```

## CardView

```java
/*设置卡片背景色、圆角效果、阴影效果、卡片内容四周间距*/
app:cardBackgroundColor=""
app:cardCornerRadius=""
app:cardElevation=""
app:contentPadding=""
/*通过foreground设置点击效果*/
```

滚动模式

## AppBarLayout

```java
/*直接控件可设置的Layout_scrollFlags滚动模式属性*/
app:layout_scrollFlags=""
    scroll|exitUnilCollapsed:子控件可以滚动，向上滚动出父布局
  	scroll|enterAlways:向下滚动该布局就会显示出来，向上滑动时该布局就会向上收缩
    scroll|enterAlwaysCollapsed:向下滚动到最低端时该布局才会显示出来
    scroll|snap:吸附效果，确保childView不会滑动并停止在中间的状态
    如果不设置该属性则布局不能滑动
```

## CollapsingToolbarLayout

```java
/*直接子控件可以设置Layout_collapseMode（折叠模式）属性*/
app:layout_collapseMode=""
    pin:滑动过程中该布局会固定在它所在的的位置不动，直到CollapsingToolbarLayout全部折叠或展开
    parallax:视差效果，滑动过程都有视差效果
    不设置就跟随一起滑动
```

Material Design动画

## Recyclerview

```xml
<recyclerview.CircleImageView>
    y
</recyclerview.CircleImageView>
```

## **Spinner**

```xml
<LinearLayout 
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical" >
        <Spinner
            android:id="@+id/spinner1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:entries="@array/languages"/>
</LinearLayout>
```

**菜单显示方式**`spinnerMode`：

```xml
android:spinnerMode="dropdown"	下拉菜单
android:spinnerMode="dialog"	弹出框
```

android:entries="@array/languages"表示Spinner的数据集合是从资源数组languages中获取的，languages数组资源定义在values/arrays.xml中

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string-array name="languages">
        <item>c语言</item>
        <item>java </item>
        <item>php</item>
        <item>xml</item>
        <item>html</item>
    </string-array>
</resources>
```

通过OnItemSelectedListener的回调方法实现选择响应事件。

数据绑定的其他方式：

- **使用ArrayAdapter**
- **自定义的BaseAdapter**

## 设置间距的最佳方案：LinearLayout 的divider

```xml
android:orientation="vertical"
android:showDividers="middle"
android:divider="@drawable/spacer"
```

### shape图形使用

1. 在`res/drawable`目录下新建一个xml文件
2. Root为`<shape>`

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:shape=["rectangle" | "oval" | "line" | "ring"]     
   //共有4种类型，矩形（默认）/椭圆形/直线形/环形
    <corners>定义圆角</corners>

    <gradient>定义渐变效果</gradient>

    <padding>定义内边距</padding>

    <size>自定义图形大小</size>

    <solid>填充色</solid>

    <stroke
        android:dashWidth="虚线宽度，0为实线"
        android:dashGap="虚线间隔">描边</stroke>

</shape>
```

