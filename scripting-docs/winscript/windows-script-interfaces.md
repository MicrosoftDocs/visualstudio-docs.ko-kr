---
title: Windows 스크립트 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 141f3f0e60e797a4104c3e276775631f6e9196c5
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835409"
---
# <a name="windows-script-interfaces"></a>Windows 스크립트 인터페이스

Microsoft Windows 스크립트 인터페이스는 애플리케이션에서 스크립팅 및 OLE 자동화를 추가할 수 있는 방법을 제공합니다. Windows 스크립트를 사용하는 스크립팅 호스트는 여러 원본 및 공급업체의 스크립팅 엔진을 사용하여 구성 요소 간의 스크립팅을 관리할 수 있습니다. 스크립트 자체의 구현(언어, 구문, 영구 형식, 실행 모델 등)은 스크립트 공급업체에 위임합니다.

Windows 스크립트 설명서는 다음 섹션으로 구분됩니다.

[Windows 스크립트 호스트](../winscript/windows-script-hosts.md)

[Windows 스크립트 엔진](../winscript/windows-script-engines.md)

[액티브 스크립트 디버깅 개요](../winscript/active-script-debugging-overview.md)

[액티브 스크립트 프로파일링 개요](../winscript/active-script-profiling-overview.md)

[Windows 스크립트 인터페이스 참조](../winscript/reference/windows-script-interfaces-reference.md)

## <a name="windows-script-background"></a>Windows 스크립트 배경 정보

Windows 스크립트 인터페이스는 Windows 스크립트 호스트와 Windows 스크립트 엔진의 두 범주로 나뉩니다. 호스트는 스크립팅 엔진을 만들고 엔진을 호출하여 스크립트를 실행합니다. Windows 스크립트 호스트의 예는 다음과 같습니다.

- Microsoft Internet Explorer

- 인터넷 작성 도구

- 셸

Windows 스크립트 엔진은 다음을 포함하여 모든 언어 또는 런타임 환경에서 개발할 수 있습니다.

- Microsoft VBScript(Visual Basic Scripting Edition)

- Perl

- Lisp

최대한 유연하게 호스트를 구현하기 위해 Windows 스크립트용 OLE 자동화 래퍼가 제공됩니다. 그러나 이 래퍼 개체를 사용하여 스크립팅 엔진을 인스턴스화하는 호스트에는 Windows 스크립트를 직접 사용하는 경우에 적용되는 런타임 네임스페이스, 지속성 모델 등에 대한 제어 수준이 없습니다.

Windows 스크립트 디자인에서는 비제작 호스트(예: 브라우저 및 뷰어) 및 스크립트 엔진(예: VBScript)을 간단하게 유지할 수 있도록 제작 환경에서만 필요한 인터페이스 요소를 격리합니다.

## <a name="windows-script-basic-architecture"></a>Windows 스크립트 기본 아키텍처

다음 그림에서는 Windows 스크립트 호스트와 Windows 스크립트 엔진 간의 상호 작용을 보여 줍니다.

호스트와 엔진 간의 상호 작용에 관련된 단계는 다음 목록에 나와 있습니다.

1. 프로젝트를 만듭니다. 호스트에서 프로젝트 또는 문서를 로드합니다. (이 단계는 Windows 스크립트만으로 한정되지 않지만 완성도를 높이기 위해 여기에 포함되었습니다.)

2. Windows 스크립트 엔진을 만듭니다. 호스트는 `CoCreateInstance`를 호출하여 새 Windows 스크립트 엔진을 만들고, 사용할 특정 스크립팅 엔진의 CLSID(클래스 식별자)를 지정합니다. 예를 들어 Internet Explorer의 HTML 브라우저는 HTML 태그의 CLSID = 특성을 통해 스크립팅 엔진의 클래스 식별자를 받습니다 \<OBJECT> .

3. 스크립트를 로드합니다. 스크립트 내용이 지속되면 호스트는 스크립트 스토리지, 스트림 또는 속성 모음을 제공하기 위해 스크립트 엔진의 `IPersist*::Load` 메서드를 호출합니다. 그렇지 않으면 호스트에서 `IPersist*::InitNew` 또는 [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) 메서드를 사용하여 Null 스크립트를 만듭니다. 스크립트를 텍스트로 유지하는 호스트는 [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)를 사용하여 `IActiveScriptParse::InitNew`를 호출한 후 스크립팅 엔진에 스크립트의 텍스트를 제공할 수 있습니다.

