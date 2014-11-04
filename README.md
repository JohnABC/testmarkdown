# 12306接口

#### 验证码接口
1. 验证码生成接口

    * method: GET
    * url: https://kyfw.12306.cn/otn/passcodeNew/getPassCodeNew
    * parameters:  
      module=login&rand=sjrand&0.5099291640799493     登录时 
      module=passenger&rand=randp&0.2637785451952368  提交订单时验证码            
    
    说明：
      - module  
      - rand
      - 最后参数带上随机数字

 * Cookie:JSESSIONID=xxx;BIGipServerotn=xxx
    说明：
      - JSESSIONID        首次访问服务器设置的cookie
      - BIGipServerotn    首次访问服务器设置的cookie
   
 * Response: 验证码图片

2. 验证码检查接口

  * method: POST
  * url: https://kyfw.12306.cn/otn/passcodeNew/checkRandCodeAnsyn
  * parameters: 
    { randCode:表单验证码, rand:sjrand }  登录时rand=sjrand，提交订单时rand=randp

  * response:
   ```javascript
   // 失败时：
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":"N",
      "messages":[],
      "validateMessages":{}
   }
   
   // 成功时：
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":"Y",
      "messages":[],
      "validateMessages":{}
   }
   ```

#### 登录接口

1. 检查是否登录
   * method: POST
   * url: https://kyfw.12306.cn/otn/login/checkUser
   * parameters:  
   _json_att 值为空
   
   * response:
   ```javascript
   // 失败时：
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":{"flag":false},
      "messages":[],
      "validateMessages":{}
   }
   
   // 成功时：
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":{"flag":true},
      "messages":[],
      "validateMessages":{}
   }
   ```

2. 登录接口
   * method: POST
   * url: https://kyfw.12306.cn/otn/login/loginAysnSuggest
   * parameters:  
   { "loginUserDTO.user_name":用户名, "userDTO.password":密码, "randCode": 验证码 }
   
   * response:
   ```javascript
   // 失败时：
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":{},
      "messages":["密码输入错误,您还有3次机会!"],
      "validateMessages":{}
   }
   
   // 成功时：
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":{"loginCheck":"Y"},
      "messages":[],
      "validateMessages":{}
   }
   ```

#### 余票查询接口
   * method: GET
   * url: https://kyfw.12306.cn/otn/lcxxcx/query
   * parameters:  
   `purpose_codes: ADULT&queryDate: 2014-10-24&from_station: BJP&to_station: NJH``
   > purpose_codes   ADULT为成人票  0X00为学生票
   > queryDate       出发日
   > from_station
   > to_station

   * response:
   ```javascript
   // 失败时：
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":{},
      "messages":["密码输入错误,您还有3次机会!"],
      "validateMessages":{}
   }
   
   // 成功时：
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":{"loginCheck":"Y"},
      "messages":[],
      "validateMessages":{}
   }
   ```
