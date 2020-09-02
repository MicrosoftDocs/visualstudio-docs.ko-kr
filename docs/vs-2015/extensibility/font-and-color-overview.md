---
title: 글꼴 및 색 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204353"
---
# <a name="font-and-color-overview"></a>글꼴 및 색 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE (통합 개발 환경)의 텍스트 글꼴 및 색 설정에 대해 설명 합니다. 또한 범주 및 표시 항목의 개념을 소개 하 고 Vspackage 및 핵심 편집기에서 텍스트 특성을 사용 하는 방법을 설명 합니다.  
  
## <a name="the-fonts-and-colors-property-page"></a>글꼴 및 색 속성 페이지  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **글꼴 및 색** 속성 페이지를 통해 IDE (통합 개발 환경)에서 표시 되는 텍스트의 특성을 관리할 수 있습니다. **글꼴 및 색** 속성 페이지를 찾으려면 **도구** 메뉴에서 **옵션**을 클릭 합니다. **환경**을 확장한 다음 **글꼴 및 색**을 클릭합니다.  
  
## <a name="categories-and-display-items"></a>범주 및 표시 항목  
 글꼴과 색은 **범주** 및 **표시 항목**으로 구성 됩니다.  
  
- **범주** 는 여러 **표시 항목**의 논리적 또는 기능 컨테이너입니다.  
  
   **범주** 목록은 **글꼴 및 색** 속성 페이지의 **설정 표시** 드롭다운 상자에 있습니다.  
  
- **표시 항목** 은 주석, 문자열 또는 표시 될 때 색을 지정할 컨트롤 구조와 같은 잘 정의 된 텍스트 엔터티입니다.  
  
  각 **표시 항목** 은 해당 항목을 포함 하는 **범주** 내에서 고유 하 게 정의 됩니다. 따라서 둘 이상의 **범주** 에 동일한 이름의 **표시 항목이** 있을 수 있습니다.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>글꼴 및 색의 VSPackage 제어  
 에서는 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] vspackage를 사용할 수 있습니다.  
  
- 글꼴 및 색 **범주**를 정의 합니다.  
  
- **표시 항목**을 표시 하는 데 사용 되는 글꼴 및 색을 지정 합니다.  
  
- **글꼴 및 색** 속성 페이지와 상호 작용 합니다.  
  
- 여러 **범주** 를 그룹으로 집계 합니다.  
  
- 기본 설정의 변경 내용을 유지 합니다.  
  
  에서 글꼴 및 색 선택과 상호 작용 하는 방법에는 두 가지가 있습니다 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
- 한 가지 방법을 *구문 색*지정 이라고 합니다. 이 클래스는 기존 편집기를 사용자 지정 하 여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 언어 서비스를 구현 하 고 소스 편집기를 만드는 VSPackage에서 사용 됩니다.  
  
   한 **범주만** 이 메커니즘 (즉, **텍스트 편집기**)을 지원 합니다.  
  
- 보다 일반적인 대안은 텍스트를 표시할 때 원본 편집기 이외의 다른 모든 **범주** 와 사용자 인터페이스 구성 요소를 지원 합니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>를 참조하세요.  
  
## <a name="core-editor-text-settings"></a>핵심 편집기 텍스트 설정  
 언어 서비스 개체의 핵심 편집기에 대 한 글꼴 및 색 설정은 **글꼴 및 색** 속성 페이지의 **설정 표시** 드롭다운 상자에 있는 **텍스트 editorcategory** 에 의해 제어 됩니다.  
  
 편집기에서 작업 하는 경우 언어 서비스에서 제공 하는 특수 글꼴 및 색 제어 메커니즘을 사용 하 여 **텍스트 편집기** 설정을 제어 하 고 확장 해야 합니다. 이 메커니즘을 *구문 색* 지정 이라고 하며 다음을 제공 합니다.  
  
- 표시 항목의 글꼴 및 색을 관리 하기 위한 단순화 된 기술입니다.  
  
   자세한 내용은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>를 참조하세요.  
  
- 잘 정의 되 고 최적화 된 색 지정 메커니즘입니다.  
  
   자세한 내용은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>를 참조하세요.  
  
- 기본 제공 항목을 사용 하 여 **텍스트 EditorCategory** 의 항목을 표시 하 고 확장 하는 기능입니다.  
  
   자세한 내용은 [방법: 기본 제공 색 항목](../extensibility/internals/how-to-use-built-in-colorable-items.md) 및 [사용자 지정 색 항목](../extensibility/internals/custom-colorable-items.md)사용을 참조 하세요.  
  
- **텍스트 편집기** 범주를 사용 하 여 기본 제공 및 사용자 지정 표시 항목의 현재 상태를 자동으로 지 속성 합니다.  
  
  구문 색 지정에 대 한 자세한 내용은 [레거시 언어 서비스의 구문 색](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)지정을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [편집기의 레거시 인터페이스](../extensibility/legacy-interfaces-in-the-editor.md)   
 [레거시 언어 서비스의 구문 색 지정](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
