# ��Ʊ�ӿ�2014.11.23

#### ��֤��ӿ�
1. ��֤�����ɽӿ�

   * method: GET
   * url: https://kyfw.12306.cn/otn/passcodeNew/getPassCodeNew
   * parameters:  
      module=login&rand=sjrand&0.5099291640799493     ��¼ʱ 
      module=passenger&rand=randp&0.2637785451952368  �ύ����ʱ��֤��            
    
   ˵����
      - module  
      - rand
      - �����������������
   
   * Cookie:JSESSIONID=xxx;BIGipServerotn=xxx
   ˵����
      - JSESSIONID        �״η��ʷ��������õ�cookie
      - BIGipServerotn    �״η��ʷ��������õ�cookie
   
   * Response: ��֤��ͼƬ

2. ��֤����ӿ�

  * method: POST
  * url: https://kyfw.12306.cn/otn/passcodeNew/checkRandCodeAnsyn
  * parameters: 
  `randCode=����֤��&rand=sjrand`
  > ��¼ʱrand=sjrand �ύ����ʱrand=randp

  * response:
   ```javascript
   // ʧ��ʱ��
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":"N",
      "messages":[],
      "validateMessages":{}
   }
   
   // �ɹ�ʱ��
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":"Y",
      "messages":[],
      "validateMessages":{}
   }
   ```

#### ��¼�ӿ�

1. ����Ƿ��¼
   * method: POST
   * url: https://kyfw.12306.cn/otn/login/checkUser
   * parameters:  
   _json_att ֵΪ��
   
   * response:
   ```javascript
   // ʧ��ʱ��
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":{"flag":false},
      "messages":[],
      "validateMessages":{}
   }
   
   // �ɹ�ʱ��
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":{"flag":true},
      "messages":[],
      "validateMessages":{}
   }
   ```

2. ��¼�ӿ�
   * method: POST
   * url: https://kyfw.12306.cn/otn/login/loginAysnSuggest
   * parameters:  
   `loginUserDTO.user_name=�û���&userDTO.password=����&randCode=��֤��`
   * response:
   ```javascript
   // ʧ��ʱ��
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":{},
      "messages":["�����������,������3�λ���!"],
      "validateMessages":{}
   }
   
   // �ɹ�ʱ��
   {
      "validateMessagesShowId":"_validatorMessage",
      "status":true,
      "httpstatus":200,
      "data":{"loginCheck":"Y"},
      "messages":[],
      "validateMessages":{}
   }
   ```

3. ��¼302�ӿ� Moved Temporarily   ò�Ʋ�����û�����
	* method: POST
	* url: https://kyfw.12306.cn/otn/login/loginAysnSuggest
	* parameters:  
		`_json_att=''`
	* response:
	```javascript
	// ����Ҫ
	```	
	
   
4. ��ȡ��¼�û���Ϣ
  * method: POST
  * url:  https://kyfw.12306.cn/otn/login/loginUserAsyn
  * parameters:
  `random=1415935440931`
  * response:
  ```javascript
  {
    "validateMessagesShowId": "_validatorMessage",
    "status": true,
    "httpstatus": 200,
    "data": {
      "username": "��˼Ȫ",
      "status": true
    },
    "messages": [],
    "validateMessages": {}
  }
  ```

#### ��ƱԤ��֮��ѯ
1. ��־   ����2һ���ͣ�
   * method: GET
   * url: https://kyfw.12306.cn/otn/leftTicket/log
   * parameters:  
   `leftTicketDTO.train_date=2014-11-04&leftTicketDTO.from_station=BJP&leftTicketDTO.to_station=HFH&purpose_codes=ADULT`
   * response:
   ```javascript
   // �ɹ�
   {
    "validateMessagesShowId":"_validatorMessage",
    "status":true,
    "httpstatus":200,
    "messages":[],
    "validateMessages":{}
   }
   ```

