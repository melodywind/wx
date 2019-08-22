# wx

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
        <!--公司名称-->
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text class="notEmptyClass">公司名称</text>            
          </view>
          <view class="info-list-right">
            <input type="text" id="companyName" name="companyName" placeholder='请输入' value='{{form.companyName}}' class="wxValidate inputName" data-validate="notEmpty" data-fieldname="公司名称" />
          </view>
        </view>
        
        <!--成立时间--->
        <view class="info-list">
          <view class="info-list-1eft">
            <text class="notEmptyClass">成立时间</text>            
          </view>
          <view class="info-list-right">
            <view class="section">
              <picker mode="date" value="{{date}}" start="1901-01-01" end="2099-12-31" bindchange="bindDateChange"
              class="wxValidate" id="date" data-validate="notEmpty" data-fieldname="成立时间">
                <text class="picker">当前选择:{{date}}</text>
                <text class="iconfont icon-arrow-right-copy-copy" id="phoneIcon"></text>
              </picker>
            </view>
          </view>
        </view>
      </view>
      <view class="line"></view>
      <view class="wide-info-list ">         
        <!--联系电话-->
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text class="notEmptyClass">手机</text>           
          </view>
          <view class="info-list-right">            
            <input id="phone" name='phone' type='number' placeholder='请输入' value='{{form.phone}}' class="wxValidate inputName" 
            data-fieldname="手机" data-validate="notEmpty|phone"/>
          </view>
        </view>
        <!--身份证-->
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text class="notEmptyClass">身份证</text>           
          </view>
          <view class="info-list-right">            
            <input id="idCard" name='idCard' type='number' placeholder='请输入' value='' class="wxValidate inputName" 
            data-fieldname="身份证" data-validate="notEmpty|idcard"/>
          </view>
        </view>
        <!--邮箱-->
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text>邮箱</text>
          </view>
          <view class="info-list-right">            
            <input type="text" name="email" placeholder='请输入' value='{{form.email}}' class="wxValidate inputName" 
            id="email" data-validate="email" data-fieldname="邮箱"/>
          </view>
        </view>
        <!--个人主页-->
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text>个人主页</text>
          </view>
          <view class="info-list-right">            
            <input type="text" name="url" placeholder='请输入' value='{{form.url}}' class="wxValidate inputName" 
            id="url" data-validate="url" data-fieldname="个人主页"/>
          </view>
        </view>
        <!--薪酬-->
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text>薪酬</text>
          </view>
          <view class="info-list-right">            
            <input type="text" name="money" placeholder='请输入' value='{{form.email}}' class="wxValidate inputName" 
            id="money" data-validate="number|range[5000,20000]" data-fieldname="薪酬" />
          </view>
        </view>

        <!--性别-->
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text class="notEmptyClass">性别</text>
          </view>
          <view class="info-list-right">            
            <radio-group name="sex" id="sex" data-validate="notEmpty" data-fieldname="性别" class="wxValidate inputName" >
              <radio value="men"/>男
              <radio value="women">女</radio>
            </radio-group>
          </view>
        </view>
        
        <!--爱好-->
        <view class="info-list">
          <view class="info-list-1eft dark">
            <text class="notEmptyClass">爱好</text>
          </view>
          <view class="info-list-right">            
            <checkbox-group name="hobby" id="hobby" data-validate="notEmpty" data-fieldname="爱好" class="wxValidate inputName" >
              <checkbox value="1">旅行</checkbox>
              <checkbox value="2">游泳</checkbox>
              <checkbox value="3">电影</checkbox>
            </checkbox-group>
          </view>
        </view>


      </view>
 
    </view>
      <!--按钮--->
    <view class="buttons-kind">
       <button  class="fabu" form-type="submit">发布</button>
    </view>
</form>
