---
title: ProjectExtensions 요소(MSBuild) | Microsoft Docs
description: MSBuild 프로젝트 파일에 비 MSBuild 정보를 포함할 수 있도록 하는 MSBuildProjectExtensions 요소에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7b186fa1d7a5ecb8297045d4b0bbb111d136d1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905288"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions 요소(MSBuild)

MSBuild 프로젝트 파일이 MSBuild 이외의 정보를 포함하도록 허용합니다. MSBuild에서는 `ProjectExtensions` 요소 내의 모든 항목을 무시합니다.

 \<Project> \<ProjectExtensions>

## <a name="syntax"></a>구문

```xml
<ProjectExtensions>
    Non-MSBuild information to include in file.
</ProjectExtensions>
```

## <a name="attributes-and-elements"></a>특성 및 요소

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

 None

### <a name="child-elements"></a>자식 요소

 없음

### <a name="parent-elements"></a>부모 요소

| 요소 | 설명 |
| - | - |
| [프로젝트](../msbuild/project-element-msbuild.md) | MSBuild 프로젝트 파일의 필수 루트 요소입니다. |

## <a name="remarks"></a>설명

 MSBuild 프로젝트에서는 `ProjectExtensions` 요소를 하나만 사용할 수 있습니다.

## <a name="example"></a>예제

 다음 코드 예제에서는 통합 개발 환경의 정보가 `ProjectExtensions` 요소에 저장되는 방식을 보여 줍니다.

```xml
<ProjectExtensions>
    <VSIDE>
        <External>
            <!--
            Raw XML passed to the IDE by an external source
            -->
        </External>
    </VSIDE>
</ProjectExtensions>
```

## <a name="see-also"></a>참조

- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
