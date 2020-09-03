---
title: 저장 된 글꼴 및 색 설정 액세스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821840"
---
# <a name="accessing-stored-font-and-color-settings"></a>저장된 글꼴 및 색 설정에 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]IDE (통합 개발 환경)는 레지스트리의 글꼴 및 색에 대 한 수정 된 설정을 저장 합니다. 인터페이스를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 하 여 이러한 설정에 액세스할 수 있습니다.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>글꼴 및 색의 상태 지 속성을 시작 하려면  
 글꼴 및 색 정보는 다음 레지스트리 위치에 범주별로 저장 됩니다. [HKCU\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \Omandcolors \\ *\<CategoryGUID>* ]. 여기서 *\<CategoryGUID>* 는 범주 GUID입니다.  
  
 따라서 지 속성을 시작 하려면 VSPackage은 다음을 수행 해야 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> `QueryService` 전역 서비스 공급자에 대해를 호출 하 여 인터페이스를 가져옵니다.  
  
     `QueryService` 는의 서비스 ID 인수와 `SID_SVsFontAndColorStorage` 의 인터페이스 id 인수를 사용 하 여 호출 해야 합니다 `IID_IVsFontAndColorStorage` .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A>범주 GUID와 모드 플래그를 인수로 사용 하 여 보관할 범주를 열려면 메서드를 사용 합니다.  
  
  인수에 의해 지정 되는 모드는 `fFlags` 열거형의 값에서 생성 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . 이 모드 컨트롤:  

  - 인터페이스를 통해 액세스할 수 있는 설정입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  

  - 모든 설정 또는 사용자가 수정 하 고 인터페이스를 통해 검색할 수 있는 설정입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  

  - 사용자 설정에 대 한 변경 내용을 전파 하는 방법입니다.  

  - 사용 되는 색 값의 형식입니다.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>글꼴 및 색의 상태 지 속성을 사용 하려면  
 글꼴 및 색 유지에는 다음이 포함 됩니다.  
  
- 레지스트리에 저장 된 설정과 IDE 설정 동기화  
  
- 레지스트리 수정 정보를 전파 합니다.  
  
- 레지스트리에 저장 된 설정을 설정 하 고 검색 합니다.  
  
  저장소 설정과 IDE 설정의 동기화는 주로 투명 합니다. 기본 IDE는 **표시 항목** 의 업데이트 된 설정을 범주에 대 한 레지스트리 항목에 자동으로 기록 합니다.  
  
  여러 Vspackage 특정 범주를 공유 하는 경우에는 인터페이스의 메서드를 사용 하 여 저장 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 레지스트리 설정을 수정할 때 이벤트를 생성 해야 합니다.  
  
  기본적으로 이벤트 생성은 사용 하도록 설정 되어 있지 않습니다. 이벤트 생성을 사용 하도록 설정 하려면를 사용 하 여 범주를 열어야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . 이렇게 하면 IDE에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackage가 구현 하는 적절 한 메서드를 호출 합니다.  
  
> [!NOTE]
> **글꼴 및 색** 속성 페이지를 통해 수정 하면에 관계 없이 이벤트가 생성 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> 됩니다. 인터페이스를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> 클래스의 메서드를 호출 하기 전에 캐시 된 글꼴 및 색 설정 업데이트가 필요한 지 여부를 결정할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  
  
### <a name="storing-and-retrieving-information"></a>정보 저장 및 검색  
 사용자가 열린 범주의 명명 된 표시 항목에 대해 수정할 수 있는 정보를 가져오거나 구성 하려면 Vspackage가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> 및 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> 합니다.  
  
 특정 범주에 대 한 글꼴 특성에 대 한 정보는 및 메서드를 사용 하 여 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> .  
  
> [!NOTE]
> `fFlags`해당 범주를 열 때 메서드로 전달 되는 인수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> 및 메서드의 동작을 정의 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> . 기본적으로 이러한 메서드는 변경 된 aboutdisplay 항목만 반환 합니다. 그러나 플래그를 사용 하 여 범주를 열 경우 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> 업데이트 된 표시 항목과 변경 되지 않은 표시 항목 모두 및에서 액세스할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> .  
  
 기본적으로 변경 된 **표시 항목** 정보만 레지스트리에 보관 됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>인터페이스는 글꼴 및 색에 대 한 모든 설정을 검색 하는 데 사용할 수 없습니다.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>및 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> 변경 되지 않은 **표시 항목**에 대 한 정보를 검색 하는 데 사용할 때 REGDB_E_KEYMISSING (0x80040152L)를 반환 합니다.  
  
 인터페이스의 메서드를 사용 하 여 특정 **범주의** 모든 **표시 항목** 에 대 한 설정을 가져올 수 있습니다 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` .  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [사용자 지정 범주 및 표시 항목 구현](../extensibility/implementing-custom-categories-and-display-items.md)
