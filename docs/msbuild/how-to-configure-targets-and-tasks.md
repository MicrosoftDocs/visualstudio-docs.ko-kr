---
title: '방법: 대상 및 작업 구성 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe2955feb50a28e5ba631cdeddd169973a42ed25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633891"
---
# <a name="how-to-configure-targets-and-tasks"></a>방법: 대상 및 작업 구성

선택된 MSBuild 작업은 개발 컴퓨터의 환경에 관계 없이 대상으로 지정된 환경에서 실행되도록 설정할 수 있습니다. 예를 들어 64비트 컴퓨터를 사용하여 32비트 아키텍처를 대상으로 하는 애플리케이션을 빌드할 경우 선택한 작업은 32비트 프로세스에서 실행됩니다.
선택된 MSBuild 작업은 개발 컴퓨터의 환경에 관계 없이 대상으로 지정된 환경에서 실행되도록 설정할 수 있습니다. 예를 들어 64비트 컴퓨터를 사용하여 32비트 아키텍처를 대상으로 하는 애플리케이션을 빌드할 경우 선택한 작업은 32비트 프로세스에서 실행됩니다.

> [!NOTE]
> 빌드 작업이 Visual C# 또는 Visual Basic 같은 .NET 언어로 작성되고 네이티브 리소스 또는 도구를 사용하지 않는 경우 조정 없이도 모든 대상 컨텍스트에서 실행됩니다.

## <a name="usingtask-attributes-and-task-parameters"></a>UsingTask 특성 및 작업 매개 변수

다음 `UsingTask` 특성은 특정 빌드 프로세스에서 작업의 모든 작동에 영향을 줍니다.

- `Runtime` 특성(있는 경우)은 CLR(공용 언어 런타임) 버전을 설정하고 `CLR2`, `CLR4`, `CurrentRuntime` 또는 `*`(임의 런타임) 값 중 하나를 사용할 수 있습니다.

- `Architecture` 특성(있는 경우)은 플랫폼 및 비트를 설정하고 `x86`, `x64`, `CurrentArchitecture` 또는 `*`(임의 아키텍처) 값 중 하나를 사용할 수 있습니다.

- `TaskFactory` 특성은(있는 경우) 작업 인스턴스를 만들고 실행하는 작업 팩터리를 설정하고 값 `TaskHostFactory`만 사용합니다. 자세한 내용은 이 문서 뒷부분에 나오는 [작업 팩터리](#task-factories)를 참조하세요.

```xml
<UsingTask TaskName="SimpleTask"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />
```

`MSBuildRuntime` 및 `MSBuildArchitecture` 매개 변수를 사용하여 개별 작업의 대상 컨텍스트를 설정할 수도 있습니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

MSBuild가 작업을 실행하기 전에 동일한 대상 컨텍스트를 갖는 일치하는 `UsingTask`를 찾습니다. `UsingTask`에 지정되어 있으나 해당 작업에는 지정되지 않은 매개 변수는 일치하는 항목으로 간주됩니다. 작업에 지정되어 있으나 해당 `UsingTask`에는 지정되지 않은 매개 변수도 일치하는 항목으로 간주됩니다. 매개 변수 값이 `UsingTask` 및 작업 둘 다에 지정되지 않은 경우 값의 기본값은 `*`(임의 매개 변수)입니다.

> [!WARNING]
> 둘 이상의 `UsingTask`가 존재하며 모두 일치하는 `TaskName`, `Runtime` 및 `Architecture` 특성을 갖는 경우 마지막으로 평가되는 특성이 다른 특성을 대신합니다.

 매개 변수가 작업에 설정되어 있으면 MSBuild는 이러한 매개 변수와 일치하거나 적어도 충돌하지 않는 `UsingTask`를 찾으려고 합니다. 둘 이상의 `UsingTask`는 동일한 작업의 대상 컨텍스트를 지정할 수 있습니다. 예를 들어, 대상 환경마다 다른 실행 파일을 갖는 작업은 다음과 비슷할 수 있습니다.

```xml
<UsingTask TaskName="MyTool"
    Runtime="CLR2"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />

<UsingTask TaskName="MyTool"
    Runtime="CLR4"
    Architecture="x86"
    AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />

<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>
    </Target>
</Project>

```

## <a name="task-factories"></a>작업 팩터리

작업을 실행하기 전에 MSBuild는 작업이 현재 소프트웨어 컨텍스트에서 실행되도록 지정되어 있는지 여부를 확인합니다. 작업이 이렇게 지정된 경우 MSBuild는 작업을 현재 프로세스에서 실행하는 AssemblyTaskFactory로 전달하고, 그렇지 않으면 대상 컨텍스트와 일치하는 프로세스에서 작업을 실행하는 TaskHostFactory로 작업을 전달합니다. 현재 컨텍스트 및 대상 컨텍스트가 일치하더라도 `TaskFactory`를 `TaskHostFactory`로 설정하여 강제로 작업이 out-of-process로 실행되도록 할 수 있습니다(격리, 보안 또는 기타 이유로).

```xml
<UsingTask TaskName="MisbehavingTask"
    TaskFactory="TaskHostFactory"
    AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">
</UsingTask>
```

## <a name="phantom-task-parameters"></a>가상 작업 매개 변수

다른 모든 작업 매개 변수와 마찬가지로 `MSBuildRuntime` 및 `MSBuildArchitecture`는 빌드 속성에서 설정할 수 있습니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <FrameworkVersion>3.0</FrameworkVersion>
    </PropertyGroup>
    <Target Name="MyTarget">
        <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>
    </Target>
</Project>
```

다른 작업 매개 변수와 달리 `MSBuildRuntime` 및 `MSBuildArchitecture`는 작업 자체에 표시되지 않습니다. 실행되는 컨텍스트를 인식하는 작업을 작성하려면 .NET Framework를 호출하여 컨텍스트를 테스트하거나 빌드 속성을 사용하여 다른 작업 매개 변수를 통해 컨텍스트 정보를 전달해야 합니다.

> [!NOTE]
> `UsingTask` 특성은 도구 집합 및 환경 속성에서 설정할 수 있습니다.

`MSBuildRuntime` 및 `MSBuildArchitecture` 매개 변수는 대상 컨텍스트 뿐만 아니라 가장 제한적인 범위를 설정하는 가장 유연한 방법을 제공합니다. 한편 이러한 매개 변수는 작업 인스턴스 자체에서 설정되고 작업이 실행된 다음에야 평가되기 때문에 평가 시간과 빌드 시간에 모두 사용할 수 있는 전체 범위의 속성에서 값을 파생시킬 수 있습니다. 반면 이러한 매개 변수는 특정 대상에 있는 특정 작업 인스턴스에만 적용됩니다.

> [!NOTE]
> 작업 매개 변수는 작업 호스트의 컨텍스트가 아니라 부모 노드의 컨텍스트에서 평가됩니다. 런타임 종속적 또는 아키텍처 종속적 환경 변수(예: *프로그램 파일* 위치)는 부모 노드와 일치하는 값으로 평가됩니다. 그러나 동일한 환경 변수를 작업에서 직접 읽을 경우 작업 호스트의 컨텍스트에서 올바르게 평가됩니다.

## <a name="see-also"></a>참고 항목

- [대상 및 작업 구성](../msbuild/configuring-targets-and-tasks.md)
