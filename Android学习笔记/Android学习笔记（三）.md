# Android学习笔记（三）`FragmentDialog`注册页面与页面跳转

需求：增加注册按钮，能够在点击后弹出注册界面并完成简单的注册功能，账号密码输入成功后可以跳转页面。

 ## 一、实现注册的`FragmentDialog`界面

### 1.新建一个界面，命名为create_dialog，并在其中写入所需要的与注册相关的控件

#### 1.1.添加背景

这里就不放入图片了，直接添加一个空白背景

```xml
 <ImageView
        android:id="@+id/iv_dialog_background"
        android:layout_width="350dp"
        android:layout_height="650dp"
        android:background="@color/white"
        android:contentDescription="@string/background"
        tools:ignore="MissingConstraints" />
```

#### 1.2.添加用于注册的控件、确认注册和取消注册的按钮

怎么来写这些东西在前两篇笔记中写了，这里就不再细说，直接上代码了

```xml
<ImageView
        android:id="@+id/iv_dialog_head"
        android:layout_width="125dp"
        android:layout_height="125dp"
        android:layout_marginBottom="68dp"
        android:contentDescription="@string/head"
        android:src="@drawable/ic_main_head"
        app:layout_constraintBottom_toTopOf="@+id/til_dialog_username"
        app:layout_constraintEnd_toEndOf="@+id/til_dialog_username"
        app:layout_constraintHorizontal_bias="0.502"
        app:layout_constraintStart_toStartOf="@+id/til_dialog_username" />

<com.google.android.material.textfield.TextInputLayout
        android:id="@+id/til_dialog_username"
        android:layout_width="300dp"
        android:layout_height="wrap_content"
        android:hint="@string/input_username"
        app:layout_constraintBottom_toTopOf="@+id/til_dialog_password1"
        app:layout_constraintEnd_toEndOf="@+id/til_dialog_password1"
        app:layout_constraintStart_toStartOf="@+id/til_dialog_password1">

        <EditText
            android:id="@+id/et_dialog_username"
            android:layout_width="300dp"
            android:layout_height="wrap_content"
            android:autofillHints="username"
            android:background="@color/white"
            android:inputType="text"
            android:lines="1"
            tools:ignore="LabelFor" />
</com.google.android.material.textfield.TextInputLayout>

<com.google.android.material.textfield.TextInputLayout
        android:id="@+id/til_dialog_password1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="@string/input_password"
        app:layout_constraintBottom_toTopOf="@+id/til_dialog_password2"
        app:layout_constraintEnd_toEndOf="@+id/til_dialog_password2"
        app:layout_constraintStart_toStartOf="@+id/til_dialog_password2"
        app:passwordToggleEnabled="true">

        <EditText
            android:id="@+id/et_dialog_password1"
            android:layout_width="300dp"
            android:layout_height="wrap_content"
            android:autofillHints="password"
            android:background="@color/white"
            android:inputType="textPassword"
            android:lines="1"
            tools:ignore="LabelFor" />
</com.google.android.material.textfield.TextInputLayout>

<com.google.android.material.textfield.TextInputLayout
        android:id="@+id/til_dialog_password2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="@string/create_password_check"
        app:layout_constraintBottom_toTopOf="@+id/btn_dialog_yes"
        app:layout_constraintEnd_toEndOf="@+id/btn_dialog_yes"
        app:layout_constraintStart_toStartOf="@+id/btn_dialog_yes"
        app:passwordToggleEnabled="true">

        <EditText
            android:id="@+id/et_dialog_password2"
            android:layout_width="300dp"
            android:layout_height="wrap_content"
            android:autofillHints="password"
            android:background="@color/white"
            android:inputType="textPassword"
            android:lines="1"
            tools:ignore="LabelFor" />
</com.google.android.material.textfield.TextInputLayout>

<Button
        android:id="@+id/btn_dialog_yes"
        android:layout_width="300dp"
        android:layout_height="wrap_content"
        android:hint="@string/create_yes"
        android:textColorHint="@color/white"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/btn_dialog_cancel"
        app:layout_constraintEnd_toEndOf="@+id/btn_dialog_cancel"
        app:layout_constraintStart_toStartOf="@+id/btn_dialog_cancel" />

<Button
        android:id="@+id/btn_dialog_cancel"
        android:layout_width="300dp"
        android:layout_height="wrap_content"
        android:layout_marginBottom="112dp"
        android:hint="@string/create_cancel"
        android:textColorHint="@color/white"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.537"
        app:layout_constraintStart_toStartOf="parent" />
```

