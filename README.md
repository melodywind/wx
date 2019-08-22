## 微信小程序表单验证插件 -- WxValidate 
一、wxml文件

```js
<form bindsubmit="formSubmit">
    <view class="wide-info">      
      <view class="wide-info-list">
        <!--姓名-->
        <view class="info-list">
          <view class="info-list-1eft">
            <text class="notEmptyClass">姓名</text>
          </view>
          <view class="info-list-right">
            <input id="name" name='name' placeholder='请输入' value='{{form.name}}' class="wxValidate inputName" 
            data-validate="notEmpty|size[4,10]" data-fieldname="姓名"/>
          </view>
        </view>
 
        <!--密码-->
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text class="notEmptyClass">密码</text>
          </view>
          <view class="info-list-right">            
            <input type="text" id="password" name="password" placeholder='请输入' value='{{form.age}}' class="wxValidate inputName"
            data-fieldname="密码" data-validate="notEmpty"/>
          </view>
        </view>
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text class="notEmptyClass">重复密码</text>
          </view>
          <view class="info-list-right">            
            <input type="text" id="cfpassword" name="cfpassword" placeholder='请输入' value='{{form.age}}' class="wxValidate inputName"
            data-fieldname="重复密码" data-validate="notEmpty|equals[password]"/>
          </view>
        </view>
 
        <!--年龄-->
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text class="notEmptyClass">年龄</text>
          </view>
          <view class="info-list-right">            
            <input type="text" id="age" name="age" placeholder='请输入' value='{{form.age}}' class="wxValidate inputName"
            data-fieldname="年龄" data-validate="notEmpty|int|range[18,60]"/>
          </view>
        </view>
 
      </view>
 
    </view>
      <!--按钮--->
    <view class="buttons-kind">
       <button  class="fabu" form-type="submit">发布</button>
    </view>
</form>

 
## 重点：每一个表单控件必须有3个属性和一个特定的样式关键字。

## 参数说明
| 参数 | 类型 | 描述 |
| --- | --- | --- |
| rules | <code>object</code> | 验证字段的规则 |
| messages | <code>object</code> | 验证字段的提示信息 |


| 属性 | 说明 |
| id | 表单控件的ID |
| data-validate	| 
需要做相关验证的关键字，多种验证用‘|’隔开，例如上面的姓名要验证不为空同时长度在4-10个字符：
data-validate="notEmpty|size[4,10]" | 
| data-fieldname | 当出现错误时，显示在错误提示中的表单名称。| 
 

样式	说明
wxValidate
代表此表单控件要做相关验证，必须写。
 

二.js文件

import WxValidate from '../../utils/WxValidate.js'
const util = require('../../utils/util.js')
Page({
  /**
   * 页面的初始数据
   */
  data: {
    date:""   
  },
 
  /**
   * 生命周期函数--监听页面加载
   */
  onLoad: function (options) {
    
  },
  /**
   * 生命周期函数--监听页面初次渲染完成
   */
  onReady: function () {
    //验证方法
    this.WxValidate = new WxValidate();  
  },
  bindDateChange : function(e){    
    this.setData({date:e.detail.value})
  }, 
  /***调用验证函数***/
  formSubmit: function (e) {
    console.log('form发生了submit事件，携带的数据为：', e.detail.value)
    const params = e.detail.value
    e.detail.value.osscation_address = this.data.osscation_address
    e.detail.value.date = this.data.date
    console.log(e.detail.value)
    console.log(this.WxValidate.rules)
    console.log(this.WxValidate.messages)
    //校验表单
    if (!this.WxValidate.checkForm(params)) {
      const error = this.WxValidate.errorList[0]
      util.alert("错误提示",error.msg)
      return false
    }
    //向后台发送时数据 wx.request...    
    util.alert("成功提示", '提交成功 :' + e.detail.value.date)
  }
 
})
  重点： 此页面只要在渲染完的方法里new WxValidate();然后在提交的操作里加上判断即可。


三、验证关键字

关键字	说明	用法
notEmpty	不能为空	 
size[4,10]
输入字符的长度	
可以只写一个数字，注意根据判断的不同，判断要不要写“，”。例如
长度最小为4则可写成：size[4];
长度最大为10则可写成：size[,10]，注意逗号不能少;
int
整数	 
number
数字	 
range[18,60]
数值的范围	
类似与size，但此关键字还多一种判断，例如是不包含首尾的数值，例如
薪酬必须大于5000 小于等于20000： range(5000,20000]；
或者年龄必须18-60之间，但不包含18岁和60岁：range(18,60)
equals[id]
等于另一个表单的值	 
tel
电话格式（中国大陆）	 
phone	手机格式（中国大陆）	 
idcard
身份证（中国大陆）	 
date
日期	 
dateISO
日期（ISO），例如：2009-06-23，1998/01/22	 
email	邮箱地址	 
url	网站地址	 


