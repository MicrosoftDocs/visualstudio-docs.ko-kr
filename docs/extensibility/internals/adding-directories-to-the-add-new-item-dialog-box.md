---
title: 새 항목 대화 상자에 디렉터리 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710261"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>새 항목 추가 대화 상자에 디렉터리 추가
다음 코드 예제에서는 **새 항목 추가** 대화 상자에 대 한 디렉터리 집합을 등록 하는 방법을 보여 줍니다. 새 항목 추가 대화 상자의 디렉터리마다 다른 **디렉터리입니다.** 따라서 디렉터리는 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\프로젝트에서**발견되는 **프로젝트** 하위 키 아래에 등록됩니다.

## <a name="registry-script"></a>레지스트리 스크립트

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 이 `%Template_Path%` 값은 프로젝트 템플릿을 포함하는 디렉터리 전체 경로를 지정합니다. 이러한 템플릿은 *복제할 .vsz* 파일 또는 프로토타입 템플릿 파일일 수 있습니다.

 이 `SortPriority` 값은 정렬 우선 순위를 지정합니다.

## <a name="add-items-to-an-existing-project"></a>기존 프로젝트에 항목 추가
 기존 프로젝트에 항목을 추가할 수도 있습니다. 예를 들어 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 프로젝트의 경우 * \<루트>\프로그램 파일\Microsoft 비주얼 스튜디오\VC#\CSharpProjectItems\LocalProjectItems* 폴더에 항목을 추가할 수 있습니다. 이 경우 `%GUID_Project%` C# 프로젝트의 GUID입니다({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 프로젝트 하위 유형을 프로그래밍하여 기존 프로젝트를 확장할 수도 있습니다. 프로젝트 하위 유형을 사용하면 새 프로젝트 형식을 작성하지 않고 프로젝트를 확장할 수 있습니다. 프로젝트 하위 유형에 대한 자세한 내용은 [프로젝트 하위 유형을](../../extensibility/internals/project-subtypes.md)참조하십시오.

## <a name="see-also"></a>참조
- [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [새 프로젝트 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
