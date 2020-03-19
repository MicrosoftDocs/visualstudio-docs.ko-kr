---
title: 웹 성능 테스트 플러그 인 만들기
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc2eeafa41b953f9d853c7ff435a6a9706ae73ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589112"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>방법: 웹 성능 테스트 플러그 인 만들기

웹 성능 테스트 플러그 인을 사용하면 웹 성능 테스트의 주 선언문 외부에서 코드를 분리하여 다시 사용할 수 있습니다. 사용자 지정 웹 성능 테스트 플러그 인을 사용하면 웹 성능 테스트를 실행하는 일부 코드를 호출할 수 있습니다. 웹 성능 테스트 플러그 인은 테스트가 반복될 때마다 한 번씩 실행됩니다. 또한 테스트 플러그 인에서 PreRequest 또는 PostRequest 메서드를 재정의하면 이러한 요청 플러그 인이 각 요청 전이나 후에 실행됩니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

사용자 지정 웹 성능 테스트 플러그 인은 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> 기본 클래스에서 사용자 클래스를 파생시켜 만들 수 있습니다.

기록한 웹 성능 테스트와 함께 사용자 지정 웹 성능 테스트 플러그 인을 사용하면 최소한의 코드만 작성해도 되므로 웹 성능 테스트를 훨씬 효과적으로 제어할 수 있습니다. 코딩된 웹 성능 테스트와 함께 사용할 수도 있습니다. 자세한 내용은 [코딩된 웹 성능 테스트 생성 및 실행](../test/generate-and-run-a-coded-web-performance-test.md)를 참조하세요.

> [!NOTE]
> 부하 테스트 플러그 인도 만들 수 있습니다. [방법: 부하 테스트 플러그 인 만들기](../test/how-to-create-a-load-test-plug-in.md)를 참조하세요.

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>사용자 지정 웹 성능 테스트 플러그 인을 만들려면

1. 웹 성능 테스트가 포함된 웹 성능 및 부하 테스트 프로젝트를 엽니다.

2. **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가**를 선택한 다음, **새 프로젝트**를 선택합니다.

3. 새 **클래스 라이브러리** 프로젝트를 만듭니다.

   새 클래스 라이브러리 프로젝트가 **솔루션 탐색기**에 추가되고 새 클래스가 **코드 편집기**에 나타납니다.

4. **솔루션 탐색기**의 새 클래스 라이브러리에서 **References** 폴더를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

   **참조 추가** 대화 상자가 표시됩니다.

5. **.NET** 탭을 선택하고 아래로 스크롤하여 **Microsoft.VisualStudio.QualityTools.WebTestFramework**를 선택

6. **확인**을 선택합니다.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework**에 대한 참조가 **솔루션 탐색기**의 **Reference** 폴더에 추가됩니다.

7. **솔루션 탐색기**에서 웹 성능 테스트 플러그 인을 추가할 부하 테스트를 포함하는 웹 성능 및 부하 테스트 프로젝트의 최상위 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

8. **참조 추가 대화 상자가 표시됩니다**.

9. **프로젝트** 탭을 선택하고 **클래스 라이브러리 프로젝트**를 선택합니다.

10. **확인**을 선택합니다.

11. **코드 편집기**에서 플러그 인의 코드를 작성합니다. 먼저 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>에서 파생되는 새 공용 클래스를 만듭니다.

12. 하나 이상의 이벤트 처리기에서 코드를 구현합니다. 샘플 구현을 보려면 다음 예제 단원을 참조하십시오.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. 코드를 작성한 후 새 프로젝트를 빌드합니다.

14. 웹 성능 테스트를 엽니다.

15. 웹 성능 테스트 플러그 인을 추가하려면 도구 모음에서 **웹 테스트 플러그 인 추가**를 선택합니다.

     **웹 테스트 플러그 인 추가** 대화 상자가 표시됩니다.

16. **플러그 인 선택**에서 웹 성능 테스트 플러그 인 클래스를 선택합니다.

17. **선택한 플러그 인에 대한 속성** 창에서 런타임에 사용할 플러그 인의 초기 값을 설정합니다.

    > [!NOTE]
    > 플러그 인에서 속성을 원하는 만큼 노출할 수 있습니다. 속성을 공용이고 설정 가능한 기본 형식(정수, 부울 또는 문자열 등)으로 지정하기만 하면 됩니다. 나중에 [속성] 창을 사용하여 웹 성능 테스트 플러그 인 속성을 변경할 수도 있습니다.

18. **확인**을 선택합니다.

     플러그 인이 **웹 테스트 플러그 인** 폴더에 추가됩니다.

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

다음 코드에서는 테스트 반복을 나타내는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext>에 항목을 추가하는 사용자 지정 웹 성능 테스트 플러그 인이 만들어집니다.

웹 성능 테스트를 실행한 후 이 플러그 인을 사용하여 **웹 성능 테스트 결과 뷰어**의 **컨텍스트** 탭에서 **TestIteratnionNumber**라는 추가한 항목을 볼 수 있습니다.

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleRules
{
    [Description("This plugin can be used to set the ParseDependentsRequests property for each request")]
    public class SampleWebTestPlugin : WebTestPlugin
    {
        private bool m_parseDependents = true;

        public override void PreWebTest(object sender, PreWebTestEventArgs e)
        {
            // TODO: Add code to execute before the test.
        }

        public override void PostWebTest(object sender, PostWebTestEventArgs e)
        {
            // TODO: Add code to execute after the test.
        }

        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            // Code to execute before each request.
            // Set the ParseDependentsRequests value on the request
            e.Request.ParseDependentRequests = m_parseDependents;
        }

        // Properties for the plugin.
        [DefaultValue(true)]
        [Description("All requests will have their ParseDependentsRequests property set to this value")]
        public bool ParseDependents
        {
            get
            {
                return m_parseDependents;
            }
            set
            {
                m_parseDependents = value;
            }
        }
    }
}
```

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [방법: 요청 수준 플러그 인 만들기](../test/how-to-create-a-request-level-plug-in.md)
- [웹 성능 테스트에 대한 사용자 지정 추출 규칙 코딩](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [웹 성능 테스트에 대한 사용자 지정 유효성 검사 규칙 코딩](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [방법: 부하 테스트 플러그 인 만들기](../test/how-to-create-a-load-test-plug-in.md)
- [코딩된 웹 성능 테스트 생성 및 실행](../test/generate-and-run-a-coded-web-performance-test.md)
