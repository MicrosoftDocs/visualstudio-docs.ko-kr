---
title: Message 작업 | Microsoft Docs
description: 빌드 중에 메시지를 기록하는 MSBuild Message 작업의 매개 변수 및 설정에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b7a2854220a7ee85fd680cedd8c8e0c5c3ada89
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903842"
---
# <a name="message-task"></a>Message 작업

빌드하는 동안 메시지를 로깅합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `Message` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`Importance`|선택적 `String` 매개 변수입니다.<br /><br /> 메시지의 중요도를 지정합니다. 이 매개 변수는 `high`, `normal` 또는 `low` 값을 가질 수 있습니다. 기본값은 `normal`입니다.|
|`Text`|선택적 `String` 매개 변수입니다.<br /><br /> 기록할 오류 텍스트입니다.|

## <a name="remarks"></a>설명

 `Message` 작업을 통해 MSBuild 프로젝트는 빌드 프로세스의 여러 다른 단계에서 로거로 메시지를 발급할 수 있습니다.

 `Condition` 매개 변수가 `true`이면 `Text` 매개 변수 값은 로깅되고 빌드가 계속 실행됩니다. `Condition` 매개 변수가 없으면 메시지 텍스트가 로깅됩니다. 로깅에 대한 자세한 내용은 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)를 참조하세요.

 기본적으로 메시지는 등록된 모든 로거에 전송됩니다. 로거는 `Importance` 매개 변수를 해석합니다. 일반적으로 `high`로 설정된 메시지는 로거의 세부 정보 표시 수준이 <xref:Microsoft.Build.Framework.LoggerVerbosity>.`Minimal`로 설정된 경우에 전송됩니다. 필요합니다. `low`로 설정된 메시지는 로거의 세부 정보 표시 수준이 <xref:Microsoft.Build.Framework.LoggerVerbosity>.`Detailed`로 설정된 경우에 전송됩니다.

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

 다음 코드 예제에서는 등록된 모든 로거에 메시지를 로깅합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="DisplayMessages">
        <Message Text="Project File Name = $(MSBuildProjectFile)" />
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>참고 항목

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)
