---
title: 코딩된 웹 성능 테스트
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, creating
- code, Web performance tests
- Web performance tests, coded
ms.assetid: 169e48f9-52fd-4d0b-83d9-54913bde506b
dev_langs:
- CSharp
- VB
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4297f60c74e32b904d7c36912a8377d33f23ebdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75589580"
---
# <a name="generate-and-run-a-coded-web-performance-test"></a>코딩된 웹 성능 테스트 생성 및 실행

웹 성능 테스트는 사용자의 웹 응용 프로그램을 탐색하여 기록됩니다. 테스트는 부하 테스트에 포함되어 여러 사용자의 스트레스 환경에서 웹 애플리케이션의 성능을 측정합니다. 웹 성능 테스트는 코드 기반 스크립트로 변환한 후에 다른 소스 코드처럼 편집하고 사용자 정의할 수 있습니다. 예를 들어, 루프 및 분기 구문을 추가할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="generate-a-coded-web-performance-test"></a>코딩된 웹 성능 테스트 생성

1. 웹 성능 테스트를 만들지 않은 경우 [웹 성능 테스트 기록](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-web-performance-and-load-test-project)을 참조하세요.

2. 코딩된 테스트를 생성합니다.

     ![코딩된 웹 성능 테스트 생성](../test/media/web_test_coded_generate.png)

3. 테스트 이름을 지정합니다.

     ![코딩된 웹 성능 테스트의 이름 입력](../test/media/web_test_coded_generate_nametest.png)

     새로 코딩된 테스트가 코드 편집기에서 열립니다.

     솔루션에 추가한 웹 성능 및 부하 테스트 프로젝트 템플릿에 따라 Visual C# 또는 Visual Basic에서 코드가 생성됩니다.

     ![새 코딩된 테스트가 코드 편집기에서 열립니다.](../test/media/web_test_coded_generate_opencodeeditor.png)

     C#의 GetRequestEnumerator() 메서드 또는 Visual Basic의 Run() 메서드에 기록된 테스트에 있는 각 유효성 검사 규칙 및 웹 요청이 포함된다는 것을 코드에서 볼 수 있습니다.

4. 몇 가지 간단한 코드를 추가하는 방법을 보여주기 위해, 메서드 끝부분으로 스크롤하고 마지막 웹 요청에 대한 코드 뒤에서 다음 코드를 추가합니다.

    ```c#
    if (DateTime.Today.DayOfWeek == DayOfWeek.Wednesday)
    {
        WebTestRequest customRequest = new WebTestRequest("http://weather.msn.com/");
        yield return customRequest;
    }
    else
    {
        WebTestRequest customRequest = new WebTestRequest("https://msdn.microsoft.com/");
        yield return customRequest;
    }
    ```

    ```vb
    If DateTime.Today.DayOfWeek = DayOfWeek.Wednesday Then
        Dim customRequest As WebTestRequest = New WebTestRequest("http://weather.msn.com/")
        MyBase.Send(customRequest)
    Else
        Dim customRequest As WebTestRequest = New WebTestRequest("https://msdn.microsoft.com/")
        MyBase.Send(customRequest)
    End If
    ```

5. 사용자 지정 코드가 컴파일되는지 확인하려면 솔루션을 빌드합니다.

6. 테스트를 실행합니다.

     ![코딩된 웹 성능 테스트 실행](../test/media/web_test_coded_generate_run.png)

     테스트 실행일이 수요일이었으므로…

     ![코딩된 웹 성능 테스트 결과](../test/media/web_test_coded_generate_results.png)

## <a name="qa"></a>Q&A

### <a name="q-can-i-run-more-than-one-test-at-a-time"></a>Q: 두 개 이상의 테스트를 동시에 실행할 수 있습니까?
**A:** 예. **솔루션 탐색기**에서 오른쪽 클릭(상황에 맞는) 메뉴를 사용합니다.

### <a name="q-should-i-add-a-data-source-before-or-after-i-generate-a-coded-test"></a>Q: 코딩된 테스트를 생성하기 전이나 후에 데이터 소스를 추가해야 합니까?
**A:** 코드는 자동으로 생성되므로 코딩된 테스트를 생성하기 전에 [데이터 원본](../test/add-a-data-source-to-a-web-performance-test.md)으로 쉽게 추가할 수 있습니다.

데이터 소스로 코딩된 테스트를 실행하면 다음과 같은 오류 메시지가 표시될 수 있습니다.

**\<Computer Name> 에이전트에서 \<Test Name>을 테스트할 수 없음: 개체 참조가 개체의 인스턴스로 설정되지 않았습니다.**

이 오류는 해당하는 DataBindingAttribute 없이 테스트 클래스에 DataSourceAttribute를 정의한 경우에 발생할 수 있습니다. 이 오류를 해결하려면 적절한 DataBindingAttribute를 추가하고, 이를 삭제하거나 코드에서 주석 처리합니다.

### <a name="q-should-i-add-validation-and-extraction-rules-before-or-after-i-generate-a-coded-test"></a>Q: 코딩된 테스트를 생성하기 전이나 후에 유효성 검사 및 추출 규칙을 추가해야 합니까?
**A:** 코딩된 테스트를 생성하기 전에 유효성 검사 규칙과 추출 규칙을 추가하기 쉽지만 유효성 검사에는 [코딩된 UI 테스트](../test/use-ui-automation-to-test-your-code.md)를 사용하는 것이 좋습니다.
