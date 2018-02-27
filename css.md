### 限制文本行数，多行文本溢出处理
```
<!-- 英文文本处理 -->
word-break: break-all;
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 3;
overflow: hidden;
```
### 小图标由基线对齐修改为中心对齐
- 将`line-height`设置得足够小
- 通过修改字体大小`font-size: 0`间接修改line-height
- 将父元素的`vertical-align`改为`middle`
- 将图标设置为`display: block`,让`vertical-align`失效

### 水平垂直居中的几种方法
- 文本的水平垂直居中
```
height: 100px;
line-height: 100px;
text-align: center;
```
- flex布局
```
display: flex;
justify-content: center;
align-item: center;
```
- position(设置相对定位元素后)
```
width: 100px;
height: 100px;
position: absolute;
top: 50%;
left: 50%;
margin-left: -50px;
margin-top: -50px;
```
- transform(设置相对定位元素后)
```
width: 100px;
height: 100px;
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
```
- 通过`margin: auto`方法
```
.wrap{
  position: relative;
  width: 500px;
  height: 500px;
  background: #333;
  .ele{
    position: absolute;
    width: 100px;
    height: 100px;
    left: 0;
    top: 0;
    bottom: 0;
    right: 0;
    margin: auto;
    background: #ddd;
  }
}
```
