---
title: 글꼴 및 색 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177230"
---
# <a name="using-fonts-and-colors"></a>글꼴 및 색 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

는 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 글꼴 및 색을 사용 하 여 텍스트를 표시 하는 기능을 지원 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [글꼴 및 색 개요](../extensibility/font-and-color-overview.md)  
 IDE (통합 개발 환경)의 텍스트 글꼴 및 색 설정에 대해 설명 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다. 또한 범주 및 표시 항목의 개념을 소개 하 고 Vspackage 및 핵심 편집기에서 텍스트 특성을 사용 하는 방법을 설명 합니다.  
  
 [텍스트 색 지정을 위해 글꼴 및 색 정보 가져오기](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 **텍스트 편집기**이외의 **범주** 를 관리 하는 vspackage에서 텍스트 색 지정을 구현 하기 위한 지침을 제공 합니다.  
  
 [저장된 글꼴 및 색 설정에 액세스](../extensibility/accessing-stored-font-and-color-settings.md)  
 현재 글꼴 및 색 설정을 저장 하 고, 검색 하 고, 적용할 수 있는 방법을 설명 합니다.  
  
 [사용자 지정 범주 및 표시 항목 구현](../extensibility/implementing-custom-categories-and-display-items.md)  
 창에서 텍스트 표시를 지 원하는 **표시 항목** 및 **범주** 를 만들고 사용할 수 있는 기본 단계를 설명 합니다.  
  
 이 접근 방식에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> 인터페이스 및 관련 된 인터페이스를 구현 하는 VSPackage 필요 합니다.  
  
 [방법: 기본 제공 글꼴 및 색 구성표에 액세스](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 기본 제공 글꼴 및 색을 사용 하 여 범주를 정의 하 고 등록 하 고 시스템에서 제공 하는 글꼴과 색의 사용을 시작 하는 방법을 설명 합니다.  
  
## <a name="reference"></a>참고  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 `IVsFontAndColorDefaults` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> **옵션** 대화 상자의 **글꼴 및 색** 페이지에 있는 **설정 표시** 목록에 나열 된 특정 항목에 해당 하는 또는 인터페이스의 인스턴스를 제공 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 창이 나 UI 구성 요소의 기본 글꼴 및 색을 정의 하 여 VSPackage에서 IDE **글꼴 및 색** 페이지를 지원할 수 있도록 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 글꼴 및 색 지원을 제공 하는 VSPackage에서 표시 항목 그룹을 지정할 수 있는 메커니즘을 제공 합니다 .이 메커니즘은 둘 이상의 범주에 대 한 합집합을 나타내는 상위 범주입니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 VSPackage가 글꼴 및 색 데이터를 검색 하거나 레지스트리에 저장할 수 있습니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 글꼴 및 색 설정의 변경 내용에 대 한 글꼴 및 색 정보를 사용 하는 Vspackage에 게 알립니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **글꼴 및 색** 메커니즘의 메서드에서 사용 되는 입력 및 출력 데이터를 사용 하기 위한 도구를 제공 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 글꼴 및 색 설정의 캐싱을 제어 합니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [레거시 언어 서비스 개발](../extensibility/internals/developing-a-legacy-language-service.md)  
 Vspackage에서 언어 서비스를 사용 하 여 편집기를 사용자 지정 하는 방법을 설명 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다.  
  
 [사용자 지정 편집기의 구문 색 지정](../extensibility/syntax-coloring-in-custom-editors.md)  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]편집기에서 언어 서비스를 사용 하 여 구문 색 지정을 구현 하는 방법을 Descries.  
  
 [Visual Studio의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 서비스를 사용하여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 나머지와 일치하는 UI 요소를 만드는 방법을 설명합니다.
