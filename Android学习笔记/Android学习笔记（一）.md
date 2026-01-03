# Android学习笔记（二）

## 登陆界面的美化

上次写完了一个简单的登陆界面，但由于过于简单，个人看着有些不爽，于是就想将他美化一下……

## 1.图片储存

美化界面，当然要用到图片啦，所以，先找到一些图片来让这个登陆界面更加美丽！

### 1.1.图片命名格式

**图片命名格式**：`模块名_ic_位置_作用`（下面依旧会省去模块名）

`png、jpg` 等类型的图片应放在 `drawable-xhdpi` 中

`xml `这种类型的图片统一放在 `drawable` 中

**`drawable-xhdpi` 快速创建方式**：

右键`res`文件夹，选择`New`——`Android Resource Rirectory`

![image-20211220221400836](https://gitee.com/yimuzhexi/pic/raw/master/img/image-20211220221400836.png)

在`Resource Type`里选择` drawable `，然后在`Available qualifiers`内选择` Density`，点击`>>`按键，在`Density`内选择`X-High Density`，点击ok即创建成功。

![image-20211220222006822](https://gitee.com/yimuzhexi/pic/raw/master/img/image-20211220222006822.png)

![image-20211220222050446](https://gitee.com/yimuzhexi/pic/raw/master/img/image-20211220222050446.png)

### 1.2.存入图片

+ 选择你想用的图片，直接cv到文件夹内（记得改名字）。

这里，我放入了一张背景图和一张头像

![image-20211220222806940](https://gitee.com/yimuzhexi/pic/raw/master/img/image-20211220222806940.png)

## 2.使用图片

使用图片的时候我们需要用到`ImageView`控件，来，让我们设置一个背景图和头像吧：

背景：

```xml
<ImageView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="@drawable/ic_main_background"
        tools:ignore="MissingConstraints"
        android:contentDescription="@string/background" />
```

头像：

```xml
<ImageView
        android:id="@+id/iv_main_head"
        android:layout_width="125dp"
        android:layout_height="125dp"
        android:layout_marginBottom="52dp"
        android:contentDescription="@string/head"
        android:src="@drawable/ic_main_head"
        app:layout_constraintBottom_toTopOf="@+id/et_main_username"
        app:layout_constraintEnd_toEndOf="@+id/et_main_username"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="@+id/et_main_username"
        tools:ignore="MissingConstraints" />
```

效果图：

<img src="https://gitee.com/yimuzhexi/pic/raw/master/img/image-20211220224130718.png" alt="image-20211220224130718"  />

但我还觉得他不太好看，我想让他输入框的文字有一个上浮的效果这该咋办呢？在网上查了查，查到了一篇介绍文章：[Android Material Design 系列之 TextInputLayout 使用详解_一名互联网时代苟且偷生的 Android码农-CSDN博客_textinputlayout](https://blog.csdn.net/jaynm/article/details/106918713)

原来，可以通过`TextInputLayout`来实现我的目标，那么，赶紧来实践了一下……

## 3.简单使用了一下`TextInputLayout`来进行美化

先将用户名输入框替换一下：

```xml
<com.google.android.material.textfield.TextInputLayout
        android:id="@+id/til_main_username"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="@string/input_username"
        android:minHeight="48dp"
        app:layout_constraintBottom_toTopOf="@+id/et_main_password"
        app:layout_constraintEnd_toEndOf="@+id/et_main_password"
        tools:ignore="MissingConstraints">

        <EditText
            android:id="@+id/et_main_username"
            android:layout_width="300dp"
            android:layout_height="wrap_content"
            android:autofillHints="AUTOFILL_HINT_USERNAME"
            android:background="@color/white"
            android:inputType="text"
            android:lines="1"
            tools:ignore="LabelFor,TextContrastCheck,SpeakableTextPresentCheck" />
    </com.google.android.material.textfield.TextInputLayout>
```

先试试效果：

<img src="https://gitee.com/yimuzhexi/pic/raw/master/img/QQ%E8%A7%86%E9%A2%9120211220225154%2000_00_00-00_00_30.gif" alt="QQ视频20211220225154 00_00_00-00_00_30" style="zoom:50%;" />

发现效果不错，立马把密码栏也换掉：

```xml
<com.google.android.material.textfield.TextInputLayout
        android:id="@+id/til_main_password"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="@string/input_password"
        android:minHeight="48dp"
        app:layout_constraintBottom_toTopOf="@+id/btn_main_login"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.505"
        app:layout_constraintStart_toStartOf="parent">

        <EditText
            android:id="@+id/et_main_password"
            android:layout_width="300dp"
            android:layout_height="wrap_content"
            android:layout_marginBottom="104dp"
            android:autofillHints="AUTOFILL_HINT_PASSWORD"
            android:background="@color/white"
            android:inputType="textPassword"
            android:lines="1"
            tools:ignore="LabelFor,TextContrastCheck,SpeakableTextPresentCheck" />
    </com.google.android.material.textfield.TextInputLayout>
```

再次运行，发现这玩意果然很不错，接下来，只要实现密码可见就行了，在密码栏的`TextInputLayout`加入这样一句：`app:passwordToggleEnabled="true"`，发现预览图中出现了一个小眼睛，盯着这只小眼睛，我露出了邪恶的笑容，这不赶紧运行试验一下？

![QQ视频20211220230328 00_00_00-00_00_30](https://gitee.com/yimuzhexi/pic/raw/master/img/QQ%E8%A7%86%E9%A2%9120211220230328%2000_00_00-00_00_30.gif)

不戳，针不戳

## 4.完整代码

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="@drawable/ic_main_background"
        android:contentDescription="@string/background"
        tools:ignore="MissingConstraints,ImageContrastCheck" />

    <ImageView
        android:id="@+id/iv_main_head"
        android:layout_width="125dp"
        android:layout_height="125dp"
        android:layout_marginBottom="52dp"
        android:contentDescription="@string/head"
        android:src="@drawable/ic_main_head"
        app:layout_constraintBottom_toTopOf="@+id/til_main_username"
        app:layout_constraintEnd_toEndOf="@+id/til_main_username"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="@+id/til_main_username"
        tools:ignore="MissingConstraints,ImageContrastCheck" />

    <com.google.android.material.textfield.TextInputLayout
        android:id="@+id/til_main_username"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="@string/input_username"
        android:minHeight="48dp"
        app:layout_constraintBottom_toTopOf="@+id/til_main_password"
        app:layout_constraintEnd_toEndOf="@+id/til_main_password"
        tools:ignore="MissingConstraints">

        <EditText
            android:id="@+id/et_main_username"
            android:layout_width="300dp"
            android:layout_height="wrap_content"
            android:autofillHints="AUTOFILL_HINT_USERNAME"
            android:background="@color/white"
            android:inputType="text"
            android:lines="1"
            tools:ignore="LabelFor,TextContrastCheck,SpeakableTextPresentCheck" />
    </com.google.android.material.textfield.TextInputLayout>

    <com.google.android.material.textfield.TextInputLayout
        android:id="@+id/til_main_password"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="@string/input_password"
        android:minHeight="48dp"
        app:layout_constraintBottom_toTopOf="@+id/btn_main_login"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.505"
        app:layout_constraintStart_toStartOf="parent"
        app:passwordToggleEnabled="true">

        <EditText
            android:id="@+id/et_main_password"
            android:layout_width="300dp"
            android:layout_height="wrap_content"
            android:layout_marginBottom="104dp"
            android:autofillHints="AUTOFILL_HINT_PASSWORD"
            android:background="@color/white"
            android:inputType="textPassword"
            android:lines="1"
            tools:ignore="LabelFor,TextContrastCheck,SpeakableTextPresentCheck" />
    </com.google.android.material.textfield.TextInputLayout>

    <Button
        android:id="@+id/btn_main_login"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="140dp"
        android:text="@string/login"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

