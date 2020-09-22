---
title: 사용자 지정 범주 및 표시 항목 구현 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841606"
---
# <a name="implementing-custom-categories-and-display-items"></a>사용자 지정 범주 및 표시 항목 구현
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 사용자 지정 범주와 표시 항목을 통해 IDE (통합 개발 환경)에 대 한 텍스트의 글꼴 및 색 제어를 제공할 수 있습니다.  
  
 사용자 지정 범주 및 표시 항목은 **글꼴 및 색** 속성 페이지에 있습니다. **글꼴 및 색** 속성 페이지를 열려면 **도구** 메뉴에서 **옵션**을 클릭 합니다. **환경** 을 확장 한 다음 **글꼴 및 색**을 클릭 합니다.  
  
 이 메커니즘을 사용 하는 경우 Vspackage는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> 인터페이스와 연결 된 인터페이스를 구현 해야 합니다.  
  
 원칙적으로이 메커니즘을 사용 하 여 기존의 모든 **표시 항목과 해당 항목** 을 포함 하는 **범주** 를 수정할 수 있습니다. 그러나 **텍스트 EditorCategory** 또는 **표시 항목**을 수정 하는 데 사용 하면 안 됩니다. 자세한 내용은 [글꼴 및 색 개요](../extensibility/font-and-color-overview.md)를 참조 하세요.  
  
 사용자 지정 **범주** 또는 **표시 항목**을 구현 하려면 VSPackage가 다음을 수행 해야 합니다.  
  
- 레지스트리에서 범주를 만들거나 식별 합니다.  
  
   **글꼴 및 색** 속성 페이지의 IDE 구현에서는이 정보를 사용 하 여 지정 된 범주를 지 원하는 서비스를 올바르게 쿼리 합니다.  
  
- 레지스트리에서 그룹을 만들거나 식별 합니다 (선택 사항).  
  
   두 개 이상의 범주의 합집합을 나타내는 그룹을 정의 하는 것이 유용할 수 있습니다. 그룹이 정의 된 경우 IDE는 자동으로 하위 범주를 병합 하 고 그룹 내에 표시 항목을 배포 합니다.  
  
- IDE 지원을 구현 합니다.  
  
- 글꼴 및 색 변경을 처리 합니다.  
  
  자세한 내용은 [저장 된 글꼴 및 색 설정 액세스](../extensibility/accessing-stored-font-and-color-settings.md)를 참조 하세요.  
  
## <a name="to-create-or-identify-categories"></a>범주를 만들거나 식별 하려면  
  
- [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \Omandcolors \\ `<Category>` ]에서 특수 한 종류의 범주 레지스트리 항목을 생성 합니다.  
  
   *\<Category>* 는 범주의 지역화 되지 않은 이름입니다.  
  
- 레지스트리를 다음 두 값으로 채웁니다.  
  
  |Name|유형|데이터|Description|  
  |----------|----------|----------|-----------------|  
  |범주|REG_SZ|GUID|범주를 식별 하기 위해 만든 GUID입니다.|  
  |패키지|REG_SZ|GUID|범주를 지 원하는 VSPackage 서비스의 GUID입니다.|  
  
  레지스트리에 지정 된 서비스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> 해당 범주에 대 한 구현을 제공 해야 합니다.  
  
## <a name="to-create-or-identify-groups"></a>그룹을 만들거나 식별 하려면  
  
- [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \Omandcolors \\ *\<group>* ]에서 특수 한 종류의 범주 레지스트리 항목을 생성 합니다.  
  
   *\<group>* 는 그룹의 지역화 되지 않은 이름입니다.  
  
