---
title: DownloadFile 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81a9c3b1c22277261276ced1940f1f2e83d11882
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634255"
---
# <a name="downloadfile-task"></a>DownloadFile 작업

HTTP(Hypertext Transfer Protocol)를 사용하여 지정된 파일을 다운로드합니다.

>[!NOTE]
>DownloadFile 작업은 MSBuild 15.8 이상에서만 사용할 수 있습니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 `DownloadFile` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`DestinationFileName`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수<br /><br /> 다운로드한 파일에 사용할 이름입니다.  기본적으로 파일 이름은 `SourceUrl` 또는 원격 서버에서 파생됩니다.|
|`DestinationFolder`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 파일을 다운로드할 대상 폴더를 지정합니다.  폴더가 존재하지 않는 경우 폴더가 만들어집니다.|
|`DownloadedFile`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 출력 매개 변수입니다.<br /><br /> 다운로드한 파일을 지정합니다.|
|`Retries`|선택적 `Int32` 매개 변수입니다.<br /><br /> 이전 시도가 모두 실패한 경우 다운로드를 시도할 횟수를 지정합니다. 기본값은 0입니다.|
|`RetryDelayMilliseconds`|선택적 `Int32` 매개 변수입니다.<br /><br /> 필요한 다시 시도 간의 지연 시간(밀리초)을 지정합니다. 기본값은 5000입니다.|
|`SkipUnchangedFiles`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 변경되지 않은 파일의 다운로드를 건너뜁니다. 기본값은 `true`입니다. 파일 크기가 같고 원격 서버에 따라 마지막으로 수정된 시간이 같으면 `DownloadFile` 작업에서 파일이 변경되지 않은 것으로 간주합니다. <br /><br />**참고:** 일부 HTTP 서버는 파일의 마지막으로 수정한 날짜를 표시하지 않으므로 파일이 다시 다운로드됩니다.|
|`SourceUrl`|필수 `String` 매개 변수입니다.<br /><br /> 다운로드할 URL을 지정합니다.|

## <a name="remarks"></a>설명

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Utilities.Task> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

다음 예제에서는 파일을 다운로드하고, 프로젝트를 빌드하기 전 `Content` 항목에 포함시킵니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
