---
title: Visual Studio Build Tools 2019 워크로드 및 구성 요소 ID
titleSuffix: ''
description: Visual Studio 작업 및 구성 요소 ID를 사용하여 기존 Windows 기반 애플리케이션을 빌드합니다.
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 08/05/2020
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: include
ms.openlocfilehash: abcffcfe6a7a22b2001ff38852d9bef916d2d119
ms.sourcegitcommit: 78face15e71c305a2146358df51f8f1fefe3388f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87805850"
---
## <a name="azure-development-build-tools"></a>Azure 개발 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.AzureBuildTools

**설명:** Azure 애플리케이션을 빌드하기 위한 MSBuild 작업 및 대상입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 타기팅 팩 | 16.7.30310.162 | 필수
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | 필수
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 개발 도구 | 16.3.29207.166 | 필수
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure 작성 도구 | 16.0.28625.61 | 필수
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET용 Azure 라이브러리 | 16.0.28315.86 | 필수
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services 빌드 도구 | 16.3.29207.166 | 필수
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 컨테이너 개발 도구 - 빌드 도구 | 16.0.28625.61 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 16.1.28829.92 | 필수
Microsoft.VisualStudio.Component.TypeScript.3.9 | TypeScript 3.9 SDK | 16.0.30310.162 | 필수
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Windows Communication Foundation 빌드 도구 | 16.0.28516.191 | 필수
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | 웹 개발 빌드 도구 | 16.0.28516.191 | 필수
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 개발 도구 | 16.0.28516.191 | 권장
Microsoft.VisualStudio.Component.AspNet45 | 고급 ASP.NET 기능 | 16.0.28315.86 | 권장
Microsoft.VisualStudio.Component.WebDeploy | 웹 배포 | 16.0.28517.75 | 권장
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 개발 도구 | 16.0.28517.75 | 옵션
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 16.0.28517.75 | 옵션
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 타기팅 팩 | 16.0.28517.75 | 옵션
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 타기팅 팩 | 16.7.30310.162 | 옵션
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 타기팅 팩 | 16.7.30310.162 | 옵션
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 타기팅 팩 | 16.4.29313.120 | 옵션
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 개발 도구 | 16.4.29318.151 | 옵션
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 런타임(LTS) | 16.7.30310.162 | 옵션
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS 런타임 | 16.7.30310.162 | 옵션
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.7.30310.162 | 옵션

## <a name="data-storage-and-processing-build-tools"></a>데이터 스토리지 및 처리 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.DataBuildTools

**설명:** SQL Server 데이터베이스 프로젝트 빌드

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 개발 도구 | 16.0.28516.191 | 권장
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 16.0.28714.129 | 권장
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 및 Visual Basic | 16.7.30310.162 | 권장
Microsoft.VisualStudio.Component.SQL.SSDTBuildSku | SQL Server Data Tools - 빌드 도구 | 16.0.28315.86 | 권장

## <a name="net-desktop-build-tools"></a>.NET 데스크톱 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**설명:** C#, Visual Basic 및 F#을 사용하여 WPF, Windows Forms 및 콘솔 애플리케이션을 빌드하기 위한 도구입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 16.0.28517.75 | 필수
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 16.1.28829.92 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 16.0.28714.129 | 필수
Microsoft.Component.ClickOnce.MSBuild | ClickOnce 빌드 도구 | 16.0.28625.61 | 권장
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 개발 도구 | 16.0.28516.191 | 권장
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 런타임(LTS) | 16.7.30310.162 | 권장
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS 런타임 | 16.7.30310.162 | 권장
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.7.30310.162 | 권장
Microsoft.VisualStudio.Component.TestTools.BuildTools | 테스트 도구 핵심 기능 - 빌드 도구 | 16.4.29409.204 | 권장
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Windows Communication Foundation 빌드 도구 | 16.0.28516.191 | 권장
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 개발 도구 | 16.0.28517.75 | 옵션
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 타기팅 팩 | 16.0.28517.75 | 옵션
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 타기팅 팩 | 16.7.30310.162 | 옵션
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 타기팅 팩 | 16.7.30310.162 | 옵션
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 타기팅 팩 | 16.4.29313.120 | 옵션
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 개발 도구 | 16.4.29318.151 | 옵션
Microsoft.VisualStudio.Component.FSharp.MSBuild | F# 컴파일러 | 16.0.28528.71 | 옵션

