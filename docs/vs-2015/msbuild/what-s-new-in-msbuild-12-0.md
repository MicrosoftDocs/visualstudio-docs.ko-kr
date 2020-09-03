---
title: MSBuild 12.0의 새로운 기능 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976a6ad-c052-4017-b848-35b5ae4a2f66
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba733b7ef20c9a03ad19d9847a4046e4d72ebdef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844462"
---
# <a name="what39s-new-in-msbuild-120"></a>MSBuild 12.0의 새로운 기능
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild는 이제 .NET Framework의 일부가 아니라 Visual Studio의 일부로 설치되었습니다. 현재 MSBuild 버전 번호는 12.0입니다. MSBuild를 개별적으로 설치하려면 [MSBuild 다운로드](https://www.microsoft.com/download/details.aspx?id=40760)에서 설치 패키지를 다운로드하세요.  
  
## <a name="changed-path"></a>변경된 경로  
 이제 MSBuild는 *%ProgramFiles%* 아래(예: C:\Program Files\MSBuild\\)에 직접 설치됩니다.  
  
## <a name="changed-properties"></a>변경된 속성  
 다음 MSBuild 속성은 새 버전 번호의 결과로 변경됩니다.  
  
- 이 도구 버전의 `MSBuildToolsVersion`은 12.0입니다.  
  
- `MSBuildToolsPath`는 이제 32비트 운영 체제에서 %ProgramFiles%\MSBuild\12.0\bin 또는 64비트 운영 체제에서 %ProgramFiles%\MSBuild\12.0\bin\amd64입니다.  
  
- `ToolsVersion` 값은 32비트 운영 체제에서는 HKLM\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0에서 찾을 수 있고 64비트 운영 체제에서는 HKLM\SOFTWARE\Wow6432Node\Microsoft\MSBuild\ToolsVersions\12.0에서 찾을 수 있습니다.  
  
- `SDK35ToolsPath` 및 `SDK40ToolsPath` 속성은 이 버전의 Visual Studio(예: 4.X 도구의 8.1A)를 사용하여 패키지된 .NET Framework SDK를 가리킵니다.  
  
## <a name="new-properties"></a>새 속성  
  
- `MSBuildFrameworkToolsPath`는 32비트 운영 체제에서 %windir%\Microsoft.NET\Framework\v4.0.30319의 값을 갖거나 64비트 운영 체제에서 %windir%\Microsoft.NET\Framework64\v4.0.30319의 값을 갖는 새 속성입니다. 이것은 .NET Framework 도구 및 유틸리티를 가리키는 데 사용할 수 있는 `MSBuildToolsPath`의 대체물입니다.  
  
- `MSBuildToolsPath` 및 `MSBuildFrameworkToolsPath`는 32비트에 해당하는 `MSBuildToolsPath32` 및 `MSBuildFrameworkToolsPath32`를 갖고 있으며, 이는 32비트나 64비트 MSBuild가 사용되는 여부와 상관없이 항상 32비트 위치를 가리킵니다.

## <a name="see-also"></a>관련 항목
[MSBuild](msbuild.md)
