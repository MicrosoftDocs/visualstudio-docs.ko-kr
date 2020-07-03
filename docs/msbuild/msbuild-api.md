---
title: MSBuild API | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9d3cdaf2bcc7d7c62f7224c3a8c439d03282ef0
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371926"
---
# <a name="use-the-msbuild-api"></a>MSBuild API 사용

MSBuild는 프로그램이 빌드를 수행하고 프로젝트를 검사할 수 있도록 공용 API 화면을 제공합니다. 최신 버전의 MSBuild API는 다음 NuGet 패키지에서 찾을 수 있습니다.

| 패키지 이름 | 설명 |
| ------------ | ----------- |
| [Microsoft.Build](https://www.nuget.org/packages/Microsoft.Build) | MSBuild 프로젝트를 만들고, 편집 및 평가하는 데 사용하는 Microsoft.Build 어셈블리를 포함합니다.|
| [Microsoft.Build.Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| 다른 MSBuild 어셈블리에서 사용하는 공용 MSBuild 프레임워크 어셈블리를 포함합니다. |
| [Microsoft.Build.Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | MSBuild의 전체 실행 파일 복사본을 제공합니다. 애플리케이션에서 MSBuild를 설치할 필요 없이 프로젝트를 로드하거나 in-process 빌드를 실행해야 하는 경우에만 이 패키지를 참조합니다. 이 패키지를 사용하여 프로젝트를 평가하려면 추가 구성 요소(예: 컴파일러)를 애플리케이션 디렉터리에 집계해야 합니다. |
| [Microsoft.Build.Tasks.Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | MSBuild의 일반적으로 사용되는 작업을 구현하는 Microsoft.Build.Tasks 어셈블리를 포함합니다. |
| [Microsoft.Build.Utilities.Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | 사용자 지정 MSBuild 작업을 구현하는 데 사용하는 Microsoft.Build.Utilities.Core 어셈블리를 포함합니다. |

또한 NuGet은 더 이상 사용되지 않는 레거시 어셈블리인 [Microsoft.Build.Engine](https://www.nuget.org/packages/Microsoft.Build.Engine)을 호스트합니다.

MSBuild API의 다양한 버전이 있으며, 버전 15 및 16의 경우 NuGet 패키지에 두 가지 형식의 어셈블리가 있습니다. 하나는 .NET Framework로 컴파일되며 다른 하나는 .NET Framework API 표면에 속한 .NET Core로 컴파일됩니다.  MSBuild의 .NET Core 버전은 `dotnet` 명령을 호출할 때와 Mac 및 Linux 시스템에서 MSBuild를 사용할 때 사용됩니다.

MSBuild API에 관한 설명서는 [.NET API 브라우저](/dotnet/api)를 사용하거나 다음 목록에서 네임스페이스를 검색하여 찾을 수 있습니다.

::: moniker range="vs-2017"
| 네임스페이스 | 적용 대상 | 설명 |
|-----------| -----------| ----------- |
| [Microsoft.Build.Construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15) | 모두 |  MSBuild 개체 모델이 평가되지 않은 값으로 프로젝트 루트를 생성하는 데 사용하는 형식을 포함합니다. 각 프로젝트 루트는 프로젝트 또는 대상 파일에 해당합니다. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15) | 모두 | 프로젝트 생성을 지원하는 `ProjectOptions` 클래스를 포함합니다. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15) | 모두 | MSBuild 개체 모델이 프로젝트를 평가하는 데 사용하는 형식을 포함합니다. 각 프로젝트는 하나 이상의 프로젝트 루트와 연결됩니다. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15) | 모두 | 전체 호출에 평가 상태를 저장하는 데 사용하는 `EvaluationContext` 클래스를 포함합니다. |
| [Microsoft.Build.Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15) | 모두 | 빌드 프로세스 중에 throw될 수 있는 예외 형식을 포함합니다. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15) | 모두 | MSBuild 개체 모델이 프로젝트를 빌드하는 데 사용하는 형식을 포함합니다. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15) | 모두 | 작업과 로거가 MSBuild 엔진과 상호 작용하는 방법을 정의하는 형식을 포함합니다.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15) | 모두 | 성능 프로파일링을 지원하는 형식을 포함합니다. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15) | .NET Framework만 해당 | 파일, 규칙 및 기타 소스에서 구문 분석된 XAML 형식을 나타내는 데 사용하는 클래스를 포함합니다. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15) | 모두 | 와일드카드 처리를 지원하는 클래스를 포함합니다. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15) | 모두 | 와일드카드 처리에 대한 확장을 지원하는 형식을 포함합니다. |
| [Microsoft.Build.Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15) | 모두 | `-graph` MSBuild 스위치를 지원하는 형식을 포함합니다. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15) | 모두 | 빌드 진행률을 기록하는 데 사용하는 형식을 포함합니다. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15) | 모두 | MSBuild의 원격 통신을 지원하는 형식을 포함합니다. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15) | 모두 | MSBuild와 함께 제공되는 모든 작업의 구현을 포함합니다. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15) | .NET Framework만 해당 | MSBuild에서 내부적으로 사용하는 클래스를 포함합니다. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15) | .NET Framework만 해당 | MSBuild에서 사용하는 클래스를 포함합니다.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15) | 모두 | MSBuild에서 내부적으로 사용하는 클래스를 포함합니다. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15) | .NET Framework만 해당 | XAML 빌드 작업과 관련된 클래스를 포함합니다. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15) | 모두 | 고유한 MSBuild 로거 및 작업을 만드는 데 사용할 수 있는 도우미 클래스를 포함합니다.|
:::moniker-end
:::moniker range=">=vs-2019"
| 네임스페이스 | 적용 대상 | 설명 |
|-----------| -----------| ----------- |
| [Microsoft.Build.Construction](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16) | 모두 |  MSBuild 개체 모델이 평가되지 않은 값으로 프로젝트 루트를 생성하는 데 사용하는 형식을 포함합니다. 각 프로젝트 루트는 프로젝트 또는 대상 파일에 해당합니다. |
| [Microsoft.Build.Definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16) | 모두 | 프로젝트 생성을 지원하는 `ProjectOptions` 클래스를 포함합니다. |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16) | 모두 | MSBuild 개체 모델이 프로젝트를 평가하는 데 사용하는 형식을 포함합니다. 각 프로젝트는 하나 이상의 프로젝트 루트와 연결됩니다. |
| [Microsoft.Build.Evaluation.Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16) | 모두 | 전체 호출에 평가 상태를 저장하는 데 사용하는 `EvaluationContext` 클래스를 포함합니다. |
| [Microsoft.Build.Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16) | 모두 | 빌드 프로세스 중에 throw될 수 있는 예외 형식을 포함합니다. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16) | 모두 | MSBuild 개체 모델이 프로젝트를 빌드하는 데 사용하는 형식을 포함합니다. |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16) | 모두 | 작업과 로거가 MSBuild 엔진과 상호 작용하는 방법을 정의하는 형식을 포함합니다.|
| [Microsoft.Build.Framework.Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16) | 모두 | 성능 프로파일링을 지원하는 형식을 포함합니다. |
| [Microsoft.Build.Framework.XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16) | .NET Framework만 해당 | 파일, 규칙 및 기타 소스에서 구문 분석된 XAML 형식을 나타내는 데 사용하는 클래스를 포함합니다. |
| [Microsoft.Build.Globbing](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16) | 모두 | 와일드카드 처리를 지원하는 클래스를 포함합니다. |
| [Microsoft.Build.Globbing.Extensions](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16) | 모두 | 와일드카드 처리에 대한 확장을 지원하는 형식을 포함합니다. |
| [Microsoft.Build.Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16) | 모두 | `-graph` MSBuild 스위치를 지원하는 형식을 포함합니다. |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16) | 모두 | 빌드 진행률을 기록하는 데 사용하는 형식을 포함합니다. |
| [Microsoft.Build.ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16) | 모두 | MSBuild의 원격 통신을 지원하는 형식을 포함합니다. |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16) | 모두 | MSBuild와 함께 제공되는 모든 작업의 구현을 포함합니다. |
| [Microsoft.Build.Tasks.Deployment.Bootstrapper](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16) | .NET Framework만 해당 | MSBuild에서 내부적으로 사용하는 클래스를 포함합니다. |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16) | .NET Framework만 해당 | MSBuild에서 사용하는 클래스를 포함합니다.|
| [Microsoft.Build.Tasks.Hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16) | 모두 | MSBuild에서 내부적으로 사용하는 클래스를 포함합니다. |
| [Microsoft.Build.Tasks.Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16) | .NET Framework만 해당 | XAML 빌드 작업과 관련된 클래스를 포함합니다. |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16) | 모두 | 고유한 MSBuild 로거 및 작업을 만드는 데 사용할 수 있는 도우미 클래스를 포함합니다.|
:::moniker-end

위의 표에서 적용 대상 열의 모두는 MSBuild API의 .NET Framework 및 .NET Core 버전에서 둘 다 네임스페이스의 형식을 사용할 수 있음을 의미합니다.
