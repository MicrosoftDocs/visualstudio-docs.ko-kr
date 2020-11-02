---
title: GetFrameworkSdkPath 작업 | Microsoft Docs
description: MSBuild GetFrameworkSdkPath 작업을 사용하여 Windows SDK 경로를 검색하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4061dbe96c84648aacf136c0d59b92a2af037e2
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436809"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath 작업

Windows SDK(소프트웨어 개발 키트) 경로를 검색합니다.
## <a name="task-parameters"></a>작업 매개 변수

다음 표에서는 `GetFrameworkSdkPath` 작업의 매개 변수에 대해 설명합니다.
다음 표에서는 `GetFrameworkSdkPath` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|선택적 `String` 읽기 전용 출력 매개 변수입니다.<br /><br /> .NET SDK 버전 2.0에 대한 경로가 있는 경우 반환합니다. 그렇지 않으면 `String.Empty`를 반환합니다.|
|`FrameworkSdkVersion35Path`|선택적 `String` 읽기 전용 출력 매개 변수입니다.<br /><br /> .NET SDK 버전 3.5에 대한 경로가 있는 경우 반환합니다. 그렇지 않으면 `String.Empty`를 반환합니다.|
|`FrameworkSdkVersion40Path`|선택적 `String` 읽기 전용 출력 매개 변수입니다.<br /><br /> .NET SDK 버전 4.0에 대한 경로가 있는 경우 반환합니다. 그렇지 않으면 `String.Empty`를 반환합니다.|
|`Path`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 버전이 있는 경우 최신 .NET SDK에 대한 경로를 포함합니다. 그렇지 않으면 `String.Empty`를 반환합니다.|

## <a name="remarks"></a>설명

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

다음 예제에서는 `GetFrameworkSdkPath` 작업을 사용하여 `SdkPath` 속성에 Windosws SDK 경로를 저장합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkSdkPath>
            <Output
                TaskParameter="Path"
                PropertyName="SdkPath" />
        </GetFrameworkSdkPath>
        <Message Text="$(SdkPath)"/>
    </Target>
</Project>
```

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
