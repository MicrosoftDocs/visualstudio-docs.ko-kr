---
title: 텍스트 색 지정을 위한 글꼴 및 색 정보 가져오기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696851"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>텍스트 색 지정을 위해 글꼴 및 색 정보 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UI (사용자 인터페이스) 요소에서 색이 지정 된 텍스트를 렌더링 하거나 표시 하는 프로세스는 프로젝트의 유형, 기술 및 개발자 기본 설정에 따라 달라 집니다. **글꼴 및 색** 속성 페이지에는 설정이 저장 됩니다.  
  
 색이 있는 텍스트를 표시 하는 대부분의 구현에는 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` 텍스트 표시 설정을 표시, 검색 및 저장 하기 위한 및 관련 인터페이스가 필요 합니다.  
  
> [!NOTE]
> **텍스트 EditorCategory**를 지 원하는 핵심 편집기를 사용자 지정 하는 경우 언어 서비스에서 색 지정 기술을 사용 하는 것이 좋습니다. 자세한 내용은 [글꼴 및 색 개요](../extensibility/font-and-color-overview.md)를 참조 하세요.  
  
## <a name="getting-default-font-and-color-information"></a>기본 글꼴 및 색 정보 가져오기  
 텍스트를 표시 하는 모든 창의 **글꼴 및 색** 설정은 한 **범주의** **표시 항목** 에서 지정 해야 합니다. 자세한 내용은 [옵션 대화 상자, 환경, 글꼴 및 색](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)을 참조 하세요.  
  
 색상화를 위해 VSPackage는 현재 **글꼴 및 색** 설정을 가져와야 합니다. VSPackage는 필요에 따라 다음과 같은 방법으로이 작업을 수행할 수 있습니다.  
  
- 글꼴 및 색 지 속성 메커니즘을 사용 하 여 저장 된 상태 또는 현재 상태를 검색 합니다. 자세한 내용은 [저장 된 글꼴 및 색 설정 액세스](../extensibility/accessing-stored-font-and-color-settings.md)를 참조 하세요.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> VSPackage가 글꼴 및 색 공급자가 아닌 경우 글꼴 및 색 데이터를 제공 하는 서비스의 인터페이스를 사용 하 여 인스턴스를 가져올 수 있습니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 인터페이스를 구현합니다.  
  
  폴링을 통해 얻은 결과가 최신 상태 인지 확인 하려면 인터페이스를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> 인터페이스의 검색 메서드를 호출 하기 전에 업데이트가 필요한 지 확인 하는 것이 유용할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  
  
  글꼴 및 색 정보를 가져온 후에는 표시 될 텍스트를 구문 분석 하 여 색을 지정 해야 하는 요소를 식별 한 다음 적절 한 글꼴 및 색을 사용 하 여 창에 텍스트를 표시 합니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [글꼴 및 텍스트 사용](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [색 작업](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (그래픽 장치 인터페이스)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