2. ��ѯ�ӿ�
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
                "start_station_name": "������",            
                "end_station_telecode": "HFH",
                "end_station_name": "�Ϸ�",
                "from_station_telecode": "VNP",
                "from_station_name": "������",
                "to_station_telecode": "HFH",
                "to_station_name": "�Ϸ�",
                "start_time": "13:35",
                "arrive_time": "17:25",
                "day_difference": "0",
                "train_class_name": "",
                "lishi": "03:50",
                "canWebBuy": "Y",
                "lishiValue": "230",
                "yp_info": "O042750001M0720500749135050026",      // ��Ʊ��Ϣ��
                "control_train_day": "20201231",
                "start_train_date": "20141104",
                "seat_feature": "O3M393",               // 
                "yp_ex": "O0M090",
                "train_seat_feature": "3",                
                "seat_types": "OM9",                  // O �Ƕ����� M��һ����  9��������
                "location_code": "P3",
                "from_station_no": "01",                // ����վ����
                "to_station_no": "04",                  // Ŀ��վ����
                "control_day": 19,
                "sale_time": "1400",                  // ����ʱ��
                "is_support_card": "1",
                "gg_num": "--",
                "gr_num": "--",                       // �߼����� 
                "qt_num": "--",                       // ����
                "rw_num": "--",                       // ����
                "rz_num": "--",                       // ����
                "tz_num": "--",                       // �ص���
                "wz_num": "--",                       // ����
                "yb_num": "--",
                "yw_num": "--",                       // Ӳ��
                "yz_num": "--",                       // Ӳ��
                "ze_num": "1",                        // ������
                "zy_num": "��",                       // һ����
                "swz_num": "��"                       // ������
            },
            "secretStr": "MjAxNC0xMS0wNCMwMCNHMjkjMDM6NTAjMTM6MzUjMjQwMDAwMEcyOTA3I1ZOUCNIRkgjMTc6MjUj5YyX5Lqs5Y2XI%2BWQiOiCpSMwMSMwNCNPMDQyNzUwMDAxTTA3MjA1MDA3NDkxMzUwNTAwMjYjUDMjMTQxNTA2OTIwMzExMSMxNDk0RUYzMzYzNjEyRURFMUYwMjNFOTRFRUU1RDEyNkZGN0YzRTdEQzc1QURGQTdDOTNCNjBDMA%3D%3D",
            "buttonTextInfo": "Ԥ��"
         }
      ],
      "messages": [],
      "validateMessages": {}
   }
   
   // ����secretStr��base64���룬decode��ԭ��ʽ����
   // 2014-11-04#00#G29#03:50#13:35#2400000G2907#VNP#HFH#17:25#������#�Ϸ�#01#04#O042750001M0720500749135050026#P3#1415069203111#1494EF3363612EDE1F023E94EEE5D126FF7F3E7DC75ADFA7C93B60C0
   ```

3. �г���;��վ��ѯ
    * method: GET
    * url: https://kyfw.12306.cn/otn/czxx/queryByTrainNo
    * parameters:  
    `train_no=2400000G2907&from_station_telecode=VNPto_station_telecode=HFH&depart_date=2014-11-04`

    > train_no  �г�ȫ���
    > from_station_telecode �г�����ʼվ (ע�ⲻ���ÿ͵ĳ���վ) 
    > to_station_telecode   �г����յ�վ
    > depart_date           ��������
    
    * response:
    ```javascript
    {
      "validateMessagesShowId": "_validatorMessage",
      "status": true,
      "httpstatus": 200,
      "data": {
          "data": [
              {
                  "start_station_name": "������",
                  "arrive_time": "----",
                  "station_train_code": "G29",    // �г����Ժ�
                  "station_name": "������",      
                  "train_class_name": "����",     // �г���������
                  "service_type": "1",        // ���Ϊ0, 2, 4���޿յ�
                  "start_time": "13:35",
                  "stopover_time": "----",
                  "end_station_name": "�Ϸ�",
                  "station_no": "01",
                  "isEnabled": true
              },
              {
                  "arrive_time": "14:09",       // ��վʱ��
                  "station_name": "�����",      // ��վ��
                  "start_time": "14:11",        // ����ʱ��
                  "stopover_time": "2����",     // ͣ��ʱ��
                  "station_no": "02",         // վ��
                  "isEnabled": true         // �Ƿ�ͨ
              },
              {
                  "arrive_time": "15:14",
                  "station_name": "������",
                  "start_time": "15:17",
                  "stopover_time": "3����",
                  "station_no": "03",
                  "isEnabled": true
              },
              {
                  "arrive_time": "17:25",
                  "station_name": "�Ϸ�",
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

4. ��ѯƱ��
    * method: GET
    * url:  
      https://kyfw.12306.cn/otn/leftTicket/queryTicketPriceFL 
      https://kyfw.12306.cn/otn/leftTicket/queryTicketPrice
    * parameters:
    `train_no=240000T1670N&from_station_no=01&to_station_no=03&seat_types=1413&train_date=2014-11-04`
    
    > seat_types ����2��ѯ�ӿڷ��ص�seat_types�Ĳ�����Ϊ����   1 Ӳ�� (A1��ԪΪ��λ)  3 Ӳ�� (A3��ԪΪ��λ) 4 ���� (A4��ԪΪ��λ)
    
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
          "A1": "��43.5",
          "A4": "��141.5",
          "A3": "��94.5",
          "OT": [],
          "WZ": "��43.5",
          "train_no": "240000T1670N"
      },
      "messages": [],
      "validateMessages": {}
    }
    ```

#### Ԥ����Ʊ
1. ����û��Ƿ��¼
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
2. ����Ԥ����Ʊ
  * method: POST
  * url: https://kyfw.12306.cn/otn/leftTicket/submitOrderRequest
  * parameter
  `secretStr=xxx&train_date=2014-11-16&back_train_date=2014-11-20&tour_flag=dc&purpose_codes=ADULT&query_from_station_name=����&query_to_station_name=�Ͼ�&undefined`
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

3. ��ȡ�˿���Ϣ
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
            "passenger_name": "��˼Ȫ",
            "sex_code": "M",
            "sex_name": "��",
            "born_date": "1985-08-29 00:00:00",
            "country_code": "CN",
            "passenger_id_type_code": "1",          
            "passenger_id_type_name": "�������֤",
            "passenger_id_no": "340503198508290637",
            "passenger_type": "1",                        // 1 �������֤  C �۰�ͨ��֤  G ̨��ͨ��֤ B ���� 
            "passenger_flag": "0",
            "passenger_type_name": "����",
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

#### �ύ����
1. �����֤��
  * method: POST
  * url: https://kyfw.12306.cn/otn/passcodeNew/checkRandCodeAnsyn
  * parameters: 
  `randCode=����֤��&rand=randp&_json_att=&REPEAT_SUBMIT_TOKEN=toke��`
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
2. ��鶩����Ϣ (���ѡ��ĳ˿���Ϣ�ĺϷ���)
  * method: POST
  * url: https://kyfw.12306.cn/otn/confirmPassenger/checkOrderInfo
  * parameters:
  `cancel_flag=2&bed_level_order_num=000000000000000000000000000000&passengerTicketStr=O%2C0%2C1%2C%E5%90%B4%E6%80%9D%E6%B3%89%2C1%2C340503198508290637%2C18500238337%2CN&oldPassengerStr=%E5%90%B4%E6%80%9D%E6%B3%89%2C1%2C340503198508290637%2C1_&tour_flag=dc&randCode=xxx&_json_att=&REPEAT_SUBMIT_TOKEN=xxx`
  
  > cancel_flag �� bed_level_order_num ��ֵ�̶� 
  > passengerTicketStr: .seat_type + ",0," + .ticket_type + "," + .name + "," + .id_type + "," + .id_no + .phone_no + "N"                            ��λ���,0,Ʊ����,�˿���,֤������,֤����,�ֻ�����,���泣����ϵ��(Y��N)  
  > oldPassengerStr: .name + "," + .passenger_id_type_code + "," + passenger_id_no + "," + passenger_type + "_"
                      �˿���,֤������,֤����,�˿�����
  > tour_flag: dc(����)
  
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
  
3. ��ȡ��ǰ�г���ʣ��Ʊ�����Ŷ�����
  * method: POST
  * url: https://kyfw.12306.cn/otn/confirmPassenger/getQueueCount
  * parameters:
  `train_date=Tue Nov 18 2014 00:00:00 GMT+0800 (China Standard Time)&train_no=240000G60310&stationTrainCode=G603&seatType=O&fromStationTelecode=BXPtoStationTelecode=SJP&leftTicket=O012850490M0206500869040750020&purpose_codes=00&_json_att=&REPEAT_SUBMIT_TOKEN=xxx`
  * response:
  ```javascript
  {
    "validateMessagesShowId": "_validatorMessage",
    "status": true,
    "httpstatus": 200,
    "data": {
        "count": "1",
        "ticket": "O012850489M0206500869040750020",
        "op_2": "false",
        "countT": "0",
        "op_1": "false"
    },
    "messages": [],
    "validateMessages": {}
  }

  {"validateMessagesShowId":"_validatorMessage","status":true,"httpstatus":200,"data":{"count":"16","ticket":"O055300000M0933000639174800004","op_2":"false","countT":"0","op_1":"true"},"messages":[],"validateMessages":{}}

  // Ŀǰ�Ŷ������Ѿ�������Ʊ����������ѡ������ϯ��򳵴�
  {"validateMessagesShowId":"_validatorMessage","status":true,"httpstatus":200,"data":{"count":"28","ticket":"O055300000M0933000579174800004","op_2":"true","countT":"0","op_1":"true"},"messages":[],"validateMessages":{}}
  

  /*
    ����ticketȥ����ʣ��Ʊ��
  function B(G, F) {
    rt = "";
    seat_1 = -1;
    seat_2 = -1;
    i = 0;
    while (i < G.length) {
        s = G.substr(i, 10);
        c_seat = s.substr(0, 1);
        if (c_seat == F) {
            count = s.substr(6, 4);
            while (count.length > 1 && count.substr(0, 1) == "0") {
                count = count.substr(1, count.length)
            }
            count = parseInt(count);
            if (count < 3000) {
                seat_1 = count
            } else {
                seat_2 = (count - 3000)
            }
        }
        i = i + 10
    }
    if (seat_1 > -1) {
        rt += seat_1
    }
    if (seat_2 > -1) {
        rt += "," + seat_2
    }
    return rt
}
console.log(B("O055300000M0933000489174800002", "M")); // ʣ��һ����

// �����߼�  passengerInfo_js.js
$.ajax({url: ctx + "confirmPassenger/getQueueCount",type: "post",data: {train_date: new Date(orderRequestDTO.train_date.time).toString(),train_no: orderRequestDTO.train_no,stationTrainCode: orderRequestDTO.station_train_code,seatType: limit_tickets[0].seat_type,fromStationTelecode: orderRequestDTO.from_station_telecode,toStationTelecode: orderRequestDTO.to_station_telecode,leftTicket: ticketInfoForPassengerForm.queryLeftTicketRequestDTO.ypInfoDetail,purpose_codes: F,isCheckOrderInfo: G},dataType: "json",success: function(I) {
                        if (I.status) {
                            if (I.data.isRelogin == "Y") {
                                window.location.href = ctx + "login/init?random=" + new Date().getTime()
                            }
                            var J = B(I.data.ticket, limit_tickets[0].seat_type).split(",");
                            H = "�����г���ʣ��" + (limit_tickets[0].seat_type_name).split("��")[0] + "<strong>" + J[0] + "</strong>��";
                            if (J.length > 1) {
                                H += ",����<strong>" + J[1] + "</strong>��"
                            }
                            H += "��";
                            if (I.data.op_2 == "true") {
                                H += '<font color="red">Ŀǰ�Ŷ������Ѿ�������Ʊ����������ѡ������ϯ��򳵴Ρ�</font>';
                                $("#qr_submit_id").hide()
                            } else {
                                if (I.data.countT > 0) {
                                    H += 'Ŀǰ�Ŷ�����<font color="red">' + I.data.countT + "</font>�ˣ�";
                                    H += "<br/>��ȷ��������Ϣ�Ƿ���ȷ�������ȷ�ϡ���ϵͳ��Ϊ���������ϯλ��"
                                }
                            }
                            var K = $("#sy_ticket_num_id");
                            if (K != null) {
                                K.html(H)
                            }
                            doTicketTitleShow(true);
                            renderCheckTickInfo(limit_tickets);
                            y("checkticketinfo_id");
                            if (parseInt(J[0]) > 0 || parseInt(J[1]) > 0) {
                                C()
                            }
                        } else {
                            C()
                        }
                    },error: function(I, K, J) {
                        C();
                        return
                    }})
            } else {
                doTicketTitleShow(true);
                renderCheckTickInfo(limit_tickets);
                y("checkticketinfo_id");
                C()
            }
  */
  ```
#### ȷ�϶���
1. ȷ�϶����Ŷ�
  * method: POST
  * url: https://kyfw.12306.cn/otn/confirmPassenger/confirmSingleForQueue
  * parameters: 
  > passengerTicketStr
  > oldPassengerStr
  > randCode
  > purpose_codes=00
  > key_check_isChange
  > leftTicketStr
  > train_location=P3
  > _json_att
  > REPEAT_SUBMIT_TOKEN
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
2. queryOrderWaitTime
  * method: GET
  * url: https://kyfw.12306.cn/otn/confirmPassenger/queryOrderWaitTime
  * parameters: 
  `random=1415939886105&tourFlag=dc&_json_att=&REPEAT_SUBMIT_TOKEN=e01d5b39887ec5348e87525706582f2b`
  * response:
  ```javascript
 // ��һ��
 {
    "validateMessagesShowId": "_validatorMessage",
    "status": true,
    "httpstatus": 200,
    "data": {
        "queryOrderWaitTimeStatus": true,
        "count": 0,
        "waitTime": 4,
        "requestId": 5938882285874015000,
        "waitCount": 1,
        "tourFlag": "dc",
        "orderId": null
    },
    "messages": [],
    "validateMessages": {}
  }
  
  // �ڶ���
  {
    "validateMessagesShowId": "_validatorMessage",
    "status": true,
    "httpstatus": 200,
    "data": {
        "queryOrderWaitTimeStatus": true,
        "count": 0,
        "waitTime": -1,
        "requestId": 5938882285874015000,
        "waitCount": 0,
        "tourFlag": "dc",
        "orderId": "E752931597"
    },
    "messages": [],
    "validateMessages": {}
  }
  ```
3. ռλ�ɹ���ȡ����
  * method: POST
  * url: https://kyfw.12306.cn/otn/confirmPassenger/resultOrderForDcQueue
  * parameters: 
  `orderSequence_no=E752931597&_json_att=&REPEAT_SUBMIT_TOKEN=e01d5b39887ec5348e87525706582f2b`
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
