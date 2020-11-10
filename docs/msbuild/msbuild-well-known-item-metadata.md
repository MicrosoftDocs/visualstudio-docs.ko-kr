---
title: MSBuild 잘 알려진 항목 메타데이터 | Microsoft Docs
description: 모든 항목을 만들 때 할당되는 MSBuild 메타데이터 및 빌드 동작을 제어하기 위해 정의할 수 있는 몇 가지 선택적 MSBuild 메타데이터에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 047fe5ef6edc57681b8382a9f2a1069991e0f513
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049015"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild 잘 알려진 항목 메타데이터

항목 메타데이터는 항목에 연결된 값입니다. 일부는 항목을 만들 때 MSBuild가 항목에 할당하지만 필요한 메타데이터를 직접 정의할 수도 있습니다. 일부 사용자 정의 메타데이터 값은 MSBuild, 특정 작업 또는 .NET SDK와 같은 SDK에서 유효합니다.

이 문서의 첫 번째 표에서는 모든 항목을 만들 때 할당되는 메타데이터에 대해 설명합니다. 다음 표에서는 MSBuild에서 유효한 몇 가지 선택적 메타데이터를 보여 줍니다. 이러한 메타데이터를 정의하여 빌드 동작을 제어할 수 있습니다. 각 예제에서 프로젝트에 파일 *C:\MyProject\Source\Program.cs* 를 포함하는 데 다음과 같은 항목 선언이 사용되었습니다.

```xml
<ItemGroup>
    <MyItem Include="Source\Program.cs" />
</ItemGroup>
```

|항목 메타데이터|설명|
|-------------------|-----------------|
|%(FullPath)|항목의 전체 경로를 포함합니다. 다음은 그 예입니다.<br /><br /> *C:\MyProject\Source\Program.cs*|
|%(RootDir)|항목의 루트 디렉터리를 포함합니다. 다음은 그 예입니다.<br /><br /> *C:\\*|
|%(Filename)|확장명 없이 항목의 파일 이름을 포함합니다. 다음은 그 예입니다.<br /><br /> *Program*|
|%(Extension)|항목의 파일 이름 확장명을 포함합니다. 다음은 그 예입니다.<br /><br /> *.cs*|
|%(RelativeDir)|마지막 백슬래시(\\)까지 `Include` 특성에 지정된 경로를 포함합니다. 예를 들어:<br /><br /> *Source\\*<br /><br /> `Include` 특성이 전체 경로인 경우 `%(RelativeDir)`는 루트 디렉터리 `%(RootDir)`로 시작합니다.  다음은 그 예입니다. <br /><br /> *C:\MyProject\Source\\*|
|%(Directory)|루트 디렉터리를 제외한 항목의 디렉터리를 포함합니다. 예를 들어:<br /><br /> *MyProject\\Source\\*|
|%(RecursiveDir)|`Include` 특성에 와일드카드 \*\*가 포함되는 경우 메타데이터는 와일드카드를 대신하는 경로 부분을 지정합니다. 와일드카드에 대한 자세한 내용은 [방법: 빌드할 파일 선택](../msbuild/how-to-select-the-files-to-build.md)을 참조하세요.<br /><br /> 폴더 *C:\MySolution\MyProject\Source\\* 에 *Program.cs* 파일이 포함되고 프로젝트 파일에 다음 항목이 포함된 경우:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> `%(MyItem.RecursiveDir)` 값은 *MySolution\MyProject\Source\\* 가 됩니다.|
|%(Identity)|`Include` 특성에 지정된 항목입니다. 다음은 그 예입니다.<br /><br /> *Source\Program.cs*|
|%(ModifiedTime)|항목을 마지막으로 수정한 시간의 타임스탬프를 포함합니다. 예를 들어:<br /><br /> `2004-07-01 00:21:31.5073316`|
|%(CreatedTime)|항목을 만든 시간의 타임스탬프를 포함합니다. 예를 들어:<br /><br /> `2004-06-25 09:26:45.8237425`|
|%(AccessedTime)|항목을 마지막으로 액세스한 시간의 타임스탬프를 포함합니다.<br /><br /> `2004-08-14 16:52:36.3168743`|

## <a name="see-also"></a>참조

- [공통 MSBuild 항목 메타데이터](common-msbuild-item-metadata.md)
- [항목](../msbuild/msbuild-items.md)
- [일괄 처리](../msbuild/msbuild-batching.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
