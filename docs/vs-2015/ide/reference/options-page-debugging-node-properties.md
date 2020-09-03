---
title: 옵션 페이지, 디버깅 노드 속성 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 564cc8b2-0084-420e-b560-200cc5621a7e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10537fb64e6ae0ebbe185024b76442704437e273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668837"
---
# <a name="options-page-debugging-node-properties"></a>옵션 페이지, 디버깅 노드 속성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음 표에서는 **옵션** 대화 상자의 **디버깅** 범주, `DTE.Properties("Debugging", <Property Page>)`와 연관된 일부 페이지(또는 속성 컬렉션)에 대해 설명합니다.

## <a name="general"></a>일반
 `DTE.Properties("Debugging", "General")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|PromptOnBreakpointDelete|Get/Set (Boolean)|프로젝트에서 모든 중단점을 삭제하기 전에 디버거에서 권한에 대한 프롬프트를 표시할지 결정합니다.|
|BreakAllProcesses|Get/Set (Boolean)|단일 프로세스가 중단될 때마다 디버거에서 모든 프로세스를 중단할지 결정합니다.|
|BreakAtBoundaries|Get/Set (Boolean)|AppDomain 간에 또는 관리 코드와 네이티브 코드 간에 예외가 경계를 넘을 경우 디버거가 예외를 중간할지 결정합니다.|
|EnableAddressLevelDebugging|Get/Set (Boolean)|주소 수준 디버깅 기능을 사용할지 결정합니다.|
|ShowDisassemblyIfNoSource|Get/Set (Boolean)|소스 코드를 사용할 수 없을 때 디버거가 디스어셈블리 코드를 표시할지 결정합니다.|
|EnableBreakpointFilters|Get/Set (Boolean)|중단점 필터링을 사용할지 결정합니다.|
|EnableExceptionAssistant|Get/Set (Boolean)|관리되는 예외에 예외 도우미를 사용할지 결정합니다.|
|UnwindCallstack|Get/Set (Boolean)|디버거가 처리되지 않은 예외에 대한 호출 스택을 해제할지 결정합니다.|
|EnableJustMyCode|Get/Set (Boolean)|C# 및 Visual Basic 코드에 내 코드만을 사용할지 결정합니다.|
|ShowAllMembers|Get/Set (Boolean)|사용자가 작성하지 않은 개체의 경우 디버거가 변수 창에 모든 개체 멤버를 표시할지 결정합니다. 내 코드만이 사용될 경우 이 옵션은 아무런 영향이 없습니다.|
|WarnIfNoUserCode|Get/Set (Boolean)|사용자가 사용자 코드가 없는 프로세스에 연결하려고 할 때 디버거가 경고를 내보낼지 결정합니다. 내 코드만이 사용될 경우 이 옵션은 아무런 영향이 없습니다.|
|EnablePropertyEvaluation|Get/Set (Boolean)|디버거가 관리 코드에서 자동으로 속성 및 암시적 함수 호출을 평가할지 결정합니다.|
|CallStringConversion|Get/Set (Boolean)|디버거가 변수 창에서 개체에 대한 문자열 변환 함수를 암시적으로 호출할지 결정합니다. 이 옵션은 C# 및 JScript 코드에만 적용됩니다.|
|EnableSourceServer|Get/Set (Boolean)|디버거가 소스 서버에서 코드에 액세스할 수 있는지 결정합니다.|
|PrintSourceServerDiagnostics|Get/Set (Boolean)|[출력] 창에 소스 서버에 관련된 진단 메시지를 표시할지 결정합니다. 소스 서버 액세스가 사용하도록 설정되지 않으면 이 옵션은 아무런 영향이 없습니다.|
|HighlightEntireLine|Get/Set (Boolean)|디버거가 중단점 및 현재 문의 의 전체 줄을 강조 표시할지 결정합니다.|
|RequireSourceToMatch|Get/Set (Boolean)|디버거에서 디버깅을 위해 파일을 열 때 소스 파일이 원래 버전과 정확히 일치하도록 할지 결정합니다.|
|RedirectOutputToImmediate|Get/Set (Boolean)|[출력] 창의 출력을 [직접 실행] 창으로 리디렉션할지 결정합니다.|
|ShowRawVariableStructure|Get/Set (Boolean)|변수 창의 개체를 원시 형식으로 표시할지 결정합니다.|
|SuppressJitOptimization|Get/Set (Boolean)|관리 코드의 경우 디버거가 Just-In-Time 최적화를 억제할지 결정합니다.|
|WarnIfNoSymbols|Get/Set (Boolean)|프로세스가 시작될 때 디버깅 기호를 사용할 수 없는 경우 디버거가 경고를 표시할지 결정합니다.|
|WarnIfScriptDisabled|Get/Set (Boolean)|프로세스가 시작될 때 스크립트 디버깅이 사용되지 않는 경우 디버거가 경고를 표시할지 결정합니다.|
|ShowMarkersForAllThreads|Get/Set (Boolean)|디버거가 스레드 마커를 표시할지 결정합니다.|
|StepOverPropertiesAndOperators|Get/Set (Boolean)|관리 코드에서만 속성과 연산자를 건너뛸지 지정합니다.|

## <a name="edit-and-continue"></a>편집하며 계속하기
 `DTE.Properties("Debugging", "EditAndContinue")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|EnableEditAndContinue|Get/Set (Boolean)|편집하며 계속하기를 사용할지 결정합니다. 이 옵션은 편집하며 계속하기를 지원하는 모든 언어에 적용됩니다.|
