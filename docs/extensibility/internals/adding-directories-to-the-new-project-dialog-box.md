---
title: 새 프로젝트 대화 상자에 디렉터리 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827e383bba13c9742deb654bf3d680adeb3c109b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710239"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>새 프로젝트 대화 상자에 디렉터리 추가
새 프로젝트 유형을 만들 때 **새 프로젝트** 대화 상자에 새 디렉터리를 등록하여 템플릿으로 사용할 수 있도록 표시할 수도 있습니다. 다음 코드 예제에서는 노드라고도 하는 새 디렉터리를 등록하는 방법을 설명합니다. 이 예제에서는 VSPackage, *CLSID_Package*에 의해 노출된 템플릿이 등록됩니다. 결과적으로 **새 프로젝트** 대화 상자의 왼쪽에는 추가된 노드가 제공되며 *이름은 Folder_Label_ResID* 리소스에 의해 결정됩니다. 이 리소스는 VSPackage 위성 DLL에서 로드됩니다.

 **폴더** 값은 *Folder_Label_ResID* 노드가 표시되는 폴더의 GUID를 나타냅니다. 이 예제에서 GUID는 새 프로젝트 대화 상자의 **프로젝트 유형** 창에서 **다른** **프로젝트** 폴더를 나타냅니다. 기타 **프로젝트** 값이 없는 경우 레이블은 최상위 수준에 배치됩니다.

 이 `TemplatesDir` 값은 프로젝트 템플릿을 포함하는 디렉터리 전체 경로를 지정합니다. 이러한 파일은 *.vsz* 파일 또는 복제할 일반적인 템플릿 파일일 수 있습니다.

 을 지정하는 `TemplatesLocalizedSubDir`경우 지역화된 템플릿을 보유하는 하위 디렉터리 `TemplatesDir` 이름을 지정하는 문자열의 리소스 ID여야 합니다. 위성 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DLL이 있는 경우 위성 DLL에서 문자열 리소스를 로드하므로 각 위성 DLL에는 다른 하위 디렉터리 이름이 포함될 수 있습니다. 이 `SortPriority` 값은 정렬 우선 순위를 지정합니다.

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
