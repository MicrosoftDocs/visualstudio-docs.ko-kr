---
title: '방법: 기본 제공 글꼴 및 색 구성표 액세스 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685315"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>방법: 기본 제공 글꼴 및 색 구성표에 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio IDE (통합 개발 환경)에는 편집기 창과 연결 된 글꼴 및 색의 스키마가 있습니다. 인터페이스를 통해이 체계에 액세스할 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
 기본 제공 글꼴 및 색 구성표를 사용 하려면 VSPackage가 다음을 수행 해야 합니다.  
  
- 기본 글꼴 및 색 서비스에 사용할 범주를 정의 합니다.  
  
- 기본 글꼴 및 색 서버를 사용 하 여 범주를 등록 합니다.  
  
- 및 인터페이스를 사용 하 여 특정 창이 기본 제공 표시 항목 및 범주를 사용 한다는 것을 IDE에 알립니다 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` .  
  
  IDE는 결과 범주를 창의 핸들로 사용 합니다. 범주 이름은 **글꼴 및 색** 속성 페이지의 **설정 표시:** 드롭다운 상자에 표시 됩니다.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>기본 제공 글꼴 및 색을 사용 하 여 범주를 정의 하려면  
  
1. 임의의 GUID를 만듭니다.  
  
    이 GUID는 범주를 고유 하 게 식별 하는 데 사용 됩니다<strong>.</strong> 이 범주는 IDE의 기본 글꼴 및 색 사양을 재사용 합니다.  
  
   > [!NOTE]
   > 또는 다른 인터페이스를 사용 하 여 글꼴 및 색 데이터를 검색 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> vspackage는이 GUID를 사용 하 여 기본 제공 정보를 참조 합니다.  
  
2. 범주 이름을 VSPackage의 리소스 (.rc) 파일 내의 문자열 테이블에 추가 하 여 IDE에 표시 될 때 필요에 따라 지역화할 수 있도록 해야 합니다.  
  
    자세한 내용은 [문자열 추가 또는 삭제](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab)를 참조 하세요.  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>기본 제공 글꼴 및 색을 사용 하 여 범주를 등록 하려면  
  
1. 다음 위치에서 특수 한 종류의 범주 레지스트리 항목을 생성 합니다.  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \\Omandcolors \\ *\<Category>* ]  
  
     *\<Category>* 는 범주의 지역화 되지 않은 이름입니다.  
  
2. 다음 네 가지 값을 사용 하 여 스톡 글꼴 및 색 구성표를 사용 하도록 레지스트리를 채웁니다.  
  
    |Name|형식|데이터|Description|  
    |----------|----------|----------|-----------------|  
    |범주|REG_SZ|GUID|스톡 글꼴 및 색 구성표를 포함 하는 범주를 식별 하는 임의의 GUID입니다.|  
    |패키지|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> 이 GUID는 기본 글꼴 및 색 구성을 사용 하는 모든 Vspackage 사용 됩니다.|  
    |NameID|REG_DWORD|ID|VSPackage에 있는 지역화할 수 있는 범주 이름의 리소스 ID입니다.|  
    |ToolWindowPackage|REG_SZ|GUID|인터페이스를 구현 하는 VSPackage의 GUID입니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>시스템에서 제공 하는 글꼴 및 색의 사용을 시작 하려면  
  
1. `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer`창의 구현 및 초기화의 일부로 인터페이스의 인스턴스를 만듭니다.  
  
2. 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> 하 여 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` 현재 인스턴스에 해당 하는 인터페이스의 인스턴스를 가져옵니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>를 두 번 호출 합니다.  
  
   - 를 인수로 사용 하 여 한 번 호출 `VSEDITPROPID_ViewGeneral_ColorCategory` 합니다.  
  
   - 를 인수로 사용 하 여 한 번 호출 `VSEDITPROPID_ViewGeneral_FontCategory` 합니다.  
  
     이렇게 하면 기본 글꼴 및 색 서비스를 창의 속성으로 설정 하 고 노출 합니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 기본 제공 글꼴 및 색의 사용을 시작 합니다.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [글꼴 및 색 사용](../extensibility/using-fonts-and-colors.md)   
 [텍스트 색 지정을 위한 글꼴 및 색 정보 가져오기](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [저장 된 글꼴 및 색 설정 액세스](../extensibility/accessing-stored-font-and-color-settings.md)   
 [글꼴 및 색 개요](../extensibility/font-and-color-overview.md)
