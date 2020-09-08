---
title: 코딩된 UI 테스트 로그를 사용하여 코딩된 UI 테스트 분석
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ec1025eaa53861fae2cf92395d8842854649fa8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591218"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>코딩된 UI 테스트 로그를 사용하여 코딩된 UI 테스트 분석

코딩된 UI 테스트 로그는 코딩된 UI 테스트 실행에 대한 중요한 정보를 필터링하고 기록합니다. 로그는 문제를 신속하게 디버깅할 수 있는 형식으로 표시됩니다.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="step-1-enable-logging"></a>1단계: 로깅 사용

시나리오에 따라 다음 방법 중 하나를 사용하여 로그를 사용하도록 설정할 수 있습니다.

- 테스트 프로젝트에 *App.config* 파일이 없는 경우:

   1. 테스트를 실행할 때 어떤 *QTAgent\*.exe* 프로세스를 시작할지 결정합니다. 이것을 결정하는 한 가지 방법은 Windows **작업 관리자**에서 **세부 정보** 탭을 확인하는 것입니다.

   2. *%ProgramFiles(x86)%\Microsoft Visual Studio\\\<version>\\\<edition>\Common7\IDE* 폴더에서 해당 *.config* 파일을 엽니다. 예를 들어 *QTAgent_40.exe* 프로세스를 실행하는 경우에는 *QTAgent_40.exe.config*를 엽니다.

   2. **EqtTraceLevel**의 값을 원하는 로그 수준으로 수정합니다.

      ```xml
      <!-- You must use integral values for "value".
           Use 0 for off, 1 for error, 2 for warn, 3 for info, and 4 for verbose. -->
      <add name="EqtTraceLevel" value="4" />
      ```

   3. 파일을 저장합니다.

- 테스트 프로젝트에 *App.config* 파일이 있는 경우:

  - 프로젝트에서 *App.config* 파일을 열고 구성 노드 아래에 다음 코드를 추가합니다.

    ```xml
    <system.diagnostics>
      <switches>
        <add name="EqtTraceLevel" value="4" />
      </switches>
    </system.diagnostics>`
    ```

- 테스트 코드 자체에서 로깅을 사용하는 경우.

   ```csharp
   Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState = HtmlLoggerState.AllActionSnapshot;
   ```

## <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>2단계: 코딩된 UI 테스트를 실행하고 로그 보기

현재 위치에서 *QTAgent\*.exe.config* 파일을 적절하게 수정한 코딩된 UI 테스트를 실행하는 경우 **테스트 탐색기** 결과에 출력 링크가 표시됩니다. 로그 파일은 테스트에 실패한 경우뿐만 아니라 추적 수준이 **verbose**로 설정되었을 때 성공한 테스트의 경우에도 생성됩니다.

1. **테스트** 메뉴에서 **창**을 선택한 다음, **테스트 탐색기**를 선택합니다.

2. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

3. **테스트 탐색기**에서 실행하려는 코딩된 UI 테스트를 선택하고 해당 테스트의 바로 가기 메뉴를 연 다음, **선택한 테스트 실행**을 선택합니다.

     자동화된 테스트가 실행되고 성공 또는 실패 여부를 나타냅니다.

    > [!TIP]
    > **테스트 탐색기**를 보려면 **테스트** > **Windows**를 선택한 다음, **테스트 탐색기**를 선택합니다.

4. **테스트 탐색기** 결과에서 **출력** 링크를 선택합니다.

     ![테스트 탐색기의 출력 링크](../test/media/cuit_htmlactionlog1.png)

     그러면 작업 로그에 대한 링크를 포함하는 테스트에 대한 출력이 표시됩니다.

     ![코딩된 UI 테스트의 결과 및 출력 링크](../test/media/cuit_htmlactionlog2.png)

5. *UITestActionLog.html* 링크를 선택합니다.

     웹 브라우저에 로그가 표시됩니다.

     ![코딩된 UI 테스트 로그 파일](../test/media/cuit_htmlactionlog3.png)

## <a name="see-also"></a>참고 항목

- [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
- [방법: Microsoft Visual Studio에서 테스트 실행](https://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
