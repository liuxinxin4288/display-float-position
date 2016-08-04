# display && position && float
## display
- 之前浏览前端大牛的blog，大牛说，前端最难的是html,其次css，再次js.不知道什么时候能从程序猴进化成大牛。o(^▽^)o



```
display:inline-block;
display:inline;
```
正常来说行局元素不能设置宽高，但是实际上，像 input textarea select button 等是可以设置宽高的，因为它们的display属性为inline-block;
- inline-block 是将元素表现为inline，但是元素的内容作为block来呈现（有正常的盒模型 margin border padding content），也就是说，这些元素的margin 和padding 是可以设置并且能正常显示的。
- 除了这些比较特殊的行局元素，其它的设置padding 和margin的时候，left and right是好使的。但是竖直方向不会产生边距效果。
```
display:none;
visibility:hidden;  
```
- 元素都是不显示，区别是前者就像该元素从来没有存在，后者是元素还占用原来的位置只是被隐藏。

```
display:block;
```
- 让行局元素以块局元素来显示。可以正常设置margin padding
-
## position
CSS 有三种基本的定位机制：普通流、浮动和绝对定位
```
position:static;
```
- static是默认属性。

```
position：relative;
```
- 相对定位相对自己原来的位置定位。
**在使用相对定位时，无论元素是否移动，元素在文档流中占据原来的空间，只是表现会改变。**

```
    //为了方便展示，使用内联样式。每个div宽高都是100px;
   <div class="content">
       <div style="background-color: red">1</div>
       <div style="background-color: green;position: relative;left: 50px;top: 50px;">2</div>
       <div style="background-color: yellow">3</div>
   </div>
```
![Alt text](./1470035758650.png)

```
position:absolute;
```
**绝对定位:元素绝对定位后生成一个块级框，而不论原来它在正常流中生成何种类型的框。也就是说，行局元素定位后变成块局元素**
- 绝对定位会脱离文档流。
- 绝对定位会相对于距离最近的非static祖先元素定位。如果没有，则相对于最初的包含块（html）。
```
    //为了方便展示，使用内联样式。每个div宽高都是100px;
   <div class="content">
       <div style="background-color: red">1</div>
       <div style="background-color: green;position: absolute;left: 50px;top: 50px;">2</div>
       <div style="background-color: yellow">3</div>
   </div>
```
![Alt text](./1470036237292.png)
*div2脱离文档流,div2绝对定位之后，div1和div3布局时就像div2不存在一样*

```
position:fixed;
```
- 相对于浏览器的可视窗口定位。
```
    //为了方便展示，使用内联样式。每个div宽高都是100px;
   <div class="content">
       <div style="background-color: red">1</div>
       <div style="background-color: green;position: fixed;left: 0;buttom: 0;">2</div>
       <div style="background-color: yellow">3</div>
   </div>
```
![Alt text](./1470037389005.png)

+ 细节部分：如果一个设置了margin的元素定位，它的定位距离left top是从margin开始算起，不是content
![Alt text](./1470038159958.png)
其中div4是div2设置了margin之前的位置。div2设置了margin:20px;
## float
- 浮动后的元素会生成一个块级框，而不论这个元素本身是什么。
- 浮动的元素之间从来不会彼此覆盖。（这一点跟定位不同）
- 当元素与浮动元素覆盖时，行内元素完全覆盖了浮动元素（边框和内容），块元素只是将内容展示在浮动元素之上，但其背景和边框都在浮动元素之下。
- 浮动元素不能比之前**所有浮动元素或块级元素的顶端**更高。

##### 清除浮动：

```
 clear:both
```
**- 只能通过改变使用清除的元素本身，并不能影响其他元素。**

- div1 div2 左浮  div3 右浮
![Alt text](./1470129053817.png)

- div3 使用clear后
![Alt text](./1470128988787.png)

- div2使用clear:both后（注意div3的高度）
![Alt text](./1470129225982.png)










