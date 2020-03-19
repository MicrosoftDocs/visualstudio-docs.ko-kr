---
title: 빌드 로거 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a00bbb8ce239275ff140dbedf2157e4cdc41d44c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634528"
---
# <a name="build-loggers"></a>빌드 로거

로거는 빌드 출력을 사용자 지정하고 특정 빌드 이벤트에 대한 응답에 메시지, 오류 또는 경고를 표시하는 방법을 제공합니다. 각 로거는 <xref:Microsoft.Build.Framework.ILogger> 인터페이스를 구현하는 .NET 클래스로 구현됩니다. 이 인터페이스는 *Microsoft.Build.Framework.dll* 어셈블리에서 정의됩니다.

로거를 구현할 때 다음 두 가지 방법을 사용할 수 있습니다.

- <xref:Microsoft.Build.Framework.ILogger> 인터페이스를 직접 구현합니다.
- 도우미 클래스 <xref:Microsoft.Build.Utilities.Logger>에서 클래스를 파생합니다. 이 클래스는 *Microsoft.Build.Utilities.dll* 어셈블리에서 정의됩니다. <xref:Microsoft.Build.Utilities.Logger>는 <xref:Microsoft.Build.Framework.ILogger>를 구현하고 일부 <xref:Microsoft.Build.Framework.ILogger> 멤버의 기본 구현을 제공합니다.

  이 항목에서는 <xref:Microsoft.Build.Utilities.Logger>에서 파생되는 단순 로거를 작성하는 방법을 설명하고 특정 빌드 이벤트에 대한 응답으로 콘솔에 메시지를 표시합니다.

## <a name="register-for-events"></a>이벤트에 등록

로거의 목적은 빌드 엔진에 의해 보고되는 빌드 진행률에 대한 정보를 수집한 후 해당 정보를 유용한 방식으로 보고하는 것입니다. 모든 로거는 로거가 이벤트를 등록하는 위치에 해당하는 <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> 메서드를 재정의해야 합니다. 이 예제에서는 로거가 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> 및 <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> 이벤트를 등록합니다.

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>이벤트에 응답

로거를 특정 이벤트에 등록했으므로 이제 이벤트가 발생할 때 해당 이벤트를 처리해야 합니다. <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> 및 <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> 이벤트에 대해 로거는 이벤트와 관련된 프로젝트 파일의 이름과 짧은 구를 간단히 씁니다. 로거에서 발생한 모든 메시지는 콘솔 창에 기록됩니다.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>로거 세부 정보 표시 값에 대한 응답

MSBuild.exe **-verbosity** 스위치에 특정 값이 포함되어 있을 때만 이벤트의 정보를 로그하려는 경우도 있습니다. 이 예제에서 <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> 이벤트 처리기는 **-verbosity** 스위치에 의해 설정된 <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> 속성이 <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`인 경우에만 메시지를 로그합니다.

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>로거 지정

로거가 어셈블리로 컴파일되면 빌드하는 동안 MSBuild에 해당 로거를 사용하도록 지시해야 합니다. 이 작업은 *MSBuild.exe*와 함께 **-logger** 스위치를 사용하여 수행합니다. *MSBuild.exe*에 대해 사용할 수 있는 스위치에 대한 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조하세요.

다음 명령줄은 프로젝트 *MyProject.csproj*를 빌드하고 *SimpleLogger.dll*에서 구현된 로거 클래스를 사용합니다. **nologo** 스위치는 배너 및 저작권 메시지를 숨기고 **-noconsolelogger** 스위치는 기본 MSBuild 콘솔 로거를 사용하지 않도록 설정합니다.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

다음 명령줄은 동일한 로거를 사용하지만 `Verbosity` 수준 `Detailed`를 사용하여 프로젝트를 빌드합니다.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예제에서는 로거에 대한 전체 코드를 보여 줍니다.

### <a name="code"></a>코드

[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예제에서는 로그를 콘솔 창에 표시하지 않고 파일에 쓰는 로거를 구현하는 방법을 보여 줍니다.

### <a name="code"></a>코드

[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>참조

- [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
