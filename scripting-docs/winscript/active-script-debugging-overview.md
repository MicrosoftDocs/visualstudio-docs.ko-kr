---
title: 액티브 스크립트 디버깅 개요 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0181ee305c99a1d0af1d3e1e965c6ac8fe16f375
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835669"
---
# <a name="active-script-debugging-overview"></a>액티브 스크립트 디버깅 개요
액티브 스크립트 디버깅 인터페이스는 언어 중립적, 호스트 중립적 디버깅을 허용하고 다양한 개발 환경을 지원합니다.  
  
 ![스크립트 호스트 프로세스](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
그림 1  
  
 언어 중립적 디버깅 환경은 이러한 언어 중 하나에 대한 특정 지식이 없어도 모든 프로그래밍 언어 또는 혼합된 프로그래밍 언어를 지원할 수 있습니다. 또한 디버깅 환경은 언어 간 단계별 실행 및 중단점을 지원합니다. (이 개요에서는 주로 VBScript 및 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]와 같은 스크립트 언어 지원에 대해 중점적으로 설명합니다.)  
  
 호스트 중립적 디버거는 Internet Explorer 또는 사용자 지정 호스트와 같은 모든 액티브 스크립팅 호스트에서 자동으로 사용할 수 있습니다. 호스트는 문서 트리 구조에서 디버그 문서의 내용 및 구문 색 지정에 이르기까지 디버거에서 사용자에게 제공하는 항목을 제어합니다. 이렇게 하면 디버그된 소스 코드를 호스트 문서의 컨텍스트에 표시할 수 있습니다. 예를 들어 Internet Explorer에서 HTML 페이지에 스크립트를 표시할 수 있습니다.  
  
 아래의 하위 섹션에서는 활성 디버깅의 각 핵심 구성 요소와 관련 인터페이스에 대해 설명합니다. 그러나 계속하기 전에 몇 가지 주요 활성 디버깅 개념을 정의해야 합니다.  
  
 **호스트 애플리케이션**  
 스크립트 엔진을 호스팅하고 스크립트 가능한 개체 집합(또는 "개체 모델")을 제공하는 애플리케이션입니다.  
  
 **언어 엔진**  
 특정 언어에 대한 구문 분석, 실행 및 디버깅 추상화를 제공하는 구성 요소입니다.  
  
 **디버거 IDE**  
 호스트 애플리케이션 및 언어 엔진과 통신하여 디버깅 UI를 제공하는 애플리케이션입니다.  
  
 **머신 디버그 관리자** 디버깅 가능한 애플리케이션 프로세스의 레지스트리를 유지 관리하는 구성 요소입니다.  
  
 **프로세스 디버그 관리자**  
 특정 애플리케이션에 대해 디버깅 가능한 문서 트리 유지 관리, 실행 중인 스레드 추적 등을 수행하는 하는 구성 요소입니다.  
  
 **문서 컨텍스트**  
 문서 컨텍스트는 호스트 문서의 소스 코드에서 특정 범위를 나타내는 추상화입니다.  
  
 **코드 컨텍스트**  
 코드 컨텍스트는 언어 엔진의 실행 코드에서 특정 위치("가상 명령 포인터")를 나타냅니다.  
  
 **식 컨텍스트**  
 언어 엔진에서 식을 평가할 수 있는 특정 컨텍스트(예: 스택 프레임)입니다.  
  
 **개체 검색**  
 "조사식 창" UI를 구현하는 데 적합한 개체의 이름, 형식, 값 및 하위 개체의 구조화된 언어 독립적 표현입니다.  
  
 다음은 주요 활성 디버깅 구성 요소 및 이와 관련된 해당 인터페이스에 대한 개요이며, 인터페이스에는 해당 세부 정보가 뒤따릅니다.  
  
## <a name="language-engine"></a>언어 엔진  
 언어 엔진은 다음을 제공합니다.  
  
- 언어 구문 분석 및 실행  
  
- 디버깅 지원(중단점 등)  
  
- 식 계산  
  
- 구문 색 지정  
  
- 개체 검색  
  