## <a name="msbuild-tools"></a>MSBuild 도구

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**설명:** MSBuild 기반 애플리케이션을 빌드하는 데 필요한 도구를 제공합니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 필수
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools 핵심 | 16.7.30310.162 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 16.0.28714.129 | 필수

## <a name="net-core-build-tools"></a>.NET Core 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**설명:** .NET Core, ASP.NET 코어, HTML/JavaScript 및 컨테이너를 사용하여 애플리케이션을 빌드하기 위한 도구입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.NetCore.BuildTools.ComponentGroup | .NET Core 빌드 도구 | 16.3.29102.218 | 필수
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS 런타임 | 16.7.30310.162 | 필수
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.7.30310.162 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 16.1.28829.92 | 필수
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 런타임(LTS) | 16.7.30310.162 | 권장

## <a name="nodejs-build-tools"></a>Node.js 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.NodeBuildTools

**설명:** 비동기 이벤트 구동 JavaScript 런타임인 Node.js를 사용하여 확장성 있는 네트워크 애플리케이션을 빌드하기 위한 MSBuild 작업 및 대상입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Node.js MSBuild 지원 | 16.0.28517.75 | 필수
Microsoft.VisualStudio.Component.TypeScript.3.9 | TypeScript 3.9 SDK | 16.0.30310.162 | 필수

## <a name="officesharepoint-build-tools"></a>Office/SharePoint 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.OfficeBuildTools

**설명:** Office 및 SharePoint 추가 기능, VSTO 추가 기능을 빌드합니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.ClickOnce.MSBuild | ClickOnce 빌드 도구 | 16.0.28625.61 | 필수
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 필수
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 16.0.28517.75 | 필수
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 16.0.28517.75 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 16.0.28517.75 | 필수
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 타기팅 팩 | 16.7.30310.162 | 필수
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | 필수
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 16.0.28517.75 | 필수
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 개발 도구 | 16.3.29207.166 | 필수
Microsoft.VisualStudio.Component.NuGet | NuGet 패키지 관리자 | 16.1.28829.92 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 16.1.28829.92 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 16.0.28714.129 | 필수
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Office/SharePoint 개발 빌드 도구 | 16.0.28625.61 | 필수
Microsoft.VisualStudio.Component.Workflow.BuildTools | Windows Workflow Foundation 빌드 도구 | 16.0.28315.86 | 필수
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Windows Communication Foundation 빌드 도구 | 16.0.28516.191 | 필수
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | 웹 개발 빌드 도구 | 16.0.28516.191 | 필수
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | VSTO(Visual Studio Tools for Office) 빌드 도구 | 16.0.28625.61 | 권장
Microsoft.VisualStudio.Component.WebDeploy | 웹 배포 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 타기팅 팩 | 16.0.28517.75 | 옵션
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 타기팅 팩 | 16.7.30310.162 | 옵션
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 타기팅 팩 | 16.7.30310.162 | 옵션
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 타기팅 팩 | 16.4.29313.120 | 옵션
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 개발 도구 | 16.4.29318.151 | 옵션

## <a name="universal-windows-platform-build-tools"></a>유니버설 Windows 플랫폼 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.UniversalBuildTools

**설명:** 유니버설 Windows 플랫폼 애플리케이션을 빌드하는 데 필요한 도구를 제공합니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 필수
Microsoft.Component.NetFX.Native | .NET 네이티브 | 16.5.29515.121 | 필수
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | 필수
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS 런타임 | 16.7.30310.162 | 필수
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.7.30310.162 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 16.1.28829.92 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 16.0.28714.129 | 필수
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | 유니버설 Windows 플랫폼 빌드의 필수 구성 요소 | 16.3.29207.166 | 필수
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK(10.0.18362.0) | 16.1.28829.92 | 권장
Microsoft.Net.Component.4.7.2.SDK | .NET Framework 4.7.2 SDK | 16.4.29409.204 | 옵션
Microsoft.VisualStudio.Component.UWP.VC.ARM64 | v142 빌드 도구용 C++ 유니버설 Windows 플랫폼 지원(ARM64) | 16.3.29207.166 | 옵션
Microsoft.VisualStudio.Component.VC.Tools.ARM | MSVC v142 - VS 2019 C++ ARM 빌드 도구(v14.27) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | MSVC v142 - VS 2019 C++ ARM64 빌드 도구(v14.27) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.27) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.VC.v141.ARM | MSVC v141 – VS 2017 C++ ARM 빌드 도구(v14.16) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.VC.v141.ARM64 | MSVC v141 – VS 2017 C++ ARM64 빌드 도구(v14.16) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 – VS 2017 C++ x64/x86 빌드 도구(v14.16) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK(10.0.16299.0) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK(10.0.17134.0) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK(10.0.17763.0) | 16.0.28517.75 | 옵션
Microsoft.VisualStudio.ComponentGroup.UWP.VC.BuildTools | C++(v142) 유니버설 Windows 플랫폼 도구 | 16.3.29207.166 | 옵션
Microsoft.VisualStudio.ComponentGroup.UWP.VC.v141.BuildTools | C++(v141) 유니버설 Windows 플랫폼 도구 | 16.3.29207.166 | 옵션

