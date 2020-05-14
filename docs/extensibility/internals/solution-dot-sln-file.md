---
title: 솔루션(. Sln) 파일
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705326"
---
# <a name="solution-sln-file"></a>솔루션(.sln) 파일

솔루션은 Visual Studio에서 프로젝트를 구성하는 구조입니다. 이 솔루션은 두 파일에서 프로젝트의 상태 정보를 유지 관리합니다.

- .sln 파일(텍스트 기반, 공유)

- .suo 파일(바이너리, 사용자별 솔루션 옵션)

.suo 파일에 대한 자세한 내용은 [솔루션 사용자 옵션(를 참조하십시오. Suo) 파일](../../extensibility/internals/solution-user-options-dot-suo-file.md).

.sln 파일에서 참조된 결과로 VSPackage가 로드된 경우 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> .sln 파일에서 읽기를 호출합니다.

.sln 파일에는 환경이 지속된 데이터와 참조하는 프로젝트 VSPackages에 대한 이름 값 매개 변수를 찾고 로드하는 데 사용하는 텍스트 기반 정보가 포함되어 있습니다. 사용자가 솔루션을 열면 환경은 .sln 파일의 `preSolution`에서 의 및 `Project` `postSolution` 정보를 순환하여 솔루션을 로드하고, 솔루션 내의 프로젝트 및 솔루션에 연결된 모든 지속된 정보를 로드합니다.

각 프로젝트의 파일에는 해당 프로젝트의 항목으로 계층 구조를 채우기 위해 환경에서 읽은 추가 정보가 포함되어 있습니다. 계층 데이터 지속성은 프로젝트에 의해 제어됩니다. 데이터는 일반적으로 .sln 파일에 저장되지 않지만.sln 파일에 프로젝트 정보를 의도적으로 쓸 수 있습니다. 지속성에 대한 자세한 내용은 [프로젝트 지속성](../../extensibility/internals/project-persistence.md) 및 [프로젝트 항목 열기 및 저장을](../../extensibility/internals/opening-and-saving-project-items.md)참조하십시오.

## <a name="file-header"></a>파일 헤더

.sln 파일의 헤더는 다음과 같습니다.

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>정의

`Microsoft Visual Studio Solution File, Format Version 12.00`\
파일 형식 버전을 정의하는 표준 헤더입니다.

`# Visual Studio 15`\
(가장 최근에) 이 솔루션 파일을 저장한 Visual Studio의 주요 버전입니다. 이 정보는 솔루션 아이콘의 버전 번호를 제어합니다.

`VisualStudioVersion = 15.0.26730.15`\
(가장 최근에) 솔루션 파일을 저장 한 Visual Studio의 전체 버전입니다. 동일한 주 버전을 사용하는 최신 버전의 Visual Studio에 솔루션 파일을 저장하는 경우 솔루션 파일의 이탈을 줄이도록 이 값이 업데이트되지 않습니다.

`MinimumVisualStudioVersion = 10.0.40219.1`\
이 솔루션 파일을 열 수 있는 최소(가장 오래된) 버전의 Visual Studio입니다.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>정의

`Microsoft Visual Studio Solution File, Format Version 12.00`\
파일 형식 버전을 정의하는 표준 헤더입니다.

`# Visual Studio Version 16`\
(가장 최근에) 이 솔루션 파일을 저장한 Visual Studio의 주요 버전입니다. 이 정보는 솔루션 아이콘의 버전 번호를 제어합니다.

`VisualStudioVersion = 16.0.28701.123`\
(가장 최근에) 솔루션 파일을 저장 한 Visual Studio의 전체 버전입니다. 동일한 주 버전을 사용하는 최신 버전의 Visual Studio에 솔루션 파일을 저장하는 경우 이 값은 파일의 변동을 줄이도록 업데이트되지 않습니다.

`MinimumVisualStudioVersion = 10.0.40219.1`\
이 솔루션 파일을 열 수 있는 최소(가장 오래된) 버전의 Visual Studio입니다.

::: moniker-end

## <a name="file-body"></a>파일 본문

.sln 파일의 본문에는 다음과 같이 `GlobalSection`레이블이 지정된 여러 섹션으로 구성됩니다.

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

솔루션을 로드하기 위해 환경은 다음과 같은 작업 순서를 수행합니다.

1. 환경은 .sln 파일의 전역 섹션을 읽고 로 `preSolution`표시된 모든 섹션을 처리합니다. 이 예제 파일에는 다음과 같은 문이 하나 있습니다.

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   환경에서 `GlobalSection('name')` 태그를 읽을 때 레지스트리를 사용하여 VSPackage에 이름을 매핑합니다. 키 이름은 [HKLM\\<응용 프로그램 ID 레지스트리 루트\>\SolutionPersistence\AggregateGUIDs]에서 레지스트리에 있어야 합니다. 키의 기본값은 항목을 작성한 VSPackage의 패키지 GUID(REG_SZ)입니다.

