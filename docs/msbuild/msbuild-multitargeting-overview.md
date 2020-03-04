---
title: MSBuild 멀티 타기팅 개요 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af7649a75fbf3ded0cf5d09e9063b49f4fcab1b2
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633332"
---
# <a name="msbuild-multitargeting-overview"></a>MSBuild 멀티 타기팅 개요

MSBuild를 사용하면 .NET Framework의 여러 버전 중 하나 및 여러 시스템 플랫폼 중 하나에서 실행되는 애플리케이션을 컴파일할 수 있습니다. 예를 들어 32비트 플랫폼의 .NET Framework 2.0에서 실행되도록 애플리케이션을 컴파일하고 동일한 애플리케이션을 64비트 플랫폼의 .NET Framework 4.5에서 실행되도록 컴파일할 수 있습니다.

> [!IMPORTANT]
> 이름이 “멀티 타기팅”이지만 프로젝트는 한 번에 하나의 프레임워크만, 그리고 하나의 플랫폼만 대상으로 지정할 수 있습니다.

 MSBuild 대상 지정의 몇 가지 기능은 다음과 같습니다.

- .NET Framework의 이전 버전(예: 2.0, 3.5 또는 4)을 대상으로 하는 애플리케이션을 개발할 수 있습니다.

- .NET Framework 외에 Silverlight 프레임워크 등의 다른 프레임워크를 대상으로 지정할 수 있습니다.

- 대상 프레임워크의 미리 정의된 하위 집합인 *프레임워크 프로필*을 대상으로 지정할 수 있습니다.

- 현재 버전의 .NET Framework용 서비스 팩이 릴리스될 경우 해당 서비스 팩을 대상으로 지정할 수 있습니다.

- MSBuild 대상 지정은 대상 프레임워크 및 플랫폼에서 사용 가능한 기능만 애플리케이션에서 사용되도록 합니다.

## <a name="target-framework-and-platform"></a>대상 프레임워크 및 플랫폼

 *대상 프레임워크*는 프로젝트가 실행되도록 기본 제공되는 .NET Framework의 버전이고 *대상 플랫폼*은 프로젝트가 실행되도록 기본 제공되는 시스템 플랫폼입니다.  예를 들어 802x86 프로세서 제품군(x86)과 호환되는 32비트 플랫폼에서 실행할 .NET Framework 2.0 애플리케이션을 대상으로 지정할 수 있습니다. 대상 프레임워크와 대상 플랫폼의 조합을 *대상 컨텍스트*라고 합니다. 자세한 내용은 [대상 프레임워크 및 대상 플랫폼](../msbuild/msbuild-target-framework-and-target-platform.md)을 참조하세요.

## <a name="toolset-toolsversion"></a>도구 집합(ToolsVersion)

 도구 집합은 애플리케이션을 만드는 데 사용되는 도구, 작업 및 대상을 함께 수집합니다. 도구 집합에는 *csc.exe* 및 *vbc.exe*와 같은 컴파일러, 일반 대상 파일(*microsoft.common.targets*) 및 일반 작업 파일(*microsoft.common.tasks*)이 포함됩니다. 4\.5 도구 집합은 .NET Framework 버전 2.0, 3.0, 3.5, 4, 4.5를 대상으로 지정하는 데 사용될 수 있습니다. 하지만 2.0 도구 집합은 .NET Framework 버전 2.0을 대상으로 지정하는 데만 사용될 수 있습니다. 자세한 내용은 [도구 집합(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)을 참조하세요.

## <a name="reference-assemblies"></a>참조 어셈블리

 도구 집합에 지정된 참조 어셈블리를 사용하여 애플리케이션을 디자인하고 빌드할 수 있습니다. 이러한 참조 어셈블리는 특정 대상 빌드를 사용하도록 설정하고 Visual Studio IDE의 구성 요소와 기능을 대상과 호환되는 구성 요소와 기능으로 제한합니다. 자세한 내용은 [디자인 타임에 어셈블리 확인](../msbuild/resolving-assemblies-at-design-time.md)을 참조하세요.

## <a name="configure-targets-and-tasks"></a>대상 및 작업 구성

 MSBuild 대상 및 작업을 구성하여 MSBuild를 통해 out-of-process로 실행할 수 있으므로 현재 실행하고 있는 컨텍스트와는 상당히 다른 컨텍스트를 대상으로 지정할 수 있습니다.  예를 들어, .NET Framework 4.5가 설치된 64비트 플랫폼에서 개발 컴퓨터가 실행되는 동안 32비트 .NET Framework 2.0 애플리케이션을 대상으로 지정할 수 있습니다. 자세한 내용은 [대상 및 작업 구성](../msbuild/configuring-targets-and-tasks.md)을 참조하세요.

## <a name="troubleshooting"></a>문제 해결

 대상 컨텍스트에 포함되지 않은 어셈블리를 참조하려고 하면 오류가 발생할 수 있습니다. 이러한 오류 및 수행할 관련 작업에 대한 자세한 내용은 [.NET Framework 대상 지정 오류 문제 해결](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)을 참조하세요.
