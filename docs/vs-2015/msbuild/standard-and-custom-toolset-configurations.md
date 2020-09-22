---
title: 표준 및 사용자 지정 도구 집합 구성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d08a7eb20c01568b3501f16348eb19afdcaefa2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841710"
---
# <a name="standard-and-custom-toolset-configurations"></a>표준 및 사용자 지정 도구 집합 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild 도구 집합은 애플리케이션 프로젝트를 빌드하는 데 사용할 수 있는 작업, 대상 및 도구에 대한 참조를 포함합니다. MSBuild는 표준 도구 집합을 포함하지만 사용자 지정 도구 집합을 만들 수도 있습니다. 도구 집합을 지정하는 방법에 대한 내용은 [도구 집합(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)을 참조하세요.  

## <a name="standard-toolset-configurations"></a>표준 도구 집합 구성  
 MSBuild 12.0은 다음 표준 도구 집합을 포함합니다.  

| ToolsVersion | 도구 집합 경로(MSBuildBinPath 또는 MSBuildToolsPath 빌드 속성에 지정된 대로) |
|--------------|--------------------------------------------------------------------------------------|
|     2.0      |           *Windows 설치 경로*\Microsoft.Net\Framework\v2.0.50727\            |
|     3.5      |              *Windows 설치 경로*\Microsoft.NET\Framework\v3.5\               |
|     4.0      |           *Windows 설치 경로*\Microsoft.NET\Framework\v4.0.30319\            |
|     12.0     |                          *%ProgramFiles%* \MSBuild\12.0\bin                           |

 `ToolsVersion` 값은 Visual Studio에서 생성하는 프로젝트에서 사용되는 도구 집합을 결정합니다. [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]에서 기본값은 "12.0"(프로젝트 파일에 지정된 버전과 관계 없이)이지만 명령 프롬프트에서 **/toolsversion** 스위치를 사용하여 해당 특성을 재정의할 수 있습니다. 이 특성과를 지정 하는 다른 방법에 대 한 자세한 내용은 `ToolsVersion` [ToolsVersion 설정 재정의](../msbuild/overriding-toolsversion-settings.md)를 참조 하세요.  

 `ToolsVersion`이 지정되지 않은 경우 레지스트리 키 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\\<Version Number\>\DefaultToolsVersion**은 `ToolsVersion`을 정의합니다. 이는 항상 2.0입니다.  

 다음 레지스트리 키는 MSBuild.exe의 설치 경로를 지정합니다.  

|레지스트리 키|키 이름|문자열 키 값|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0\|MSBuildToolsPath|.NET Framework 2.0 설치 경로|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\|MSBuildToolsPath|.NET Framework 3.5 설치 경로|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\|MSBuildToolsPath|.NET Framework 4 설치 경로|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\12.0\|MSBuildToolsPath|MSBuild 설치 경로|  

