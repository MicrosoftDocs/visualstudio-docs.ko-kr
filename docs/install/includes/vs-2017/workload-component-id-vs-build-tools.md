---
title: Visual Studio Build Tools 2017 워크로드 및 구성 요소 ID
titleSuffix: ''
description: Visual Studio 작업 및 구성 요소 ID를 사용하여 기존 Windows 기반 애플리케이션을 빌드합니다.
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 2/12/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: 2f2092143a79dae17c5c0138e51c10fc5d164cbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "76159533"
---
## <a name="azure-development-build-tools"></a>Azure 개발 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.AzureBuildTools

**설명:** Azure 애플리케이션을 빌드하기 위한 MSBuild 작업 및 대상입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 개발 도구 | 15.8.27825.0 | 필수
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 작성 도구 | 15.9.28307.421 | 필수
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET용 Azure 라이브러리 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services 빌드 도구 | 15.7.27617.1 | 필수
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 컨테이너 개발 도구 - 빌드 도구 | 15.7.27617.1 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 15.9.28016.0 | 필수
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 필수
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | WCF 개발 빌드 도구 | 15.6.27309.0 | 필수
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | 웹 개발 빌드 도구 | 15.8.27729.1 | 필수
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 개발 도구 | 15.6.27406.0 | 권장
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 개발 도구 | 15.8.27924.0 | 권장
Microsoft.VisualStudio.Component.AspNet45 | 고급 ASP.NET 기능 | 15.7.27625.0 | 권장
Microsoft.VisualStudio.Component.WebDeploy | 웹 배포 | 15.8.27729.1 | 권장
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 개발 도구 | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | 옵션
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 타기팅 팩 | 15.8.27825.0 | 옵션
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 개발 도구 | 15.6.27406.0 | 옵션
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 개발 도구 | 15.6.27406.0 | 옵션
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | .NET Framework 4.7.2 개발 도구 | 15.8.27825.0 | 옵션
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 개발 도구 | 15.6.27406.0 | 옵션

## <a name="data-storage-and-processing-build-tools"></a>데이터 스토리지 및 처리 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.DataBuildTools

**설명:** SQL Server 데이터베이스 프로젝트 빌드

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 개발 도구 | 15.6.27406.0 | 권장
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 15.6.27309.0 | 권장
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 및 Visual Basic | 15.8.27729.1 | 권장
Microsoft.VisualStudio.Component.SQL.SSDTBuildSku | SQL Server Data Tools - 빌드 도구 | 15.8.27825.0 | 권장
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 정적 분석 도구 | 15.0.26208.0 | 권장

## <a name="net-desktop-build-tools"></a>.NET 데스크톱 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**설명:** C#, Visual Basic 및 F#을 사용하여 WPF, Windows Forms 및 콘솔 애플리케이션을 빌드하기 위한 도구입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 필수
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 15.9.28016.0 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 15.6.27309.0 | 필수
Microsoft.Component.ClickOnce.MSBuild | ClickOnce 빌드 도구 | 15.7.27617.1 | 권장
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 개발 도구 | 15.6.27406.0 | 권장
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 개발 도구 | 15.6.27406.0 | 권장
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 개발 도구 | 15.8.27924.0 | 권장
Microsoft.VisualStudio.Component.TestTools.BuildTools | 테스트 도구 핵심 기능 - 빌드 도구 | 15.7.27625.0 | 권장
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | WCF 개발 빌드 도구 | 15.6.27309.0 | 권장
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 개발 도구 | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | 옵션
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 타기팅 팩 | 15.8.27825.0 | 옵션
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 개발 도구 | 15.6.27406.0 | 옵션
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 개발 도구 | 15.6.27406.0 | 옵션
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | .NET Framework 4.7.2 개발 도구 | 15.8.27825.0 | 옵션
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 개발 도구 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 개발 도구 | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.FSharp.MSBuild | F# 컴파일러 | 15.8.27825.0 | 옵션

## <a name="msbuild-tools"></a>MSBuild 도구

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**설명:** MSBuild 기반 애플리케이션을 빌드하는 데 필요한 도구를 제공합니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 필수
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools 핵심 | 15.6.27309.0 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 15.6.27309.0 | 필수

