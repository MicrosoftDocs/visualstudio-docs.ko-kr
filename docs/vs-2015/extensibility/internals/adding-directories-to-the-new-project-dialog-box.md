---
title: 새 프로젝트 대화 상자에 디렉터리 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203868"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>새 프로젝트 대화 상자에 디렉터리 추가
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

새 프로젝트 형식을 만들 **때 새 프로젝트 대화 상자** 에서 새 디렉터리를 등록 하 여 템플릿으로 사용 하도록 표시할 수도 있습니다. 다음 코드 예제에서는 노드 라고도 하는 새 디렉터리를 등록 하는 방법을 설명 합니다. 이 예제에서는 VSPackage CLSID_Package에 의해 노출 된 템플릿이 등록 됩니다. 따라서 **새 프로젝트** 대화 상자의 왼쪽에는 Folder_Label_ResID 리소스에 의해 결정 된 이름과 함께 추가 된 노드가 제공 됩니다. 이 리소스는 VSPackage 위성 DLL에서 로드 됩니다.  
  
 **폴더** 값은 Folder_Label_ResID 노드가 표시 되는 폴더의 GUID를 나타냅니다. 이 예제에서 GUID는 **새 프로젝트** 대화 상자의 **프로젝트 형식** 창에 있는 **다른 프로젝트** 폴더를 나타냅니다. **다른 프로젝트** 값이 없으면 레이블이 최상위 수준에 배치 됩니다.  
  
 Templates Dir 값은 프로젝트 템플릿이 포함 된 디렉터리의 전체 경로를 지정 합니다. 이러한 파일은 .vsz 파일 이거나 복제할 일반적인 템플릿 파일 일 수 있습니다.  
  
 TemplatesLocalizedSubDir를 지정 하는 경우 지역화 된 템플릿을 포함 하는 템플릿 디렉터리의 하위 디렉터리 이름을 지정 하는 문자열의 리소스 ID 여야 합니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]는 위성 dll (있는 경우)에서 문자열 리소스를 로드 하므로 각 위성 dll은 다른 하위 디렉터리 이름을 포함할 수 있습니다. SortPriority 값은 정렬 우선 순위를 지정 합니다.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 템플릿 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)   
 [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [새 항목 추가 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
