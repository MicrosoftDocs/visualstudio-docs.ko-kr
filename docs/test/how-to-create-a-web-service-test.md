---
title: 웹 서비스 테스트 만들기
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67aff3b1486224c93a6a8302feb96caea91afcff
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287898"
---
# <a name="how-to-create-a-web-service-test"></a>방법: 웹 서비스 테스트 만들기

웹 성능 테스트를 사용하여 웹 서비스를 테스트할 수 있습니다. **요청 삽입** 및 **웹 서비스 요청 삽입** 옵션을 사용하면 **웹 성능 테스트 편집기**에서 개별 요청을 사용자 지정하여 웹 서비스 페이지를 찾을 수 있습니다. 일반적으로 이러한 페이지는 웹 애플리케이션에 표시되지 않습니다. 따라서 이러한 페이지에 액세스하려면 요청을 사용자 지정해야 합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

다음 절차에서는 Commerce 시작 키트 내에 포함된 웹 서비스를 사용합니다. [ASP.NET Commerce 시작 키트](https://sourceforge.net/projects/ppcsk/)에서 다운로드할 수 있습니다.

**요구 사항**

Visual Studio Enterprise

## <a name="to-test-a-web-service"></a>웹 서비스를 테스트하려면

1. 새 웹 성능 테스트를 만듭니다. 브라우저가 열리면 바로 **중지**를 선택합니다.

2. **웹 성능 테스트 편집기**에서 웹 성능 테스트를 마우스 오른쪽 단추로 클릭한 다음, **웹 서비스 요청 추가**를 선택합니다.

3. 새 요청의 **Url** 속성에 **http://localhost/storecsvs/InstantOrder.asmx** 와 같은 웹 서비스 이름을 입력합니다.

4. 별도의 브라우저 세션을 열고 **주소** 도구 모음에 *.asmx* 페이지의 URL을 입력합니다. 테스트할 방법을 선택하고 SOAP 메시지를 검사합니다. SOAP 메시지에 `SOAPAction`이 있습니다.

5. **웹 성능 테스트 편집기**에서 요청을 마우스 오른쪽 단추로 클릭한 다음, **머리글 추가**를 선택하여 새 머리글을 추가합니다. **이름** 속성에 `SOAPAction`을 입력합니다. **값** 속성에 `SOAPAction`에 표시되는 `"http://tempuri.org/CheckStatus"`와 같은 값을 입력합니다.

6. 편집기에서 URL 노드를 확장한 다음, **문자열 본문** 노드를 선택하고 **콘텐츠 형식** 속성에 `text/xml` 값을 입력합니다.

7. 4단계의 브라우저로 돌아가서 웹 서비스 설명 페이지에서 SOAP 요청의 XML 부분을 선택하여 클립보드에 복사합니다.

8. XML 내용은 다음 예제와 비슷합니다.

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
     <soap:Body>
       <CheckStatus xmlns="http://tempuri.org/">
         <userName>string</userName>
         <password>string</password>
         <orderID>int</orderID>
       </CheckStatus>
     </soap:Body>
     </soap:Envelope>
     ```

9. **웹 성능 테스트 편집기**로 돌아가서 **문자열 본문** 속성의 줄임표 **(…)** 를 선택합니다. 클립보드의 내용을 속성에 붙여넣습니다.

10. 테스트가 성공하려면 XML에서 자리 표시자 값을 유효한 값으로 바꿔야 합니다. 앞의 예제에서 `string`의 두 인스턴스와 한 `int`를 바꿨을 것입니다. 이 웹 서비스 작업은 요청한 사용자가 등록되어 있는 경우에만 완료됩니다.

11. 웹 서비스 요청을 마우스 오른쪽 단추로 클릭한 다음, **URL QueryString 매개 변수 추가**를 선택합니다.

12. 쿼리 문자열 매개 변수에 이름과 값을 할당합니다. 앞의 예제에서 이름은 `op`이고 값은 `CheckStatus`입니다. 이러한 이름과 값은 수행할 웹 서비스 작업을 식별합니다.

    > [!NOTE]
    > SOAP 본문에서 데이터 바인딩을 사용하면 `{{DataSourceName.TableName.ColumnName}}` 구문을 사용하여 자리 표시자 값을 데이터 바인딩 값으로 바꿀 수 있습니다.

13. 테스트를 실행합니다. **웹 성능 테스트 결과 뷰어**의 위쪽 창에서 웹 서비스 요청을 선택합니다. 아래쪽 창에서 [웹 브라우저] 탭을 선택합니다. 웹 서비스에서 반환되는 XML및 작업 결과가 표시됩니다.

## <a name="see-also"></a>참조

- [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)
