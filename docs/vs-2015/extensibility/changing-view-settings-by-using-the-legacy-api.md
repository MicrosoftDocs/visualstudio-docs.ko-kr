---
title: 레거시 API를 사용 하 여 보기 설정 변경 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184473"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>레거시 API를 사용하여 보기 설정 변경
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자가 **옵션** 대화 상자를 사용 하 여 자동 줄 바꿈, 선택 여백, 가상 공간 등의 핵심 편집기 기능에 대 한 설정을 변경할 수 있습니다. 그러나 이러한 설정을 프로그래밍 방식으로 변경할 수도 있습니다.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>레거시 API를 사용 하 여 설정 변경  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>인터페이스는 텍스트 편집기 속성의 집합을 노출 합니다. 텍스트 뷰에는 텍스트 보기의 프로그래밍 방식으로 변경 된 설정 그룹을 나타내는 속성 (GUID_EditPropCategory_View_MasterSettings) 범주가 포함 되어 있습니다. 이러한 방식으로 보기 설정이 변경 된 후에는 다시 설정 될 때까지 **옵션** 대화 상자에서 변경할 수 없습니다.  
  
 핵심 편집기의 인스턴스에 대 한 보기 설정을 변경 하는 일반적인 프로세스는 다음과 같습니다.  
  
1. `QueryInterface` <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 인터페이스에 대해 ()를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> .  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>매개 변수에 대 한 GUID_EditPropCategory_View_MasterSettings 값을 지정 하 여 메서드를 호출 합니다 `rguidCategory` .  
  
     이렇게 하면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> 뷰의 강제 속성 집합이 포함 된 인터페이스에 대 한 포인터가 반환 됩니다. 이 그룹의 모든 설정은 영구적으로 강제 적용 됩니다. 이 그룹에 없는 설정은 **옵션** 대화 상자 또는 사용자의 명령에 지정 된 옵션을 따릅니다.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>매개 변수에 적절 한 설정 값을 지정 하 여 메서드를 호출 `idprop` 합니다.  
  
     예를 들어 자동 줄 바꿈이 적용 되도록 하려면를 호출 하 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 고 매개 변수에 대해 VSEDITPROPID_ViewLangOpt_WordWrap 값을 지정 `vt` `idprop` 합니다. 이 호출에서 `vt` 는 VT_BOOL 형식의 변형 이며 `vt.boolVal` VARIANT_TRUE 됩니다.  
  
## <a name="resetting-changed-view-settings"></a>변경 된 보기 설정 다시 설정  
 핵심 편집기의 인스턴스에 대 한 변경 된 뷰 설정을 다시 설정 하려면 메서드를 호출 하 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> 고 매개 변수에서 적절 한 설정 값을 지정 합니다 `idprop` .  
  
 예를 들어 자동 줄 바꿈이 부동으로 표시 되도록 하려면를 호출 하 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> 고 매개 변수에 VSEDITPROPID_ViewLangOpt_WordWrap 값을 지정 하 여 속성 범주에서 제거 `idprop` 합니다.  
  
 핵심 편집기에 대 한 모든 변경 된 설정을 한 번에 제거 하려면 매개 변수에 대 한 VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt 값을 지정 `idprop` 합니다. 이 호출에서 vt는 VT_BOOL 형식의 변형 이며 boolVal는 VARIANT_TRUE 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [핵심 편집기 내부](../extensibility/inside-the-core-editor.md)   
 [레거시 API를 사용 하 여 theText View에 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [옵션 대화 상자](../ide/reference/options-dialog-box-visual-studio.md)
