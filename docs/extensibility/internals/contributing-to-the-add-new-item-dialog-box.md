---
title: 새 항목 대화 상자 추가에 기여 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709284"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>새 항목 추가 대화 상자에 기여
프로젝트 하위 유형은 **프로젝트** 레지스트리 하위 키 아래에 **항목 추가** 템플릿을 등록하여 새 **항목 추가** 대화 상자에 대한 항목의 완전한 새 디렉터리를 제공할 수 있습니다.

## <a name="register-add-new-item-templates"></a>새 항목 추가 템플릿 등록
 이 섹션은 레지스트리의 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\프로젝트** 아래에 있습니다. 아래 레지스트리 항목은 가상프로젝트 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 하위유형으로 집계된 프로젝트를 가정합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 항목은 다음과 같습니다.

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

 **AddItemTemplates\TemplateDirs** 하위 키에는 **새 항목 추가** 대화 상자에서 사용할 수 있는 항목이 배치된 디렉터리 경로가 있는 레지스트리 항목이 포함되어 있습니다.

 환경은 **프로젝트** 레지스트리 하위 키 아래에 모든 **AddItemTemplates** 데이터를 자동으로 로드합니다. 이 데이터에는 기본 프로젝트 구현에 대한 데이터와 특정 프로젝트 하위 유형 형식에 대한 데이터가 포함될 수 있습니다. 각 프로젝트 하위 유형은 프로젝트 유형 **GUID로**식별됩니다. 프로젝트 하위 유형은 구현에서 `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 열거를 지원하여 프로젝트 하위 유형의 GUID 값을 반환하여 특정 맛있는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 프로젝트 인스턴스에 대해 항목 **추가** 템플릿의 대체 집합을 사용하도록 지정할 수 있습니다. `VSHPROPID_AddItemTemplatesGuid` 속성을 지정하지 않으면 기본 프로젝트 GUID가 사용됩니다.

 프로젝트 하위 유형 애그리게이터 개체에서 인터페이스를 구현하여 **새 항목 추가** 대화 상자의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> 항목을 필터링할 수 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 예를 들어, 프로젝트를 집계하여 데이터베이스 프로젝트를 구현하는 프로젝트 하위 유형은 필터링을 구현하여 새 항목 **추가** 대화 상자에서 `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 특정 항목을 필터링할 수 있으며, 차례로 에서 지원하여 데이터베이스 프로젝트별 항목을 추가할 수 있습니다. **새 항목 추가** 대화 상자에 항목을 필터링하고 추가하는 방법에 대한 자세한 내용은 새 항목 [추가 대화 상자에 항목 추가 상자를](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)참조하십시오.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [일반적으로 프로젝트를 확장하는 데 사용되는 개체에 대한 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
