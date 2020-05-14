---
title: 웹 성능 테스트용 요청 수준 플러그 인 만들기
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6e57f92a3f45983321a866f3524974ea99dba82
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589158"
---
# <a name="how-to-create-a-request-level-plug-in"></a>방법: 요청 수준 플러그 인 만들기

‘요청’은 웹 성능 테스트를 구성하는 선언문입니다.  웹 성능 테스트 플러그 인을 사용하면 웹 성능 테스트의 주 선언문 외부에서 코드를 분리하여 다시 사용할 수 있습니다. 플러그 인을 만들어 개별 요청과 요청을 포함하는 웹 성능 테스트에 추가할 수 있습니다. 사용자 지정 ‘요청 플러그 인’을 사용하면 웹 성능 테스트에서 특정 요청을 실행하는 코드를 호출할 수 있습니다. 

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

모든 웹 성능 테스트 요청 플러그 인에는 PreRequest 메서드와 PostRequest 메서드가 있습니다. 특정 HTTP 요청에 요청 플러그 인을 연결하고 나면 요청을 실행하기 전에는 PreRequest 이벤트가 발생하고 응답을 받은 후에는 PostRequest가 발생합니다.

사용자 지정 웹 성능 테스트 요청 플러그 인은 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> 기본 클래스에서 사용자 클래스를 파생시켜 만들 수 있습니다.

기록한 웹 성능 테스트와 함께 사용자 지정 웹 성능 테스트 요청 플러그 인을 사용할 수 있습니다. 사용자 지정 웹 성능 테스트 요청 플러그 인을 사용하면 최소한의 코드만 작성해도 되므로 웹 성능 테스트를 훨씬 효과적으로 제어할 수 있습니다. 코딩된 웹 성능 테스트와 함께 사용할 수도 있습니다. [코딩된 웹 성능 테스트 생성 및 실행](../test/generate-and-run-a-coded-web-performance-test.md)을 참조하세요.

## <a name="to-create-a-request-level-plug-in"></a>요청 수준 플러그 인을 만들려면

1. **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가**를 선택한 다음, **새 프로젝트**를 선택합니다.

2. 새 **클래스 라이브러리** 프로젝트를 만듭니다.

3. **솔루션 탐색기**의 새 클래스 라이브러리에서 **References** 폴더를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

     **참조 추가** 대화 상자가 표시됩니다.

4. **.NET** 탭을 선택하고 아래로 스크롤하여 **Microsoft.VisualStudio.QualityTools.WebTestFramework**를 선택한 다음, **확인**을 선택합니다.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework**에 대한 참조가 **솔루션 탐색기**의 **Reference** 폴더에 추가됩니다.

5. **솔루션 탐색기**에서 웹 성능 테스트 요청 테스트 플러그 인을 추가할 부하 테스트를 포함하는 웹 성능 및 부하 테스트 프로젝트의 최상위 노드를 마우스 오른쪽 단추로 클릭합니다. **참조 추가**를 선택합니다.

     **참조 추가 대화 상자가 표시됩니다**.

6. **프로젝트** 탭을 선택하고, **클래스 라이브러리 프로젝트**를 선택한 다음, **확인**을 선택합니다.

7. **코드 편집기**에서 플러그 인의 코드를 작성합니다. 먼저 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>에서 파생되는 새 공용 클래스를 만듭니다.

8. <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> 및 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> 이벤트 처리기 중 하나 또는 둘 모두에서 코드를 구현합니다. 샘플 구현을 보려면 다음 예제 단원을 참조하십시오.

9. 코드를 작성한 후 새 프로젝트를 빌드합니다.

10. 요청 플러그 인을 추가할 웹 성능 테스트를 엽니다.

11. 요청 플러그 인을 추가할 요청을 마우스 오른쪽 단추로 클릭한 다음, **요청 플러그 인 추가**를 선택합니다.

     **웹 테스트 요청 플러그 인 추가** 대화 상자가 표시됩니다.

12. **플러그 인 선택**에서 새 플러그 인을 선택합니다.

13. **선택한 플러그 인에 대한 속성** 창에서 런타임에 사용할 플러그 인의 초기 값을 설정합니다.

    > [!NOTE]
    > 플러그 인에서 속성을 원하는 만큼 노출할 수 있습니다. 속성을 공용이고 설정 가능한 기본 형식(정수, 부울 또는 문자열 등)으로 지정하기만 하면 됩니다. 나중에 [속성] 창을 사용하여 웹 성능 테스트 플러그 인 속성을 변경할 수도 있습니다.

14. **확인**을 선택합니다.

     해당 플러그 인이 HTTP 요청의 자식 폴더인 **요청 플러그 인** 폴더에 추가됩니다.

    > [!WARNING]
    > 이 플러그 인을 사용하는 부하 테스트 또는 웹 성능 테스트를 실행할 때 다음과 유사한 오류가 발생할 수 있습니다.
    >
    > **요청 실패: \<플러그 인> 이벤트의 예외: 파일 또는 어셈블리 '\<"플러그 인 이름".dll 파일>, 버전=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' 또는 해당 종속성 중 하나를 로드할 수 없습니다. 지정한 파일을 찾을 수 없습니다.**
    >
    > 이 오류는 플러그 인의 코드를 변경하고 새 DLL 버전 **(버전=0.0.0.0)** 을 만들었지만 해당 플러그 인이 계속해서 원래 플러그 인 버전을 참조하는 경우에 발생합니다. 이 문제를 해결하려면 다음 단계를 수행합니다.
    >
    > 1. 웹 성능 및 부하 테스트 프로젝트에서는 참조에 경고가 표시됩니다. 참조를 제거했다가 플러그 인 DLL에 다시 추가합니다.
    > 2. 테스트 또는 적절한 위치에서 플러그 인을 제거했다가 다시 추가합니다.

## <a name="example"></a>예제

다음 코드를 사용하여 두 대화 상자를 표시하는 사용자 지정 웹 성능 테스트 플러그 인을 만들 수 있습니다. 첫 번째 대화 상자에는 요청 추가 기능을 연결할 요청과 연결된 URL이 표시됩니다. 두 번째 대화 상자에 에이전트의 컴퓨터 이름이 표시됩니다.

> [!NOTE]
> 다음 코드를 실행하려면 System.Windows.Forms에 대한 참조를 추가해야 합니다.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [웹 성능 테스트에 대한 사용자 지정 추출 규칙 코딩](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [웹 성능 테스트에 대한 사용자 지정 유효성 검사 규칙 코딩](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [방법: 부하 테스트 플러그 인 만들기](../test/how-to-create-a-load-test-plug-in.md)
- [코딩된 웹 성능 테스트 생성 및 실행](../test/generate-and-run-a-coded-web-performance-test.md)
