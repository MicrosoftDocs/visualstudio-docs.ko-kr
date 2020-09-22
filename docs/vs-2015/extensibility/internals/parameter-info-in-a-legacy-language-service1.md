---
title: 레거시 언어 Service1의 매개 변수 정보 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b1707313c40e7ea720fff3b9f70546af00ea486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841387"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>레거시 언어 서비스의 매개 변수 정보
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IntelliSense 매개 변수 정보 도구 설명에서는 사용자에 게 언어 구문의 위치에 대 한 힌트를 제공 합니다.  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/extending-the-editor-and-language-services.md)을 참조 하세요.  
  
> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.  
  
## <a name="how-parameter-info-tooltips-work"></a>매개 변수 정보 도구 설명의 작동 방식  
 편집기에서 문을 입력 하면 VSPackage는 입력 하는 문의 정의를 포함 하는 작은 도구 설명 창을 표시 합니다. 예를 들어 Microsoft Foundation Classes (MFC) 문 (예:)을 입력 하 `pMainFrame ->UpdateWindow` 고 여는 괄호 키를 눌러 매개 변수 목록을 시작 하는 경우 메서드 정의를 표시 하는 메서드 팁이 나타납니다 `UpdateWindow` .  
  
 매개 변수 정보 도구 설명은 일반적으로 문 완성과 함께 사용 됩니다. 메서드 이름 또는 키워드 다음에 매개 변수 또는 기타 형식이 지정 된 정보를 포함 하는 언어에 가장 유용 합니다.  
  
 매개 변수 정보 도구 설명은 명령 가로채기를 통해 언어 서비스에 의해 시작 됩니다. 사용자 문자를 가로채는 경우 언어 서비스 개체는 인터페이스를 구현 하 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 고 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 인터페이스에서 메서드를 호출 하 여 텍스트 뷰를 구현에 전달 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . 명령 필터는 코드 창에 입력 하는 명령을 차단 합니다. 명령 정보를 모니터링 하 여 사용자에 게 매개 변수 정보를 표시 하는 시기를 확인 합니다. 문 완성, 오류 표식 등에 동일한 명령 필터를 사용할 수 있습니다.  
  
 언어 서비스에서 힌트를 제공할 수 있는 키워드를 입력 하면 언어 서비스에서 개체를 만들고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 인터페이스에서 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 힌트를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 표시 하도록 IDE에 알립니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>를 사용 하 여 개체를 만들고 `VSLocalCreateInstance` coclass를 지정 `CLSID_VsMethodTipWindow` 합니다. `VsLocalCreateInstance` 는 로컬 레지스트리를 호출 하 `QueryService` 고에 `CreateInstance` 대해이 개체에서를 호출 하는 헤더 파일 vsdoc에 정의 된 함수입니다 `CLSID_VsMethodTipWindow` .  
  
## <a name="providing-a-method-tip"></a>메서드 설명 제공  
 메서드 설명을 제공 하려면 인터페이스에서 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 인터페이스의 구현을 전달 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 합니다.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>클래스가 호출 될 때 해당 메서드는 다음 순서로 호출 됩니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     현재 텍스트 버퍼에 있는 관련 데이터의 위치와 길이를 반환 합니다. 이렇게 하면 도구 설명 창에서 해당 데이터를 가리지 않도록 IDE에 지시 합니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     처음에 표시 하려는 메서드 번호 (0부터 시작)를 반환 합니다. 예를 들어 0을 반환 하는 경우 첫 번째 오버 로드 된 메서드가 처음에 표시 됩니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     현재 컨텍스트에서 적용할 수 있는 오버 로드 된 메서드의 수를 반환 합니다. 이 메서드에 대해 1 보다 큰 값을 반환 하면 텍스트 뷰는 위쪽 및 아래쪽 화살표를 표시 합니다. 아래쪽 화살표를 클릭 하면 IDE에서 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> . 위쪽 화살표를 클릭 하면 IDE에서 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     매개 변수 정보 도구 설명의 텍스트는 및 메서드를 여러 번 호출 하는 동안 생성 됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     메서드에 표시할 매개 변수 수를 반환 합니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     표시 하려는 오버 로드에 해당 하는 메서드 번호를 반환 하는 경우이 메서드를 호출한 다음 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> 합니다.  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     메서드 설명이 표시 될 때 편집기를 업데이트 하도록 언어 서비스에 알립니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>메서드에서 다음을 호출 합니다.  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>메서드 팁 창을 닫을 때 메서드에 대 한 호출을 받게 됩니다.
