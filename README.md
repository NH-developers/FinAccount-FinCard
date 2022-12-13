# fincard/finaccount
시작하기 API
## 1 소개
### 핀-어카운트  
계좌정보가 필요한 경우, 계좌번호 보호를 위해 계좌번호의 매칭 핀번호(핀-어카운트)를 발급하여 사용하는 서비스입니다.  
프로세스는 ARS를 이용한 고객 확인 후 발급>발급확인>해지>해지확인으로 이루어집니다.
#### 핀-어카운트 NH API 목록
| 전문명 | API |
|:---:|:---:|
| 핀-어카운트 직접발급 | OpenFinAccountDirect |
| 핀-어카운트 직접발급 확인 | CheckOpenFinAccountDirect |

### 핀-카드
카드번호가 필요한 경우, 카드번호 보호를 위해 카드번호의 매칭 핀번호(핀-카드)를 발급하여 사용하는 서비스입니다.
#### 핀-카드 NH API 목록
| 전문명 | API |
|:---:|:---:|
| 핀-카드 직접발급 |	OpenFinCardDirect |	
|핀-카드 직접발급확인 |	CheckOpenFinCardDirect |

## 2 resource url
#### 2.1 핀어카운트 직접발급 
https://developers.nonghyup.com/OpenFinAccountDirect.nh
#### 2.2 핀어카운트 직접발급 확인
https://developers.nonghyup.com/CheckOpenFinAccountDirect.nh
#### 2.3 핀카드 직접발급
https://developers.nonghyup.com/OpenFinCardDirect.nhh
#### 2.4 핀카드 직접발급 확인
https://developers.nonghyup.com/CheckOpenFinCardDirect.nh

