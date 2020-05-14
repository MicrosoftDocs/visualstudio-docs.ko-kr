---
title: '방법: 빌드 시 환경 변수 사용 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afc679f9b782b8bc9ed3e04a2b8fb684cdbc1a20
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633787"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>방법: 빌드 시 환경 변수 사용

프로젝트를 빌드할 때 프로젝트 파일이나 프로젝트를 구성하는 파일에 없는 정보를 사용하여 빌드 옵션을 설치해야 하는 경우가 많습니다. 이 정보는 대개 환경 변수에 저장되어 있습니다.

## <a name="reference-environment-variables"></a>환경 변수 참조

 모든 환경 변수를 Microsoft Build Engine(MSBuild) 프로젝트 파일에 속성으로 사용할 수 있습니다.

> [!NOTE]
> 프로젝트 파일에 환경 변수와 이름이 같은 명시적 속성 정의가 포함되어 있으면 프로젝트 파일의 속성이 환경 변수의 값을 재정의합니다.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>MSBuild 프로젝트에서 환경 변수를 사용하려면

- 프로젝트 파일에서 선언된 변수를 참조하는 것과 같은 방식으로 환경 변수를 참조합니다. 예를 들어 다음 코드는 BIN_PATH 환경 변수를 참조합니다.

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  환경 변수가 설정되지 않은 경우 `Condition` 특성을 사용하여 속성의 기본값을 제공할 수 있습니다.

#### <a name="to-provide-a-default-value-for-a-property"></a>속성의 기본값을 제공하려면

- 속성에 값이 없는 경우에만 속성에서 `Condition` 특성을 사용하여 값을 설정합니다. 예를 들어 다음 코드는 `ToolsPath` 환경 변수가 설정되지 않은 경우에만 `ToolsPath` 속성을 *c:\tools*로 설정합니다.

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > 속성 이름은 대/소문자를 구분하지 않으므로 `$(ToolsPath)` 및 `$(TOOLSPATH)`는 둘 다 같은 속성 또는 환경 변수를 참조합니다.

## <a name="example"></a>예제

 다음 프로젝트 파일에서는 환경 변수를 사용하여 디렉터리의 위치를 지정합니다.

```xml
<Project DefaultTargets="FakeBuild">
    <PropertyGroup>
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">
            C:\Tools
        </ToolsPath>
    </PropertyGroup>
    <Target Name="FakeBuild">
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>참조

- [MSBuild](../msbuild/msbuild.md)
- [MSBuild 속성](../msbuild/msbuild-properties.md)
- [방법: 다른 옵션을 사용하여 동일한 원본 파일 빌드](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
