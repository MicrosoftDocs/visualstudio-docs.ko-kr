---
title: ToolsVersion 설정 재정의 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding ToolsVersion setting
- MSBuild, building solutions with
ms.assetid: ccd42c07-0fb6-4e8b-9ebb-a6a6db18aa2e
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 468561a627a3ad7eb477328b5afef794c7acf2c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199940"
---
# <a name="overriding-toolsversion-settings"></a>ToolsVersion 설정 재정의
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 세 가지 방법 중 하나로 프로젝트 및 솔루션에 대한 도구 집합을 변경할 수 있습니다.  
  
1. 명령줄에서 프로젝트 또는 솔루션을 빌드할 때 `/ToolsVersion` 스위치(또는 짧게 `/tv`) 사용  
  
2. MSBuild 작업에서 `ToolsVersion` 매개 변수 설정  
  
3. 솔루션 내의 프로젝트에서 `$(ProjectToolsVersion)` 속성 설정. 이 방법에서는 다른 프로젝트와는 다른 도구 집합 버전을 사용하여 솔루션에서 프로젝트를 빌드할 수 있습니다.  
  
## <a name="override-the-toolsversion-settings-of-projects-and-solutions-on-command-line-builds"></a>명령줄 빌드에서 프로젝트 및 솔루션의 ToolsVersion 설정 재정의  
 일반적으로 Visual Studio 프로젝트는 프로젝트 파일에 지정된 ToolsVersion을 사용하여 빌드되지만 명령줄에서 `/ToolsVersion`(또는 `/tv`) 스위치를 사용하여 해당 값을 재정의하고 다른 도구 집합을 사용하여 모든 프로젝트 및 프로젝트 간 종속성을 빌드할 수 있습니다. 다음은 그 예입니다.  
  
```  
msbuild.exe someproj.proj /tv:12.0 /p:Configuration=Debug  
```  
  
 이 예제에서 모든 프로젝트는 ToolsVersion 12.0을 사용하여 빌드됩니다. 그러나 이 항목의 뒷부분에서 “우선 순위”를 참조하세요.  
  
 명령줄에서 `/tv` 스위치를 사용하면 개별 프로젝트에서 선택적으로 `$(ProjectToolsVersion)` 속성을 사용하여 솔루션의 다른 프로젝트와 다른 ToolsVersion 값으로 프로젝트를 빌드할 수 있습니다.  
  
## <a name="override-the-toolsversion-settings-using-the-toolsversion-parameter-of-the-msbuild-task"></a>MSBuild 작업의 ToolsVersion 매개 변수를 사용하여 ToolsVersion 설정 재정의  
 MSBuild 작업은 한 프로젝트로 다른 프로젝트를 빌드할 수 있는 기본 수단입니다. MSBuild 작업이 프로젝트에 지정된 것과 다른 ToolsVersion으로 프로젝트를 빌드할 수 있도록 `ToolsVersion`이라는 선택적 작업 매개 변수를 제공합니다. 다음 예제에서는 이 매개 변수를 사용하는 방법을 보여 줍니다.  
  
1. 다음 코드가 포함된 `projectA.proj`라는 파일을 만듭니다.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go" >   
            <Message Text="projectA.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
  
            <MSBuild Projects="projectB.proj"  
                ToolsVersion="2.0"  
                Targets="go" />  
        </Target>  
    </Project>  
    ```  
  
2. 다음 코드가 포함된 `projectB.proj`라는 또 다른 파일을 만듭니다.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
    ToolsVersion="12.0">  
  
        <Target Name="go">  
            <Message Text="projectB.proj" />  
            <Message Text="MSBuildToolsVersion: $(MSBuildToolsVersion)" />  
            <Message Text="MSBuildToolsPath:    $(MSBuildToolsPath)" />  
        </Target>  
    </Project>  
    ```  
  
3. 명령 프롬프트에 다음 명령을 입력합니다.  
  
    ```  
    msbuild projectA.proj /t:go /toolsversion:3.5  
    ```  
  
4. 다음 출력이 표시됩니다. `projectA`의 경우 명령줄의 `/toolsversion:3.5` 설정이 `Project` 태그의 `ToolsVersion=12.0` 설정을 재정의합니다.  
  
     `ProjectB`는 `projectA`의 작업에 의해 호출됩니다. 해당 작업에는 `projectB`에 대한 다른 `ToolsVersion` 설정을 재정의하는 `ToolsVersion=2.0`이 있습니다.  
  
    ```  
    Output:  
      projectA.proj  
      MSBuildToolsVersion: 3.5  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v3.5  
  
      projectB.proj  
      MSBuildToolsVersion: 2.0  
      MSBuildToolsPath:    C:\Windows\Microsoft.NET\Framework\v2.0.50727  
    ```  
  
## <a name="order-of-precedence"></a>우선 순위  
 `ToolsVersion`을 결정하는 데 사용되는 최고부터 최하까지 우선 순위는 다음과 같습니다.  
  
1. 프로젝트(있는 경우)를 빌드하는 데 사용되는 MSBuild 작업의 `ToolsVersion` 특성.  
  
2. msbuild.exe 명령(있는 경우)에 사용되는 `/toolsversion`(또는 `/tv`) 스위치.  
  
3. 환경 변수 `MSBUILDTREATALLTOOLSVERSIONSASCURRENT`가 설정된 경우 현재 `ToolsVersion`을 사용합니다.  
  
4. 환경 변수 `MSBUILDTREATHIGHERTOOLSVERSIONASCURRENT`가 설정되고 프로젝트 파일에 정의된 `ToolsVersion`이 현재 `ToolsVersion`보다 큰 경우 현재 `ToolsVersion`을 사용합니다.  
  
5. 환경 변수 `MSBUILDLEGACYDEFAULTTOOLSVERSION`이 설정되거나 `ToolsVersion`이 설정되지 않은 경우에는 다음 단계가 사용됩니다.  
  
    1. 프로젝트 파일의 [Project](../msbuild/project-element-msbuild.md) 요소에 대한 `ToolsVersion` 특성. 이 특성이 없으면 현재 버전으로 간주됩니다.  
  
    2. MSBuild.exe.config 파일의 기본 도구 버전.  
  
    3. 레지스트리의 기본 도구 버전. 자세한 내용은 [표준 및 사용자 지정 도구 집합 구성](../msbuild/standard-and-custom-toolset-configurations.md)을 참조하세요.  
  
6. 환경 변수 `MSBUILDLEGACYDEFAULTTOOLSVERSION`이 설정된 경우에는 다음 단계가 사용됩니다.  
  
    1. 환경 변수 `MSBUILDDEFAULTTOOLSVERSION`가 `ToolsVersion`으로 설정된 경우 이 값을 사용합니다.  
  
    2. MSBuild.exe.config에서 `DefaultOverrideToolsVersion`이 사용되는 경우 이 값을 사용합니다.  
  
    3. 레지스트리에서 `DefaultOverrideToolsVersion`이 설정된 경우 이 값을 사용합니다.  
  
    4. 이외에는 현재 `ToolsVersion`을 사용합니다.  
  
## <a name="see-also"></a>관련 항목  
 [다중](../msbuild/msbuild-multitargeting-overview.md)   
 [MSBuild 개념](../msbuild/msbuild-concepts.md)   
 [도구 집합 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)   
 [표준 및 사용자 지정 도구 집합 구성](../msbuild/standard-and-custom-toolset-configurations.md)
