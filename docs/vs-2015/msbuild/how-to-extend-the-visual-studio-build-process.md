---
title: '방법: 빌드 프로세스 확장 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 789c60da5be841721ab3a999120e2fe560ffd588
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156604"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>방법: Visual Studio 빌드 프로세스 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 빌드 프로세스는 프로젝트 파일로 가져온 일련의 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .targets 파일로 정의됩니다. 이러한 가져온 파일 중 하나인 Microsoft.Common.targets는 빌드 프로세스의 여러 지점에서 사용자 지정 작업을 실행할 수 있도록 확장될 수 있습니다. 이 항목에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 빌드 프로세스를 확장하는 데 사용할 수 있는 두 가지 방법을 설명합니다.

- Microsoft.Common.targets에 정의된 특정 미리 정의된 대상 재정의

- Microsoft.Common.targets에 정의된 "DependsOn" 속성 재정의

## <a name="overriding-predefined-targets"></a>미리 정의된 대상 재정의
 Microsoft.Common.targets 파일은 빌드 프로세스의 일부 주요 대상의 전후에 호출되는 미리 정의된 빈 대상 집합을 포함합니다. 예를 들어 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]은(는) 메인 `BeforeBuild` 대상 전에 `CoreBuild` 대상을 호출하고 `CoreBuild` 대상 후에 `AfterBuild` 대상을 호출합니다. 기본적으로 Microsoft.Common.targets의 빈 대상은 아무 것도 수행하지 않지만 프로젝트 파일에서 Microsoft.Common.targets를 가져오는 원하는 대상을 정의하여 해당 기본 동작을 재정의할 수 있습니다. 이를 통해 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 작업을 사용하여 빌드 프로세스에 대한 더 많은 제어를 제공할 수 있습니다.

#### <a name="to-override-a-predefined-target"></a>미리 정의된 대상을 재정의하려면

1. 재정의하려는 Microsoft.Common.targets에서 미리 정의된 대상을 식별합니다. 안전하게 재정의할 수 있는 대상의 전체 목록은 아래 표를 참조하세요.

2. `</Project>` 태그 바로 앞에, 프로젝트 파일의 끝에 하나 이상의 대상을 정의합니다. 예를 들면 다음과 같습니다.

   ```
   <Project>
       ...
       <Target Name="BeforeBuild">
           <!-- Insert tasks to run before build here -->
       </Target>
       <Target Name="AfterBuild">
           <!-- Insert tasks to run after build here -->
       </Target>
   </Project>
   ```

3. 프로젝트 파일을 빌드합니다.

   다음 표는 안전하게 재정의할 수 있는 Microsoft.Common.targets에서 모든 대상을 표시합니다.

|대상 이름|Description|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|이러한 대상 중 하나에 삽입된 작업은 핵심 컴파일이 완료되기 전이나 후에 실행됩니다. 대부분의 사용자 지정은 이러한 두 개의 대상 중 하나에서 수행됩니다.|
|`BeforeBuild`, `AfterBuild`|이러한 대상 중 하나에 삽입된 작업은 빌드의 모든 작업 전이나 후에 실행됩니다. **참고:**`BeforeBuild` 및 `AfterBuild` 대상은 대부분의 프로젝트 파일 끝의 주석에서 이미 정의되어 있습니다. 이를 통해 빌드 전 및 후 이벤트를 프로젝트 파일에 쉽게 추가할 수 있습니다.|
|`BeforeRebuild`, `AfterRebuild`|이러한 대상 중 하나에 삽입된 작업은 핵심 다시 빌드 기능이 호출되기 전 또는 후에 실행됩니다. Microsoft.Common.targets에서 대상 실행 순서는 `BeforeRebuild`, `Clean`, `Build` 및 `AfterRebuild`입니다.|
|`BeforeClean`, `AfterClean`|이러한 대상 중 하나에 삽입된 작업은 핵심 정리 기능이 호출되기 전 또는 후에 실행됩니다.|
|`BeforePublish`, `AfterPublish`|이러한 대상 중 하나에 삽입된 작업은 핵심 게시 기능이 호출되기 전 또는 후에 실행됩니다.|
|`BeforeResolveReference`, `AfterResolveReferences`|이러한 대상 중 하나에 삽입된 작업은 어셈블리 참조가 확인되기 전이나 후에 실행됩니다.|
|`BeforeResGen`, `AfterResGen`|이러한 대상 중 하나에 삽입된 작업은 어셈블리 리소스가 생성되기 전이나 후에 실행됩니다.|

