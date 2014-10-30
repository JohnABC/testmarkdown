# 12306接口

1. 验证码生成接口

* Request Method: GET

* Request URL: https://kyfw.12306.cn/otn/passcodeNew/getPassCodeNew

* Query String Parameters: 
    
    module=**login**&rand=**sjrand**&**0.5099291640799493**  
    说明：  
        - module  值固定为login  
        - rand    值固定位sjrand  
        - 最后参数带上随机数字

* Cookie:JSESSIONID=xxx;BIGipServerotn=xxx
    说明：  
        - JSESSIONID        首次访问服务器设置的cookie  
        - BIGipServerotn    首次访问服务器设置的cookie 
        
* Response: 验证码图片

2. 验证码判断接口

* Request Method: GET