## <a name="net-core-build-tools"></a>.NET Core 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**설명:** .NET Core, ASP.NET 코어, HTML/JavaScript 및 컨테이너를 사용하여 애플리케이션을 빌드하기 위한 도구입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 개발 도구 | 15.8.27924.0 | 필수
Microsoft.NetCore.BuildTools.ComponentGroup | .NET Core 빌드 도구 | 15.8.27906.1 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 15.9.28016.0 | 필수
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 개발 도구 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 개발 도구 | 15.6.27406.0 | Optional

## <a name="nodejs-build-tools"></a>Node.js 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.NodeBuildTools

**설명:** 비동기 이벤트 구동 JavaScript 런타임인 Node.js를 사용하여 확장성 있는 네트워크 애플리케이션을 빌드하기 위한 MSBuild 작업 및 대상입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Node.js MSBuild 지원 | 15.8.27825.0 | 필수
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 필수

## <a name="officesharepoint-build-tools"></a>Office/SharePoint 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.OfficeBuildTools

**설명:** Office 및 SharePoint 추가 기능, VSTO 추가 기능을 빌드합니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.ClickOnce.MSBuild | ClickOnce 빌드 도구 | 15.7.27617.1 | 필수
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 필수
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 개발 도구 | 15.8.27825.0 | 필수
Microsoft.VisualStudio.Component.NuGet | NuGet 패키지 관리자 | 15.9.28016.0 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 15.9.28016.0 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 15.6.27309.0 | 필수
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Office/SharePoint 개발 빌드 도구 | 15.8.27825.0 | 필수
Microsoft.VisualStudio.Component.Workflow.BuildTools | Windows Workflow Foundation 빌드 도구 | 15.8.27906.1 | 필수
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | WCF 개발 빌드 도구 | 15.6.27309.0 | 필수
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | 웹 개발 빌드 도구 | 15.8.27729.1 | 필수
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | VSTO(Visual Studio Tools for Office) 빌드 도구 | 15.7.27617.1 | 권장
Microsoft.VisualStudio.Component.WebDeploy | 웹 배포 | 15.8.27729.1 | 권장
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | 옵션
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 타기팅 팩 | 15.8.27825.0 | 옵션
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 개발 도구 | 15.6.27406.0 | 옵션
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 개발 도구 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | .NET Framework 4.7.2 개발 도구 | 15.8.27825.0 | 옵션
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 개발 도구 | 15.6.27406.0 | 옵션

## <a name="universal-windows-platform-build-tools"></a>유니버설 Windows 플랫폼 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.UniversalBuildTools

**설명:** 유니버설 Windows 플랫폼 애플리케이션을 빌드하는 데 필요한 도구를 제공합니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 필수
Microsoft.Component.NetFX.Native | .NET 네이티브 | 15.0.26208.0 | 필수
Microsoft.Component.VC.Runtime.OSSupport | UWP용 Visual C++ 런타임 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 15.9.28016.0 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 15.6.27309.0 | 필수
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 정적 분석 도구 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM용 Visual C++ 컴파일러 및 라이브러리 | 15.8.27825.0 | 필수
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 버전 15.9 v14.16 최신 v141 도구 | 15.9.28230.55 | 필수
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | 유니버설 Windows 플랫폼 빌드의 필수 구성 요소 | 15.8.27705.0 | 필수
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK(10.0.17763.0) | 15.9.28307.102 | 권장
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK(10.0.10240.0) | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK(10.0.10586.0) | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK(10.0.14393.0) | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | 데스크톱 C++용 [x86 및 x64] Windows 10 SDK(10.0.15063.0) | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | UWP용 Windows 10 SDK(10.0.15063.0): C#, VB, JS | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | UWP용 Windows 10 SDK(10.0.15063.0): C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | 데스크톱 C++용 [x86 및 x64] Windows 10 SDK(10.0.16299.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | 데스크톱 C++용 [ARM 및 ARM64] Windows 10 SDK(10.0.16299.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | UWP용 Windows 10 SDK(10.0.16299.0): C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | UWP용 Windows 10 SDK(10.0.16299.0): C++ | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK(10.0.17134.0) | 15.9.28307.102 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK(10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK(10.0.16299.0) | 15.8.27825.0 | Optional

## <a name="visual-c-build-tools"></a>Visual C++ 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.VCTools