## <a name="c-build-tools"></a>C++ 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.VCTools

**설명:** Microsoft C++ 도구 세트, ATL 또는 MFC를 사용하여 Windows 데스크톱 애플리케이션을 빌드합니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | C++ 빌드 도구 핵심 기능 | 16.0.28625.61 | 필수
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | C++ 2019 재배포 가능 업데이트 | 16.5.29515.121 | 필수
Microsoft.VisualStudio.Component.Windows10SDK | Windows 유니버설 C 런타임 | 16.4.29409.204 | 필수
Microsoft.VisualStudio.Component.TestTools.BuildTools | 테스트 도구 핵심 기능 - 빌드 도구 | 16.4.29409.204 | 권장
Microsoft.VisualStudio.Component.VC.ASAN | C++ AddressSanitizer(실험) | 16.5.29515.121 | 권장
Microsoft.VisualStudio.Component.VC.CMake.Project | Windows용 C++ CMake 도구 | 16.3.29103.31 | 권장
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.27) | 16.7.30310.162 | 권장
Microsoft.VisualStudio.Component.Windows10SDK.18362 | Windows 10 SDK(10.0.18362.0) | 16.1.28829.92 | 권장
Microsoft.Component.VC.Runtime.UCRTSDK | Windows 유니버설 CRT SDK | 16.0.28625.61 | 옵션
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 16.0.28517.75 | 옵션
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | 옵션
Microsoft.VisualStudio.Component.VC.140 | MSVC v140 - VS 2015 C++ 빌드 도구(v14.00) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.VC.ATL | 최신 v142 빌드 도구용 C++ ATL(x86 및 x64) | 16.4.29313.120 | 옵션
Microsoft.VisualStudio.Component.VC.ATLMFC | 최신 v142 빌드 도구용 C++ MFC(x86 및 x64) | 16.4.29313.120 | 옵션
Microsoft.VisualStudio.Component.VC.CLI.Support | v142 빌드 도구용 C++/CLI 지원(14.27) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.VC.Llvm.Clang | Windows용 C++ Clang 컴파일러(10.0.0) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset | v142 빌드 도구용 C++ Clang-cl(x64/x86) | 16.3.29207.166 | 옵션
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | v142 빌드 도구용 C++ 모듈(x64/x86 – 실험적) | 16.0.28625.61 | 옵션
Microsoft.VisualStudio.Component.VC.v141.x86.x64 | MSVC v141 – VS 2017 C++ x64/x86 빌드 도구(v14.16) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.16299 | Windows 10 SDK(10.0.16299.0) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK(10.0.17134.0) | 16.7.30310.162 | 옵션
Microsoft.VisualStudio.Component.Windows10SDK.17763 | Windows 10 SDK(10.0.17763.0) | 16.0.28517.75 | 옵션
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Llvm.Clang | Windows용 C++ Clang 도구(10.0.0 - x64/x86) | 16.7.30310.162 | 옵션

## <a name="visual-studio-extension-development"></a>Visual Studio 확장 개발

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtensionBuildTools

