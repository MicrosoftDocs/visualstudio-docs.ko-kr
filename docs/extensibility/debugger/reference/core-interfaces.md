---
title: 핵심 인터페이스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737583"
---
# <a name="core-interfaces"></a>Core 인터페이스
다음 인터페이스는 을 사용하여 디버거를 확장하기 위한 [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]핵심 인터페이스입니다.

## <a name="discussion"></a>토론
 이러한 인터페이스는 주로 DE(디버그 엔진)를 만드는 데 사용됩니다. 범주별로 구성됩니다.

- [중단점](#Breakpoints)

- [컨텍스트](#Contexts)

- [코어 서버](#CoreServer)

- [디버그 엔진](#DebugEngines)

- [문서](#Documents)

- [이벤트](#Events)

- [식](#Expressions)

- [메모리](#Memory)

- [모듈](#Modules)

- [Ports](#Ports)

- [프로세스](#Processes)

- [Programs](#Programs)

- [속성](#Properties)

- [스택 프레임](#StackFrames)

- [스레드](#Threads)

- [유형 시각화 도우미](#TypeVisualizers)

  인터페이스를 구현할 수 있는 엔터티는 다음과 같습니다.

- 디버그 엔진 (DE)

- 포트 공급 업체 (PS)

- 식 평가기(EE)

- 비주얼 스튜디오 (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>중단점
 이러한 인터페이스는 중단점의 구현 및 추적과 관련이 있습니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|메모리 위치에 바인딩된 중단점을 나타냅니다.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|중단점이 메모리 위치에 바인딩될 때 DE에서 보냄|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|중단점 요청에 대한 문서 검사점을 나타냅니다.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|중단점이 메모리 위치에 바인딩되지 않을 때 DE에서 전송합니다.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|중단점에 도달하면 DE에서 전송합니다.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|중단점에 대한 요청을 나타냅니다. 보류 중인 중단점을 만드는 데 사용됩니다.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|중단점에 대한 요청을 나타냅니다. 보류 중인 중단점을 만드는 데 사용됩니다.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|중단점을 바인딩하는 데 사용되는 정보를 나타냅니다.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|중단점이 메모리 위치에서 언바운드될 때 DE에서 보송됩니다.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|잘못된 중단점(반환됨)을 `IDebugBreakpointErrorEvent2`나타냅니다.|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|잘못된 중단점에 대한 해결 정보를 나타냅니다.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|중단점이 설정된 함수의 위치를 나타냅니다.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|바인딩할 중단점을 나타냅니다. 바인딩된 중단점을 만드는 데 사용됩니다.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|바인딩된 중단점 집합에 대한 열거형입니다.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|메모리 위치에 바인딩할 수 없는 중단점 집합에 대한 열거형입니다.|

## <a name="contexts"></a><a name="Contexts"></a>컨텍스트
 이러한 인터페이스는 디버깅 중인 프로그램 내의 다양한 컨텍스트를 나타냅니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|코드 명령의 시작 위치를 나타냅니다.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|모듈 및 프로세스 인터페이스를 검색할 수 있도록 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 인터페이스를 확장합니다.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|문서의 위치를 나타냅니다.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|식을 평가할 컨텍스트를 나타냅니다.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|바이트 컬렉션의 메모리에서 시작 위치를 나타냅니다.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|중단점 또는 예외에서 스택 프레임 컨텍스트를 나타냅니다.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|중단점 또는 예외에서 스택 프레임 컨텍스트를 나타냅니다.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|코드 컨텍스트 집합에 대한 열거형을 나타냅니다.|

## <a name="core-server"></a><a name="CoreServer"></a>코어 서버
 이러한 인터페이스는 프로그램이 디버깅되는 컴퓨터를 나타냅니다. 디버그 엔진에 의해 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 구현되지만 호출할 수 있습니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|포트 및 포트 공급자에 대한 액세스 와 컴퓨터에 대한 정보를 제공합니다.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|원격 디버깅을 지원하는 [IDebugCoreServer2를](../../../extensibility/debugger/reference/idebugcoreserver2.md) 나타냅니다.|

## <a name="debug-engines"></a><a name="DebugEngines"></a>디버그 엔진
 이러한 인터페이스는 디버그 엔진과 관련 이벤트를 나타냅니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|사용자 지정 디버그 엔진을 나타냅니다.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|기호, JustMyCode 및 예외로드를 지원하는 사용자 지정 디버그 엔진을 나타냅니다.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|DE의 각 새 인스턴스에서 전송하여 디버깅 작업을 처리할 준비가 되었음을 나타냅니다.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|프로그램 시작을 지원하는 사용자 지정 디버그 엔진을 나타냅니다.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|여러 디버그 엔진을 처리하는 프로그램 노드를 나타냅니다.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|SDM이 스레드, 프로그램 또는 스택 프레임에서 디버그 엔진에 대한 인터페이스를 가져오는 방법을 제공합니다.|

## <a name="documents"></a><a name="Documents"></a>문서
 이러한 인터페이스는 문서(원본 파일) 및 관련 요소를 나타냅니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|DE에서 문서를 열어 달라고 요청합니다.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|문서에서 분해된 명령 스트림을 나타냅니다.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|이름과 클래스 ID(CLSID)를 지정하는 DE에서 제공하는 문서를 나타냅니다.|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|디버그 문서에 대한 체크섬을 나타내고 구성 요소 간에 체크섬을 전달할 수 있습니다.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|문서 컨텍스트, 특정 명령문 및 코드 컨텍스트에 해당하는 문서 내의 위치를 나타냅니다.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|문서 내의 일반적인 위치를 나타냅니다.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|소스 파일의 위치를 문자 오프셋으로 나타냅니다.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|실제 텍스트를 제공하는 [DE(IDebugDocument2에서](../../../extensibility/debugger/reference/idebugdocument2.md)파생됨)에서 제공하는 텍스트 문서를 나타냅니다.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|DE에서 전송하여 메모리에 있는 원본 파일에 대한 변경 내용을 지정합니다.|

## <a name="events"></a><a name="Events"></a>이벤트
 이러한 인터페이스는 DE와 세션 디버그 관리자(SDM) 간에 전송되는 모든 이벤트를 나타냅니다.

| 인터페이스 | 에 의해 구현 | 설명 |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | DE에서 문서를 열어 달라고 요청합니다. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | 디버그 엔진(DE)은 이 인터페이스를 세션 디버그 관리자(SDM)로 전송하여 심볼 로드 중에 상태 표시줄 메시지를 설정합니다. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | 프로그램의 중단이 완료되면 DE에서 전송합니다. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | 중단점이 바인딩될 때 DE에서 보냄 |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | 중단점을 바인딩하지 못할 때 DE에서 전송합니다. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | 중단점에 도달하면 DE에서 전송합니다. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | 중단점이 언바운드될 때 DE에서 보송됩니다. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | 특정 위치에서 중지해야 하는지 여부를 결정하기 위해 DE에서 전송됩니다. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | DE에서 전송하여 메모리에 있는 원본 파일에 대한 변경 내용을 지정합니다. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | DE의 각 새 인스턴스에서 전송하여 디버깅 작업을 처리할 준비가 되었음을 나타냅니다. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | DE에서 전송하여 디버깅 중인 프로그램이 첫 번째 명령을 실행할 준비가 되었음을 나타냅니다. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | 오류가 반환되어 사람이 읽을 수 있는 오류 메시지를 제공하기 위해 다른 이벤트 인터페이스에서 사용하는 인터페이스입니다. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | 다른 모든 이벤트 인터페이스가 파생되는 기본 인터페이스입니다. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | SDM에서 구현한 인터페이스를 나타내며 이벤트(특정 이벤트 인터페이스를 구현하는 개체로 표현)가 전송됩니다. |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | 디버깅 중인 프로그램에서 예외가 발생했을 때 DE에서 전송합니다. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | 비동기 식 평가가 완료되면 DE에 의해 전송됩니다. |
| 아이데버그파인심볼이벤트2 | | 사용되지 않습니다. 사용하지 마십시오. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | 가로채는 예외에 대한 처리가 완료될 때 DE에서 전송합니다. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | 프로그램 로드가 완료되면 DE에서 전송됩니다. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | IDE가 사용자에게 정보 메시지를 표시하도록 DE에 의해 전송됩니다. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | 모듈이 로드되거나 언로드될 때 DE에서 전송됩니다. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | 디버거 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI에 시작된 실행 에 대한 기호를 사용할 수 없다는 경고를 표시합니다. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | IDE가 임의의 문자열을 표시하도록 DE에서 전송합니다. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | 모든 수신기에 포트 이벤트를 알리기 위해 포트에서 전송됩니다. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | 프로세스가 생성되면 DE 또는 포트에서 전송됩니다. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | 프로세스가 소멸되면 DE 또는 포트에서 전송됩니다. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | 프로그램이 생성되면 DE 또는 포트에서 전송됩니다. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | 프로그램이 소멸되었을 때 DE 또는 포트에서 전송됩니다. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | 디버그 세션을 종료할 때 디버그 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 엔진이 UI의 기본 동작을 재정의할 수 있도록 합니다. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | 프로그램 이름이 변경될 때 DE(디버그 엔진)에서 세션 디버그 관리자(SDM)로 전송됩니다. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | `IDebugProperty2` 새 속성(인터페이스로 표시)이 생성되었을 때 DE에서 보송합니다. |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | 속성이 소멸되었을 때 DE에 의해 전송됩니다. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | 함수를 벗어나거나 함수를 통해 스테핑할 때 DE에서 전송되므로 반환 값이 올바르게 표시될 수 있습니다. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | 디버그 엔진이 메트릭 설정을 원격으로 읽을 수 있도록 합니다. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | 명령의 입력, 수행 또는 해제가 완료되면 DE에서 전송합니다. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | 모듈에 대한 기호 로드의 성공 또는 실패를 나타내기 위해 DE에서 전송합니다. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | 스레드가 생성될 때 DE에서 보냄 |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | 스레드가 소멸되었을 때 DE에 의해 전송됩니다. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | 스레드가 이름을 변경했을 때 DE에서 보냄 |

## <a name="expressions"></a><a name="Expressions"></a> 식
 이러한 인터페이스는 특정 컨텍스트에서 평가할 식을 나타냅니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|평가할 식을 나타냅니다. [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) 인터페이스에서 가져옵니다.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|식이 평가되는 컨텍스트를 나타냅니다. [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) 인터페이스에서 가져옵니다.|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|비동기 식 평가가 완료되면 DE에 의해 전송됩니다.|

## <a name="memory"></a><a name="Memory"></a>메모리
 이러한 인터페이스는 메모리에 있는 바이트 시퀀스를 나타냅니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|메모리에서 읽거나 쓸 수 있는 바이트 시퀀스를 나타냅니다.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|일련의 바이트를 메모리에 있는 위치를 나타냅니다.|

## <a name="modules"></a><a name="Modules"></a>모듈
 이러한 인터페이스는 실행 또는 에 해당하는 모듈을 나타냅니다. DLL 파일입니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|단일 실행 형 또는 DLL을 나타냅니다.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|기호를 지원하는 [IDebugModule2를](../../../extensibility/debugger/reference/idebugmodule2.md) 나타냅니다.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|모듈이 로드되거나 언로드될 때 DE에서 전송됩니다.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|PDB 파일에 포함된 원본 서버 정보를 나타냅니다.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|[IDebugProgram2에서](../../../extensibility/debugger/reference/idebugprogram2.md)알려진 모듈 집합에 대한 열거형입니다.|

## <a name="ports"></a><a name="Ports"></a>포트
 이러한 인터페이스는 포트 및 포트 공급자를 나타냅니다.

| 인터페이스 | 에 의해 구현 | 설명 |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | 로컬 컴퓨터의 기본 포트를 나타냅니다. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | DCOM을 사용하는 디버그 엔진이 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 방화벽이 원격 디버깅을 차단하지 않도록 UI에 요청하도록 합니다. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | 포트를 나타냅니다. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | 모든 수신기에 포트 이벤트를 알리기 위해 포트에서 전송됩니다. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | 프로세스를 시작하고 종료할 수 있는 포트를 나타냅니다. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | 포트에 프로그램을 등록하고 등록 취소하는 데 사용됩니다. 포트가 현재 디버깅 중인 프로그램을 추적할 수 있습니다. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | 포트를 선택 하기 위한 사용자 지정 된 UI를 나타냅니다. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | 새 포트가 만들어지거나 있는 포트에 대한 요청을 나타냅니다. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | 포트 공급업체를 나타냅니다. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | 생성된 포트에 대한 정보를 유지(디스크에 저장)할 수 있는 포트 공급자를 나타냅니다. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | UI가 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 프로세스에 연결 대화 상자의 **전송 정보** 섹션 내에 텍스트를 **표시할 수 있도록 합니다.** |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | 대상 컴퓨터에 대한 정보를 쿼리할 수 있습니다. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | 포트 집합에 대한 열거형입니다. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | 포트 공급자 집합에 대한 열거형입니다. |

## <a name="processes"></a><a name="Processes"></a>프로세스
 이러한 인터페이스는 하나 이상의 프로그램을 포함하는 단일 실행 프로세스인 프로세스를 나타냅니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|컴퓨터에서 실행 중인 프로세스를 나타냅니다.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|디버깅을 적극적으로 지원하는 프로세스를 [나타냅니다(IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스에서 단계, 계속 및 실행 메서드를 대체하는 데 사용).|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|프로세스가 생성되면 DE 또는 포트에서 전송됩니다.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|프로세스가 소멸되면 DE 또는 포트에서 전송됩니다.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|연결된 세션을 추적해야 하는 프로세스를 나타냅니다.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|포트의 프로세스 집합열거를 나타냅니다.|

## <a name="programs"></a><a name="Programs"></a>프로그램
 이러한 인터페이스는 프로그램, 반드시 물리적 실행 또는 모듈에 해당 하지 않는 실행의 논리적 단위를 나타냅니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|동시에 디버깅되는 다른 프로그램과 함께 작업해야 하는 [IDebugProgram2를](../../../extensibility/debugger/reference/idebugprogram2.md) 나타냅니다.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|논리적 실행 단위를 나타냅니다.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|프로그램이 생성되면 DE 또는 포트에서 전송됩니다.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|프로그램이 소멸되었을 때 DE 또는 포트에서 전송됩니다.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|여러 디버그 엔진에서 처리할 수 있는 [IDebugProgramNode2를](../../../extensibility/debugger/reference/idebugprogramnode2.md) 나타냅니다.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|연결된 세션을 추적할 수 있어야 하는 [IDebugProgram2를](../../../extensibility/debugger/reference/idebugprogram2.md) 나타냅니다.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|실행 중인 프로세스에 대 한 정보를 반환할 수 있는 [IDebugProgram2를](../../../extensibility/debugger/reference/idebugprogram2.md) 나타냅니다.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|디버깅할 수 있는 프로그램을 나타냅니다.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|프로그램 노드가 연결된 프로그램에 연결하려는 시도에 대한 알림을 받을 수 있습니다.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|SDM이 해당 DE에서 제어하는 프로그램에 대해 DE를 쿼리하는 방법을 제공합니다.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|DEs에서 DDM에 프로그램을 등록하여 디버깅 중임을 표시하는 데 사용됩니다.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|스레드 또는 프로세스 경계에서 인터페이스를 마샬링할 수 있는 [IDebugProgramNode2를](../../../extensibility/debugger/reference/idebugprogramnode2.md) 나타냅니다.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|프로그램 집합의 열거를 나타냅니다.|

## <a name="properties"></a><a name="Properties"></a> 속성
 이러한 인터페이스는 특정 컨텍스트와 연결된 값인 속성(일반적으로 식 평가의 결과)을 나타냅니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|사용자 지정 방식으로 값을 표시할 수 있는 [IDebugProperty2를](../../../extensibility/debugger/reference/idebugproperty2.md) 나타냅니다.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|스택 프레임, 문서 또는 식 평가 의 결과를 나타냅니다.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|임의로 긴 문자열을 지원하는 [IDebugProperty2를](../../../extensibility/debugger/reference/idebugproperty2.md) 나타냅니다.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|[새 속성(IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스로 표시)이 생성되었을 때 DE에서 전송합니다.|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|속성이 소멸되었을 때 DE에 의해 전송됩니다.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|특정 스택 프레임 외부에 존재할 수 있는 속성에 대한 참조를 나타냅니다.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|변수, 레지스터, 매개 변수 및 식을 설명하는 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조 집합에 대한 열거를 나타냅니다.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조 집합에 대한 열거형입니다.|

## <a name="stack-frames"></a><a name="StackFrames"></a>스택 프레임
 이러한 인터페이스는 중단점 또는 예외가 발생한 컨텍스트인 스택 프레임을 나타냅니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|중단점 또는 예외가 발생한 컨텍스트를 나타냅니다.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|가로채기된 예외를 처리할 수 있는 [IDebugStackFrame2를](../../../extensibility/debugger/reference/idebugstackframe2.md) 나타냅니다.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|특정 스택 프레임에 도달하는 데 사용되는 함수 호출 시퀀스를 지정하는 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) 구조 집합에 대한 열거를 나타냅니다.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|스택 프레임을 설명하는 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조 집합에 대한 열거를 나타냅니다.|

## <a name="threads"></a><a name="Threads"></a>스레드
 이러한 인터페이스는 스레드 및 관련 이벤트를 나타냅니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|실행 스레드를 나타냅니다.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|스레드가 생성될 때 DE에서 보냄|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|스레드가 소멸되었을 때 DE에 의해 전송됩니다.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|스레드가 이름을 변경했을 때 DE에서 보냄|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|스레드 집합에 대한 열거형입니다.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>유형 시각화 도우미
 이러한 인터페이스는 형식 시각화 도우미에 대 한 지원을 제공 합니다. 이러한 인터페이스는 일반적으로 식 계산기에서 구현됩니다.

|인터페이스|에 의해 구현|설명|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|형식 시각화 도우미에 제시할 바이트 배열을 나타냅니다.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|형식 시각화 도우미에 전달될 데이터에 대한 액세스 권한을 가져오는 메서드를 제공합니다.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 구현에 대한 액세스를 제공하는 속성을 나타냅니다.|

## <a name="see-also"></a>참조
- [API 참조](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [사용자 지정 디버그 엔진 만들기](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
