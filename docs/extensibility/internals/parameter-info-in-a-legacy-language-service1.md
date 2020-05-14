---
title: 레거시 언어 서비스의 매개 변수 정보1 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706796"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>레거시 언어 서비스의 매개 변수 정보
IntelliSense 매개 변수 정보 도구 설명은 언어 구문에 있는 위치에 대한 힌트를 사용자에게 제공합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/extending-the-editor-and-language-services.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="how-parameter-info-tooltips-work"></a>매개 변수 정보 도구 설명의 작동 방식
 편집기에서 문을 입력하면 VSPackage는 입력할 명령문의 정의가 포함된 작은 도구 설명 창을 표시합니다. 예를 들어 Microsoft 기초 클래스(MFC) `pMainFrame ->UpdateWindow`문을 입력하고 여참조 괄호 키를 눌러 매개 변수를 나열하면 메서드 정의가 표시되는 `UpdateWindow` 메서드 설명이 나타납니다.

 매개 변수 정보 도구 설명은 일반적으로 문 완성과 함께 사용됩니다. 메서드 이름 또는 키워드 다음에 매개 변수 또는 기타 형식정보가 있는 언어에 가장 유용합니다.

 매개 변수 정보 도구 설명은 명령 차단을 통해 언어 서비스에 의해 시작됩니다. 사용자 문자를 가로채려면 언어 서비스 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 개체가 인터페이스를 구현하고 인터페이스에서 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 호출하여 텍스트 뷰에 포인터를 전달해야 합니다. 명령 필터는 코드 창에 입력하는 명령을 가로채는 것입니다. 명령 정보를 모니터링하여 사용자에게 매개 변수 정보를 표시할 시기를 알 수 있습니다. 문 완료, 오류 마커 등에 동일한 명령 필터를 사용할 수 있습니다.

 언어 서비스가 힌트를 제공할 수 있는 키워드를 입력하면 언어 서비스가 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 개체를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 만들고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 인터페이스에서 메서드를 호출하여 IDE에 힌트를 표시하도록 알립니다. 공동 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 클래스를 `VSLocalCreateInstance` `CLSID_VsMethodTipWindow`사용하고 지정하는 개체를 만듭니다. `VsLocalCreateInstance`은 로컬 레지스트리를 호출하고 `QueryService` 에 대해 이 개체를 호출하는 `CreateInstance` 헤더 파일 `CLSID_VsMethodTipWindow`vsdoc.h에 정의된 함수입니다.

## <a name="providing-a-method-tip"></a>방법 팁 제공
 메서드 팁을 제공하려면 인터페이스에서 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 호출하여 인터페이스 구현을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 전달합니다.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 클래스가 호출되면 해당 메서드는 다음 순서로 호출됩니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     현재 텍스트 버퍼에서 관련 데이터의 위치와 길이를 반환합니다. 이렇게 하면 IDE가 도구 설명 창을 사용하여 해당 데이터를 모호하게 하지 않도록 지시합니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     처음에 표시할 메서드 번호(0기반 인덱스)를 반환합니다. 예를 들어 0을 반환하면 첫 번째 오버로드된 메서드가 처음에 표시됩니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     현재 컨텍스트에서 적용할 수 있는 오버로드된 메서드의 수를 반환합니다. 이 메서드에 대해 1보다 큰 값을 반환하면 텍스트 보기가 위쪽 및 아래쪽 화살표를 표시합니다. 아래쪽 화살표를 클릭하면 IDE가 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> 메서드를 호출합니다. 위쪽 화살표를 클릭하면 IDE가 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> 메서드를 호출합니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     매개 변수 정보 도구 설명의 텍스트는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> 메서드에 대한 여러 호출 중에 생성됩니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     메서드에 표시할 매개 변수 수를 반환합니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     표시하려는 오버로드와 해당하는 메서드 번호를 반환하면 이 메서드가 호출되고 메서드에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 대한 호출이 옵니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     메서드 팁이 표시될 때 언어 서비스에 편집기를 업데이트하도록 알립니다. 메서드에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 다음을 호출합니다.

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     메서드 팁 창을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 닫을 때 메서드에 대 한 호출을 받습니다.
