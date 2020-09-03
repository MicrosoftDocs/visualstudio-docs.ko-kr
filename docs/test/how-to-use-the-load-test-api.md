---
title: 부하 테스트 API
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1fc3ff1aa238249f7425c61b5b28d2a96e299fec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287105"
---
# <a name="how-to-use-the-load-test-api"></a>방법: 부하 테스트 API 사용

Visual Studio에서는 부하 테스트를 제어하거나 향상시킬 수 있는 부하 테스트 플러그 인을 지원합니다. 부하 테스트 플러그 인은 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> 네임스페이스에 있는 <xref:Microsoft.VisualStudio.TestTools.LoadTesting> 인터페이스를 구현하는 사용자 정의 클래스입니다. 부하 테스트 플러그 인을 사용하여 카운터 또는 오류 임계값에 도달한 경우 부하 테스트 중단과 같은 사용자 지정의 부하 테스트 작업을 수행할 수 있습니다. <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> 클래스의 속성을 사용하여 사용자 정의 코드에서 부하 테스트 매개 변수를 가져오거나 설정합니다. <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> 클래스의 이벤트를 사용하여 부하 테스트가 실행될 때 알림용 대리자를 연결합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> 개체 브라우저를 사용하여 <xref:Microsoft.VisualStudio.TestTools.LoadTesting> 네임스페이스를 검사합니다. Visual C# 및 Visual Basic 편집기는 모두 네임스페이스의 클래스를 사용하여 코딩하기 위한 IntelliSense 지원을 제공합니다.

웹 성능 테스트 플러그 인도 만들 수 있습니다. 자세한 내용은 [방법: 웹 성능 테스트 플러그 인 만들기](../test/how-to-create-a-web-performance-test-plug-in.md) 및 [방법: 요청 수준 플러그 인 만들기](../test/how-to-create-a-request-level-plug-in.md)를 참조하세요.

## <a name="to-use-the-loadtesting-namespace"></a>LoadTesting 네임스페이스를 사용하려면

1. 부하 테스트가 포함된 웹 성능 및 부하 테스트 프로젝트를 엽니다.

2. 테스트 솔루션에 Visual C# 또는 Visual Basic 클래스 라이브러리 프로젝트를 추가합니다.

3. 클래스 라이브러리 프로젝트에 웹 성능 및 부하 테스트 프로젝트의 참조를 추가합니다.

4. 클래스 라이브러리 프로젝트에 Microsoft.VisualStudio.QualityTools.LoadTestFramework DLL에 대한 참조를 추가합니다.

5. 클래스 라이브러리 프로젝트에 있는 클래스 파일에 `using` 네임스페이스에 대한 <xref:Microsoft.VisualStudio.TestTools.LoadTesting> 문을 추가합니다.

6. <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> 인터페이스를 구현하는 공용 클래스를 만듭니다.

7. 프로젝트를 빌드합니다.

8. 부하 테스트 편집기를 사용하여 새 부하 테스트 플러그 인을 추가합니다.

    1. 부하 테스트의 루트 노드를 마우스 오른쪽 단추로 클릭한 다음, **부하 테스트 플러그 인 추가**를 선택합니다.

    2. **부하 테스트 플러그 인 추가** 대화 상자가 표시됩니다.

    3. **선택한 플러그 인에 대한 속성** 창에서 런타임에 사용할 플러그 인의 초기 값을 설정합니다.

        > [!NOTE]
        > 플러그 인에서 속성을 원하는 만큼 노출할 수 있습니다. 속성을 공용의 설정 가능한 문자열, 정수 또는 부울 값 등의 기본 형식으로 설정하십시오. 나중에 **속성** 창을 사용하여 부하 테스트 플러그 인 속성을 편집할 수도 있습니다.

9. 부하 테스트를 실행합니다.

     <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>의 구현에 대한 자세한 내용은 [방법: 부하 테스트 플러그 인 만들기](../test/how-to-create-a-load-test-plug-in.md)를 참조하세요.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [방법: 웹 성능 테스트 API 사용](../test/how-to-use-the-web-performance-test-api.md)
- [방법: 부하 테스트 플러그 인 만들기](../test/how-to-create-a-load-test-plug-in.md)