2. 환경은 VSPackage를 로드하고, `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> 인터페이스에 대한 VSPackage를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> 호출하고, VSPackage가 데이터를 저장할 수 있도록 섹션의 데이터와 함께 메서드를 호출합니다. 환경은 각 `preSolution` 섹션에 대해 이 프로세스를 반복합니다.

3. 환경은 프로젝트 지속성 블록을 통해 계속됩니다. 이 경우 하나의 프로젝트가 있습니다.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   이 명령문에는 고유한 프로젝트 GUID 및 프로젝트 유형 GUID가 포함되어 있습니다. 이 정보는 솔루션에 속한 프로젝트 파일 또는 파일과 각 프로젝트에 필요한 VSPackage를 찾는 데 환경에서 사용됩니다. 프로젝트 GUID는 프로젝트와 관련된 특정 VSPackage를 로드하기 위해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 전달된 다음 VSPackage에서 프로젝트를 로드합니다. 이 경우 이 프로젝트에 로드된 VS패키지는 시각적 기본입니다.

   각 프로젝트는 솔루션의 다른 프로젝트에서 필요에 따라 액세스할 수 있도록 고유한 프로젝트 인스턴스 ID를 유지합니다. 이상적으로 솔루션 및 프로젝트가 소스 코드 제어하에 있는 경우 프로젝트의 경로는 솔루션경로와 관련이 있어야 합니다. 솔루션이 처음 로드되면 프로젝트 파일이 사용자의 컴퓨터에 있을 수 없습니다. 프로젝트 파일을 솔루션 파일을 기준으로 서버에 저장하면 프로젝트 파일을 찾아 사용자의 컴퓨터에 복사하는 것이 비교적 간단합니다. 그런 다음 프로젝트에 필요한 나머지 파일을 복사하고 로드합니다.

4. .sln 파일의 프로젝트 섹션에 포함된 정보에 따라 환경은 각 프로젝트 파일을 로드합니다. 그런 다음 프로젝트 자체는 프로젝트 계층 구조를 채우고 중첩된 프로젝트를 로드합니다.

5. .sln 파일의 모든 섹션이 처리되면 솔루션 탐색기에 솔루션이 표시되고 사용자가 수정할 준비가 됩니다.

솔루션에서 프로젝트를 구현하는 VSPackage가 로드되지 않으면 메서드가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> 호출되고 솔루션의 다른 모든 프로젝트에로드 하는 동안 변경 한 내용을 무시할 수 있습니다. 구문 분석 오류가 발생하면 솔루션 파일과 함께 가능한 한 많은 정보가 보존되고 환경에는 솔루션이 손상되었다는 경고하는 대화 상자가 표시됩니다.

솔루션이 저장되거나 닫히면 메서드가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> 호출되어 계층 구조로 전달되어 .sln 파일에 입력해야 하는 솔루션이 변경되었는지 확인합니다. 에 전달되는 `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>null 값은 솔루션에 대한 정보가 유지되고 있음을 나타냅니다. 값이 null이 아닌 경우 지속성 정보는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 인터페이스에 대한 포인터에 의해 결정되는 특정 프로젝트에 대한 것입니다.

저장할 정보가 있으면 메서드에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 대한 포인터를 사용하여 인터페이스가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> 호출됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> 그런 다음 메서드를 호출하여 인터페이스에서 `IPropertyBag` 이름 값 쌍을 검색하고 .sln 파일에 정보를 씁니다.

`SaveSolutionProps`.sln 파일에 모든 변경 내용을 입력할 때까지 `WriteSolutionProps` `IPropertyBag` 인터페이스에서 저장할 정보를 검색하기 위해 환경에서 개체를 재귀적으로 호출합니다. 이러한 방식으로 정보가 솔루션과 함께 유지되고 다음에 솔루션을 열 때 사용할 수 있는지 확인할 수 있습니다.

로드된 모든 VSPackage는 .sln 파일에 저장할 것이 있는지 확인하기 위해 열거됩니다. 로드 시에만 레지스트리 키가 쿼리됩니다. 환경은 솔루션이 저장될 때 메모리에 있기 때문에 로드된 모든 패키지에 대해 알고 있습니다.

.sln 파일만 `preSolution` 및 `postSolution` 섹션의 항목을 포함합니다. 솔루션이 제대로 로드하려면 이 정보가 필요하므로 .suo 파일에는 유사한 섹션이 없습니다. .suo 파일에는 개인 메모와 같은 사용자 별 옵션이 포함되어 있으며, 이 옵션은 소스 코드 제어하에 공유되거나 배치되지 않았습니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [솔루션 사용자 옵션(.Suo) 파일](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [솔루션](../../extensibility/internals/solutions-overview.md)
