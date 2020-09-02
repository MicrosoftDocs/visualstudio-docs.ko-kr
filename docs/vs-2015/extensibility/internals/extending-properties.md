---
title: 속성 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b5d2e7d15f7b479941c3186d8cd694c92f762bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690992"
---
# <a name="extending-properties"></a>속성 확장
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **속성** 창은 COM 및 com + 구성 요소에 대 한 유니버설 속성 브라우저 이며 모든 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 제품을 지원 합니다. **속성** 창은 `ITypeInfo` 형식 정보 및 com + 메타 데이터와 함께 작동 하 여 IDE (통합 개발 환경)의 다른 창에서 현재 선택 된 개체에 대 한 디자인 타임 속성을 나열 합니다.  
  
 키보드에서 F4 키를 누르거나 **보기** 메뉴에서 **속성 창** 을 선택 하 여 열 수 있는 **속성** 창은 선택 된 개체의 구성 독립적, 디자인 타임 속성 및 이벤트를 보고 편집 하는 데 사용 됩니다. 솔루션 및 프로젝트와 관련 된 구성 종속 속성은 [속성 페이지](../../extensibility/internals/property-pages.md)에 표시 됩니다. 자세한 내용은 [NIB: 프로젝트 속성](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [관리 구성 옵션](../../extensibility/internals/managing-configuration-options.md)및 [프로젝트의 NIB: 항목 관리](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0)를 참조 하세요.  
  
 ![속성 창 개요](../../extensibility/internals/media/vspropertieswindow.png "Vswebsite 창")  
속성 창  
  
 이 섹션에서는 **속성** 창의 개별 영역과 관련 된 자세한 정보를 제공 하 고, 창을 채우도록를 호출 하 고 호출 해야 하는 인터페이스를 제공 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [속성 창 개요](../../extensibility/internals/properties-window-overview.md)  
 도구 창과 문서 창에 상대적인 **속성** 창의 용도에 대해 설명 합니다.  
  
 [템플릿 정책 및 속성 창](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 프로젝트가 엔터프라이즈 템플릿 프로젝트에 포함 되는 방법 및 엔터프라이즈 템플릿 프로젝트에서 정책을 적용할 수 있는 방법에 대해 설명 합니다.  
  
 [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 **속성** 창에 표시 되는 정보를 결정 하는 선택의 기준에 대해 설명 합니다.  
  
 [속성 창 개요 목록](../../extensibility/internals/properties-window-object-list.md)  
 **속성** 창 개체 목록의 용도를 설명 하 고,이 목록의 다른 개체가 호출을 트리거하는 환경에 새 개체를 선택 했다는 알림이 표시 되는 방법을 설명 합니다.  
  
 [속성 창 단추](../../extensibility/internals/properties-window-buttons.md)  
 **속성** 창 도구 모음에 표시 되는 네 가지 기본 단추에 대 한 목적을 설명 합니다.  
  
 [속성 표시 그리드](../../extensibility/internals/properties-display-grid.md)  
 표에서 속성 이름 및 속성 값 필드를 찾을 수 있는 위치를 설명 합니다.  
  
 [속성 창 선택 영역 추적 발표](../../misc/announcing-property-window-selection-tracking.md)  
 **속성** 창의 선택 추적에 대해 설명 합니다.  
  
 [자식 속성을 가진 속성 숨기기](../../misc/hiding-properties-that-have-child-properties.md)  
 인터페이스를 구현 하 여 자식 속성을 포함 하는 속성을 숨기는 방법을 설명 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> .  
  
 [사용자 지정 속성 창 제공](../../misc/providing-a-custom-properties-window.md)  
 고유한 속성 브라우저를 제공 하는 단계에 대해 자세히 설명 합니다.  
  
 [속성 창에서 필드 설명 가져오기](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 선택한 속성 필드와 관련 된 정보를 표시 하는 설명 영역을 찾을 수 있는 위치를 설명 합니다.  
  
 [속성 창에서 속성 값을 업데이트합니다.](../../misc/updating-property-values-in-the-properties-window.md)  
 속성 창이 속성 값 변경과 **동기화 된 상태** 를 유지 하는 두 가지 방법을 보여 주는 단계별 지침을 제공 합니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [프로젝트 형식](../../extensibility/internals/project-types.md):  
 프로젝트를 IDE의 빌딩 블록으로 설명 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 합니다.  
  
 [컴파일 및 빌드](../../ide/compiling-and-building-in-visual-studio.md)  
 플랫폼을 사용 하 여 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 응용 프로그램을 빌드할 때 응용 프로그램을 지속적으로 테스트 하 고 디버깅 하는 방법을 설명 합니다.  
  
 [HTML 문서 속성, 속성 창](https://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 속성 창에서 직접 HTML 문서를 편집 하는 방법에 대 한 지침을 제공 하 고 속성 창 HTML 문서에 있는 필드를 자세히 설명 하는 표를 제공 합니다.  
  
 [IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 `IDispatch`개체의 메서드 및 속성에 대 한 정보를 액세스 하 고 검색 하는 런타임에 바인딩된 메커니즘을 제공 하 여 자동화를 지원 하도록 처음 설계 된 인터페이스에 대해 설명 합니다.  
  
 [NIB: 동적 속성 소개 (Visual Studio)](https://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 응용 프로그램의 컴파일된 코드가 아닌 외부 구성 파일에 속성 값이 저장 되도록 응용 프로그램을 구성 하는 데 사용할 수 있는 동적 속성에 대 한 개요를 제공 합니다.  
  
 [NIB: 컨테이너로서의 프로젝트](https://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 응용 프로그램을 구성 하는 항목을 논리적으로 관리, 빌드 및 디버그할 수 있도록 솔루션의 컨테이너로 프로젝트의 역할을 설명 합니다.  
  
 [NIB: 프로젝트 속성](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 프로젝트에서 전체 프로젝트에 적용 되는 속성과 프로젝트의 특정 빌드 구성으로 제한 되는 속성을 제어 하는 데 사용할 수 있는 설정을 관리 하는 방법을 설명 합니다.  
  
 [솔루션 및 프로젝트](../../ide/solutions-and-projects-in-visual-studio.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]솔루션 및 프로젝트를 통해 개발 작업에 필요한 참조, 데이터 연결, 폴더 및 파일과 같은 항목을 효율적으로 관리 하는 방법을 설명 합니다.  
  
 [Visual Studio의 다른 부분 확장](../../extensibility/extending-other-parts-of-visual-studio.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 서비스를 사용하여 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]의 나머지와 일치하는 UI 요소를 만드는 방법을 설명합니다.