## <a name="overriding-dependson-properties"></a>"DependsOn" 속성 재정의
 미리 정의된 대상 재정의는 빌드 프로세스를 확장하는 쉬운 방법이지만 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]에서 대상의 정의를 순차적으로 평가하므로 프로젝트를 가져오는 다른 프로젝트에서 이미 재정의한 대상을 재정의하는 것을 방지할 방법이 없습니다. 따라서 예를 들어 다른 모든 프로젝트를 가져온 후 프로젝트에서 정의된 마지막 `AfterBuild` 대상은 빌드 중 사용되는 대상이 됩니다.

 Microsoft.Common.targets 파일 전체의 `DependsOnTargets` 특성에서 사용되는 "DependsOn" 속성을 재정의하여 의도하지 않은 대상의 재정의를 방지할 수 있습니다. 예를 들어 `Build` 대상은 `"$(BuildDependsOn)"`의 `DependsOnTargets` 특성 값을 포함합니다. 고려할 사항은 다음과 같습니다.

```
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

 이 XML 조각은 `Build` 대상 전에 실행할 수 있음을 나타내며 `BuildDependsOn` 속성에 지정된 모든 대상은 먼저 실행되어야 합니다. `BuildDependsOn` 속성은 다음으로 정의됩니다.

```
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

 프로젝트 파일의 끝에서 `BuildDependsOn`이라는 다른 속성을 선언하여 이 속성 값을 재정의할 수 있습니다. 새 속성에서 이전 `BuildDependsOn` 속성을 포함하여 대상 목록의 시작과 끝에 새 대상을 추가할 수 있습니다. 예를 들면 다음과 같습니다.

```
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

 프로젝트 파일을 가져오는 프로젝트는 만든 사용자 지정 항목을 덮어쓰지 않고 이러한 속성을 재정의할 수 있습니다.

#### <a name="to-override-a-dependson-property"></a>"DependsOn" 속성을 재정의하려면

1. 재정의하려는 Microsoft.Common.targets에서 미리 정의된 "DependsOn" 속성을 식별합니다. 일반적으로 재정의된 "DependsOn" 속성의 목록은 아래 표를 참조하세요.

2. 프로젝트 파일의 끝에서 속성의 다른 인스턴스를 정의합니다. 새 속성에 원래 속성을 포함합니다(예: `$(BuildDependsOn)`).

3. 속성 정의 앞 또는 뒤에 사용자 지정 대상을 정의합니다.

4. 프로젝트 파일을 빌드합니다.

### <a name="commonly-overridden-dependson-properties"></a>일반적으로 재정의된 "DependsOn" 속성

|속성 이름|Description|
|-------------------|-----------------|
|`BuildDependsOn`|전체 빌드 프로세스 앞이나 뒤에 사용자 지정 대상을 삽입하려는 경우 재정의할 속성입니다.|
|`CleanDependsOn`|사용자 지정 빌드 프로세스에서 출력을 정리하려는 경우 재정의할 속성입니다.|
|`CompileDependsOn`|컴파일 단계 앞이나 뒤에 사용자 지정 프로세스를 삽입하려는 경우 재정의할 속성입니다.|

## <a name="see-also"></a>관련 항목
 [Visual Studio 통합](../msbuild/visual-studio-integration-msbuild.md) [MSBuild 개념](../msbuild/msbuild-concepts.md) [.Targets 파일](../msbuild/msbuild-dot-targets-files.md)