### <a name="sub-toolsets"></a>하위 도구 집합  
 이전 테이블의 레지스트리 키에 하위 키가 있는 경우 MSBuild는 이를 사용하여 하위 도구 집합의 경로가 부모 도구 집합의 경로를 재정의할 수 있는지를 결정합니다. 다음 하위 키는 예제입니다.  

 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  

 속성이 기본 도구 집합 및 선택한 하위 도구 집합에 모두 정의된 경우 하위 도구 집합의 속성 정의가 사용됩니다. 예를 들어 MSBuild 4.0 도구 집합은 7.0A SDK를 가리키도록 `SDK40ToolsPath`를 정의하지만 MSBuild 4.0\11.0 도구 집합은 8.0A SDK를 가리키도록 동일한 속성을 정의합니다. `VisualStudioVersion`이 설정되지 않은 경우 `SDK40ToolsPath`는 7.0A를 가리키지만 `VisualStudioVersion`이 11.0으로 설정된 경우 속성은 대신 8.0A를 가리킵니다.  

 `VisualStudioVersion` 빌드 속성은 하위 도구 집합의 활성화 여부를 나타냅니다. 예를 들어 "12.0"의 `VisualStudioVersion` 값은 MSBuild 12.0 하위 도구 집합을 지정합니다. 자세한 내용은의 [MSBuild 도구 집합(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)의 하위 도구 집합 섹션을 참조하세요.  

> [!NOTE]
> 이러한 설정을 변경하지 않는 것이 좋습니다. 그럼에도 불구하고 고유한 설정을 추가하고 다음 섹션에 설명된 대로 컴퓨터 수준의 사용자 지정 도구 집합 정의를 정의할 수 있습니다.  

## <a name="custom-toolset-definitions"></a>사용자 지정 도구 집합 정의  
 표준 도구 집합이 빌드 요구 사항을 충족하지 않는 경우 사용자 지정 도구 집합을 만들 수 있습니다. 예를 들어 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 프로젝트 빌드를 위해 별도 시스템이 있어야 하는 곳에 빌드 랩 시나리오를 가질 수 있습니다. 사용자 지정 도구 집합을 사용하여 프로젝트를 만들거나 MSBuild.exe를 실행할 때 `ToolsVersion` 특성에 사용자 지정 값을 할당할 수 있습니다. 이 작업을 수행하여 해당 도구 집합을 사용하는 모든 프로젝트에 사용할 수 있는 사용자 고유의 사용자 지정 도구 집합 속성을 정의할 뿐만 아니라 `$(MSBuildToolsPath)` 속성을 사용하여 해당 디렉터리에서 .targets 파일을 가져올 수도 있습니다.  

 MSBuild.exe(또는 사용 중인 MSBuild 엔진을 호스팅하는 사용자 지정 도구)에 대한 구성 파일에 사용자 지정 도구 집합을 지정합니다. 예를 들어 MSBuild.exe에 대한 구성 파일은 ToolsVersion 12.0의 기본 동작을 재정의하려는 경우 다음 도구 집합 정의를 포함할 수 있습니다.  

```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  

 `<msbuildToolsets>`는 또한 다음과 같이 구성 파일에서 정의되어야 합니다.  

```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  

> [!NOTE]
> 제대로 읽으려면 `<configSections>`는 `<configuration>` 섹션에서 첫 번째 하위 섹션이어야 합니다.  

 `ToolsetConfigurationSection`은 사용자 지정 구성에 대한 MSBuild 호스트에서 사용할 수 있는 사용자 지정 구성 섹션입니다. 사용자 지정 도구 집합을 사용하는 경우 호스트는 구성 파일 항목을 제공하기만 하면 빌드 엔진을 초기화하기 위해 아무 작업도 수행할 필요가 없습니다. 레지스트리에서 항목을 정의하여 MSBuild.exe, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 MSBuild의 모든 호스트에 적용되는 컴퓨터 수준 도구 집합을 지정할 수 있습니다.  

> [!NOTE]
> 구성 파일이 레지스트리에 이미 정의된 `ToolsVersion`에 대한 설정을 정의하는 경우 두 개의 정의가 병합되지 않습니다. 구성 파일의 정의가 우선 순위를 가지며 해당 `ToolsVersion`에 대한 레지스트리의 설정은 무시됩니다.  

 다음 속성은 프로젝트에 사용되는 `ToolsVersion`의 값에 관련됩니다.  

- **$(MSBuildBinPath)** 는 레지스트리 또는 `ToolsVersion`이 정의된 구성 파일에 지정된 `ToolsPath` 값으로 설정됩니다. 레지스트리 또는 구성 파일의 `$(MSBuildToolsPath)` 설정은 핵심 작업 및 대상의 위치를 지정합니다. 프로젝트 파일에서 $(MSBuildBinPath) 속성 및 $(MSBuildToolsPath) 속성에 매핑됩니다.  

- `$(MSBuildToolsPath)`는 구성 파일에 지정된 MSBuildToolsPath 속성에서 제공되는 예약된 속성입니다. (이 속성은 `$(MSBuildBinPath)`를 대체합니다. 그러나 `$(MSBuildBinPath)` 는 호환성을 위해 앞으로 전달 됩니다.) 사용자 지정 도구 집합은 모두 `$(MSBuildToolsPath)` `$(MSBuildBinPath)` 동일한 값을 갖지 않는 한 또는 중 하나만 정의 해야 합니다.  

  또한 MSBuildToolsPath 속성을 추가하는 데 사용하는 동일한 구문을 사용하여 구성 파일에 ToolsVersion 관련 사용자 지정 속성을 추가할 수도 있습니다. 이러한 사용자 지정 속성을 프로젝트 파일에 사용할 수 있도록 하려면 구성 파일에 지정된 값의 이름과 동일한 이름을 사용합니다. 구성 파일에서 하위 도구 집합이 아닌 도구 집합을 정의할 수 있습니다.  

## <a name="see-also"></a>참고 항목  
 [도구 집합(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
