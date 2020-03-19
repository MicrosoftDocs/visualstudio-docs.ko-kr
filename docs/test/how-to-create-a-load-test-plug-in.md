---
title: 부하 테스트 플러그 인 만들기
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.loadtestplugin
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- load tests, plug-ins
ms.assetid: 27806972-1b15-4388-833d-6d0632816f1f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97952f65d78f7204410d07b90e0e538fb8499116
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589125"
---
# <a name="how-to-create-a-load-test-plug-in"></a>방법: 부하 테스트 플러그 인 만들기

부하 테스트 플러그 인을 만들어 부하 테스트가 실행되는 동안 코드를 여러 시점에서 실행할 수 있습니다. 플러그 인을 만들어 부하 테스트의 기본 제공 기능을 확장하거나 수정합니다. 예를 들어 부하 테스트 플러그 인을 코딩하여 부하 테스트가 실행되는 동안 부하 테스트 패턴을 설정하거나 수정할 수 있습니다. 그러기 위해서는 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> 인터페이스를 상속하는 클래스를 만들어야 합니다. 이 클래스는 이 인터페이스의 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin.Initialize*> 메서드를 구현해야 합니다. 자세한 내용은 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>를 참조하세요.

> [!TIP]
> 웹 성능 테스트 플러그 인도 만들 수 있습니다. 자세한 내용은 [방법: 웹 성능 테스트 플러그 인 만들기](../test/how-to-create-a-web-performance-test-plug-in.md)를 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<!-- markdownlint-disable MD003 MD020 -->
## <a name="to-create-a-load-test-plug-in-in-c"></a>C#에 부하 테스트 플러그 인을 만들려면
<!-- markdownlint-enable MD003 MD020 -->

1. 웹 성능 테스트가 포함된 웹 성능 및 부하 테스트 프로젝트를 엽니다.

2. 테스트 프로젝트에 부하 테스트를 추가한 다음, 웹 성능 테스트를 실행하도록 구성합니다.

     자세한 내용은 [빠른 시작: 부하 테스트 프로젝트 만들기](../test/quickstart-create-a-load-test-project.md)를 참조하세요.

3. 새 **클래스 라이브러리** 프로젝트를 솔루션에 추가합니다. (**솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가**를 선택한 다음, **새 프로젝트**를 선택합니다.)

4. **솔루션 탐색기**의 새 클래스 라이브러리에서 **References** 폴더를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

   **참조 추가** 대화 상자가 표시됩니다.

5. **.NET** 탭을 선택하고 아래로 스크롤하여 **Microsoft.VisualStudio.QualityTools.LoadTestFramework**를 선택합니다.

6. **확인**을 선택합니다.

   **Microsoft.VisualStudio.QualityTools.LoadTestFramework**에 대한 참조가 **솔루션 탐색기**의 **Reference** 폴더에 추가됩니다.

7. **솔루션 탐색기**에서 부하 테스트 플러그 인을 추가할 부하 테스트가 포함된 웹 성능 및 부하 테스트 프로젝트의 최상위 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

   **참조 추가 대화 상자가 표시됩니다**.

8. **프로젝트** 탭을 선택하고 클래스 라이브러리 프로젝트를 선택합니다.

9. **확인**을 선택합니다.

10. **코드 편집기**에서 <xref:Microsoft.VisualStudio.TestTools.LoadTesting> 네임스페이스에 대한 `using` 문을 추가합니다.

11. 클래스 라이브러리 프로젝트에서 만들어진 클래스에 대한 <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> 인터페이스를 구현합니다. 샘플 구현을 보려면 다음 예제 단원을 참조하십시오.

12. 코드를 작성한 후 새 프로젝트를 빌드합니다.

13. 부하 테스트의 최상위 노드를 마우스 오른쪽 단추로 클릭하고 **부하 테스트 플러그 인 추가**를 선택합니다.

     **부하 테스트 플러그 인 추가** 대화 상자가 표시됩니다.

14. **플러그 인 선택**에서 부하 테스트 플러그 인 클래스를 선택합니다.

15. **선택한 플러그 인에 대한 속성** 창에서 런타임에 사용할 플러그 인의 초기 값을 설정합니다.

    > [!NOTE]
    > 플러그 인에서 속성을 원하는 만큼 노출할 수 있습니다. 속성을 공용이고 설정 가능한 기본 형식(정수, 부울 또는 문자열 등)으로 지정하기만 하면 됩니다. 나중에 **속성** 창을 사용하여 웹 성능 테스트 플러그 인 속성을 변경할 수도 있습니다.

16. **확인**을 선택합니다.

     해당 플러그 인이 **부하 테스트 플러그 인** 폴더에 추가됩니다.

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

다음 코드에서는 LoadTestFinished 이벤트가 발생한 후 사용자 지정 코드를 실행하는 부하 테스트 플러그 인을 보여 줍니다. 이 코드가 원격 컴퓨터의 테스트 에이전트에서 실행되는 경우 테스트 에이전트에 localhost SMTP 서비스가 없으면 메시지 상자가 열려 있으므로 부하 테스트가 "진행 중" 상태로 유지됩니다.

> [!NOTE]
> 다음 코드를 실행하려면 System.Windows.Forms에 대한 참조를 추가해야 합니다.

```csharp
using System;
using Microsoft.VisualStudio.TestTools.LoadTesting;
using System.Net.Mail;
using System.Windows.Forms;

namespace LoadTestPluginTest
{
    public class MyLoadTestPlugin : ILoadTestPlugin
    {
        LoadTest myLoadTest;

        public void Initialize(LoadTest loadTest)
        {
            myLoadTest = loadTest;
            myLoadTest.LoadTestFinished += new
                EventHandler(myLoadTest_LoadTestFinished);
        }

        void myLoadTest_LoadTestFinished(object sender, EventArgs e)
        {
            try
            {
                // place custom code here
                MailAddress MyAddress = new MailAddress("someone@example.com");
                MailMessage MyMail = new MailMessage(MyAddress, MyAddress);
                MyMail.Subject = "Load Test Finished -- Admin Email";
                MyMail.Body = myLoadTest..Name + " has finished.";

                SmtpClient MySmtpClient = new SmtpClient("localhost");
                MySmtpClient.Send(MyMail);
            }

            catch (SmtpException ex)
            {
                MessageBox.Show(ex.InnerException.Message +
                    ".\r\nMake sure you have a valid SMTP.", "LoadTestPlugin", MessageBoxButtons.OK, MessageBoxIcon.Warning, MessageBoxDefaultButton.Button1);
            }
        }
    }
}
```

부하 테스트와 함께 사용자 지정 코드를 실행하도록 부하 테스트 플러그 인에서 처리할 수 있는 여덟 개의 이벤트가 부하 테스트와 연결되어 있습니다. 다음은 부하 테스트 실행의 여러 기간에 대한 액세스를 제공하는 이벤트 목록입니다.

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestWarmupComplete>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestStarting>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.TestFinished>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.ThresholdExceeded>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.Heartbeat>

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest.LoadTestAborted>

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>
- [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [방법: 웹 성능 테스트 플러그 인 만들기](../test/how-to-create-a-web-performance-test-plug-in.md)