- 레지스트리를 다음 두 값으로 채웁니다.  
  
  |Name|유형|데이터|Description|  
  |----------|----------|----------|-----------------|  
  |범주|REG_SZ|GUID|그룹을 식별 하기 위해 만든 GUID입니다.|  
  |패키지|REG_SZ|GUID|범주를 지 원하는 서비스의 GUID입니다.|  
  
  레지스트리에 지정 된 서비스는 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` 해당 그룹에 대 한 구현을 제공 해야 합니다.  
  
## <a name="to-implement-ide-support"></a>IDE 지원을 구현 하려면  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>을 구현 합니다 .이 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> 제공 된 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` 각 **범주** 또는 그룹 GUID에 대해 인터페이스 또는 인터페이스를 IDE에 반환 합니다.  
  
- 지원 되는 모든 **범주** 에 대해 VSPackage는 인터페이스의 개별 인스턴스를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> 합니다.  
  
- 를 통해 구현 된 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> IDE에를 제공 해야 합니다.  
  
  - 범주의 **표시 항목** 목록 **입니다.**  
  
  - **표시 항목**의 지역화할 수 있는 이름입니다.  
  
  - **범주의**각 멤버에 대 한 정보를 표시 합니다.  
  
  > [!NOTE]
  > 모든 **범주** 에는 하나 이상의 **표시 항목이**포함 되어야 합니다.  
  
- IDE는 인터페이스를 사용 하 여 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` 여러 범주의 합집합을 정의 합니다.  
  
   구현에서는 다음과 같이 IDE를 제공 합니다.  
  
  - 지정 된 그룹을 구성 하는 **범주** 목록입니다.  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>그룹 내에서 각 **범주** 를 지 원하는 인스턴스에 액세스 합니다.  
  
  - 지역화할 수 있는 그룹 이름.  
  
- IDE 업데이트:  
  
   IDE는 **글꼴 및 색** 설정에 대 한 정보를 캐시 합니다. 따라서 IDE **글꼴 및 색** 구성을 수정한 후 캐시가 최신 상태 인지 확인 하는 것이 좋습니다.  
  
  캐시 업데이트는 인터페이스를 통해 수행 되며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> , 선택 된 항목에 대해 전역적으로 또는만 수행할 수 있습니다.  
  
## <a name="to-handle-font-and-color-changes"></a>글꼴 및 색 변경을 처리 하려면  
 VSPackage에 표시 되는 텍스트의 색 지정을 제대로 지원 하려면 VSPackage를 지 원하는 색 지정 서비스에서 **글꼴 및 색** 속성 페이지를 통해 사용자가 시작한 변경 내용에 응답 해야 합니다. VSPackage는 다음을 수행 합니다.  
  
- 인터페이스를 구현 하 여 IDE에서 생성 된 이벤트 처리 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
     IDE는 **글꼴 및 색** 페이지의 사용자 수정에 따라 적절 한 메서드를 호출 합니다. 예를 들어 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> 새 글꼴이 선택 된 경우 메서드를 호출 합니다.  
  
     또는  
  
- 변경 내용에 대해 IDE를 폴링합니다.  
  
     시스템 구현 인터페이스를 통해이 작업을 수행할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . 주로 지 속성을 지원 하기 위해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 메서드를 사용 하 여 **표시 항목**의 글꼴 및 색 정보를 가져올 수 있습니다. 자세한 내용은 [저장 된 글꼴 및 색 설정 액세스](../extensibility/accessing-stored-font-and-color-settings.md)를 참조 하세요.  
  
    > [!NOTE]
    > 폴링을 통해 얻은 결과가 올바른지 확인 하려면 인터페이스를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> 인터페이스의 검색 메서드를 호출 하기 전에 캐시 플러시 및 업데이트가 필요한 지 확인 하는 것이 유용할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [텍스트 색 지정을 위한 글꼴 및 색 정보 가져오기](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [저장 된 글꼴 및 색 설정 액세스](../extensibility/accessing-stored-font-and-color-settings.md)   
 [방법: 기본 제공 글꼴 및 색 구성표 액세스](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [글꼴 및 색 개요](../extensibility/font-and-color-overview.md)