|InvokedByCommands|Get/Set (Boolean)|사용자가 **한 단계 실행** 또는 **계속**과 같은 디버깅 명령을 선택할 때 편집하며 계속하기가 자동으로 코드 변경 내용을 적용할지 결정합니다. 이 옵션은 네이티브 코드에만 적용됩니다.|
|InvokedByCommandsAskFirst|Get/Set (Boolean)|사용자가 **한 단계 실행** 또는 **계속**과 같은 디버깅 명령을 선택할 때 편집하며 계속하기가 코드 변경 내용을 적용하기 위한 권한에 대한 프롬프트를 사용자에게 표시할지 결정합니다. 이 옵션은 네이티브 코드에만 적용됩니다.|
|WarnAboutStaleCode|Get/Set (Boolean)|편집하며 계속하기에서 오래되거나 부실한 코드가 실행될 경우 디버거가 경고 메시지를 실행할지 결정합니다. 이 옵션은 네이티브 코드에만 적용됩니다.|
|RelinkChangesOnStop|Get/Set(Short)|애플리케이션 실행이 중지될 때 편집하며 계속하기에 의해 적용된 코드 변경 내용을 Visual Studio가 다시 연결할지 결정합니다. 이 옵션은 네이티브 코드에만 적용됩니다.|
|AllowPrecompiling|Get/Set(Short)|편집하며 계속하기가 백그라운드에서 미리 컴파일된 헤더를 로드하도록 허용할지 결정합니다. 이 옵션은 네이티브 코드에만 적용됩니다.|

## <a name="just-in-time"></a>Just-In-Time
 `DTE.Properties("Debugging", "JustInTime")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|JitManaged|Get/Set (Boolean)|관리 코드에 Just-In-Time 디버깅을 사용할지 결정합니다.|
|JitNative|Get/Set (Boolean)|네이티브 코드에 Just-In-Time 디버깅을 사용할지 결정합니다.|
|JitScript|Get/Set (Boolean)|스크립트 코드에 Just-In-Time 디버깅을 사용할지 결정합니다.|

## <a name="native"></a>네이티브
 `DTE.Properties("Debugging", "Native")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|LoadDllExports|Get/Set (Boolean)|디버거가 DLL 내보내기 테이블을 로드할지 결정합니다.|
|EnableRPC|Get/Set (Boolean)|디버거가 COM 원격 프로시저 호출에 대해 한 단계씩 코드를 실행할 수 있는지 결정합니다.|

## <a name="see-also"></a>관련 항목
 [옵션 설정 제어](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [옵션 페이지](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [옵션 페이지, 글꼴 및 색 노드 속성](../../ide/reference/options-page-fonts-and-colors-node-properties.md) [옵션 페이지, 텍스트 편집기 노드 속성](../../ide/reference/options-page-text-editor-node-properties.md) [일반, 디버깅, 옵션 대화](../../debugger/general-debugging-options-dialog-box.md) 상자 [,](https://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103) 디버깅, 옵션 대화 상자, 디버깅, 옵션 대화 상자, [디버깅,](../../debugger/just-in-time-debugging-options-dialog-box.md) 옵션 대화 상자, 디버깅, 옵션 대화 상자