4. 명명된 항목을 추가합니다. 호스트에서 스크립팅 엔진의 네임스페이스로 가져온 명명된 최상위 항목(예: 페이지 및 양식) 각각에 대해 [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) 메서드를 호출하여 엔진의 네임스페이스에 항목을 만듭니다. 명명된 최상위 항목이 이미 3단계에서 로드된 스크립트의 지속성 상태의 일부인 경우 이 단계는 필요하지 않습니다. 호스트는 `IActiveScript::AddNamedItem`을 사용하여 명명된 하위 수준 항목(예: HTML 페이지의 컨트롤)을 추가하지 않습니다. 대신 엔진에서 호스트의 `ITypeInfo` 및 `IDispatch` 인터페이스를 사용하여 최상위 항목의 하위 수준 항목을 간접적으로 가져옵니다.

5. 스크립트를 실행합니다. 호스트는 [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) 메서드에 SCRIPTSTATE_CONNECTED 플래그를 설정하여 엔진에서 스크립트 실행을 시작하도록 합니다. 이 호출은 스크립팅된 `main()` 함수와 비슷한 방식으로 정적 바인딩, 이벤트 연결(아래 참조) 및 코드 실행을 포함한 모든 스크립팅 엔진 생성 작업을 수행할 가능성이 높습니다.

6. 항목 정보를 가져옵니다. 스크립트 엔진은 기호를 최상위 항목에 연결해야 할 때마다 지정된 항목에 대한 정보를 반환하는 [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) 메서드를 호출합니다.

7. 이벤트를 연결합니다. 실제 스크립트를 시작하기 전에 스크립팅 엔진은 `IConnectionPoint` 인터페이스를 통해 관련된 모든 개체의 이벤트에 연결합니다.

8. 속성 및 메서드를 호출합니다. 스크립트가 실행되면 스크립팅 엔진은 `IDispatch::Invoke` 또는 다른 표준 OLE 바인딩 메커니즘을 통해 명명된 개체에 대한 메서드 및 속성에 대한 참조를 인식합니다.

## <a name="windows-script-terms"></a>Windows 스크립트 용어

이 목록에는 이 문서에서 사용된 스크립팅 관련 용어에 대한 정의가 포함되어 있습니다.

|용어|정의|
|----------|----------------|
|코드 개체|Visual Basic의 양식 뒤에 있는 모듈 또는 명명된 항목과 연결된 C++ 클래스와 같이 명명된 항목과 연결된 스크립팅 엔진에서 만든 인스턴스입니다. 오히려 이는 호스트 또는 스크립트가 아닌 다른 엔터티에서 코드 개체를 조작할 수 있도록 OLE 자동화를 지원하는 OLE COM(구성 요소 개체 모델) 개체입니다.|
|명명된 항목|호스트가 스크립트에 흥미로운 것으로 간주하는 OLE COM 개체(오히려 OLE 자동화를 지원하는 개체)입니다. 예를 들어 웹 브라우저의 HTML 페이지 및 브라우저와 Microsoft Word의 문서 및 대화 상자가 있습니다.|
|스크립트|스크립팅 엔진에서 실행하는 프로그램을 구성하는 데이터입니다. 스크립트는 텍스트 조각, `pcode` 블록 또는 컴퓨터 전용의 실행 가능 바이트 코드를 포함하여 실행 가능한 모든 연속 데이터일 수 있습니다. 호스트는 `IPersist*` 인터페이스 중 하나 또는 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 인터페이스를 통해 스크립팅 엔진에 스크립트를 로드합니다.|
|스크립팅 엔진|스크립트를 처리하는 OLE 개체입니다. 스크립팅 엔진은 [IActiveScript](../winscript/reference/iactivescript.md) 및 필요에 따라 [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 인터페이스를 구현합니다.|
|스크립팅 호스트|Windows 스크립트 엔진을 소유하는 애플리케이션 또는 프로그램입니다. 호스트는 [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 및 필요에 따라 [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md) 인터페이스를 구현합니다.|
|스크립틀릿|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md) 인터페이스를 통해 개체에 연결되는 스크립트의 일부입니다. 스크립틀릿의 집계 컬렉션이 스크립트입니다.|
|스크립트 언어|스크립트가 작성된 언어(예: VBScript) 및 해당 언어의 의미 체계입니다.|