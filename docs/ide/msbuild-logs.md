---
title: MSBuild의 문제 해결 및 로그 만들기
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: ae91f7b9c90f0b06c449d26f67fe4fcc3434518e
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768699"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>MSBuild의 문제 해결 및 로그 만들기

다음 절차는 Visual Studio 프로젝트에서 빌드 문제를 진단하고 필요한 경우 조사를 위해 Microsoft로 보낼 로그를 만드는 데 도움이 됩니다.

## <a name="a-property-value-is-ignored"></a>속성 값은 무시됩니다.

프로젝트 속성이 특정 값으로 설정된 것으로 보이지만 빌드에 영향을 주지는 않는 경우 다음 단계를 수행합니다.

1. Visual Studio의 버전에 해당하는 Visual Studio 개발자 명령 프롬프트를 엽니다.
1. 솔루션 경로, 구성 및 프로젝트 이름을 값으로 대체한 후 다음 명령을 실행합니다.

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    이 명령은 “전처리된” msbuild 프로젝트 파일 (out.xml)을 생성합니다. 해당 파일을 검색하여 특정 속성이 정의된 위치를 볼 수 있습니다.

빌드에서는 속성의 마지막 정의가 사용됩니다. 속성이 두 번 설정된 경우에는 두 번째 값이 첫 번째 값을 덮어씁니다. 또한 MSBuild는 여러 단계에서 프로젝트를 평가합니다.

- PropertyGroups 및 Imports
- ItemDefinitionGroups
- ItemGroups
- 대상

따라서 다음과 같은 순서인 경우:

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

“MyFile.txt” 항목에 대한 “MyMetadata” 값은 빌드 중에 “B”로 평가됩니다(“A”가 아니며 공백도 아님).

## <a name="incremental-build-is-building-more-than-it-should"></a>증분 빌드는 필요한 정도보다 더 많이 빌드합니다.

MSBuild가 프로젝트 또는 프로젝트 항목을 불필요하게 다시 빌드하는 경우 자세한 또는 이진 빌드 로그를 만듭니다. 불필요하게 빌드 또는 컴파일된 파일에 대한 로그를 검색할 수 있습니다. 출력은 다음과 같습니다.

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

Visual Studio IDE(출력 창의 자세한 정도가 지정된)에서 빌드하는 경우 **출력 창**은 각 프로젝트가 최신 상태가 아닌 이유를 표시합니다.

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>이진 msbuild 로그 만들기

1. Visual Studio 버전에 맞는 개발자 명령 프롬프트 열기
1. 명령 프롬프트에서 다음 명령 중 하나를 실행합니다. (실제 프로젝트 및 구성 값을 사용해야 합니다.)

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    또는

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Msbuild.binlog 파일이 MSBuild를 실행한 디렉터리에 만들어집니다. [Msbuild 구조적 로그 뷰어](http://www.msbuildlog.com/)를 사용하여 보고 검색할 수 있습니다.

## <a name="create-a-detailed-log"></a>자세한 로그를 만들기

1. Visual Studio 주 메뉴에서 **도구** > **옵션** > **프로젝트 및 솔루션** >**빌드 및 실행**으로 이동합니다.
1. 두 콤보 상자 모두에서 **Msbuild 프로젝트 빌드 자세한 정도**를 **자세히**로 설정합니다. 첫 번째 컨트롤은 **출력 창**의 세부 정보 표시를 빌드하고 두 번째 컨트롤은 빌드 중에 각 프로젝트의 중간 디렉터리에서 만들어진 \<projectname\>.log 파일의 세부 정보 표시를 빌드합니다.
2. Visual Studio 개발자 명령 프롬프트에서 실제 경로 및 구성 값을 대체하는 이러한 명령 중 하나를 입력합니다.

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    또는

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Msbuild.log 파일이 msbuild를 실행한 디렉터리에 만들어집니다.
