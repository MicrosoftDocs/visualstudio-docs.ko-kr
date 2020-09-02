---
title: VSPackage 상태 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62979997"
---
# <a name="vspackage-state"></a>VSPackage 상태
많은 요소는 응용 프로그램의 지속형 값 또는 상태 집합을 결정 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- 프로젝트에는 프로젝트 및 구성 속성이 있습니다.  
  
- 솔루션에는 속성이 있습니다.  
  
- 사용자 설정에 따라 문서 창, 도구 창, 도킹 상태 및 바로 가기 키의 크기와 위치가 결정 됩니다.  
  
- 응용 프로그램에는 사용자가 설정 하는 옵션이 있을 수 있습니다.  
  
- 응용 프로그램에서 만드는 개체에는 고유한 속성이 있을 수 있습니다.  
  
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]응용 프로그램 상태를 관리할 수 있는 몇 가지 방법은 다음과 같습니다.  
  
- 프로젝트 및 솔루션 속성 페이지를 통해  
  
- **설정 가져오기 및 내보내기 마법사**를 통해 사용자가 한 컴퓨터에서 다른 컴퓨터로 설정을 이동할 수 있습니다.  
  
- 응용 프로그램과 관련 된 옵션을 포함 하는 **옵션** 대화 상자를 통해  
  
- 개체의 속성을 노출 하는 **속성** 창을 통해  
  
- Automation. 응용 프로그램은 자동화에 노출 된 VSPackage 및 개체 속성에 액세스할 수 있습니다.  
  
  기본 응용 프로그램 상태는 응용 프로그램 상태를 저장 하 고 복원할 수 있도록 하는 다양 한 지 속성 메커니즘입니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [상태 지속성 지원](../misc/support-for-state-persistence.md)  
 VSPackage 상태의 저장, 복원, 재설정 등에 대한 일반적인 전략이 표시됩니다.  
  
 [옵션 및 옵션 페이지](../extensibility/internals/options-and-options-pages.md)  
 일반 및 사용자 지정 옵션 페이지를 소개 하 고이를 구현 하는 방법을 설명 합니다.  
  
 [옵션 페이지 만들기](../extensibility/creating-an-options-page.md)  
 간단한 페이지와 사용자 지정 페이지의 두 옵션 페이지를 만드는 방법에 대해 설명 합니다.  
  
 [설정 범주에 대한 지원](../misc/support-for-settings-categories.md)  
 사용자 설정 및 이러한 설정이 만들어지고 지속 되는 방법에 대해 설명 합니다.  
  
 [설정 범주 만들기](../extensibility/creating-a-settings-category.md)  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]설정 범주를 만들어 설정 파일에서 값을 저장 하 고 값을 복원 하는 데 사용 하는 방법을 설명 합니다.  
  
 [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)  
 **속성** 창에서 개체의 값을 표시 하 고 변경 하는 방법을 설명 합니다.  
  
 [속성 창에 속성 노출](../extensibility/exposing-properties-to-the-properties-window.md)  
 개체의 public 속성을 **속성** 창에 노출 하는 방법을 설명 합니다.  
  
 [프로젝트 및 구성 속성 지원](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 프로젝트 및 구성 속성을 표시 하 고 변경 하는 방법을 설명 합니다.  
  
 [프로젝트 속성 가져오기](../extensibility/getting-project-properties.md)  
 도구 창에 프로젝트 속성을 표시 하는 관리 되는 VSPackage을 만드는 단계를 안내 합니다.  
  
 [설정 저장소 사용](../extensibility/using-the-settings-store.md)  
 설정 저장소 지 속성 메커니즘 및 사용 방법에 대해 설명 합니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Vspackage을 만들고 사용 하는 방법을 설명 하는 항목에 대 한 일반적인 지침을 제공 합니다.