### 2.写好界面对应的java代码

#### 2.1.了解`SharedPreferences`储存信息的方法

[SharedPreferences存储、查看_u013441613的博客-CSDN博客_sharedpreferences存储位置](https://blog.csdn.net/u013441613/article/details/80361817?ops_request_misc=%7B%22request%5Fid%22%3A%22164034953216780366559522%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=164034953216780366559522&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-4-80361817.pc_search_insert_es_download&utm_term=SharedPreferences&spm=1018.2226.3001.4187)

**`SharedPreferences`只能储存少量信息，不建议将大量数据塞进`SharedPreferences`内储存。**

这里我们要用到的主要有`.remove``.putString``.apply`方法。

#### 2.2.创建`CreateDialog`并继承`DialogFragment`类、实现`View.OnClickListener`接口

```java
public class CreateDialog extends DialogFragment implements View.OnClickListener {

    View view;
    
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
    }

    public static CreateDialog newInstance() {
        Bundle args = new Bundle();
        CreateDialog fragment = new CreateDialog();
        fragment.setArguments(args);
        return fragment;
    }

    @SuppressLint("InflateParams")
    @Override
    public View onCreateView(LayoutInflater inflater, @Nullable ViewGroup container, @Nullable Bundle savedInstanceState) {
        // 加载 xml 布局
        view = inflater.inflate(R.layout.create_dialog, null, false);
        view.setElevation(30);
        return view;
    }

    @Override
    public void onClick(View v) {

    }
}
```

#### 2.3.绑定控件并设置监听

##### 2.3.1.绑定所需的控件到相应对象

```java
private EditText mEtUsername;
private EditText mEtPassword1;
private EditText mEtPassword2;
private Button mBtnCreate;
private Button mBtnCancel;

//绑定控件
public void initView(){
        mEtUsername = view.findViewById(R.id.et_dialog_username);
        mEtPassword1 = view.findViewById(R.id.et_dialog_password1);
        mEtPassword2 = view.findViewById(R.id.et_dialog_password2);
        mBtnCreate = view.findViewById(R.id.btn_dialog_yes);
        mBtnCancel = view.findViewById(R.id.btn_dialog_cancel);
}
```

##### 2.3.2.设置监听

```java
//设置
public void setView(){
        mBtnCreate.setOnClickListener(this);
        mBtnCancel.setOnClickListener(this);
}
```

#### 2.4.`SharedPreferences`、注册判断与数据写入

##### 2.4.1.创建并绑定`SharedPreferences`

```java
SharedPreferences sharedPreferences;
SharedPreferences.Editor editor;
```

```java
sharedPreferences = requireContext().getSharedPreferences("Data", Context.MODE_PRIVATE);
editor = sharedPreferences.edit();
```

##### 2.4.2.注册数据判断与数据写入

首先判断用户名是否为空，如果为空则弹出“吐司”提示用户民不能为空<br/>其次，判断两次输入的密码是否匹配，匹配则写入新数据并关闭此`Dialog`，失败则提示两次密码不匹配

实现代码：

```java
public void create(){
        String username = mEtUsername.getText().toString();
        String password1 = mEtPassword1.getText().toString();
        String password2 = mEtPassword2.getText().toString();
        if(username.equals("")){
            Toast.makeText(getActivity(), "用户名不能为空！", Toast.LENGTH_SHORT).show();
        }else if(!password1.equals(password2)){
            Toast.makeText(getActivity(),"两次密码不匹配，请重新检查！",Toast.LENGTH_SHORT).show();
        }else{
            //清除原数据并写入新数据
            editor.remove("username");
            editor.remove("password");
            editor.putString("username",username);
            editor.putString("password",password1);
            editor.apply();
            Toast.makeText(getActivity(), "注册成功", Toast.LENGTH_SHORT).show();
            //关闭注册窗口
            dismiss();
        }
}
```

#### 2.5.设置点击事件

设置点击事件，选择注册则进入注册方法进行判断，否则关闭`Dialog`窗口

```java
@SuppressLint("NonConstantResourceId")
    @Override
    public void onClick(View v) {
        switch (v.getId()){
            case R.id.btn_dialog_yes:
                create();
                break;
            case R.id.btn_dialog_cancel:
                dismiss();
                break;
        }
}
```

### 3.在主界面添加注册按键并在`MainActivity`设置点击弹出注册窗口

弹出窗口代码：`CreateDialog.newInstance().show(getSupportFragmentManager(), "dialog");`

### 4.效果

注册点击与取消注册点击：

![QQ视频20211224220655 00_00_00-00_00_30](https://gitee.com/yimuzhexi/pic/raw/master/img/QQ%E8%A7%86%E9%A2%9120211224220655%2000_00_00-00_00_30.gif)

账号判断：

用户名为空

![用户名为空 00_00_00-00_00_30](https://gitee.com/yimuzhexi/pic/raw/master/img/%E7%94%A8%E6%88%B7%E5%90%8D%E4%B8%BA%E7%A9%BA%2000_00_00-00_00_30.gif)

密码不匹配

![密码不匹配 00_00_00-00_00_30](https://gitee.com/yimuzhexi/pic/raw/master/img/%E5%AF%86%E7%A0%81%E4%B8%8D%E5%8C%B9%E9%85%8D%2000_00_00-00_00_30.gif)

注册成功

![注册成功 00_00_00-00_00_30](https://gitee.com/yimuzhexi/pic/raw/master/img/%E6%B3%A8%E5%86%8C%E6%88%90%E5%8A%9F%2000_00_00-00_00_30.gif)

## 二、实现页面跳转

首先，写好一个界面用于跳转后显示（这里就简单写一个意思一下）

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".DemoActivity">

    <ImageView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:src="@drawable/ic_demo_show"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        android:contentDescription="@string/show" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

在demo的java代码里面写上一个静态`startActivity`方法用来给主界面连接跳转

```java
public static void startActivity(Context context){
        Intent intent = new Intent(context,DemoActivity.class);
        context.startActivity(intent);
}
```

在主界面java代码中写上点击登录成功则跳转界面的代码

```java
public void login(){
        String username = mEtUsername.getText().toString();
        String password = mEtPassword.getText().toString();
        if(!username.equals(sharedPreferences.getString("username",""))){
            Toast.makeText(this,"用户名错误",Toast.LENGTH_SHORT).show();
        }else if(!password.equals(sharedPreferences.getString("password",""))){
            Toast.makeText(this,"您的密码错误",Toast.LENGTH_SHORT).show();
        }else{
            Toast.makeText(this,"登陆成功",Toast.LENGTH_SHORT).show();
            DemoActivity.startActivity(this);
        }
}
```

效果图

![页面跳转 00_00_00-00_00_30](https://gitee.com/yimuzhexi/pic/raw/master/img/%E9%A1%B5%E9%9D%A2%E8%B7%B3%E8%BD%AC%2000_00_00-00_00_30.gif)

## 三、完整代码

### 1.`activity_main.xml`

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
        android:layout_width="300dp"
        android:layout_height="wrap_content"
        android:text="@string/login"
        app:layout_constraintBottom_toTopOf="@+id/btn_main_create"
        app:layout_constraintEnd_toEndOf="@+id/btn_main_create"
        app:layout_constraintStart_toStartOf="@+id/btn_main_create" />

    <Button
        android:id="@+id/btn_main_create"
        android:layout_width="300dp"
        android:layout_height="wrap_content"
        android:layout_marginBottom="84dp"
        android:text="@string/create"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
```

### 2.`MainActivity.java`

```java
package com.example.demo;

import androidx.appcompat.app.AppCompatActivity;

import android.annotation.SuppressLint;
import android.content.Context;
import android.content.SharedPreferences;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity implements View.OnClickListener {

    private EditText mEtUsername;
    private EditText mEtPassword;
    private Button mBtnLogin;
    private Button mBtnCreate;

    SharedPreferences sharedPreferences;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        initView();
        setView();
    }

    public void initView() {
        mEtUsername = findViewById(R.id.et_main_username);
        mEtPassword = findViewById(R.id.et_main_password);
        mBtnLogin = findViewById(R.id.btn_main_login);
        mBtnCreate = findViewById(R.id.btn_main_create);
        sharedPreferences = getSharedPreferences("Data", Context.MODE_PRIVATE);
    }

    public void setView(){
        mBtnLogin.setOnClickListener(this);
        mBtnCreate.setOnClickListener(this);
    }

    @SuppressLint("NonConstantResourceId")
    @Override
    public void onClick(View v) {
        switch (v.getId()) {
            case R.id.btn_main_login:
                login();
                break;
            case R.id.btn_main_create:
                CreateDialog.newInstance().show(getSupportFragmentManager(), "dialog");
                break;
        }
    }

    public void login(){
        String username = mEtUsername.getText().toString();
        String password = mEtPassword.getText().toString();
        if(!username.equals(sharedPreferences.getString("username",""))){
            Toast.makeText(this,"用户名错误",Toast.LENGTH_SHORT).show();
        }else if(!password.equals(sharedPreferences.getString("password",""))){
            Toast.makeText(this,"您的密码错误",Toast.LENGTH_SHORT).show();
        }else{
            Toast.makeText(this,"登陆成功",Toast.LENGTH_SHORT).show();
            DemoActivity.startActivity(this);
        }
    }
}
```

### 3.`create_dialog.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".CreateDialog">

    <ImageView
        android:id="@+id/iv_dialog_background"
        android:layout_width="350dp"
        android:layout_height="650dp"
        android:background="@color/white"
        android:contentDescription="@string/background"
        tools:ignore="MissingConstraints" />

    <ImageView
        android:id="@+id/iv_dialog_head"
        android:layout_width="125dp"
        android:layout_height="125dp"
        android:layout_marginBottom="68dp"
        android:contentDescription="@string/head"
        android:src="@drawable/ic_main_head"
        app:layout_constraintBottom_toTopOf="@+id/til_dialog_username"
        app:layout_constraintEnd_toEndOf="@+id/til_dialog_username"
        app:layout_constraintHorizontal_bias="0.502"
        app:layout_constraintStart_toStartOf="@+id/til_dialog_username" />

    <com.google.android.material.textfield.TextInputLayout
        android:id="@+id/til_dialog_username"
        android:layout_width="300dp"
        android:layout_height="wrap_content"
        android:hint="@string/input_username"
        app:layout_constraintBottom_toTopOf="@+id/til_dialog_password1"
        app:layout_constraintEnd_toEndOf="@+id/til_dialog_password1"
        app:layout_constraintStart_toStartOf="@+id/til_dialog_password1">

        <EditText
            android:id="@+id/et_dialog_username"
            android:layout_width="300dp"
            android:layout_height="wrap_content"
            android:autofillHints="username"
            android:background="@color/white"
            android:inputType="text"
            android:lines="1"
            tools:ignore="LabelFor" />
    </com.google.android.material.textfield.TextInputLayout>

    <com.google.android.material.textfield.TextInputLayout
        android:id="@+id/til_dialog_password1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="@string/input_password"
        app:layout_constraintBottom_toTopOf="@+id/til_dialog_password2"
        app:layout_constraintEnd_toEndOf="@+id/til_dialog_password2"
        app:layout_constraintStart_toStartOf="@+id/til_dialog_password2"
        app:passwordToggleEnabled="true">

        <EditText
            android:id="@+id/et_dialog_password1"
            android:layout_width="300dp"
            android:layout_height="wrap_content"
            android:autofillHints="password"
            android:background="@color/white"
            android:inputType="textPassword"
            android:lines="1"
            tools:ignore="LabelFor" />
    </com.google.android.material.textfield.TextInputLayout>

    <com.google.android.material.textfield.TextInputLayout
        android:id="@+id/til_dialog_password2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:hint="@string/create_password_check"
        app:layout_constraintBottom_toTopOf="@+id/btn_dialog_yes"
        app:layout_constraintEnd_toEndOf="@+id/btn_dialog_yes"
        app:layout_constraintStart_toStartOf="@+id/btn_dialog_yes"
        app:passwordToggleEnabled="true">

        <EditText
            android:id="@+id/et_dialog_password2"
            android:layout_width="300dp"
            android:layout_height="wrap_content"
            android:autofillHints="password"
            android:background="@color/white"
            android:inputType="textPassword"
            android:lines="1"
            tools:ignore="LabelFor" />
    </com.google.android.material.textfield.TextInputLayout>

    <Button
        android:id="@+id/btn_dialog_yes"
        android:layout_width="300dp"
        android:layout_height="wrap_content"
        android:hint="@string/create_yes"
        android:textColorHint="@color/white"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/btn_dialog_cancel"
        app:layout_constraintEnd_toEndOf="@+id/btn_dialog_cancel"
        app:layout_constraintStart_toStartOf="@+id/btn_dialog_cancel" />

    <Button
        android:id="@+id/btn_dialog_cancel"
        android:layout_width="300dp"
        android:layout_height="wrap_content"
        android:layout_marginBottom="112dp"
        android:hint="@string/create_cancel"
        android:textColorHint="@color/white"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.537"
        app:layout_constraintStart_toStartOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### 4.`CreateDialog.java`

```java
package com.example.demo;

import androidx.annotation.Nullable;
import androidx.fragment.app.DialogFragment;

import android.annotation.SuppressLint;
import android.content.Context;
import android.content.SharedPreferences;
import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class CreateDialog extends DialogFragment implements View.OnClickListener {

    View view;
    private EditText mEtUsername;
    private EditText mEtPassword1;
    private EditText mEtPassword2;
    private Button mBtnCreate;
    private Button mBtnCancel;

    SharedPreferences sharedPreferences;
    SharedPreferences.Editor editor;

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
    }

    public static CreateDialog newInstance() {
        Bundle args = new Bundle();
        CreateDialog fragment = new CreateDialog();
        fragment.setArguments(args);
        return fragment;
    }

    @SuppressLint("InflateParams")
    @Override
    public View onCreateView(LayoutInflater inflater, @Nullable ViewGroup container, @Nullable Bundle savedInstanceState) {
        // 加载 xml 布局
        view = inflater.inflate(R.layout.create_dialog, null, false);
        view.setElevation(30);
        initView();
        setView();
        return view;
    }

    //绑定控件
    public void initView(){
        mEtUsername = view.findViewById(R.id.et_dialog_username);
        mEtPassword1 = view.findViewById(R.id.et_dialog_password1);
        mEtPassword2 = view.findViewById(R.id.et_dialog_password2);
        mBtnCreate = view.findViewById(R.id.btn_dialog_yes);
        mBtnCancel = view.findViewById(R.id.btn_dialog_cancel);
        sharedPreferences = requireContext().getSharedPreferences("Data", Context.MODE_PRIVATE);
        editor = sharedPreferences.edit();
    }

    //设置
    public void setView(){
    mBtnCreate.setOnClickListener(this);
    mBtnCancel.setOnClickListener(this);
    }

    @SuppressLint("NonConstantResourceId")
    @Override
    public void onClick(View v) {
        switch (v.getId()){
            case R.id.btn_dialog_yes:
                create();
                break;
            case R.id.btn_dialog_cancel:
                dismiss();
                break;
        }
    }

    public void create(){
        String username = mEtUsername.getText().toString();
        String password1 = mEtPassword1.getText().toString();
        String password2 = mEtPassword2.getText().toString();
        if(username.equals("")){
            Toast.makeText(getActivity(), "用户名不能为空！", Toast.LENGTH_SHORT).show();
        }else if(!password1.equals(password2)){
            Toast.makeText(getActivity(),"两次密码不匹配，请重新检查！",Toast.LENGTH_SHORT).show();
        }else{
            //清除原数据并写入新数据
            editor.remove("username");
            editor.remove("password");
            editor.putString("username",username);
            editor.putString("password",password1);
            editor.apply();
            Toast.makeText(getActivity(), "注册成功", Toast.LENGTH_SHORT).show();
            //关闭注册窗口
            dismiss();
        }
    }
}
```

### 5.`activity_demo.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".DemoActivity">

    <ImageView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:src="@drawable/ic_demo_show"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        android:contentDescription="@string/show" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

### 6.`DemoActivity.java`

```java
package com.example.demo;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Context;
import android.content.Intent;
import android.os.Bundle;

public class DemoActivity extends AppCompatActivity {

    public static void startActivity(Context context){
        Intent intent = new Intent(context,DemoActivity.class);
        context.startActivity(intent);
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_demo);
    }
}
```

