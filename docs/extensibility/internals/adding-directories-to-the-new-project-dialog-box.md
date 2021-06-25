---
title: 새 프로젝트 대화 상자에 디렉터리 추가 | Microsoft Docs
description: 새 프로젝트 형식을 만들고 템플릿으로 사용할 수 있도록 표시할 수 있도록 Visual Studio 새 프로젝트 대화 상자에 디렉터리를 추가하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44554c8bd7b758f1bf191d1a4bef9ba07941191d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901840"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>새 프로젝트 대화 상자에 디렉터리 추가
새 프로젝트 형식을 만들 때 새 프로젝트 대화 상자에서 **새** 디렉터리를 등록하여 템플릿으로 사용하도록 표시할 수도 있습니다. 다음 코드 예제에서는 노드라고도 하는 새 디렉터리를 등록하는 방법을 설명합니다. 이 예제에서는 VSPackage에서 CLSID_Package 템플릿이 등록됩니다. 따라서 **새 프로젝트** 대화 상자의 왼쪽은 *추가된* 노드를 제공하며 Folder_Label_ResID 리소스에 의해 이름이 결정됩니다. 이 리소스는 VSPackage 위성 DLL에서 로드됩니다.

 **폴더** 값은 *Folder_Label_ResID* 노드가 표시되는 폴더의 GUID를 나타냅니다. 예제에서 GUID는 새 프로젝트 대화 상자의 **프로젝트 형식** 창에 있는 **기타** **프로젝트** 폴더를 나타냅니다. 기타 **프로젝트** 값이 없으면 레이블이 최상위 수준에 배치됩니다.

 `TemplatesDir`값은 프로젝트 템플릿을 포함하는 디렉터리 전체 경로를 지정합니다. 이러한 파일은 *.vsz* 파일 또는 복제할 일반적인 템플릿 파일일 수 있습니다.

 를 지정하는 경우 `TemplatesLocalizedSubDir` 지역화된 템플릿을 보유하는 의 하위directory 이름을 지정하는 문자열의 리소스 ID여야 `TemplatesDir` 합니다. 가 있는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 경우 위성 DLL에서 문자열 리소스를 로드하기 때문에 각 위성 DLL은 다른 하위 디렉토리 이름을 포함할 수 있습니다. `SortPriority`값은 정렬 우선 순위를 지정합니다.

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

## <a name="see-also"></a>참조
- [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [새 항목 추가 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