- 스택 열거 및 구문 분석  
  
  다음은 디버깅, 식 평가 및 개체 검색을 제공하기 위해 스크립트 엔진에서 지원해야 하는 인터페이스입니다. 이러한 인터페이스는 호스트 애플리케이션에서 문서 컨텍스트와 엔진의 코드 컨텍스트 간에 매핑하고, 디버거 UI를 통해 식 평가, 스택 열거 및 개체 검색을 수행하는 데 사용됩니다.  
  
  [IActiveScriptDebug 인터페이스](../winscript/reference/iactivescriptdebug-interface.md)  
  구문 색 지정 및 코드 컨텍스트 열거를 제공합니다.  
  
  [IActiveScriptErrorDebug 인터페이스](../winscript/reference/iactivescripterrordebug-interface.md)  
  오류에 대한 문서 컨텍스트와 스택 프레임을 반환합니다.  
  
  [IActiveScriptSiteDebug 인터페이스](../winscript/reference/iactivescriptsitedebug-interface.md)  
  호스트가 스크립트 엔진에서 디버거로 링크를 제공했습니다.  
  
  [IDebugCodeContext 인터페이스](../winscript/reference/idebugcodecontext-interface.md)  
  스레드에서 가상 "명령 포인터"를 제공합니다.  
  
  [IEnumDebugCodeContexts 인터페이스](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  문서 컨텍스트에 해당하는 코드 컨텍스트를 열거합니다.  
  
  [IDebugStackFrame 인터페이스](../winscript/reference/idebugstackframe-interface.md)  
  스레드 스택의 논리 스택 프레임을 나타냅니다.  
  
  [IDebugExpressionContext 인터페이스](../winscript/reference/idebugexpressioncontext-interface.md)  
  식을 평가할 수 있는 컨텍스트를 제공합니다.  
  
  [IDebugStackFrameSniffer 인터페이스](../winscript/reference/idebugstackframesniffer-interface.md)  
  논리 스택 프레임을 열거하는 방법을 제공합니다.  
  
  [IDebugExpression 인터페이스](../winscript/reference/idebugexpression-interface.md)  
  비동기적으로 평가된 식을 나타냅니다.  
  
  [IDebugSyncOperation 인터페이스](../winscript/reference/idebugsyncoperation-interface.md)  
  스크립트 엔진이 차단된 특정 스레드에 중첩된 상태에서 수행해야 할 작업을 추상화할 수 있도록 합니다.  
  
  [IDebugAsyncOperation 인터페이스](../winscript/reference/idebugasyncoperation-interface.md)  
  동기식 디버그 작업에 대한 비동기 액세스를 제공합니다.  
  
  [IDebugAsyncOperationCallBack 인터페이스](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  `IDebugAsyncOperation` 인터페이스 평가의 진행 상황과 관련된 상태 이벤트를 제공합니다.  
  
  [IEnumDebugExpressionContexts 인터페이스](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  `IDebugExpressionContexts` 개체의 컬렉션을 열거합니다.  
  
  [IProvideExpressionContexts 인터페이스](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  특정 구성 요소에서 인식하고 있는 식 컨텍스트를 열거하는 방법을 제공합니다.  
  
  [IDebugFormatter 인터페이스](../winscript/reference/idebugformatter-interface.md)  
  언어 또는 IDE에서 VARIANT 값 또는 VARTYPE 형식 및 문자열 간의 변환을 사용자 지정할 수 있도록 합니다.  
  
  [IDebugStackFrameSnifferEx 인터페이스](../winscript/reference/idebugstackframesnifferex-interface.md)  
  PDM에 대한 논리 스택 프레임을 열거합니다.  
  
## <a name="hosts"></a>호스트  
 호스트는 다음을 수행합니다.  
  
- 언어 엔진을 호스팅합니다.  
  
- 개체 모델(스크립트할 수 있는 개체 집합)을 제공합니다.  
  
- 디버그할 수 있는 문서 트리 및 해당 내용을 정의합니다.  
  
- 스크립트를 가상 애플리케이션으로 구성합니다.  
  
  호스트에는 다음 두 가지 종류가 있습니다.  
  
- 단순 호스트는 기본 액티브 스크립팅 인터페이스만 지원합니다. 문서 구조 또는 조직은 제어할 수 없습니다. 이는 언어 엔진에 제공된 스크립트에서 전적으로 결정됩니다.  
  
- 스마트 호스트는 문서 트리, 문서 내용 및 구문 색 지정을 정의할 수 있는 더 큰 인터페이스 집합을 지원합니다. 다음 하위 섹션에서 설명하는 일단의 도우미 인터페이스가 있으므로 호스트를 스마트 호스트로 훨씬 쉽게 만들 수 있습니다.  
  
### <a name="smart-host-helper-interfaces"></a>스마트 호스트 도우미 인터페이스  
 `IDebugDocumentHelper` 메서드는 호스트에서 전체 호스트 인터페이스의 완전한 복잡성(및 성능)을 처리하지 않고도 스마트 호스팅의 이점을 얻는 데 사용할 수 있는 매우 간단한 인터페이스 집합을 제공합니다.  
  
 물론 호스트에서 이러한 인터페이스를 사용할 필요가 없습니다. 그러나 이러한 인터페이스를 사용하면 여러 가지 복잡한 인터페이스를 구현하거나 사용하지 않아도 됩니다.  
  
 [IDebugDocumentHelper 인터페이스](../winscript/reference/idebugdocumenthelper-interface.md)  
 PDM에서 구현되고, 스마트 호스팅에 필요한 많은 인터페이스에 대한 구현을 제공합니다.  
  
 [IDebugDocumentHost 인터페이스](../winscript/reference/idebugdocumenthost-interface.md)  
 구문 색 지정과 같은 호스트 관련 기능을 디버거에 노출하기 위해 호스트에서 구현되었습니다(선택 사항).  
  
 자세한 내용은 [스마트 호스트 도우미 인터페이스 구현](../winscript/implementing-smart-host-helper-interfaces.md)을 참조하세요.  
  
### <a name="full-smart-host-interfaces"></a>전체 스마트 호스트 인터페이스  
 다음은 스마트 호스트가 도우미 인터페이스를 사용하지 않는 경우 구현하거나 사용해야 하는 인터페이스의 전체 집합입니다.  
  
 호스트에서 구현하는 인터페이스:  
  
 [IDebugDocumentInfo 인터페이스](../winscript/reference/idebugdocumentinfo-interface.md)  
 인스턴스화될 수도 있고 그렇지 않을 수도 있는 문서에 대한 정보를 제공합니다.  
  
 [IDebugDocumentProvider 인터페이스](../winscript/reference/idebugdocumentprovider-interface.md)  
 요청 시 문서를 인스턴스화하는 방법을 제공합니다.  
  
 [IDebugDocument 인터페이스](../winscript/reference/idebugdocument-interface.md)  
 모든 디버그 문서에 대한 기본 인터페이스입니다.  
  
 [IDebugDocumentText 인터페이스](../winscript/reference/idebugdocumenttext-interface.md)  
 디버그 문서의 텍스트 전용 버전에 대한 액세스를 제공합니다.  
  
 [IDebugDocumentTextAuthor 인터페이스](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 디버그 문서의 텍스트 전용 버전을 편집할 수 있습니다.  
  
 [IDebugDocumentContext 인터페이스](../winscript/reference/idebugdocumentcontext-interface.md)  
 디버그 중인 문서의 일부에 대한 추상 표현을 제공합니다.  
  
 호스트를 대신하여 PDM에서 구현하는 인터페이스:  
  
 [IDebugApplicationNode 인터페이스](../winscript/reference/idebugapplicationnode-interface.md)  
 프로젝트 트리 내에 컨텍스트를 제공하여 `IDebugDocumentProvider` 인터페이스의 기능을 확장합니다.  
  
## <a name="debugger-ide"></a>디버거 IDE  
 IDE는 언어 독립적 디버깅 UI입니다. 다음과 같은 것을 제공합니다.  
  
- 문서 뷰어/편집기  
  
- 중단점 관리  
  
- 식 평가 및 조사식 창  
  
- 스택 프레임 검색  
  
- 개체/클래스 검색  
  
- 가상 애플리케이션 구조 검색  
  
  디버거에서 구현하는 인터페이스:  
  
  [IApplicationDebugger 인터페이스](../winscript/reference/iapplicationdebugger-interface.md)  
  디버거 IDE 세션에서 노출되는 기본 인터페이스입니다.  
  
  [IApplicationDebuggerUI 인터페이스](../winscript/reference/iapplicationdebuggerui-interface.md)  
  디버거의 UI(사용자 인터페이스)를 통해 외부 구성 요소에 더 많은 제어를 제공합니다.  
  
  [IDebugExpressionCallBack 인터페이스](../winscript/reference/idebugexpressioncallback-interface.md)  
  `IDebugExpression` 평가 진행 상황에 대한 이벤트를 제공합니다.  
  
  [IDebugDocumentTextEvents 인터페이스](../winscript/reference/idebugdocumenttextevents-interface.md)  
  관련 텍스트 문서의 변경 내용을 나타내는 이벤트를 제공합니다.  
  
  [IDebugApplicationNodeEvents 인터페이스](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  `IDebugApplicationNode` 인터페이스에 대한 이벤트 인터페이스를 제공합니다.  
  
### <a name="machine-debug-manager"></a>컴퓨터 디버그 관리자  
 컴퓨터 디버그 관리자는 활성 가상 애플리케이션 목록을 유지 관리하고 열거하여 가상 애플리케이션과 디버거 간의 연결 지점을 제공합니다.  
  
 [IDebugSessionProvider 인터페이스](../winscript/reference/idebugsessionprovider-interface.md)  
 실행 중인 애플리케이션에 대한 디버그 세션을 설정합니다.  
  
 [IMachineDebugManager 인터페이스](../winscript/reference/imachinedebugmanager-interface.md)  
 컴퓨터 디버그 관리자에 대한 기본 인터페이스입니다.  
  
 [IMachineDebugManagerCookie 인터페이스](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 `IMachineDebugManager` 인터페이스와 비슷하지만 이 인터페이스는 디버그 쿠키를 지원합니다.  
  
 [IMachineDebugManagerEvents 인터페이스](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 컴퓨터 디버그 관리자에서 관리하는 실행 중인 애플리케이션 목록의 변경을 알립니다.  
  
 [IEnumRemoteDebugApplications 인터페이스](../winscript/reference/ienumremotedebugapplications-interface.md)  
 컴퓨터에서 실행 중인 애플리케이션을 열거합니다.  
  
### <a name="process-debug-manager"></a>프로세스 디버그 관리자  
 PDM은 다음을 수행합니다.  
  
- 여러 언어 엔진의 디버깅을 동기화합니다.  
  
- 디버깅 가능한 문서의 트리를 유지 관리합니다.  
  
- 스택 프레임을 병합합니다.  
  
- 중단점을 조정하고 언어 엔진을 단계별로 실행합니다.  
  
- 스레드를 추적합니다.  
  
- 비동기 처리에 대한 디버거 스레드를 유지 관리합니다.  
  
- 컴퓨터 디버그 관리자 및 디버거 IDE와 통신합니다.  
  
  다음은 프로세스 디버그 관리자에서 제공하는 인터페이스입니다.  
  
  [IProcessDebugManager 인터페이스](../winscript/reference/iprocessdebugmanager-interface.md)  
  프로세스 디버그 관리자에 대한 기본 인터페이스입니다. 이 인터페이스는 프로세스에서 가상 애플리케이션을 작성, 추가 또는 제거할 수 있습니다.  
  
  [IRemoteDebugApplication 인터페이스](../winscript/reference/iremotedebugapplication-interface.md)  
  실행 중인 애플리케이션을 나타냅니다.  
  
  [IDebugApplication 인터페이스](../winscript/reference/idebugapplication-interface.md)  
  언어 엔진 및 호스트에서 사용할 비원격 디버깅 메서드를 노출합니다.  
  
  [IRemoteDebugApplicationThread 인터페이스](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  특정 애플리케이션 내의 실행 스레드를 나타냅니다.  
  
  [IDebugApplicationThread 인터페이스](../winscript/reference/idebugapplicationthread-interface.md)  
  언어 엔진과 호스트에서 스레드 동기화를 제공하고 스레드별 디버그 상태 정보를 유지할 수 있도록 합니다.  
  
  [IEnumRemoteDebugApplicationThreads 인터페이스](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  애플리케이션에서 실행 중인 스레드를 열거합니다.  
  
  [IDebugThreadCall 인터페이스](../winscript/reference/idebugthreadcall-interface.md)  
  마샬링된 호출을 발송합니다.  
  
  [IDebugApplicationNode 인터페이스](../winscript/reference/idebugapplicationnode-interface.md)  
  계층 구조에서 문서의 위치를 유지 관리합니다.  
  
  [IEnumDebugApplicationNodes 인터페이스](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  애플리케이션과 연결된 노드의 자식 노드를 열거합니다.  
  
  [IEnumDebugStackFrames 인터페이스](../winscript/reference/ienumdebugstackframes-interface.md)  
  엔진에서 병합된 스레드에 해당하는 스택 프레임을 열거합니다.  
  
  [IDebugCookie 인터페이스](../winscript/reference/idebugcookie-interface.md)  
  스크립트 디버거에서 디버그 쿠키를 설정할 수 있도록 합니다.  
  
  [IDebugHelper 인터페이스](../winscript/reference/idebughelper-interface.md)  
  개체 브라우저에 대한 팩터리 및 스크립트 엔진에 대한 간단한 연결 지점으로 사용됩니다.  
  
  [ISimpleConnectionPoint 인터페이스](../winscript/reference/isimpleconnectionpoint-interface.md)  
  특정 연결 지점에서 발생한 이벤트를 설명하고 열거하는 간단한 방법을 스크립트 엔진에 제공합니다.  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 인터페이스](../winscript/reference/active-script-debugger-interfaces.md)
