# 票接口2

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
  `randCode=表单验证码&rand=sjrand`
  > 登录时rand=sjrand 提交订单时rand=randp

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
   `loginUserDTO.user_name=用户名&userDTO.password=密码&randCode=验证码`
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

#### 车票预订之查询
1. 日志   （与2一起发送）
   * method: GET
   * url: https://kyfw.12306.cn/otn/leftTicket/log
   * parameters:  
   `leftTicketDTO.train_date=2014-11-04&leftTicketDTO.from_station=BJP&leftTicketDTO.to_station=HFH&purpose_codes=ADULT`
   * response:
   ```javascript
   // 成功
   {
    "validateMessagesShowId":"_validatorMessage",
    "status":true,
    "httpstatus":200,
    "messages":[],
    "validateMessages":{}
   }
   ```

2. 查询接口
   * method: GET
   * url: https://kyfw.12306.cn/otn/leftTicket/query
   * parameters:  
   `leftTicketDTO.train_date=2014-11-04&leftTicketDTO.from_station=BJP&leftTicketDTO.to_station=HFH&purpose_codes=ADULT`
   
   * response:
   ```javascript
   {
      "validateMessagesShowId": "_validatorMessage",
      "status": true,
      "httpstatus": 200,
      "data": [
        {
            "queryLeftNewDTO": {
                "train_no": "2400000G2907",
                "station_train_code": "G29",
                "start_station_telecode": "VNP",
                "start_station_name": "北京南",            
                "end_station_telecode": "HFH",
                "end_station_name": "合肥",
                "from_station_telecode": "VNP",
                "from_station_name": "北京南",
                "to_station_telecode": "HFH",
                "to_station_name": "合肥",
                "start_time": "13:35",
                "arrive_time": "17:25",
                "day_difference": "0",
                "train_class_name": "",
                "lishi": "03:50",
                "canWebBuy": "Y",
                "lishiValue": "230",
                "yp_info": "O042750001M0720500749135050026",      // 余票信息？
                "control_train_day": "20201231",
                "start_train_date": "20141104",
                "seat_feature": "O3M393",               // 
                "yp_ex": "O0M090",
                "train_seat_feature": "3",                
                "seat_types": "OM9",                  // O 是二等座 M是一等座  9是商务座
                "location_code": "P3",
                "from_station_no": "01",                // 出发站点编号
                "to_station_no": "04",                  // 目的站点编号
                "control_day": 19,
                "sale_time": "1400",                  // 出售时间
                "is_support_card": "1",
                "gg_num": "--",
                "gr_num": "--",                       // 高级软卧 
                "qt_num": "--",                       // 其他
                "rw_num": "--",                       // 软卧
                "rz_num": "--",                       // 软座
                "tz_num": "--",                       // 特等座
                "wz_num": "--",                       // 无座
                "yb_num": "--",
                "yw_num": "--",                       // 硬卧
                "yz_num": "--",                       // 硬座
                "ze_num": "1",                        // 二等座
                "zy_num": "有",                       // 一等座
                "swz_num": "有"                       // 商务座
            },
            "secretStr": "MjAxNC0xMS0wNCMwMCNHMjkjMDM6NTAjMTM6MzUjMjQwMDAwMEcyOTA3I1ZOUCNIRkgjMTc6MjUj5YyX5Lqs5Y2XI%2BWQiOiCpSMwMSMwNCNPMDQyNzUwMDAxTTA3MjA1MDA3NDkxMzUwNTAwMjYjUDMjMTQxNTA2OTIwMzExMSMxNDk0RUYzMzYzNjEyRURFMUYwMjNFOTRFRUU1RDEyNkZGN0YzRTdEQzc1QURGQTdDOTNCNjBDMA%3D%3D",
            "buttonTextInfo": "预订"
         }
      ],
      "messages": [],
      "validateMessages": {}
   }
   
   // 其中secretStr是base64编码，decode还原格式如下
   // 2014-11-04#00#G29#03:50#13:35#2400000G2907#VNP#HFH#17:25#北京南#合肥#01#04#O042750001M0720500749135050026#P3#1415069203111#1494EF3363612EDE1F023E94EEE5D126FF7F3E7DC75ADFA7C93B60C0
   ```

3. 列车沿途车站查询
    * method: GET
    * url: https://kyfw.12306.cn/otn/czxx/queryByTrainNo
    * parameters:  
    `train_no=2400000G2907&from_station_telecode=VNPto_station_telecode=HFH&depart_date=2014-11-04`

    > train_no  列车全编号
    > from_station_telecode 列车的起始站 (注意不是旅客的出发站) 
    > to_station_telecode   列车的终点站
    > depart_date           出发日期
    
    * response:
    ```javascript
    {
      "validateMessagesShowId": "_validatorMessage",
      "status": true,
      "httpstatus": 200,
      "data": {
          "data": [
              {
                  "start_station_name": "北京南",
                  "arrive_time": "----",
                  "station_train_code": "G29",    // 列车缩略号
                  "station_name": "北京南",      
                  "train_class_name": "高速",     // 列车种类名称
                  "service_type": "1",        // 如果为0, 2, 4则无空调
                  "start_time": "13:35",
                  "stopover_time": "----",
                  "end_station_name": "合肥",
                  "station_no": "01",
                  "isEnabled": true
              },
              {
                  "arrive_time": "14:09",       // 到站时间
                  "station_name": "天津南",      // 车站名
                  "start_time": "14:11",        // 出发时间
                  "stopover_time": "2分钟",     // 停留时间
                  "station_no": "02",         // 站序
                  "isEnabled": true         // 是否开通
              },
              {
                  "arrive_time": "15:14",
                  "station_name": "济南西",
                  "start_time": "15:17",
                  "stopover_time": "3分钟",
                  "station_no": "03",
                  "isEnabled": true
              },
              {
                  "arrive_time": "17:25",
                  "station_name": "合肥",
                  "start_time": "17:25",
                  "stopover_time": "----",
                  "station_no": "04",
                  "isEnabled": true
              }
          ]
      },
      "messages": [],
      "validateMessages": {}
    }
    ```