**설명:** Visual Studio용 추가 기능 및 확장(새 명령, 코드 분석기 및 도구 창 포함)을 빌드하기 위한 도구입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 필수
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 16.0.28517.75 | 필수
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 타기팅 팩 | 16.7.30310.162 | 필수
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | 필수
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 개발 도구 | 16.3.29207.166 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 16.1.28829.92 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 16.0.28714.129 | 필수
Microsoft.VisualStudio.Component.VSSDKBuildTools | Visual Studio SDK Build Tools Core | 16.0.28315.86 | 필수
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtensionBuildTools.Prerequisites | Visual Studio 확장 개발 필수 구성 요소 | 16.4.29318.151 | 필수
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 16.0.28528.71 | 옵션
Microsoft.Component.VC.Runtime.OSSupport | v142 빌드 도구용 C++ 유니버설 Windows 플랫폼 런타임 | 16.4.29409.204 | 옵션
Microsoft.VisualStudio.Component.VC.ATL | 최신 v142 빌드 도구용 C++ ATL(x86 및 x64) | 16.4.29313.120 | 옵션
Microsoft.VisualStudio.Component.VC.ATLMFC | 최신 v142 빌드 도구용 C++ MFC(x86 및 x64) | 16.4.29313.120 | 옵션
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.27) | 16.7.30310.162 | 옵션

## <a name="web-development-build-tools"></a>웹 개발 빌드 도구

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**설명:** 웹 애플리케이션을 빌드하기 위한 MSBuild 작업 및 대상입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Net.Component.4.7.2.TargetingPack | .NET Framework 4.7.2 타기팅 팩 | 16.7.30310.162 | 필수
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | 필수
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.7.2 개발 도구 | 16.3.29207.166 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 16.1.28829.92 | 필수
Microsoft.VisualStudio.Component.TypeScript.3.9 | TypeScript 3.9 SDK | 16.0.30310.162 | 필수
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | 웹 개발 빌드 도구 | 16.0.28516.191 | 필수
Microsoft.Component.ClickOnce.MSBuild | ClickOnce 빌드 도구 | 16.0.28625.61 | 권장
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 16.0.28517.75 | 권장
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 개발 도구 | 16.0.28516.191 | 권장
Microsoft.Net.Core.Component.SDK.2.1 | .NET Core 2.1 런타임(LTS) | 16.7.30310.162 | 권장
Microsoft.NetCore.Component.Runtime.3.1 | .NET Core 3.1 LTS 런타임 | 16.7.30310.162 | 권장
Microsoft.NetCore.Component.SDK | .NET Core SDK | 16.7.30310.162 | 권장
Microsoft.VisualStudio.Component.AspNet45 | 고급 ASP.NET 기능 | 16.0.28315.86 | 권장
Microsoft.VisualStudio.Component.DockerTools.BuildTools | 컨테이너 개발 도구 - 빌드 도구 | 16.0.28625.61 | 권장
Microsoft.VisualStudio.Component.TestTools.BuildTools | 테스트 도구 핵심 기능 - 빌드 도구 | 16.4.29409.204 | 권장
Microsoft.VisualStudio.Component.WebDeploy | 웹 배포 | 16.0.28517.75 | 권장
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Windows Communication Foundation 빌드 도구 | 16.0.28516.191 | 권장
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 개발 도구 | 16.0.28517.75 | 옵션
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 16.0.28517.75 | 옵션
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 타기팅 팩 | 16.0.28517.75 | 옵션
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 타기팅 팩 | 16.7.30310.162 | 옵션
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 타기팅 팩 | 16.7.30310.162 | 옵션
Microsoft.Net.Component.4.8.TargetingPack | .NET Framework 4.8 타기팅 팩 | 16.4.29313.120 | 옵션
Microsoft.Net.ComponentGroup.4.6.1.DeveloperTools | .NET Framework 4.6.1 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 개발 도구 | 16.3.29207.166 | 옵션
Microsoft.Net.ComponentGroup.4.8.DeveloperTools | .NET Framework 4.8 개발 도구 | 16.4.29318.151 | 옵션

## <a name="mobile-development-with-net"></a>.NET을 사용한 모바일 개발

**ID:** Microsoft.VisualStudio.Workload.XamarinBuildTools

**설명:** C# 및 F#을 사용하여 iOS, Android 및 Windows용 플랫폼 간 애플리케이션을 빌드하기 위한 도구입니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | Name | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 16.5.29515.121 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 16.0.28517.75 | 필수
Microsoft.Net.Component.4.8.SDK | .NET Framework 4.8 SDK | 16.4.29313.120 | 필수
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet 대상 및 빌드 작업 | 16.1.28829.92 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 16.0.28714.129 | 필수
Component.Android.SDK28 | Android SDK 설치(API 레벨 28) | 16.2.29003.222 | 옵션
Component.OpenJDK | OpenJDK(Microsoft 배포) | 16.1.28811.260 | 옵션

