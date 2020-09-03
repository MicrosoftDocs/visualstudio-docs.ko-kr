---
title: 프로젝트 및 프로젝트 항목 템플릿 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203865"
---
# <a name="adding-project-and-project-item-templates"></a>프로젝트 및 프로젝트 항목 템플릿 추가
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자 고유의 프로젝트 형식을 만들 때 표준 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (통합 개발 환경) 대화 상자를 사용 하 여 새 프로젝트 및 프로젝트 항목을 추가할 수 있도록 지원 해야 합니다. 다음 항목에서는 프로젝트 및 프로젝트 항목을 추가 하는 여러 가지 방법에 대해 설명 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [프로젝트 컨텍스트](../../extensibility/internals/project-context.md)  
 프로젝트에서 환경의 transpires에 대 한 대부분의 컨텍스트 정보를 제공 하는 방법을 설명 합니다.  
  
 [프로젝트 우선 순위](../../extensibility/internals/project-priority.md)  
 항목을 여는 데 사용 되는 프로젝트를 명확 하 게 방지 하기 위해 프로젝트 항목을 일반적으로 하나의 프로젝트 멤버로 사용 하는 방법을 설명 합니다.  
  
 [기타 파일 프로젝트](../../extensibility/internals/miscellaneous-files-project.md)  
 프로젝트에서 파일을 여는 데 사용할 수 있는 두 가지 형식의 편집기와 프로젝트 항목을 열 때 사용할 편집기를 결정 하는 데 사용할 수 있는 역할에 대 한 정보를 제공 합니다.  
  
 [프로젝트 템플릿 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)  
 프로젝트를 만들 때 발생 하는 상황 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 을 설명 합니다.  
  
 [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 **새 항목 추가** 대화 상자에 항목을 추가 하는 프로세스에 대해 설명 합니다.  
  
 [새 프로젝트 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 VSPackage에서 사용할 수 있는 사용자 지정 템플릿을 포함 하는 새 디렉터리를 등록 하는 예를 제공 합니다.  
  
 [새 항목 추가 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 **새 항목 추가** 대화 상자에 대 한 새 디렉터리 집합을 등록 하는 예를 제공 합니다.  
  
 [프로젝트 시스템 확장을 위한 IDE 정의 명령](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 프로젝트 시스템 확장에 사용 되는 다양 한 명령 항목 유형을 나열 합니다.  
  
 [일반적으로 프로젝트를 확장하는 데 사용되는 개체에 대한 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], 및 프로젝트 시스템을 확장 하는 데 사용 되는 개체에 대 한 catid를 나열 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 합니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)  
 프로젝트의 특정 편집기에 본질적으로 바인딩된 항목을 여는 방법에 대 한 단계별 지침을 제공 합니다.  
  
 [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)  
 표준 편집기를 여는 방법에 대 한 단계별 지침을 제공 합니다.  
  
 [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)  
 프로젝트 하위 형식 개념 항목에 대 한 링크를 제공 합니다. 프로젝트 하위 유형은 기존 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 및 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 프로젝트를 확장 합니다.  
  
 [프로젝트 형식](../../extensibility/internals/project-types.md):  
 새 프로젝트 형식을 디자인 하는 방법에 대 한 정보를 제공 하는 추가 항목에 대 한 링크를 제공 합니다.
