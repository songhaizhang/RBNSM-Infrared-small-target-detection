代码注释：<!--注释文字-->
*****
强调用\<em>和\<strong>标签：\<em>表示一般强调，默认斜体，\<strong>表示更强烈的强调，默认粗体，国内大部分程序员用这个
 \<em>要强调的文本\</em>    \<strong>要强调的文本\</strong>
*****
 span作用是设置单独的样式：\<span>文本\</span>
 span{
      color:blue; }
*****
引用用\<q>: \<q>引用文本\</q>,适用于简短文本
例：\<p>最初知道庄子是从一首诗\<q>庄生晓梦迷蝴蝶，望帝春心托杜鹃\</q>\</p>
引用文本较长用\<blockquote>引用文本\</blockquote>,适用于较长的引用
*****
换行用\<br />
空格用\&nbsp;
添加水平横线用：\<hr />
显示地址信息用：\<address>地址信息\</address>,浏览器显示斜体
加入代码用\<code>:  \<code>加入代码\</code>
加入多行代码用\<pre>,加入的代码段通常会保存空格和回车
添加新闻信息列表(无序，默认前是圆点)用ul-li：例：
                                                                 \<ul>
                                                                 \<li>精彩少年</li>
								 \<li>美丽突然出现\</li>
								 \<li>触动心灵的旋律\</li>
                                                                 \</ul>
添加排行榜列表(有序，默认从序号1开始)用ol-li:  例：          
                                                                 \<ol>
								 \<li>前端面试心法\</li>
								 \<li>零基础学习html\</li>
								 \<li>JavaScribe全攻略\</li>
								 \</ol>
*****
使用div排版分块设计：\<div>...\</div>
给div命名：\<div  id="板块名称">...\</div>
*****
创建表格需要五个元素：table,tbody,th,tr,td
\<table>...</table>:表格以这个格式里
\<tbody>...</tbody>:加上标签后，会等表格全部下载才会显示
\<td>...</td>:表格的一个单元格，包含多少对\<td>就有多少列
\<tr>...</tr>:表格的一行，有多少对\<tr>就有多少行
\<th>...</th>:表格的表头
*****
摘要：\<table summary="表格简介文本">
标题：<table>
            \<caption>标题文本\</caption>
             \<tr>
             \<td>…</td>
             \<td>…</td>
                      …
             \</tr>
                      …
             \</table>
*****
使用\<a>标签实现超链接：
\<a href="目标网址"  title="鼠标滑过显示的文本">链接显示文本\</a>
例：<a  href="http://www.imooc.com"  title="点击进入慕课网">click here!</a>
上面例子作用是单击click here!文字，网页链接到http://www.imooc.com这个网页。
title属性的作用，鼠标滑过链接文字时会显示这个属性的文本内容。
这个属性在实际网页开发中作用很大，主要方便搜索引擎了解链接地址的内容（语义化更友好）
*****
在新窗口打开链接：<a  href="目标网址"   target="_blank">click here!</a>
*****
插入图片： <img src = "myimg.gif" alt = "my imag" title = "my image" />
*****
表单：\<form  method = "传送方式"  action = "服务器文件">
例：<form    method="post"   action="save.php">
        <label for="username">用户名:</label>
        <input type="text" name="username" />
        <label for="pass">密码:</label>
        <input type="password" name="pass" />
      </form>
表单的两种提交方式：get和post
get：提交的数据不超过2kb，适合提交数据量不大，安全性不高的数据。比如搜索，查询等功能。
post：将用户提交的信息封装在HTML HEADER内，适合数据量大的，安全性高的用户信息。比如，注册          ，修改,上传等功能。
*****
文本输入框和密码输入框：
<form>
<input  type = "text/password" name = "名称" value = "文本" />
</form>

1、type：
   当type="text"时，输入框为文本输入框;
   当type="password"时, 输入框为密码输入框。
2、name：为文本框命名，以备后台程序ASP 、PHP使用。
3、value：为文本输入框设置默认值。(一般起到提示作用)

多行文本框：\<textarea rows="行数" cols = "列数">默认文本</textarea>
例：<form  method="post" action="save.php">
        <label>联系我们</label>
        <textarea cols="50" rows="10" >在这里输入内容...</textarea>
      </form>
*****

下拉列表：<option value= '提交值'（向服务器提交的值）>显示的值</option>
selected= "selected"该选项被默认选中
例：<select>
      <option value="看书">看书</option>
      <option value="旅游"selected="selected">旅游</option>
      <option value="运动">运动</option>
      <option value="购物">购物</option>
     </select>
*****
提交按钮：<input type = "submit" value = "提交">（value：按钮上显示的字）
重置按钮：<input type = "reset" value = "重置">
*****
单选框：<input type = "radio" name = "名称" value = " ">
例：<input type = "email"  id = "email" placeholder = "enter email" >(placeholder是邮箱框中的显示字段)
复选框：<input type = "checkbox" name = "名称" value = " ">
*****
name和id的区别：（name可以出现很多次，可以对应多个控件 id全文只能出现一次）
以下情况只能用name：
表单（form）的控件名，提交的数据都用控件的name而不是id来控制。因为有许多name会同时对应多个控件
以下情况只能用id：
label与form的控件关联，例
<label for="MyInput">My Input</label>
<input id="MyInput" type="text">
for属性指定与label关联的元素的id，不可用name替代
*****