4. 查询票价
    * method: GET
    * url:  
      https://kyfw.12306.cn/otn/leftTicket/queryTicketPriceFL 
      https://kyfw.12306.cn/otn/leftTicket/queryTicketPrice
    * parameters:
    `train_no=240000T1670N&from_station_no=01&to_station_no=03&seat_types=1413&train_date=2014-11-04`
    
    > seat_types 由四2查询接口返回的seat_types的参数作为请求   1 硬座 (A1以元为单位)  3 硬卧 (A3以元为单位) 4 软卧 (A4以元为单位)
    
    * response
    ```javascript
    {
      "validateMessagesShowId": "_validatorMessage",
      "status": true,
      "httpstatus": 200,
      "data": {
          "1": "435",
          "3": "945",
          "4": "1415",
          "A1": "¥43.5",
          "A4": "¥141.5",
          "A3": "¥94.5",
          "OT": [],
          "WZ": "¥43.5",
          "train_no": "240000T1670N"
      },
      "messages": [],
      "validateMessages": {}
    }
    ```

#### 预订车票
1. 检查用户是否登录
  * method: POST
  * url: https://kyfw.12306.cn/otn/login/checkUser
  * headers: 
  `If-Modified-Since:0`
  * parameters:
  `_json_att=`
  * response:
  ```javascript
  {
    "validateMessagesShowId": "_validatorMessage",
    "status": true,
    "httpstatus": 200,
    "data": {
        "flag": true
    },
    "messages": [],
    "validateMessages": {}
  }
  ```
2. 发起预订车票
  * method: POST
  * url: https://kyfw.12306.cn/otn/leftTicket/submitOrderRequest
  * parameter
  `secretStr=xxx&train_date=2014-11-16&back_train_date=2014-11-20&tour_flag=dc&purpose_codes=ADULT&query_from_station_name=北京&query_to_station_name=南京&undefined`
  * response:
  ```javascript
  {
    "validateMessagesShowId": "_validatorMessage",
    "status": true,
    "httpstatus": 200,
    "messages": [],
    "validateMessages": {}
  }
  ```

3. 获取乘客信息
    * method: POST
    * url: https://kyfw.12306.cn/otn/confirmPassenger/getPassengerDTOs 
    * parameters:
    `_json_att=&REPEAT_SUBMIT_TOKEN=xxx`
    * response:
    ```javascript
    {
      "validateMessagesShowId": "_validatorMessage",
      "status": true,
      "httpstatus": 200,
      "data": {
        "isExist": true,
        "exMsg": "",
        "two_isOpenClick": [
          "93",
          "95",
          "97",
          "99"
        ],
        "other_isOpenClick": [
          "91",
          "93",
          "98",
          "99",
          "95",
          "97"
        ],
        "normal_passengers": [
          {
            "code": "1",                   
            "passenger_name": "吴思泉",
            "sex_code": "M",
            "sex_name": "男",
            "born_date": "1985-08-29 00:00:00",
            "country_code": "CN",
            "passenger_id_type_code": "1",          
            "passenger_id_type_name": "二代身份证",
            "passenger_id_no": "340503198508290637",
            "passenger_type": "1",                        // 1 二代身份证  C 港澳通行证  G 台湾通行证 B 护照 
            "passenger_flag": "0",
            "passenger_type_name": "成人",
            "mobile_no": "18500238337",     
            "phone_no": "",
            "email": "wsq19850829@163.com",
            "address": "",
            "postalcode": "",
            "first_letter": "",
            "recordCount": "1",
            "total_times": "99",
            "index_id": "0"
          }
        ],
        "dj_passengers": []
      },
      "messages": [],
      "validateMessages": {}
    }
    ```
#### 确认订单
1. 检查验证码
  * method: POST
  * url: https://kyfw.12306.cn/otn/passcodeNew/checkRandCodeAnsyn
  * parameters: 
  `randCode=表单验证码&rand=randp&_json_att=&REPEAT_SUBMIT_TOKEN=toke码`
  * response:
   ```javascript
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":t  rue,
      "httpstatus":200,
      "data":"Y",
      "messages":[],
      "validateMessages":{}
   }
   ```
2. 检查订单信息
  * method: POST
  * url: https://kyfw.12306.cn/otn/confirmPassenger/checkOrderInfo
  * parameters:
  `cancel_flag=2&bed_level_order_num=000000000000000000000000000000&passengerTicketStr=O%2C0%2C1%2C%E5%90%B4%E6%80%9D%E6%B3%89%2C1%2C340503198508290637%2C18500238337%2CN&oldPassengerStr=%E5%90%B4%E6%80%9D%E6%B3%89%2C1%2C340503198508290637%2C1_&tour_flag=dc&randCode=xxx&_json_att=&REPEAT_SUBMIT_TOKEN=xxx`
  > cancel_flag 与 bed_level_order_num 的值固定
  > passengerTicketStr:
  > oldPassengerStr:
  * response:
  ```javascript
  {
    "validateMessagesShowId": "_validatorMessage",
    "status": true,
    "httpstatus": 200,
    "data": {
        "submitStatus": true
    },
    "messages": [],
    "validateMessages": {}
  }
  ```
