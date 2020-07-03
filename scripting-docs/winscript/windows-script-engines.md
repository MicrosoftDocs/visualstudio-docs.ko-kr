---
title: Windows 스크립트 엔진 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27a500f9df91738e2db563f7e37ee646925b674e
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835695"
---
# <a name="windows-script-engines"></a>Windows 스크립트 엔진
Microsoft Windows 스크립트 엔진을 구현하려면 다음 인터페이스를 지원하는 OLE COM 개체를 만듭니다.  
  
|||  
|-|-|  
|인터페이스|설명|  
|[IActiveScript](../winscript/reference/iactivescript.md)|기본 스크립팅 기능을 제공합니다. 이 인터페이스의 구현이 필요합니다.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|스크립트 텍스트를 추가하고, 식을 평가하는 등의 기능을 제공합니다. 이 인터페이스 구현은 선택 사항입니다. 그러나 구현되지 않으면 스크립트 엔진에서 스크립트를 로드하기 위해 IPersist* 인터페이스 중 하나를 구현해야 합니다.|  
|IPersist*|지속성 지원을 제공합니다. [IActiveScriptParse](../winscript/reference/iactivescriptparse.md)가 구현되지 않은 경우 다음 인터페이스 중 하나 이상을 구현해야 합니다.<br /><br /> IPersistStorage: OBJECT 태그의 DATA={url} 특성 지원을 제공합니다.<br /><br /> IPersistStreamInit: OBJECT 태그의 DATA="string-encoded byte stream" 특성 외에도 `IPersistStorage`와 동일한 지원을 제공합니다.<br /><br /> IPersistPropertyBag: OBJECT 태그의 PARAM= 특성 지원을 제공합니다.|  
  
> [!NOTE]
> `IPersist*`를 통해 스크립트 상태를 저장하거나 복원하기 위해 스크립팅 엔진을 전혀 호출하지 않을 수 있습니다. 대신, [IActiveScriptParse](../winscript/reference/iactivescriptparse.md)는 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md)를 호출하여 빈 스크립트를 작성하는 데 사용하고, [IActiveScriptParse::AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md)를 사용하여 scriptlet을 이벤트에 추가하고 연결한 다음 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)로 일반 코드를 추가합니다. 그런데도 다른 호스트 애플리케이션에서 사용할 수 있으므로 스크립팅 엔진에서 하나 이상의 `IPersist*` 인터페이스(`IPersistStreamInit`가 선호됨)를 완벽하게 구현해야 합니다.  
  
 다음 섹션에서는 Windows 스크립팅 엔진 구현에 대해 자세히 설명합니다.  
  
 자세한 내용을 [Windows 스크립트 인터페이스 참조](../winscript/reference/windows-script-interfaces-reference.md)를 확인하세요.  
  
## <a name="registry-standard"></a>레지스트리 표준  
 Windows 스크립트 엔진에서는 범주 식별자를 사용하여 자신을 식별할 수 있습니다. Windows 스크립트에서는 현재 두 개의 범주 식별자를 정의합니다.  
  
|||  
|-|-|  
|범주|설명|  
|CATID_ActiveScript|클래스 식별자 (Clsid)가 최소한 [IActiveScript](../winscript/reference/iactivescript.md) 인터페이스와 지 속성 메커니즘 ( `IPersistStorage` , `IPersistStreamInit` 또는 IPersistPropertyBag 인터페이스)을 지 원하는 Windows 스크립트 엔진 임을 나타냅니다.|  
|CATID_ActiveScriptParse|CLSID가 최소한 [IActiveScript](../winscript/reference/iactivescript.md) 및 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 인터페이스를 지원하는 Windows 스크립트 엔진임을 나타냅니다.|  
  
 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md)는 진정한 지속성 메커니즘은 아니지만 기능적으로 `IPersist*::InitNew`와 동일한 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) 메서드를 지원합니다.  
  
## <a name="script-engine-states"></a>스크립트 엔진 상태  
 지정된 시간에 Windows 스크립트 엔진의 상태는 여러 가지 중 하나일 수 있습니다.  
  
