---
title: 새 항목 추가 대화 상자에 기여 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d288f2d007fd0f923021847179326069959d3698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197016"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>새 항목 추가 대화 상자에 적용
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 하위 유형은 레지스트리 하위 키 아래에 **항목 추가** 템플릿을 등록 하 여 **새 항목 추가** 대화 상자에 대 한 새 항목 디렉터리를 제공할 수 있습니다 `Projects` .  
  
## <a name="registering-add-new-item-templates"></a>새 항목 추가 템플릿 등록  
 이 섹션은 레지스트리의 **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\projects** 아래에 있습니다. 아래 레지스트리 항목에서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 가상 프로젝트 하위 형식으로 프로젝트를 집계 한 것으로 가정 합니다. 프로젝트에 대 한 항목은 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 다음과 같습니다.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 `AddItemTemplates\TemplateDirs`하위 키에는 **새 항목 추가** 대화 상자에서 사용 가능한 항목이 배치 된 디렉터리의 경로를 포함 하는 레지스트리 항목이 포함 되어 있습니다.  
  
 환경에서 `AddItemTemplates` 레지스트리 하위 키 아래에 있는 모든 데이터를 자동으로 로드 합니다 `Projects` . 여기에는 기본 프로젝트 구현에 대 한 데이터 및 특정 프로젝트 하위 형식 유형에 대 한 데이터가 포함 될 수 있습니다. 각 프로젝트 하위 형식은 프로젝트 형식으로 식별 됩니다 `GUID` . 프로젝트 하위 형식에서는 `Add Item` `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 프로젝트 하위 형식의 GUID 값을 반환 하기 위해 구현에서 열거형을 지원 하 여 다른 템플릿 집합을 특정 flavored 프로젝트 인스턴스에 사용 하도록 지정할 수 있습니다. `VSHPROPID_AddItemTemplatesGuid`속성을 지정 하지 않으면 기본 프로젝트 GUID가 사용 됩니다.  
  
 프로젝트 하위 형식 집계 개체에 인터페이스를 구현 하 여 **새 항목 추가** 대화 상자에서 항목을 필터링 할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> . 예를 들어 프로젝트를 집계 하 여 데이터베이스 프로젝트를 구현 하는 프로젝트 하위 유형은 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 필터링을 구현 하 여 **새 항목 추가** 대화 상자에서 특정 항목을 필터링 할 수 있으며,이 경우에서를 지원 하 여 데이터베이스 프로젝트 관련 항목을 추가할 수 있습니다 `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . **새 항목 추가** 대화 상자에서 항목을 필터링 하 고 추가 하는 방법에 대 한 자세한 내용은 [새 항목 추가 대화 상자에 항목](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)추가를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [일반적으로 프로젝트를 확장하는 데 사용되는 개체에 대한 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
