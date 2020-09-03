---
title: 웹 성능 테스트 API
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14b7320a38d474748713d687f4ee00b5b91f0208
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287079"
---
# <a name="how-to-use-the-web-performance-test-api"></a>방법: 웹 성능 테스트 API 사용

웹 성능 테스트에 대한 코드를 작성할 수 있습니다. 웹 성능 테스트 API를 사용하여 코딩된 웹 성능 테스트, 웹 성능 테스트 플러그 인, 요청 플러그 인, 요청, 추출 규칙 및 유효성 검사 규칙을 만들 수 있습니다. 이러한 형식을 구성하는 클래스는 이 API의 핵심 클래스입니다. 이 API의 다른 형식은 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> 및 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> 개체 만들기를 지원하는 데 사용됩니다. <xref:Microsoft.VisualStudio.TestTools.WebTesting> 네임스페이스를 사용하여 사용자 지정 웹 성능 테스트를 만듭니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

또한 웹 성능 테스트 API를 사용하여 프로그래밍 방식으로 선언적 웹 성능 테스트를 만들고 저장할 수도 있습니다. 이렇게 하려면 <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> 및 <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer> 클래스를 사용합니다.

> [!TIP]
> 개체 브라우저를 사용하여 <xref:Microsoft.VisualStudio.TestTools.WebTesting> 네임스페이스를 검사합니다. Visual C# 및 Visual Basic 편집기는 모두 네임스페이스의 클래스를 사용하여 코딩하기 위한 IntelliSense 지원을 제공합니다.

부하 테스트에 대한 플러그 인도 만들 수 있습니다. 자세한 내용은 [방법: 부하 테스트 API 사용](../test/how-to-use-the-load-test-api.md) 및 [방법: 부하 테스트 플러그 인 만들기](../test/how-to-create-a-load-test-plug-in.md)를 참조하세요.

## <a name="to-use-the-webtesting-namespace"></a>WebTesting 네임스페이스를 사용하려면

1. 웹 성능 테스트가 포함된 웹 성능 및 부하 테스트 프로젝트를 엽니다.

2. 테스트 솔루션에 Visual C# 또는 Visual Basic 클래스 라이브러리 프로젝트를 추가합니다.

3. 클래스 라이브러리 프로젝트에 웹 성능 및 부하 테스트 프로젝트의 참조를 추가합니다.

4. 클래스 라이브러리 프로젝트에 Microsoft.VisualStudio.QualityTools.WebTestFramework DLL에 대한 참조를 추가합니다.

5. 클래스 라이브러리 프로젝트에 있는 클래스 파일에 `using` 네임스페이스에 대한 <xref:Microsoft.VisualStudio.TestTools.WebTesting> 문을 추가합니다.

6. <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> 인터페이스를 구현하는 클래스를 만듭니다.

7. 프로젝트를 빌드합니다.

8. 웹 성능 테스트 편집기를 사용하여 새 웹 성능 테스트 플러그 인을 추가합니다.

    1. 도구 모음의 **웹 테스트 플러그 인 추가**를 선택합니다.

         **웹 테스트 플러그 인 추가** 대화 상자가 표시됩니다.

    2. **플러그 인 선택**에서 웹 성능 테스트 플러그 인 클래스를 선택합니다.

    3. **선택한 플러그 인에 대한 속성** 창에서 런타임에 사용할 플러그 인의 초기 값을 설정합니다.

        > [!NOTE]
        > 플러그 인에서 속성을 원하는 만큼 노출할 수 있습니다. 속성을 공용이고 설정 가능한 기본 형식(정수, 부울 또는 문자열 등)으로 지정하기만 하면 됩니다. 나중에 [속성] 창을 사용하여 웹 성능 테스트 플러그 인 속성을 편집할 수도 있습니다.

    4. **확인**을 선택합니다.

9. 웹 성능 테스트를 실행합니다.

     <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>의 예제 구현은 [방법: 웹 성능 테스트 플러그 인 만들기](../test/how-to-create-a-web-performance-test-plug-in.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [방법: 부하 테스트 API 사용](../test/how-to-use-the-load-test-api.md)
- [방법: 웹 성능 테스트 플러그 인 만들기](../test/how-to-create-a-web-performance-test-plug-in.md)
