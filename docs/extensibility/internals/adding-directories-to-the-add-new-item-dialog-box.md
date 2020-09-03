---
title: 새 항목 추가 대화 상자에 디렉터리 추가 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710261"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>새 항목 추가 대화 상자에 디렉터리 추가
다음 코드 예제에서는 **새 항목 추가** 대화 상자에 대 한 새 디렉터리 집합을 등록 하는 방법을 보여 줍니다. **새 항목 추가** 대화 상자의 디렉터리는 각 프로젝트 마다 다릅니다. 따라서 디렉터리는 **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp\projects**에 있는 **Projects** 하위 키 아래에 등록 됩니다.

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

 `%Template_Path%`값은 프로젝트 템플릿을 포함 하는 디렉터리의 전체 경로를 지정 합니다. 이러한 템플릿은 복제 될 *.vsz* 파일 또는 일련 템플릿 파일 일 수 있습니다.

 `SortPriority`값은 정렬 우선 순위를 지정 합니다.

## <a name="add-items-to-an-existing-project"></a>기존 프로젝트에 항목 추가
 기존 프로젝트에 항목을 추가할 수도 있습니다. 예를 들어 프로젝트의 경우 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] * \<root> Files\Microsoft Visual Studio\VC # \CSharpProjectItems\LocalProjectItems* 폴더에 항목을 추가할 수 있습니다. 이 경우 `%GUID_Project%` 는 c # 프로젝트 ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC})에 대 한 GUID입니다.

 프로젝트 하위 형식을 프로그래밍 하 여 기존 프로젝트를 확장할 수도 있습니다. 프로젝트 하위 유형을 사용 하면 새 프로젝트 유형을 작성 하지 않고 프로젝트를 확장할 수 있습니다. 프로젝트 하위 형식에 대 한 자세한 내용은 [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [프로젝트 템플릿 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [새 프로젝트 대화 상자에 디렉터리 추가](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
