---
title: MSBuild의 솔루션 필터
description: 솔루션 필터에 대해 설명하고 MSBuild를 사용하여 솔루션 필터 파일을 빌드하는 방법을 보여 줍니다.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 998103828d20827e8a1d99e0cc34d7f9beb6bd7c
ms.sourcegitcommit: 9179c33a78c2ac690ce908d7c73eef50b6e367f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87401050"
---
# <a name="solution-filters-in-msbuild"></a>MSBuild의 솔루션 필터

솔루션 필터 파일은 특정 솔루션의 모든 프로젝트에서 빌드 또는 로드할 프로젝트를 나타내는 *.slnf* 확장명을 가진 JSON 파일입니다. MSBuild 16.7부터 솔루션 필터 파일에 대해 MSBuild를 호출하여 필터링을 사용하도록 솔루션을 빌드할 수 있습니다. 

> [!NOTE]
> 솔루션 필터 파일은 로드 또는 빌드되는 프로젝트 집합을 줄이고 형식을 단순화합니다. 솔루션 파일은 계속해서 필요합니다.

## <a name="build-a-solution-filter-from-the-command-line"></a>명령줄에서 솔루션 필터 빌드

명령줄에서 솔루션 필터 파일을 빌드하면 솔루션 파일을 빌드할 때와 정확히 동일한 구문을 사용합니다. 필터링을 사용하도록 빌드할 솔루션 대신 솔루션 필터 파일을 다음과 같이 지정합니다.

```console
msbuild [options] solutionFilterFile.slnf
```

기존처럼 스위치 및 추가 속성을 추가할 수도 있습니다. [MSBuild 명령줄 참조](msbuild-command-line-reference.md)를 참조하세요. 이 명령은 필터링된 프로젝트와 해당 프로젝트가 종속되는 모든 프로젝트를 빌드합니다. 명령줄에서 솔루션 필터를 빌드하는 경우 MSBuild는 자동으로 종속성을 따릅니다. MSBuild는 필터에 지정되거나 이미 빌드된 프로젝트에서 참조되는 프로젝트를 빌드합니다.

## <a name="solution-filter-files"></a>솔루션 필터 파일

Visual Studio를 사용하여 솔루션 필터 파일 작업을 수행할 수 있습니다. Visual Studio에서 솔루션 필터를 열면 로드된 프로젝트는 물론 언로드된 프로젝트가 표시되며, 빌드에 선택할 수 있도록 더 많은 프로젝트를 로드하는 옵션이 제공됩니다. 빌드를 위해 초기 프로젝트가 종속되는 모든 프로젝트를 로드하는 것도 가능하지만 필수 사항은 아닙니다. [필터링된 솔루션](../ide/filtered-solutions.md)을 참조하세요.

솔루션 필터는 솔루션과 동일한 폴더에 있지 않아도 됩니다. 솔루션 파일의 경로는 솔루션 필터 파일의 위치를 기준으로 하지만, 각 프로젝트의 경로는 솔루션 파일 자체를 기준으로 하며 솔루션 파일의 프로젝트 경로와 일치해야 합니다. 다음 예제에서는 상대 경로를 사용하는 방법을 보여 줍니다.

```json
{
  "solution": {
    "path": "..\\..\\Documents\\GitHub\\msbuild\\MSBuild.sln",
    "projects": [
      "src\\Build.OM.UnitTests\\Microsoft.Build.Engine.OM.UnitTests.csproj"
    ]
  }
}
```

경로에서 백슬래시는 이스케이프되기 때문에 이중으로 입력해야 합니다.

## <a name="example"></a>예제

다음은 Visual Studio의 필터링된 솔루션 예제입니다.

![Visual Studio의 필터링된 솔루션 스크린샷](media/solution-with-filter.png)

이 솔루션에서 ClassLibrary1은 ProjectA 및 ProjectB 모두에서 사용되므로 ClassLibrary1은 프로젝트 참조로 나열됩니다.

다음은 Visual Studio에서 생성하는 솔루션 필터 파일입니다.

```json
{
  "solution": {
    "path": "MyApplication.sln",
    "projects": [
      "MyApplication\\MyApplication.csproj",
      "ProjectA\\ProjectA.csproj"
    ]
  }
}
```

이 예제의 경우, (`MSBuild [options] MyFilter.slnf` 명령을 사용하여) 필터링이 활성화된 상태로 빌드할 때 MSBuild는 솔루션 필터 파일에 명시적으로 나열되어 있는 MyApplication 및 ProjectA를 빌드합니다. ProjectA 빌드 과정에서 MSBuild는 ProjectA가 종속되는 Classlibrary1을 빌드합니다.  ProjectB는 빌드되지 않습니다. (이 설명에서는 클린 빌드를 가정합니다. 이전에 프로젝트가 빌드된 경우, 이미 최신 상태에 있는 프로젝트를 건너뛰는 데 일반적인 규칙이 적용됩니다.)

## <a name="see-also"></a>참조

- [필터링된 솔루션](../ide/filtered-solutions.md)
- [MSBuild 명령줄 참조](msbuild-command-line-reference.md)
