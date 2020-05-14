---
title: GetFileHash 작업 | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8f3de9a4f2fe848e1cbd41e14e82498845ca2cf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77578656"
---
# <a name="getfilehash-task"></a>GetFileHash 작업

파일 내용 또는 파일 집합의 체크섬을 계산합니다.

이 작업은 15.8에 추가되었지만 16.0 미만의 MSBuild 버전에 사용하려면 [해결 방법](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272)이 필요합니다.

## <a name="task-parameters"></a>작업 매개 변수

 다음 표에서는 `GetFileHash` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`Files`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br />해시할 파일입니다.|
|`Items`|<xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br />파일 해시로 설정된 추가 메타데이터가 포함된 `Files` 입력입니다.|
|`Hash`|`String` 출력 매개 변수입니다.<br /><br />파일의 해시입니다. 이 출력은 정확히 하나의 항목이 전달된 경우에만 설정됩니다.|
|`Algorithm`|선택적 `String` 매개 변수입니다.<br /><br />알고리즘입니다. 허용되는 값: `SHA256`, `SHA384`, `SHA512`. 기본값은 `SHA256`입니다.|
|`MetadataName`|선택적 `String` 매개 변수입니다.<br /><br />각 항목의 해시가 저장된 메타데이터 이름입니다. 기본값은 `FileHash`입니다.|
|`HashEncoding`|선택적 `String` 매개 변수입니다.<br /><br />생성된 해시에 사용할 인코딩입니다. 기본값은 `hex`입니다. 허용되는 값은 `hex`, `base64`입니다.|

## <a name="example"></a>예제

다음 예제는 `GetFileHash` 작업을 사용하여 `FilesToHash` 항목의 체크섬을 확인하고 인쇄합니다.

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)

- [작업 참조](../msbuild/msbuild-task-reference.md)