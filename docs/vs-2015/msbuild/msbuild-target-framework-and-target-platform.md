---
title: MSBuild 대상 프레임워크 및 대상 플랫폼 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a550b4a6634604594da0893e3f420fd9c38ca3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181029"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild 대상 프레임워크 및 대상 플랫폼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트는 특정 버전의 .NET Framework인 *대상 프레임워크* 및 특정 소프트웨어 아키텍처인 *대상 플랫폼*에서 실행되도록 빌드할 수 있습니다.  예를 들어 802x86 프로세서 제품군("x86")과 호환되는 32비트 플랫폼의 .NET Framework 2.0에서 실행되도록 애플리케이션을 타기팅할 수 있습니다. 대상 프레임워크와 대상 플랫폼의 조합을 *대상 컨텍스트*라고 합니다.  
  
## <a name="target-framework-and-profile"></a>대상 프레임워크 및 프로필  
 대상 프레임워크는 빌드하는 프로젝트의 실행 기반인 특정 버전의 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]입니다. 대상 프레임워크의 사양은 해당 프레임워크 버전에만 해당되는 컴파일러 기능 및 어셈블리 참조를 사용할 수 있게 하므로 필수입니다.  
  
 현재 사용할 수 있는 .NET Framework 버전은 다음과 같습니다.  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0(Visual Studio 2005에 포함됨)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.0([!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)]에 포함됨)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.5([!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)]에 포함됨)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4(Visual Studio 2010에 포함됨)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5([!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에 포함됨)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.1([!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]에 포함됨)  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.2  
  
- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.6([!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]에 포함됨)  
  
  .NET Framework의 버전은 목록에서 참조 가능하도록 만드는 어셈블리에 따라 서로 다릅니다. 예를 들어 프로젝트가 .NET Framework 버전 3.0 이상을 대상으로 하지 않는 경우 WPF(Windows Presentation Foundation) 애플리케이션을 빌드할 수 없습니다.  
  
  대상 프레임워크는 프로젝트 파일의 `TargetFrameworkVersion` 속성에서 지정됩니다. Visual Studio IDE(통합 개발 환경)의 프로젝트 속성 페이지를 사용하여 프로젝트의 대상 프레임워크를 변경할 수 있습니다. 자세한 내용은 [방법: 한 버전의 .NET Framework을 대상으로 하는 방법](../ide/how-to-target-a-version-of-the-dotnet-framework.md)을 참조 하세요. `TargetFrameworkVersion`에 사용할 수 있는 값은 `v2.0`, `v3.0`, `v3.5`, `v4.0`, `v4.5`, `v4.5.1`, `v4.5.2` 및 `v4.6`입니다.  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 *대상 프로필*은 대상 프레임워크의 하위 집합입니다. 예를 들어 .NET Framework 4 Client Profile에는 MSBuild 어셈블리에 대한 참조가 포함되지 않습니다.  
  
 대상 프로필은 프로젝트 파일의 `TargetFrameworkProfile` 속성에서 지정됩니다. IDE에서 프로젝트 속성 페이지의 대상 프레임워크 컨트롤을 사용하여 대상 프로필을 변경할 수 있습니다. 자세한 내용은 [방법: 한 버전의 .NET Framework을 대상으로 하는 방법](../ide/how-to-target-a-version-of-the-dotnet-framework.md)을 참조 하세요.  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>대상 플랫폼  
 *플랫폼*은 하드웨어 및 특정 런타임 환경을 정의하는 소프트웨어의 조합입니다. 예를 들면 다음과 같습니다.  
  
- `x86`은 Intel 80x86 프로세서 또는 이와 동등한 프로세서에서 실행되는 32비트 Windows 운영 체제를 지정합니다.  
  
- `Xbox`는 Microsoft Xbox 360 플랫폼을 지정합니다.  
  
  *대상 플랫폼*은 빌드할 프로젝트의 실행 기반이 되는 특정 플랫폼입니다. 대상 플랫폼은 프로젝트 파일의 `Platform`빌드 속성에서 지정됩니다. IDE에서 프로젝트 속성 페이지 또는 **구성 관리자**를 사용하여 대상 플랫폼을 변경할 수 있습니다.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 *대상 구성*은 대상 플랫폼의 하위 집합입니다. 예를 들어 `x86``Debug` 구성에는 대부분의 코드 최적화가 포함되지 않습니다. 대상 구성은 프로젝트 파일의 `Configuration` 빌드 속성에서 지정됩니다. 프로젝트 속성 페이지 또는 **구성 관리자**를 사용하여 대상 구성을 변경할 수 있습니다.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>관련 항목  
 [멀티 타기팅](../msbuild/msbuild-multitargeting-overview.md)
