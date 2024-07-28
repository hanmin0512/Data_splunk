# Data_splunk
log데이터를 splunk로 분석해 보기

## 데이터 업로드
- 설정 > 데이터 추가 > 업로드 > 파일 선택
- [아파치 로그파일]로그파일 추가
> ![image](https://github.com/hanmin0512/Data_splunk/assets/37041208/3e2ca7a4-7e12-4624-b0e4-24dabef13f3c)
- 다음
- Source type : access_combined으로 설정 되었는지 확인
> ![image](https://github.com/hanmin0512/Data_splunk/assets/37041208/f870375a-5512-471e-a174-edadf203db9d)
- 다음 > 새 인덱스 만들기
> ![image](https://github.com/hanmin0512/Data_splunk/assets/37041208/4f38dfd4-5023-4e14-aef8-d54a3ae365a2)
- 검토 > 제출 > 검색 시작

## 데이터 가공
- uri 필드의 데이터의 끝 부분을 가져와 file_1필드를 만들어보기.
- 아래 명령어는 git_apache 인덱스에서 uri필드의 .../(~) 이부분중 괄호로 감싼 부분을 가져와 file_1필드에 값을 넣겠다 라는 뜻이다.
```
index="git_apache" 
| eval file_1=replace(uri,".*\/(.)","\1")
```
> ![image](https://github.com/hanmin0512/Data_splunk/assets/37041208/829522f2-783a-4a55-99b8-3e614e384e3f)

> ![image](https://github.com/hanmin0512/Data_splunk/assets/37041208/e0b84bd7-0182-48b5-a4c4-97a9fd4442fe)

## 기간 별 status 필드 값 400 발생량 확인하기.
```
index="git_apache" status=400
| timechart count by status
```
> ![image](https://github.com/hanmin0512/Data_splunk/assets/37041208/7771d663-46ff-440d-96ce-94c81299352f)

## 기간별 특정ip 로그 발생 수 확인하기
```
index="git_apache"  clientip="128.30.28.58"
| timechart count by clientip
```
> ![image](https://github.com/hanmin0512/Data_splunk/assets/37041208/5bfb418e-cbf4-4252-8c35-5b9fdc2198b9)





===========
===========

<img width="660" alt="스크린샷 2024-07-28 오후 2 28 04" src="https://github.com/user-attachments/assets/14bf6a6d-f015-4129-85cf-4889f8b0a1be">
<img width="1115" alt="스크린샷 2024-07-28 오후 2 28 43" src="https://github.com/user-attachments/assets/592694f7-81fd-4430-8e54-7e986e8c2b62">
<img width="1472" alt="스크린샷 2024-07-28 오후 2 29 15" src="https://github.com/user-attachments/assets/5e13dbd2-b59b-4b25-b93d-65a98a638eff">



