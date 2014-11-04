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

  * method: GET
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
