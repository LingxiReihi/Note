# Android学习笔记（四）——RecyclerView输出图片或者类容

## 一、在输出页面设置RecyclerView控件

设置一个RecyclerView控件用于滚动输出图片：

```xml
<androidx.recyclerview.widget.RecyclerView
        android:id="@+id/rv_demo_picture"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="MissingConstraints" />
```

效果如图：

<img src="https://gitee.com/yimuzhexi/pic/raw/master/img/image-20220124172000373.png" alt="image-20220124172000373" style="zoom:50%;" />

## 二、创建item_picture

创建item_picture用来规定输出格式，在RecyclerView中输出的类容都会按照item设定格式的输出。

例如，设置只有图片输出：

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="wrap_content">
    
    <ImageView
        android:id="@+id/iv_item_picture"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:src="@drawable/ic_demo_show"
        tools:ignore="MissingConstraints"
        android:contentDescription="@string/picture" />
    
</androidx.constraintlayout.widget.ConstraintLayout>
```

## 三、设置RecyclerView

### 1、创建adapter

```java
package com.example.demo.adapter;

import androidx.annotation.NonNull;
import androidx.fragment.app.Fragment;
import androidx.fragment.app.FragmentActivity;

import java.util.ArrayList;

public class RecyclerViewAdapter extends androidx.viewpager2.adapter.FragmentStateAdapter{

    //创建arraylist用于储存fragment界面
    ArrayList<Fragment> fragments;

    public RecyclerViewAdapter(@NonNull FragmentActivity fragmentActivity,ArrayList<Fragment>fragments) {
        super(fragmentActivity);
        this.fragments=fragments;
    }

    @NonNull
    @Override
    public Fragment createFragment(int position) {
        return fragments.get(position);
    }

    @Override
    public int getItemCount() {
        return fragments.size();
    }
}
```

### 2、创建picture类用于储存picture

```java
package com.example.demo.date;

public class picture {
    
    private int num;
    
    public void setNum(int pictureNum){
        this.num=pictureNum;
    }
    
    public int getNum(){
        return num;
    }
}
```

### 3、设置RecyclerView

这里直接在Android Studio里面存入照片以调用

```java
package com.example.demo.date;

import com.example.demo.R;

public class pictureID {
    int[] pictureId = new int[26];

    pictureID() {
        pictureId[0] = R.drawable.pic1;
        pictureId[1] = R.drawable.pic2;
        pictureId[2] = R.drawable.pic3;
        pictureId[3] = R.drawable.pic4;
        pictureId[4] = R.drawable.pic5;
        pictureId[5] = R.drawable.pic6;
        pictureId[6] = R.drawable.pic7;
        pictureId[7] = R.drawable.pic8;
        pictureId[8] = R.drawable.pic9;
        pictureId[9] = R.drawable.pic10;
        pictureId[10] = R.drawable.pic11;
        pictureId[11] = R.drawable.pic12;
        pictureId[12] = R.drawable.pic13;
        pictureId[13] = R.drawable.pic14;
        pictureId[14] = R.drawable.pic15;
        pictureId[15] = R.drawable.pic16;
        pictureId[16] = R.drawable.pic17;
        pictureId[17] = R.drawable.pic18;
        pictureId[18] = R.drawable.pic19;
        pictureId[19] = R.drawable.pic20;
        pictureId[20] = R.drawable.pic21;
        pictureId[21] = R.drawable.pic22;
        pictureId[22] = R.drawable.pic23;
        pictureId[23] = R.drawable.pic24;
        pictureId[24] = R.drawable.pic25;
        pictureId[25] = R.drawable.ic_demo_show;
    }

    public int getPictureId(int num) {
        return pictureId[num - 1];
    }
}
```