**설명:** Microsoft C++ 도구 세트, ATL 또는 MFC를 사용하여 Windows 데스크톱 애플리케이션을 빌드합니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 정적 분석 도구 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Visual C++ Build Tools 핵심 기능 | 15.8.27729.1 | 필수
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Visual C++ 2017 재배포 가능 업데이트 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 버전 15.9 v14.16 최신 v141 도구 | 15.9.28230.55 | 필수
Microsoft.VisualStudio.Component.Windows10SDK | Windows 유니버설 C 런타임 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.TestTools.BuildTools | 테스트 도구 핵심 기능 - 빌드 도구 | 15.7.27625.0 | 권장
Microsoft.VisualStudio.Component.VC.CMake.Project | CMake용 Visual C++ 도구 | 15.9.28307.102 | 권장
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK(10.0.17763.0) | 15.9.28307.102 | 권장
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 유니버설 CRT SDK | 15.6.27309.0 | 옵션
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.VC.140 | 데스크톱용 VC++ 2015.3 v14.00(v140) 도구 집합 | 15.7.27617.1 | 옵션
Microsoft.VisualStudio.Component.VC.ATL | x86 및 x64용 Visual C++ ATL | 15.7.27625.0 | 옵션
Microsoft.VisualStudio.Component.VC.ATLMFC | x86 및 x64용 Visual C++ MFC | 15.7.27625.0 | 옵션
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI 지원 | 15.6.27309.0 | 옵션
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 표준 라이브러리용 모듈(실험적) | 15.6.27309.0 | 옵션
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM용 Visual C++ 컴파일러 및 라이브러리 | 15.8.27825.0 | 옵션
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | ARM64용 Visual C++ 컴파일러 및 라이브러리 | 15.9.28230.55 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK(10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK(10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK(10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | 데스크톱 C++용 [x86 및 x64] Windows 10 SDK(10.0.15063.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | UWP용 Windows 10 SDK(10.0.15063.0): C#, VB, JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | UWP용 Windows 10 SDK(10.0.15063.0): C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | 데스크톱 C++용 [x86 및 x64] Windows 10 SDK(10.0.16299.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | 데스크톱 C++용 [ARM 및 ARM64] Windows 10 SDK(10.0.16299.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | UWP용 Windows 10 SDK(10.0.16299.0): C#, VB, JS | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | UWP용 Windows 10 SDK(10.0.16299.0): C++ | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK(10.0.17134.0) | 15.9.28307.102 | 옵션
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | 옵션
Microsoft.VisualStudio.Component.WinXP | C++용 Windows XP 지원 | 15.8.27924.0 | 옵션
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK 및 UCRT SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | C++용 Windows XP 지원 | 15.8.27705.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.15063 | Windows 10 SDK(10.0.15063.0) | 15.8.27825.0 | Optional
Microsoft.VisualStudio.ComponentGroup.Windows10SDK.16299 | Windows 10 SDK(10.0.16299.0) | 15.8.27825.0 | 옵션

## <a name="visual-studio-extension-development"></a>Visual Studio 확장 개발

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtensionBuildTools

**설명:** Visual Studio용 추가 기능 및 확장(새 명령, 코드 분석기 및 도구 창 포함)을 빌드하기 위한 도구입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 필수
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 개발 도구 | 15.8.27825.0 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 15.9.28016.0 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 15.6.27309.0 | 필수
Microsoft.VisualStudio.Component.VSSDKBuildTools | Visual Studio SDK Build Tools Core | 15.8.27924.0 | 필수
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtensionBuildTools.Prerequisites | Visual Studio 확장 개발 필수 구성 요소 | 15.8.27729.1 | 필수
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | 옵션
Microsoft.Component.VC.Runtime.OSSupport | UWP용 Visual C++ 런타임 | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 정적 분석 도구 | 15.0.26208.0 | 옵션
Microsoft.VisualStudio.Component.VC.ATL | x86 및 x64용 Visual C++ ATL | 15.7.27625.0 | 옵션
Microsoft.VisualStudio.Component.VC.ATLMFC | x86 및 x64용 Visual C++ MFC | 15.7.27625.0 | 옵션
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 버전 15.9 v14.16 최신 v141 도구 | 15.9.28230.55 | 옵션

## <a name="web-development-build-tools"></a>웹 개발 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**설명:** 웹 애플리케이션을 빌드하기 위한 MSBuild 작업 및 대상입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 개발 도구 | 15.8.27825.0 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 15.9.28016.0 | 필수
Microsoft.VisualStudio.Component.TypeScript.3.1 | TypeScript 3.1 SDK | 15.0.28218.60 | 필수
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | 웹 개발 빌드 도구 | 15.8.27729.1 | 필수
Microsoft.Component.ClickOnce.MSBuild | ClickOnce 빌드 도구 | 15.7.27617.1 | 권장
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 15.6.27406.0 | 권장
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 개발 도구 | 15.6.27406.0 | 권장
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 개발 도구 | 15.8.27924.0 | 권장
Microsoft.VisualStudio.Component.AspNet45 | 고급 ASP.NET 기능 | 15.7.27625.0 | 권장
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 컨테이너 개발 도구 - 빌드 도구 | 15.7.27617.1 | 권장
Microsoft.VisualStudio.Component.TestTools.BuildTools | 테스트 도구 핵심 기능 - 빌드 도구 | 15.7.27625.0 | 권장
Microsoft.VisualStudio.Component.WebDeploy | 웹 배포 | 15.8.27729.1 | 권장
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | WCF 개발 빌드 도구 | 15.6.27309.0 | 권장
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 개발 도구 | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 타기팅 팩 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 타기팅 팩 | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 15.8.27825.0 | 옵션
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 타기팅 팩 | 15.8.27825.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | 옵션
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 타기팅 팩 | 15.6.27406.0 | 옵션
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 개발 도구 | 15.6.27406.0 | 옵션
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 개발 도구 | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.2.DeveloperTools | .NET Framework 4.7.2 개발 도구 | 15.8.27825.0 | 옵션
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 개발 도구 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 개발 도구 | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 개발 도구 | 15.6.27406.0 | 옵션

## <a name="mobile-development-with-net"></a>.NET을 사용한 모바일 개발

**ID:** Microsoft.VisualStudio.Workload.XamarinBuildTools

**설명:** C# 및 F#을 사용하여 iOS, Android 및 Windows용 플랫폼 간 애플리케이션을 빌드하기 위한 도구입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 필수
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 15.9.28016.0 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 15.6.27309.0 | 필수
Component.Android.SDK25 | Android SDK 설치(API 레벨 25) | 15.9.28107.0 | 옵션
Component.OpenJDK | Microsoft 배포 OpenJDK | 15.9.28125.51 | 옵션

## <a name="unaffiliated-components"></a>독립적 구성 요소

이러한 구성 요소는 작업에 포함되지 않지만 개별 구성 요소로 선택할 수 있습니다.

구성 요소 ID | Name | 버전
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.8.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript 2.6 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.7 | TypeScript 2.7 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27729.1
Microsoft.VisualStudio.Component.TypeScript.2.9 | TypeScript 2.9 SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.TypeScript.3.0 | TypeScript 3.0 SDK | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | ARM용 Visual C++ ATL | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Spectre Mitigations 포함 ARM용 Visual C++ ATL | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | ARM64용 Visual C++ ATL | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Spectre Mitigations 포함 ARM64용 Visual C++ ATL | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Spectre Mitigations 포함 Visual C++ ATL(x86/x64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Spectre Mitigations 포함 x86/x64용 Visual C++ MFC | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2(실험적) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | ARM용 Visual C++ MFC | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Spectre Mitigations 포함 ARM용 Visual C++ MFC | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | ARM64용 Visual C++ MFC | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Spectre Mitigations 포함 ARM64용 Visual C++ MFC 지원 | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | Spectre용 VC++ 2017 버전 15.9 v14.16 라이브러리(ARM) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | Spectre용 VC++ 2017 버전 15.9 v14.16 라이브러리(ARM64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | Spectre용 VC++ 2017 버전 15.9 v14.16 라이브러리(x86 및 x64) | 15.9.28230.55
Microsoft.VisualStudio.Component.VC.Tools.14.11 | VC++ 2017 버전 15.4 v14.11 도구 집합 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | VC++ 2017 버전 15.5 v14.12 도구 집합 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | VC++ 2017 버전 15.6 v14.13 도구 집합 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.14 | VC++ 2017 버전 15.7 v14.14 도구 집합 | 15.0.27924.0
Microsoft.VisualStudio.Component.VC.Tools.14.15 | VC++ 2017 버전 15.8 v14.15 도구 집합 | 15.0.28230.55
