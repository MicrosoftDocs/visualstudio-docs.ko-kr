---
title: 웹 서비스 테스트 만들기
ms.date: 06/30/2020
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9934f48e6d5900a418995eb96d357b4ea1ea532f
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814761"
---
# <a name="how-to-create-a-web-service-test"></a>방법: 웹 서비스 테스트 만들기

웹 성능 테스트를 사용하여 웹 서비스를 테스트할 수 있습니다. **요청 삽입** 및 **웹 서비스 요청 삽입** 옵션을 사용하면 **웹 성능 테스트 편집기**에서 개별 요청을 사용자 지정하여 웹 서비스 페이지를 찾을 수 있습니다. 일반적으로 이러한 페이지는 웹 애플리케이션에 표시되지 않습니다. 따라서 이러한 페이지에 액세스하려면 요청을 사용자 지정해야 합니다.

>[!NOTE]
> Visual Studio 2019에서는 웹 성능 및 부하 테스트 기능이 사용되지 않습니다. Application Insights의 경우 다단계 웹 테스트는 Visual Studio 웹 테스트 파일에 따라 달라집니다. Visual Studio 2019가 웹 테스트 기능을 사용하는 마지막 버전이 될 것이라고 [발표](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/)했습니다. 새 기능이 추가되는 것은 아니지만 Visual Studio 2019의 웹 테스트 기능은 현재 지원되며 제품의 지원 수명 주기 동안 계속 지원된다는 점을 이해해야 합니다. Azure Monitor 제품 팀은 [여기](https://github.com/MicrosoftDocs/azure-docs/issues/26050#issuecomment-468814101)에서 다단계 단계 가용성 테스트의 미래와 관련된 질문을 해결했습니다.

**요구 사항**

Visual Studio Enterprise

## <a name="to-create-a-simple-web-service"></a>간단한 웹 서비스를 만들려면

테스트하는 데는 고유한 웹 서비스를 사용하거나 Visual Studio에 포함된 기본 웹 서비스(ASMX) 템플릿을 사용할 수 있습니다. 이 템플릿을 사용하여 간단한 웹 서비스를 만들려면:

1. Visual Studio에서 ASP.NET 웹 애플리케이션(.NET Framework) 템플릿을 사용하여 새 프로젝트를 만들고 메시지가 표시되면 **빈** 템플릿을 선택합니다. 이름을 입력하고 프로젝트를 만듭니다.

1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고, **추가** > **새 항목**을 선택한 다음, **웹 서비스(ASMX)** 를 선택합니다. 웹 서비스를 추가합니다.

1. *WebService1.asmx*를 열고 기본 `HelloWorld` 웹 방식을 다음 코드로 바꿉니다.

   ```csharp
   public string HelloWorld(string str)
   {
      return "Hello, " + str;
   }
   ```

## <a name="install-the-load-testing-component"></a>부하 테스트 구성 요소 설치

웹 성능 및 부하 테스트 도구 구성 요소를 아직 설치하지 않은 경우 Visual Studio 설치 관리자를 통해 설치해야 합니다.

1. Windows **시작** 메뉴에서 **Visual Studio 설치 관리자**를 엽니다. 새 프로젝트 대화 상자에서 Visual Studio로 액세스하거나 메뉴 모음에서 **도구** > **도구 및 기능 가져오기**를 선택하여 액세스할 수도 있습니다.

1. **Visual Studio 설치 관리자**에서 **개별 구성 요소** 탭을 선택하고 **디버깅 및 테스트** 섹션까지 아래로 스크롤합니다. **웹 성능 및 부하 테스트 도구**를 선택합니다.

   ![웹 성능 및 부하 테스트 도구 구성 요소](media/web-perf-load-testing-tools-component.png)

1. **수정** 단추를 선택합니다.

   웹 성능 및 부하 테스트 도구 구성 요소가 설치됩니다.

## <a name="create-a-web-test-project"></a>웹 테스트 프로젝트 만들기

웹 테스트에는 웹 성능 및 부하 테스트 프로젝트 템플릿이 필요합니다. 이 섹션에서는 C# 부하 테스트 프로젝트를 만듭니다. 원하는 경우 Visual Basic 부하 테스트 프로젝트를 만들 수도 있습니다.

::: moniker range="vs-2017"

1. Visual Studio를 엽니다.

   샘플 웹 서비스(ASMX) 템플릿을 사용하는 경우 동일한 솔루션에 웹 테스트 프로젝트를 추가할 수 있습니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

   **새 프로젝트** 대화 상자가 열립니다.

3. **새 프로젝트** 대화 상자에서 **설치됨** 및 **Visual C#** 을 확장한 다음, **테스트** 범주를 선택합니다. **웹 성능 및 부하 테스트 프로젝트** 템플릿을 선택합니다.

   ![웹 성능 및 부하 테스트 프로젝트 템플릿](media/web-perf-load-test-project-template.png)

4. 기본 이름을 사용하지 않으려면 프로젝트의 이름을 입력한 다음, **확인**을 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio를 엽니다.

   샘플 웹 서비스(ASMX) 템플릿을 사용하는 경우 동일한 솔루션에 웹 테스트 프로젝트를 추가할 수 있습니다.

2. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

3. **새 프로젝트 만들기** 페이지에서 검색 상자에 **웹 테스트**를 입력하고 C#용 **웹 성능 및 부하 테스트 프로젝트\[사용되지 않음]** 템플릿을 선택합니다. **다음**을 선택합니다.

4. 기본 이름을 사용하지 않으려면 프로젝트의 이름을 입력하고 **만들기**를 선택합니다.

::: moniker-end

   Visual Studio에서 프로젝트를 만들고 **솔루션 탐색기**에 파일을 표시합니다. 프로젝트는 초기에 *WebTest1.webtest*라는 웹 테스트 파일을 포함합니다.

## <a name="to-test-a-web-service"></a>웹 서비스를 테스트하려면

1. 웹 서비스를 시작하고 필요한 경우 **중지**를 선택하여 서비스를 일시 중지합니다.

1. 웹 테스트 프로젝트에서 *WebTest1.webtest*를 엽니다. 그러면 웹 성능 테스트 편집기가 열립니다. 테스트 편집기에서 웹 성능 테스트를 마우스 오른쪽 단추로 클릭하고 **웹 서비스 요청 추가**를 선택합니다.

1. 새 요청의 **Url** 속성에 **https://localhost:44318/WebService1.asmx** 와 같은 웹 서비스 이름을 입력합니다.

1. 웹 서비스의 경우 별도의 브라우저 세션을 열고 **주소** 도구 모음에 *.asmx* 페이지의 URL을 입력합니다. 웹 페이지 위쪽에서 테스트할 메서드를 선택하고 SOAP 메시지를 검사합니다. (예제 웹 서비스에서 메서드는 HelloWorld입니다.) 해당 메서드를 열면 `SOAPAction`이 포함된 것을 알 수 있습니다.

1. **웹 성능 테스트 편집기**에서 요청을 마우스 오른쪽 단추로 클릭한 다음, **머리글 추가**를 선택하여 새 머리글을 추가합니다. **이름** 속성에 `SOAPAction`을 입력합니다. **값** 속성에 `SOAPAction`에 표시되는 *http://tempuri.org/HelloWorld* 와 같은 값을 입력합니다.

1. 테스트 편집기에서 URL 노드를 확장한 다음, **문자열 본문** 노드를 선택하고 **콘텐츠 형식** 속성에 `text/xml` 값을 입력합니다.

1. 4단계의 브라우저로 돌아가서 웹 서비스 설명 페이지에서 SOAP 요청의 XML 부분을 선택하여 클립보드에 복사합니다.

   XML 내용은 다음 예제와 비슷합니다.

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
       <soap:Body>
         <HelloWorld xmlns="http://tempuri.org/">
           <str>string</str>
         </HelloWorld>
       </soap:Body>
     </soap:Envelope>
     ```

1. 웹 성능 테스트 편집기로 돌아가서 **문자열 본문** 속성의 줄임표 **(…)** 를 선택합니다. 클립보드의 내용을 속성에 붙여넣습니다.

1. 테스트가 성공할 수 있도록 XML에서 자리 표시자 값을 유효한 값으로 바꿉니다. 이전 예제에서는 `string`의 인스턴스를 이름으로 바꿉니다.

1. 웹 서비스 요청을 마우스 오른쪽 단추로 클릭한 다음, **URL QueryString 매개 변수 추가**를 선택합니다.

1. 쿼리 문자열 매개 변수에 이름과 값을 할당합니다. 앞의 예제에서 이름은 `op`이고 값은 `HelloWorld`입니다. 이러한 이름과 값은 수행할 웹 서비스 작업을 식별합니다.

    > [!NOTE]
    > SOAP 본문에서 데이터 바인딩을 사용하면 `{{DataSourceName.TableName.ColumnName}}` 구문을 사용하여 자리 표시자 값을 데이터 바인딩 값으로 바꿀 수 있습니다.

1. 테스트를 실행합니다. **웹 성능 테스트 결과 뷰어**의 위쪽 창에서 웹 서비스 요청을 선택합니다. 아래쪽 창에서 **웹 브라우저** 탭을 선택합니다. 웹 서비스에서 반환되는 XML및 작업 결과가 표시됩니다.

   웹 서비스 요청의 결과를 찾습니다.

## <a name="see-also"></a>참조

- [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)
