# 票接口

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
   {
      "validateMessagesShowId": "_validatorMessage",
      "status": true,
      "httpstatus": 200,
      "data": {
         "datas": [
            {
               "train_no": "2400000G2106",
               "station_train_code": "G21",			   // 车次
               "start_station_telecode": "VNP",		
               "start_station_name": "北京南",			// 起始站
               "end_station_telecode": "AOH",	
               "end_station_name": "上海虹桥",			// 终点站
               "from_station_telecode": "VNP",
               "from_station_name": "北京南",			// 出发站
               "to_station_telecode": "NKH",			
               "to_station_name": "南京南",			// 到达站
               "start_time": "17:00",					// 出发时间
               "arrive_time": "21:11",					// 到达时间
               "day_difference": "0",					// 差别天数,0代表明天到达，1代表第二日到达
               "train_class_name": "",
               "lishi": "04:11",						   // 历时  小时:分钟
               "canWebBuy": "N",
               "lishiValue": "251",
               "yp_info": "O044350000M0748500009140350000",
               "control_train_day": "20201231",		   // 
               "start_train_date": "20141024",			// 出发日
               "seat_feature": "O3M393",
               "yp_ex": "O0M090",
               "train_seat_feature": "3",
               "seat_types": "OM9",					      // 
               "location_code": "P2",
               "from_station_no": "01",
               "to_station_no": "06",
               "control_day": 19,
               "sale_time": "1400",
               "is_support_card": "1",
               "note": "",
               "gg_num": "--",					
               "gr_num": "--",				// 高级软卧
               "qt_num": "--",				// 其它
               "rw_num": "--",				// 软卧
               "rz_num": "--",				// 软座
               "tz_num": "--",				// 特等座		
               "wz_num": "--",				// 无座
               "yb_num": "--",				
               "yw_num": "--",				// 硬卧
               "yz_num": "--",				// 硬座
               "ze_num": "无",				// 二等座
               "zy_num": "无",				// 一等座
               "swz_num": "无"				// 商务座
            }
        ],
        "flag": true,
        "searchDate": "2014年10月24号&nbsp;&nbsp;周五"
    },
    "messages": [],
    "validateMessages": {}
   }
   ```
