---
title: SDK 요소(MSBuild) | Microsoft Docs
description: MSBuild 프로젝트 SDK를 참조하는 MSBuild Sdk 요소의 구문, 특성 및 요소에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b348cf2af76c439a28bbb58c0050cc3d458d5457
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048366"
---
# <a name="sdk-element-msbuild"></a>Sdk 요소(MSBuild)

MSBuild 프로젝트 SDK를 참조합니다.

 \<Project> \<Sdk>

## <a name="syntax"></a>구문

```xml
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />
```

## <a name="attributes-and-elements"></a>특성 및 요소

 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|Description|
|---------------|-----------------|
|`Name`|필수 특성입니다.<br /><br /> 프로젝트 SDK의 이름입니다.|
|`Version`|선택적 특성입니다.<br /><br /> 프로젝트 SDK의 버전입니다.|

### <a name="child-elements"></a>자식 요소

 없음

### <a name="parent-elements"></a>부모 요소

| 요소 | Description |
| - | - |
| [프로젝트](../msbuild/project-element-msbuild.md) | MSBuild 프로젝트 파일의 필수 루트 요소입니다. |

## <a name="see-also"></a>참고 항목

- [방법: MSBuild 프로젝트 SDK 참조](../msbuild/how-to-use-project-sdk.md)
- [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