|||  
|-|-|  
|시스템 상태|Description|  
|초기화되지 않음|스크립트는 IPersist* 인터페이스를 사용하여 초기화 또는 로드할 수 었거나 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 인터페이스 집합이 없습니다. 일반적으로 스크립팅 엔진은 스크립트가 로드될 때까지 이 상태에서 사용할 수 없습니다.|  
|초기화됨|스크립트가 `IPersist*` 인터페이스를 통해 초기화되었으며 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 인터페이스 집합이 있지만 호스트 개체와 싱크 이벤트에 연결되지 않았습니다. 이 상태는 단순히 `IPersist*::Load`, `IPersist*::InitNew` 또는 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) 메서드가 완료되었으며 [IActiveScript::SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md) 메서드가 호출되었음을 나타냅니다. 엔진은 이 모드에서 코드를 실행할 수 없습니다. 엔진은 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) 메서드를 통해 호스트가 전달한 코드를 큐에 넣으며 시작 상태로 전환하고 나면 코드를 실행합니다.<br /><br /> 언어는 의미 체계가 광범위하게 달라질 수 있으므로 스크립팅 엔진에서 이 상태 전환을 지원하지 않아도 됩니다. 그러나 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) 메서드를 지원하는 엔진에서는 이 상태 전환을 지원해야 합니다. 호스트에서 이 전환에 대비하고 다음과 같이 적절한 조치를 취해야 합니다. 현재 스크립팅 엔진을 릴리스하고, 새 스크립팅 엔진을 만들며, `IPersist*::Load`, `IPersist*::InitNew`, 또는 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md)를 호출합니다([IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)도 호출할 가능성이 큼). 이 전환을 사용하려면 위의 단계를 최적화해야 합니다. 스크립팅 엔진이 명명된 항목에 대해 얻은 모든 정보와 명명된 항목을 설명하는 형식 정보는 유효한 상태로 유지됩니다.<br /><br /> 언어는 매우 다양하므로 이 전환의 정확한 의미 체계를 정의하는 것이 어렵습니다. 스크립팅 엔진은 최소한 모든 이벤트에서 연결을 끊고 [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) 메서드를 통해 확보한 모든 SCRIPTINFO_IUNKNOWN 포인터를 릴리스해야 합니다. 스크립트를 다시 실행하고 나면 엔진에서 이러한 포인터를 다시 얻어야 합니다. 또한 스크립팅 엔진에서는 언어에 적합한 초기 상태로 스크립트를 다시 설정해야 합니다. 예를 들어 VBScript에서는 모든 변수를 다시 설정하고 SCRIPTTEXT_ISPERSISTENT 플래그를 설정한 상태로 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)를 호출하여 동작으로 추가된 모든 코드를 유지합니다. 다른 언어에서는 현재 값(코드/데이터 분리가 없으므로 Lisp 등)을 유지하거나 잘 알려진 상태(정적으로 초기화된 변수가 있는 언어 포함)로 다시 설정해야 할 수도 있습니다.<br /><br /> 시작된 상태로 전환의 의미 체계는 스크립팅 엔진을 저장하기 위한 `IPersist*::Save` 호출과 동일(즉, 스크립팅 엔진을 동일한 상태로 둠)해야 하며, 그 다음에는 새 스크립팅 엔진을 로드하기 위한 `IPersist*::Load`와 동일해야 합니다. 이러한 조치의 의미 체계는 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md)과 동일합니다. 아직 `IActiveScript::Clone` 또는 `IPersist*`를 지원하지 않는 스크립팅 엔진에서는 `IActiveScript::Clone` 또는 `IPersist*` 지원을 나중에 추가한 경우, 시작 상태로의 전환이 위의 조건을 위반하지 않도록 해당 전환의 작동 방식을 신중하게 고려해야 합니다.<br /><br /> 이처럼 시작됨 상태로 전환하는 동안 스크립팅 엔진이 적절한 소멸자 등이 스크립트에서 실행되고 나면 이벤트 싱크에서 연결을 끊습니다. 이러한 소멸자가 실행되지 않게 하려면 호스트에서 시작됨 상태로 이동하기 전에 먼저 연결이 끊긴 상태로 스크립트를 이동할 수 있습니다.<br /><br /> [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md)를 사용하여 현재 이벤트 등이 실행을 완료할 때까지 대기하지 않고 실행 중인 스크립트 스레드를 취소합니다.|  
|시작됨|초기화됨 상태에서 시작됨 상태로 전환하면 엔진이 초기화됨 상태에서 큐에 지정된 모든 코드를 실행하게 됩니다. 시작됨 상태에 있는 동안 엔진에서 코드를 실행할 수 있지만, [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) 메서드를 통해 추가된 이벤트에는 연결하지 않습니다. 엔진은 [IActiveScript::GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md) 메서드에서 얻은 IDispatch 인터페이스를 호출하거나 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)를 호출하여 코드를 실행할 수 있습니다. 추가 백그라운드 초기화(점진적 로드)가 여전히 진행 중일 수 있으므로, SCRIPTSTATE_CONNECTED 플래그를 설정한 상태로 [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) 메서드를 호출하면 초기화가 완료될 때까지 스크립트가 차단될 수 있습니다.|  
|연결됨|호스트 개체에서 이벤트를 싱크하기 위해 스크립트를 로드하여 연결합니다. 초기화됨 상태에서 전환하는 경우, 스크립팅 엔진에서 필요한 조치를 수행하여 시작됨 상태로 전환해야, 연결된 상태로 전환되어 이벤트에 연결할 수 있습니다.|  
|연결 끊김|스크립트가 로드되어 런타임 상태에 있지만, 호스트 개체의 싱크 이벤트에서 임시로 연결이 끊겨 있습니다. 이 작업은 논리적(받은 이벤트 무시) 또는 물리적(적절한 연결 지점에서 IConnectionPoint::Unadvise 호출)으로 수행할 수 있습니다. 초기화됨 상태에서 전환하는 경우, 스크립팅 엔진에서 필요한 조치를 수행하여 시작됨 상태로 전환해야, 연결이 끊김 상태로 전환될 수 있습니다. 상태가 변경되기 전에 진행 중인 이벤트 싱크가 완료됩니다([IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md)를 사용하여 실행 중인 스크립트 스레드 취소). 이 상태로 전환해도 스크립트가 다시 설정되지 않고, 스크립트의 런타임 상태가 다시 설정되지 않으며 스크립트 초기화 절차가 실행되지 않는다는 점에서 이 상태와 초기화됨 상태는 구별됩니다.|  
|closed|스크립트가 종료되었습니다. 스크립트 엔진이 더 이상 작동하지 않고 대부분의 메서드에 대해 오류를 반환합니다.|  
  
 다음 그림은 다양한 스크립팅 엔진 상태 사이의 관계를 보여주고, 한 상태에서 다른 상태로 전환되게 하는 메서드를 보여줍니다.  
  
 다음 그림은 스크립팅 엔진이 다양한 상태 전환 중에 수행하는 작업을 보여줍니다.  
  