## 3 example
API공통부  
기본정보  
요청 : API 전문 요청 시, 공통부의 Header와 함께 요청값을 전송합니다.  
응답 : API 전문 응답 시, 공통부의 Header와 함께 응답값을 전송합니다.
### 공통부 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---:|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||
| ApiNm |	API명 |	필드 |	100 |	필수 |	테스트API명 |  
| Tsymd	| 전송일자 |	필드 |	8 |	필수 |	API 호출일자 (YYYYMMDD) , 테스트일로 변경 |
| Trtm |	전송시각 |	필드 |	6 |	필수 |	API 전송시각 (HHMMSS), 테스트시각으로 변경 |
| Iscd |	기관코드 |	필드 |	6 |	필수 |	-기관약정 시 발급된 ‘핀테크 기관코드’를 말함-“마이페이지 > 서비스 관리 > 기관코드” 로 변경 |
| FintechApsno |	핀테크 앱 일련번호 |	필드 |	3 | 필수 |	-핀테크서비스 약정 시 발급된 ‘핀테크 앱 일련번호’-테스트 과정에서는 ‘001’로 고정되며 핀테크 서비스 약정시 발급된 ‘핀테크 앱 일련번호’로 교체해야 함 |
| APISvcCd |	API서비스코드 |	필드 |	20 |	필수 |	-핀테크서비스 약정 시 신청한 ‘API 서비스 코드’-테스트과정에서는 ‘DrawingTransferA’로 고정되면 핀테크 서비스 약성시 발급된 ‘핀테크 API서비스코드’로 교체해야 함 |
| Istuno |	기관거래고유번호 |	필드 |	20 |	필수 |	-핀테크서비스별 & 전송일자별 거래고유번호 채번 -테스트과정에서는 API요청시 사용자가 항상 새로운 번호로 임의 채번해야함. (예 : 000000, 000001 …)|
| AccessToken |	인증키 |	필드 |	64 |	필수 |	“마이페이지 > 서비스 관리 > 인증키” 로 변경 |
### 공통부 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---:|:---:|:---:|:---:|:---:|:---|  
| Header || 공통부 |||||
| ApiNm |	API명 |	필드 |	100 |	필수 |	테스트API명 |  
| Tsymd	| 전송일자 |	필드 |	8 |	필수 |	API 호출일자 (YYYYMMDD) , 테스트일로 변경 |
| Trtm |	전송시각 |	필드 |	6 |	필수 |	API 전송시각 (HHMMSS), 테스트시각으로 변경 |
| Iscd |	기관코드 |	필드 |	6 |	필수 |	기관약정 시 발급된 ‘핀테크 기관코드’를 말함 “마이페이지 > 서비스 관리 > 기관코드” 로 변경 |
| FintechApsno |	핀테크 앱 일련번호 |	필드 |	3 | 필수 |	-핀테크서비스 약정 시 발급된 ‘핀테크 앱 일련번호’-테스트 과정에서는 ‘001’로 고정되며 핀테크 서비스 약정시 발급된 ‘핀테크 앱 일련번호’로 교체해야 함 |
| APISvcCd |	API서비스코드 |	필드 |	20 |	필수 |	-핀테크서비스 약정 시 신청한 ‘API 서비스 코드’-테스트과정에서는 ‘DrawingTransferA’로 고정되면 핀테크 서비스 약성시 발급된 ‘핀테크 API서비스코드’로 교체해야 함 |
| Istuno |	기관거래고유번호 |	필드 |	20 |	필수 |	-핀테크서비스별 & 전송일자별 거래고유번호 채번 -테스트과정에서는 변경안해도 됨|
| AccessToken |	인증키 |	필드 |	64 |	필수 |	“마이페이지 > 서비스 관리 > 인증키” 로 변경 |
| Rpcd |	응답코드 |	필드 |	5 |	필수 | |	 
| Rsms |	응답메세지 |	필드 |	100 |	필수 | |	 
| Rgno	| 등록번호 |	필드 |	20 |	필수 | |
### 3.1.1 핀어카운트 직접발급 Request example
```json
{
    "Header": {
        "ApiNm": "OpenFinAccountDirect",
        "Tsymd": "20191129",
        "Trtm": "113604",
        "Iscd": "900001",
        "FintechApsno": "001",
        "ApiSvcCd": "DrawingTransferA",
        "IsTuno": "201911290000000001",
        "AccessToken": "6500e3a81fe2deafd996ea437b6a4b7cfbd04a3ab7e26480b431fdf3ccf3b39b"
    },
    "DrtrRgyn": "Y",
    "BrdtBrno": "20191029",
    "Bncd": "011",
    "Acno": "3020000000039" 
}
```
### 3.1.2 핀어카운트 직접발급 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---:|:---:|:---:|:---:|:---:|:---:|  
| Header || 공통부 |||||	 
| DrtrRgyn |	출금이체 등록 여부 | 	필드 |	1 |	필수 |	Y:등록, N:미등록 |
| BrdtBrno |	생년월일(사업자번호) |	필드 |	10 |	필수 |	개인:YYYYMMDD 기업:사업자번호 |
| Bncd |	은행코드 |	필드 |	3 |	필수 |	농협은행:011, 상호금융:012 |
| Acno |	계좌번호 |	필드 |	20 |	필수 |	NH농협 계좌에 대해서만 발급 가능 |
### 3.1.3 핀어카운트 직접발급 Response example
```json
{
    "Header": {
        "Trtm": "003544",
        "Rsms": "정상처리 되었습니다.",
        "ApiNm": "OpenFinAccountDirect",
        "IsTuno": "201911290000000001",
        "Tsymd": "20191101",
        "FintechApsno": "001",
        "Iscd": "900001",
        "Rpcd": "00000",
        "ApiSvcCd": "DrawingTransferA"
    },
    "Rgno": "20191124000000249"
}
```
### 3.1.4 핀어카운트 직접발급 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---:|:---:|:---:|:---:|:---:|:---:|  
| Header || 공통부 |||||	 
| Rgno |	등록번호 |	필드 |	20 |	필수 |
### 3.2.1 핀어카운트 직접발급 확인 Request example
```json
{	
  "Header":{
    "ApiNm":"CheckOpenFinAccountDirect",
    "Tsymd":"20191129",
    "Trtm":"003544",
    "Iscd":"900001",
    "FintechApsno":"001",
    "ApiSvcCd":"DrawingTransferA",
    "IsTuno":"201911240000000001",
    "AccessToken": "6500e3a81fe2deafd996ea437b6a4b7cfbd04a3ab7e26480b431fdf3ccf3b39b"
  },
  "Rgno":"20191030000000021",
  "BrdtBrno":"20191029" 
}
```
### 3.2.2 핀어카운트 직접발급 확인 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---:|:---:|:---:|:---:|:---:|:---:|  
| Header || 공통부 |||||	 
| Rgno |	등록번호 |	필드 |	50 |	필수 |	 
| BrdtBrno |	생년월일(사업자번호) |	필드 |	10 |	필수 |	개인:YYYYMMDD 기업:사업자번호 |
### 3.2.3 핀어카운트 직접발급 확인 Response example
```json
{	
    "Header": {
        "Trtm": "003544",
        "Rsms": "정상처리 되었습니다.",
        "ApiNm": "CheckOpenFinCardDirect",
        "IsTuno": "201911240000000001",
        "Tsymd": "20191129",
        "FintechApsno": "001",
        "Iscd": "900001",
        "Rpcd": "00000",
        "ApiSvcCd": "DrawingTransferA"
    },
    "FinAcno": "00820100000190001639",
    "RgsnYmd": "20191124"
}
```
### 3.2.4 핀어카운트 직접발급 확인 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---:|:---:|:---:|:---:|:---:|:---:|  
| Header || 공통부 |||||	
| FinAcno |	핀-어카운트 |	필드 |	30 |	필수 |	 
| RgsnYmd |	등록일자 |	필드 |	8	| 필수 |	
### 3.3.1 핀카드 직접발급 Request example
```json
{	
    "Header":{
        "ApiNm":"OpenFinCardDirect",
        "Tsymd":"20191129",
        "Trtm":"003544",
        "Iscd":"900001",
        "FintechApsno":"001",
        "ApiSvcCd":"DrawingTransferA",
        "IsTuno":"201911290000000001",
        "AccessToken": "6500e3a81fe2deafd996ea437b6a4b7cfbd04a3ab7e26480b431fdf3ccf3b39b"
    },
"Brdt":"20191029",
"Cano":"9411123456782718" 
}
```
### 3.3.2 핀카드 직접발급 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---:|:---:|:---:|:---:|:---:|:---:|  
| Header || 공통부 |||||	 
| Brdt |	생년월일 |	필드 |	8 |	필수 |	YYYYMMDD |
| Cano |	카드번호 |	필드 |	16 | 	필수 |	 
### 3.3.3 핀카드 직접발급 Response example
```json
{
    "Header": {
        "Trtm": "003544",
        "Rsms": "정상처리 되었습니다.",
        "ApiNm": "OpenFinCardDirect",
        "IsTuno": "201911290000000001",
        "Tsymd": "20191129",
        "FintechApsno": "001",
        "Iscd": "900001",
        "Rpcd": "00000",
        "ApiSvcCd": "DrawingTransferA"
    },
    "Rgno": "20191124000000251"
}
```
### 3.3.4 핀카드 직접발급 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---:|:---:|:---:|:---:|:---:|:---:|  
| Header || 공통부 |||||	
| Rgno |	등록번호 |	필드 |	20 |	필수 |
### 3.4.1 핀카드 직접발급 확인 Request example
```json
{
    "Header":{
        "ApiNm":"CheckOpenFinCardDirect",
        "Tsymd":"20191129",
        "Trtm":"003544",
        "Iscd":"900001",
        "FintechApsno":"001",
        "ApiSvcCd":"DrawingTransferA",
        "IsTuno":"201911290000000001",
        "AccessToken": "6500e3a81fe2deafd996ea437b6a4b7cfbd04a3ab7e26480b431fdf3ccf3b39b"
    },
  "Rgno":"20191101000000057",
  "Brdt":"20191029" 
}
```
### 3.4.3 핀카드 직접발급 Request Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---:|:---:|:---:|:---:|:---:|:---:|  
| Header || 공통부 |||||	
| Rgno |	등록번호 |	필드 |	20 |	필수 | |	 
| Brdt |	생년월일 |	필드 |	8 |	필수 |	YYYYMMDD |
### 3.4.3 핀카드 직접발급 확인 Response example
```json
{	
    "Header": {
        "Trtm": "003544",
        "Rsms": "정상처리 되었습니다.",
        "ApiNm": "CheckOpenFinCardDirect",
        "IsTuno": "201911290000000001",
        "Tsymd": "20191129",
        "FintechApsno": "001",
        "Iscd": "900001",
        "Rpcd": "00000",
        "ApiSvcCd": "DrawingTransferA"
    },
    "FinCard": "00820100000190001620",
    "RgsnYmd": "20191124"
}
```
### 3.4.4 핀카드 직접발급 Response Element
| Element |	한글명 | Type |	Length |	optional |	Description |  
|:---:|:---:|:---:|:---:|:---:|:---:|  
| Header || 공통부 |||||	
| FinCard |	핀-카드 | 	필드 |	30 |	필수 |
| RgsnYmd |	등록일자 |	필드 |	8 |	필수 |