## <a name="unaffiliated-components"></a>독립적 구성 요소

이러한 구성 요소는 작업에 포함되지 않지만 개별 구성 요소로 선택할 수 있습니다.

구성 요소 ID | Name | 버전
--- | --- | ---
Microsoft.Net.Core.Component.SDK.2.2 | .NET Core 2.2 런타임(지원되지 않음) | 16.7.30310.162
Microsoft.Net.Core.Component.SDK.3.0 | .NET Core 3.0 런타임(지원되지 않음) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.20.ARM | MSVC v142 - VS 2019 C++ ARM 빌드 도구(v14.20) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.20.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM 스펙터 완화 라이브러리(v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ARM64 | MSVC v142 – VS 2019 C++ ARM64 빌드 도구(v14.20) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.20.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 스펙터 완화 라이브러리(v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL | v142 빌드 도구용 C++ v14.20 ATL(x86 & x64) | 16.1.28829.92
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM | v142 빌드 도구용 C++ v14.20 ATL(ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.20 ATL(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64 | v142 빌드 도구용 C++ v14.20 ATL(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.ARM64.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.20 ATL(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.ATL.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.20 ATL(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.CLI.Support | v142 빌드 도구용 C++/CLI 지원(14.20) | 16.4.29409.204
Microsoft.VisualStudio.Component.VC.14.20.MFC | v142 빌드 도구용 C++ v14.20 MFC(x86 및 x64) | 16.2.29003.222
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM | v142 빌드 도구용 C++ v14.20 MFC(ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.20 MFC(ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64 | v142 빌드 도구용 C++ v14.20 MFC(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.ARM64.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.20 MFC(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.MFC.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.20 MFC(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.20.x86.x64 | MSVC v142 – VS 2019 C++ x64/x86 빌드 도구(v14.20) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.20.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 스펙터 완화 라이브러리(v14.20) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM | MSVC v142 – VS 2019 C++ ARM 빌드 도구(v14.21) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.21.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM 스펙터 완화 라이브러리(v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ARM64 | MSVC v142 – VS 2019 C++ ARM64 빌드 도구(v14.21) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.21.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 스펙터 완화 라이브러리(v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL | v142 빌드 도구용 C++ v14.21 ATL(x86 & x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM | v142 빌드 도구용 C++ v14.21 ATL(ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.21 ATL(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64 | v142 빌드 도구용 C++ v14.21 ATL(ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.ATL.ARM64.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.21 ATL(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.ATL.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.21 ATL(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.CLI.Support | v142 빌드 도구용 C++/CLI 지원(14.21) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.14.21.MFC | v142 빌드 도구용 C++ v14.21 MFC(x86 및 x64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM | v142 빌드 도구용 C++ v14.21 MFC(ARM) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.21 MFC(ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64 | v142 빌드 도구용 C++ v14.21 MFC(ARM64) | 16.2.29019.55
Microsoft.VisualStudio.Component.VC.14.21.MFC.ARM64.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.21 MFC(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.MFC.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.21 MFC(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.21.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.21) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.21.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 스펙터 완화 라이브러리(v14.21) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM | MSVC v142 – VS 2019 C++ ARM 빌드 도구(v14.22) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.22.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM 스펙터 완화 라이브러리(v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ARM64 | MSVC v142 – VS 2019 C++ ARM64 빌드 도구(v14.22) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.22.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 스펙터 완화 라이브러리(v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL | v142 빌드 도구용 C++ v14.22 ATL(x86 및 x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM | v142 빌드 도구용 C++ v14.22 ATL(ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.22 ATL(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64 | v142 빌드 도구용 C++ v14.22 ATL(ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.ATL.ARM64.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.22 ATL(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.ATL.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.22 ATL(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.CLI.Support | v142 빌드 도구용 C++/CLI 지원(14.22) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.22.MFC | v142 빌드 도구용 C++ v14.22 MFC(x86 및 x64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM | v142 빌드 도구용 C++ v14.22 MFC(ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.22 MFC(ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64 | v142 빌드 도구용 C++ v14.22 MFC(ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.14.22.MFC.ARM64.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.22 MFC(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.MFC.Spectre | 스펙터 완화를 지원하는 v142 빌드 도구용 C++ v14.22 MFC(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.22.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.22) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.22.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 스펙터 완화 라이브러리(v14.22) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM | MSVC v142 - VS 2019 C++ ARM 빌드 도구(v14.23) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.23.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM 스펙터 완화 라이브러리(v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ARM64 | MSVC v142 - VS 2019 C++ ARM64 빌드 도구(v14.23) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.23.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 스펙터 완화 라이브러리(v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL | v142 빌드 도구용 C++ v14.23 ATL(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM | v142 빌드 도구용 C++ v14.23 ATL(ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.23 ATL(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64 | v142 빌드 도구용 C++ v14.23 ATL(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.ARM64.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.23 ATL(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.ATL.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.23 ATL(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.CLI.Support | v142 빌드 도구용 C++/CLI 지원(14.23) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.23.MFC | v142 빌드 도구용 C++ v14.23 MFC(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM | v142 빌드 도구용 C++ v14.23 MFC(ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.23 MFC(ARM) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64 | v142 빌드 도구용 C++ v14.23 MFC(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.ARM64.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.23 MFC(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.MFC.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.23 MFC(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.23.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.23) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.23.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 스펙터 완화 라이브러리(v14.23) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.14.24.ARM | MSVC v142 - VS 2019 C++ ARM 빌드 도구(v14.24) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.24.ARM.Spectre | MSVC v142 – VS 2019 C++ ARM Spectre 완화 라이브러리(v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ARM64 | MSVC v142 - VS 2019 C++ ARM64 빌드 도구(v14.24) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.24.ARM64.Spectre | MSVC v142 – VS 2019 C++ ARM64 Spectre 완화 라이브러리(v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL | v142 빌드 도구용 C++ v14.24 ATL(x86 및 x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM | v142 빌드 도구용 C++ v14.24 ATL(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.24 ATL(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64 | v142 빌드 도구용 C++ v14.24 ATL(ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.ARM64.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.24 ATL(ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.ATL.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.24 ATL(x86 및 x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.CLI.Support | v142 빌드 도구용 C++/CLI 지원(14.24) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.24.MFC | v142 빌드 도구용 C++ v14.24 MFC(x86 및 x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM | v142 빌드 도구용 C++ v14.24 MFC(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.24 MFC(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64 | v142 빌드 도구용 C++ v14.24 MFC(ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.ARM64.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.24 MFC(ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.MFC.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.24 MFC(x86 및 x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.24.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.24) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.24.x86.x64.Spectre | MSVC v142 – VS 2019 C++ x64/x86 Spectre 완화 라이브러리(v14.24) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.14.25.ARM | MSVC v142 - VS 2019 C++ ARM 빌드 도구(v14.25) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre 완화 라이브러리(v14.25) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.ARM64 | MSVC v142 - VS 2019 C++ ARM64 빌드 도구(v14.25) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre 완화 라이브러리(v14.25) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.ATL | v142 빌드 도구용 C++ v14.25 ATL(x86 및 x64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM | v142 빌드 도구용 C++ v14.25 ATL(ARM) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.25 ATL(ARM) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM64 | v142 빌드 도구용 C++ v14.25 ATL(ARM64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.ATL.ARM64.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.25 ATL(ARM64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.ATL.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.25 ATL(x86 및 x64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.CLI.Support | v142 빌드 도구용 C++/CLI 지원(14.25) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.MFC | v142 빌드 도구용 C++ v14.25 MFC(x86 및 x64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM | v142 빌드 도구용 C++ v14.25 MFC(ARM) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.25 MFC(ARM) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64 | v142 빌드 도구용 C++ v14.25 MFC(ARM64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.MFC.ARM64.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.25 MFC(ARM64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.MFC.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.25 MFC(x86 및 x64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.25) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.25.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre 완화 라이브러리(v14.25) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.ARM | MSVC v142 - VS 2019 C++ ARM 빌드 도구(v14.26) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre 완화 라이브러리(v14.26) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.ARM64 | MSVC v142 - VS 2019 C++ ARM64 빌드 도구(v14.26) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre 완화 라이브러리(v14.26) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.ATL | v142 빌드 도구용 C++ v14.26 ATL(x86 및 x64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM | v142 빌드 도구용 C++ v14.26 ATL(ARM) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.26 ATL(ARM) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64 | v142 빌드 도구용 C++ v14.26 ATL(ARM64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.ATL.ARM64.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.26 ATL(ARM64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.ATL.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.26 ATL(x86 및 x64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.CLI.Support | v142 빌드 도구용 C++/CLI 지원(14.26) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.MFC | v142 빌드 도구용 C++ v14.26 MFC(x86 및 x64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM | v142 빌드 도구용 C++ v14.26 MFC(ARM) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.26 MFC(ARM) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM64 | v142 빌드 도구용 C++ v14.26 MFC(ARM64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.MFC.ARM64.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.26 MFC(ARM64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.MFC.Spectre | Spectre 완화를 지원하는 v142 빌드 도구용 C++ v14.26 MFC(x86 및 x64) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.x86.x64 | MSVC v142 - VS 2019 C++ x64/x86 빌드 도구(v14.26) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.14.26.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre 완화 라이브러리(v14.26) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.ATL.ARM | 최신 v142 빌드 도구용 C++ ATL(ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | 스펙터 완화를 지원하는 최신 v142 빌드 도구용 C++ ATL(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | 최신 v142 빌드 도구용 C++ ATL(ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | 스펙터 완화를 지원하는 최신 v142 빌드 도구용 C++ ATL(ARM64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATL.Spectre | 스펙터 완화를 지원하는 최신 v142 빌드 도구용 C++ ATL(x86 및 x64) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | 스펙터 완화를 지원하는 최신 v142 빌드 도구용 C++ MFC(x86 및 x64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM | 최신 v142 빌드 도구용 C++ MFC(ARM) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | 스펙터 완화를 지원하는 최신 v142 빌드 도구용 C++ MFC(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | 최신 v142 빌드 도구용 C++ MFC(ARM64) | 16.4.29313.120
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | 스펙터 완화를 지원하는 최신 v142 빌드 도구용 C++ MFC(ARM64) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.Redist.MSM | C++ 2019 재배포 가능 MSM | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | MSVC v142 - VS 2019 C++ ARM Spectre 완화 라이브러리(v14.27) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | MSVC v142 - VS 2019 C++ ARM64 Spectre 완화 라이브러리(v14.27) | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | MSVC v142 - VS 2019 C++ x64/x86 Spectre 완화 라이브러리(v14.27)  | 16.7.30310.162
Microsoft.VisualStudio.Component.VC.v141.ARM.Spectre | MSVC v141 – VS 2017 C++ ARM 스펙터 완화 라이브러리(v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ARM64.Spectre | MSVC v141 – VS 2017 C++ ARM64 스펙터 완화 라이브러리(v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.VC.v141.ATL | v141 빌드 도구용 C++ ATL(x86 및 x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM | v141 빌드 도구용 C++ ATL(ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM.Spectre | 스펙터 완화를 지원하는 v141 빌드 도구용 C++ ATL(ARM) | 16.5.29721.120
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64 | v141 빌드 도구용 C++ ATL(ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.ARM64.Spectre | 스펙터 완화를 지원하는 v141 빌드 도구용 C++ ATL(ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.ATL.Spectre | 스펙터 완화를 지원하는 v141 빌드 도구용 C++ ATL(x86 및 x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.CLI.Support | v141 빌드 도구용 C++/CLI 지원(14.16) | 16.3.29207.166
Microsoft.VisualStudio.Component.VC.v141.MFC | v141 빌드 도구용 C++ MFC(x86 및 x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM | v141 빌드 도구용 C++ MFC(ARM) | 16.2.28915.88
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM.Spectre | 스펙터 완화를 지원하는 v141 빌드 도구용 C++ MFC(ARM) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64 | v141 빌드 도구용 C++ MFC(ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.ARM64.Spectre | 스펙터 완화를 지원하는 v141 빌드 도구용 C++ MFC(ARM64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.MFC.Spectre | 스펙터 완화를 지원하는 v141 빌드 도구용 C++ MFC(x86 및 x64) | 16.0.28625.61
Microsoft.VisualStudio.Component.VC.v141.x86.x64.Spectre | MSVC v141 – VS 2017 C++ x64/x86 스펙터 완화 라이브러리(v14.16) | 16.5.29515.121
Microsoft.VisualStudio.Component.WinXP | VS 2017(v141) 도구용 C++ Windows XP 지원[사용되지 않음] | 16.1.28811.260
