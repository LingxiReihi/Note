# Streamlit

## 简介

`Streamlit`是一个开源的Python库，专为数据工程师及机器学习工程师设计，用来快速基于Python代码构建交互式的web网站（无需掌握前端技术）。

官方网站：[Streamlit • A faster way to build and share data apps](https://streamlit.io/)

## 安装与运行

```powershell
pip install streamlit
```

```powershell
streamlit run ***.py
```

## 基础使用

+ 添加标题

```python
streamlitst.title(...)
streamlitst.header(...)
streamlitst.subheader(...)
```

+ 添加文本

```python
streamlitst.write(...)
```

+ 添加图像

```python
streamlit.image("....png")
```

+ 添加分割线

```python
streamlit.divider()
```

+ 添加表格

```python
streamlit.table(data)
```

例如使用以下代码：

```python
import streamlit as st

st.title("AI智能伴侣")

st.write("布偶猫是一种源于美国的大型半长毛猫")

st.image("streamlit/cat.png")

st.divider()

data = {"姓名": ["张三", "李四", "王五", "赵六", "王琳", "十三"],
        "学号": ["202121001", "202121002", "202121003", "202121004", "202121005", "202121006"],
        "语文": ["80", "90", "75", "85", "92", "88"],
        "数学": ["75", "85", "90", "88", "92", "85"],
        "英语": ["88", "92", "85", "78", "90", "88"],
        "总分": ["243", "240", "245", "243", "242", "241"]
        }
st.table(data)

```

![image-20260910175048981](https://raw.githubusercontent.com/LingxiReihi/PicGo/master/img/20260910175100135.png)