## <a name="scripting-engine-threading"></a>스크립팅 엔진 스레딩  
 Windows 스크립트 엔진은 여러 환경에서 사용할 수 있으므로, 실행 모델을 최대한 유연하게 유지하는 것이 중요합니다. 예를 들어, 서버 기반 호스트는 Windows 스크립트를 효율적인 방식으로 사용하는 동안 다중 스레드 디자인을 유지해야 합니다. 마찬가지로, 일반 애플리케이션과 같이 스레딩을 사용하지 않는 호스트에는 스레딩 관리의 부담이 없어야 합니다. Windows 스크립트에서는 자유 스레드 스크립팅 엔진이 호스트를 다시 호출할 수 있는 방법을 제한하여 호스트에 이 부담을 주지 않으므로 균형을 맞출 수 있습니다.  
  
 서버에서 사용되는 스크립팅 엔진은 일반적으로 자유 스레딩 COM 개체로 구현됩니다. 즉, [IActiveScript](../winscript/reference/iactivescript.md) 인터페이스와 해당 관련 인터페이스의 메서드를 마샬링하지 않고 프로세스의 모든 스레드에서 호출할 수 있습니다. 그러나 OLE는 현재 자유 스레드 개체의 프로세스간 마샬링을 지원 하지 않으므로이는 스크립팅 엔진을 in-process 서버로 구현 해야 함을 의미 합니다. 동기화는 스크립팅 엔진의 책임입니다. 내부적으로 재진입하지 않는 스크립팅 엔진이나 다중 스레드되지 않은 언어 모델의 경우, 동기화를 수행하기 위해 뮤텍스로 스크립트 엔진에 대한 액세스를 직렬화하기만 하면 됩니다. 물론 [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md)와 같은 특정 메서드는 이 방식으로 직렬화할 수 없으므로 다른 스레드에서 중단 스크립트를 종료해야 합니다.  
  
 일반적으로 [IActiveScript](../winscript/reference/iactivescript.md)가 자유 스레드라는 점은 대개 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 인터페이스와 호스트의 개체 모델도 자유 스레드여야 함을 나타냅니다. 따라서 호스트 구현이 상당히 어려워집니다. 특히 호스트가 개체 모델에 아파트 모델 ActiveX 제어 또는 단일 스레드를 포함하는 단일 스레드 Windows 기반 애플리케이션인 일반적인 경우에 더욱 그렇습니다. 따라서 스크립팅 엔진에서 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md)를 사용할 때 다음과 같은 제한 사항이 있습니다.  
  
 스크립트 사이트는 항상 호스트 스레드의 컨텍스트에서 호출됩니다. 즉, 스크립팅 엔진은 스크립팅 엔진이 만든 스레드의 컨텍스트에서는 스크립트 사이트를 호출하지 않으며, [IActiveScript](../winscript/reference/iactivescript.md) 및 해당 파생 항목을 통하거나, 노출된 스크립팅 엔진의 디스패치 개체를 통하거나, Windows 메시지를 통하거나, 호스트의 개체 모델에 있는 이벤트 소스에서 호출된 스크립팅 엔진 메서드에서만 호출합니다.  
  
 스크립트 사이트는 단순 스레드 상태 컨트롤 메서드의 컨텍스트(예: [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) 메서드) 또는 [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) 메서드에서는 호출되지 않습니다.  
  
## <a name="see-also"></a>참조  
 [Windows 스크립트 인터페이스](../winscript/windows-script-interfaces.md)
