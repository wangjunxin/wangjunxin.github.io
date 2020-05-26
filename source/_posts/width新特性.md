# width新属性

Created By: junxin wang
Last Edited: May 10, 2020 3:07 PM

## width:fill-available

fill-availabel自动填充满剩余空间，价值在于使inline-block元素能100%自动填充

```css
div { display:inline-block; width:fill-available; }
```

此时的元素同时具备块状元素的自动填充特性以及内联元素的定位对齐特性，可以使用line-height让块状元素垂直居中

## width：max-content

假设我们的容器有足够的宽度，足够的空间，此时，所占据的宽度是就是max-content所表示的尺寸。

## width:min-content

宽度表示的并不是内部那个宽度小就是那个宽度，而是，采用内部元素最小宽度值最大的那个元素的宽度作为最终容器的宽度。

最小宽度值：替换元素，例如图片的最小宽度值就是图片呈现的宽度，对于文本元素，如果全部是中文，则最小宽度值就是一个中文的宽度值；如果包含英文，因为默认英文单词不换行，所以，最小宽度可能就是里面最长的英文单词的宽度。

## width:fit-content

实现元素收缩效果的同时，保持原本的block水平状态，于是，就可以直接使用margin:auto实现元素向内自适应同时的居中效果了

```css
.box {
    background-color: #f0f3f9;
    padding: 10px;
    /* 这里左右方向是auto */
    margin: 10px auto 20px;
    overflow: hidden;
}
.fit-content {
    width: -webkit-fit-content;
    width: -moz-fit-content;
    width: fit-content;    
}

<div class="box fit-content">
    <img src="mm1.jpg">
    <p>display:inline-block居中要靠父元素，而width:fit-content直接margin:auto.</p>
</div>
```