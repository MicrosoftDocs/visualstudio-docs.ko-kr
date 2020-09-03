---
title: 코딩된 UI 테스트 로그를 사용하여 코딩된 UI 테스트 분석 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3ebb18aaff78d9782b6210e25bcd697d21c8570
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660759"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>코딩된 UI 테스트 로그를 사용하여 코딩된 UI 테스트 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코딩된 UI 테스트 로그는 코딩된 UI 테스트 실행에 대한 중요한 정보를 필터링하고 기록합니다.

 **요구 사항**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>이 작업을 수행해야 하는 이유
 로그는 문제를 신속하게 디버깅할 수 있는 형식으로 표시됩니다.

## <a name="how-do-i-do-this"></a>이 작업을 어떻게 수행하나요?

### <a name="step-1-enable-logging"></a>1단계: 로깅 사용
 시나리오에 따라 다음 방법 중 하나를 사용하여 로그를 사용하도록 설정할 수 있습니다.

- 테스트 프로젝트에 App.config 파일이 없는 .NET Framework 버전 4를 대상으로 지정하는 경우

  - **QTAgent32_40.exe.config** 파일을 엽니다.

    기본적으로이 파일은 파일 \ ** \<drvie> 파일 (x86) \Microsoft Visual Studio 12.0 \ Common7\IDE**에 있습니다.

    EqtTraceLevel의 값을 원하는 로그 수준으로 수정합니다.

    파일을 저장합니다.

- 테스트 프로젝트에 App.config 파일이 없는 .NET Framework 버전 4.5를 대상으로 지정하는 경우

  - **QTAgent32.exe.config** 파일을 엽니다.

    기본적으로이 파일은 파일 \ ** \<drvie> 파일 (x86) \Microsoft Visual Studio 12.0 \ Common7\IDE**에 있습니다.

    EqtTraceLevel의 값을 원하는 로그 수준으로 수정합니다.

    파일을 저장합니다.

- 테스트 프로젝트에 App.config 파일이 있는 경우

  - 프로젝트에서 App.config 파일을 엽니다.

    구성 노드 아래에 다음 코드를 추가합니다.

    `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`

- 테스트 코드 자체에서 로깅을 사용하는 경우

  - <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;

### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>2단계: 코딩된 UI 테스트를 실행하고 로그 보기
 현재 위치에서 **QTAgent32.exe.config** 파일을 적절하게 수정한 코딩된 UI 테스트를 실행하는 경우 테스트 탐색기 결과에 출력 링크가 표시됩니다. 로그 파일은 테스트에 실패한 경우뿐만 아니라 추적 수준이 “verbose”로 설정되었을 때 성공한 테스트의 경우에도 생성됩니다.

1. **테스트** 메뉴에서 **창** 을 선택한 다음 **테스트 탐색기**를 선택 합니다.

2. **빌드** 메뉴에서 **솔루션 빌드**를 선택 합니다.

3. 테스트 탐색기에서 실행 하려는 코딩 된 UI 테스트를 선택 하 고 해당 바로 가기 메뉴를 연 다음 **테스트 실행**을 선택 합니다.

     자동화된 테스트가 실행되고 성공 또는 실패 여부를 나타냅니다.

    > [!TIP]
    > 테스트 탐색기를 보려면 **테스트 메뉴**에서 **Windows**를 가리킨 다음 **테스트 탐색기**를 선택합니다.

4. 테스트 탐색기 결과에서 **출력** 링크를 선택합니다.

     ![테스트 탐색기의 출력 링크](../test/media/cuit-htmlactionlog1.png "CUIT_HTMLActionLog1")

     그러면 작업 로그에 대한 링크가 포함되는 테스트에 대한 출력이 표시됩니다.

     ![코딩된 UI 테스트의 결과 및 출력 링크](../test/media/cuit-htmlactionlog2.png "CUIT_HTMLActionLog2")

5. UITestActionLog.html 링크를 선택합니다.

     웹 브라우저에 로그가 표시됩니다.

     ![코딩된 UI 테스트 로그 파일](../test/media/cuit-htmlactionlog3.png "CUIT_HTMLActionLog3")

## <a name="q--a"></a>Q & A

### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>Q: EnableHtmlLogger 키는 어떻게 되나요?
 이전 버전의 Visual Studio에는 코딩된 UI 테스트에서 HtmlLogger를 사용하도록 설정하는 다음과 같은 구성 설정이 두 개 더 있었습니다.

```

<add key="EnableHtmlLogger" value="true"/>

<add key="EnableSnapshotInfo" value="true"/>

```

 그러나 이러한 설정은 둘 다 Visual Studio 2012 이후부터 사용되지 않습니다. EqtTraceLevel이 HtmlLogger를 사용하기 위해 수정해야 하는 유일한 설정입니다.

## <a name="see-also"></a>관련 항목
 [UI 자동화를 사용 하 여 코드 테스트](../test/use-ui-automation-to-test-your-code.md) [방법: Microsoft Visual Studio에서 테스트 실행](https://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
