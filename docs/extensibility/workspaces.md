---
title: Visual Studio의 작업 영역 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 011781b434c4d005e473c5f97c60a9269dc5d034
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952765"
---
# <a name="workspaces"></a>작업 영역

작업 영역은 Visual Studio가 [열려 있는 폴더](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)에 있는 파일의 컬렉션을 나타내는 방법 이며 형식으로 표현 됩니다 <xref:Microsoft.VisualStudio.Workspace.IWorkspace> . 작업 영역에서 폴더 내의 파일과 관련 된 내용이 나 기능을 이해 하지 못합니다. 대신, 다른 사용자가 작업할 수 있는 데이터를 생성 하 고 사용할 수 있는 기능 및 확장을 위한 일반적인 Api 집합을 제공 합니다. 생산자는 다양 한 내보내기 특성을 사용 하 여 [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF)를 통해 구성 됩니다.

## <a name="workspace-providers-and-services"></a>작업 영역 공급자 및 서비스

작업 영역 공급자 및 서비스는 작업 영역의 내용에 반응 하는 데이터와 기능을 제공 합니다. 컨텍스트 파일 정보, 소스 파일의 기호 또는 빌드 기능을 제공할 수 있습니다.

두 개념 모두 [팩터리 패턴](https://en.wikipedia.org/wiki/Factory_method_pattern) 을 사용 하며 작업 영역에서 MEF를 통해 가져옵니다. 모든 내보내기 특성 `IProviderMetadataBase` 은 또는 `IWorkspaceServiceFactoryMetadata` 을 구현 하지만 확장 된 형식에 사용 해야 하는 구체적 형식이 있습니다.

공급자와 서비스 간의 한 가지 차이점은 작업 영역에 대 한 관계입니다. 작업 영역에는 특정 형식의 공급자가 여러 개 있을 수 있지만 특정 형식의 서비스는 작업 영역 마다 하나씩만 생성 됩니다. 예를 들어 작업 영역에 많은 파일 스캐너 공급자가 있지만 작업 영역에는 작업 영역 당 하나의 인덱싱 서비스만 있습니다.

또 다른 주요 차이점은 공급자 및 서비스의 데이터를 사용 하는 것입니다. 작업 영역은 몇 가지 이유로 공급자에서 데이터를 가져오는 진입점입니다. 먼저 공급자에 게는 일반적으로 사용자가 만드는 일부 데이터 집합이 있습니다. 데이터는 c # 소스 파일에 대 한 기호 이거나 _CMakeLists.txt_ 파일의 빌드 파일 컨텍스트에 있을 수 있습니다. 작업 영역은 메타 데이터와 요청을 정렬 하는 공급자에 대 한 소비자의 요청을 일치 시킵니다. 둘째, 일부 시나리오에서는 많은 공급자가 요청에 기여할 수 있는 반면, 다른 시나리오에서는 우선 순위가 가장 높은 공급자를 사용 합니다.

반면에 확장은 인스턴스를 가져오고 작업 영역 서비스와 직접 상호 작용할 수 있습니다. 의 확장 메서드 `IWorkspace` 는 Visual Studio에서 제공 하는 서비스 (예:)에 사용할 수 있습니다 <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . 확장 프로그램은 확장 내의 구성 요소에 대 한 작업 영역 서비스를 제공 하거나 다른 확장 프로그램에서 사용할 수 있습니다. 소비자는 <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> 또는 형식에 대해 제공 하는 확장 메서드를 사용 해야 합니다 `IWorkspace` .

>[!WARNING]
> Visual Studio와 충돌 하는 서비스를 작성 하지 마세요. 예기치 않은 문제가 발생할 수 있습니다.

## <a name="disposal-on-workspace-closure"></a>작업 영역 종료 시 삭제

작업 영역을 종료 하면 extender에서 비동기 코드를 삭제 하지만 호출 해야 할 수도 있습니다. <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>이 코드를 쉽게 작성할 수 있도록 인터페이스를 사용할 수 있습니다.

## <a name="related-types"></a>관련 형식

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> 열린 폴더와 같은 열린 작업 영역에 대 한 중앙 엔터티입니다.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> 인스턴스화된 작업 영역 당 공급자를 만듭니다.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> 인스턴스화된 작업 영역 당 서비스를 만듭니다.
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> 을 (를) 삭제 하는 동안 비동기 코드를 실행 해야 하는 공급자 및 서비스에서 구현 해야 합니다.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> 잘 알려진 서비스 또는 임의 서비스에 액세스 하기 위한 도우미 메서드를 제공 합니다.

## <a name="workspace-settings"></a>작업 영역 설정

작업 영역에는 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> 간단 하지만 작업 영역을 강력 하 게 제어 하는 서비스가 있습니다. 설정에 대 한 기본 개요는 [빌드 및 디버그 작업 사용자 지정](../ide/customize-build-and-debug-tasks-in-visual-studio.md)을 참조 하세요.

대부분의 유형에 대 한 설정은 `SettingsType` _VSWorkspaceSettings.js_ 설정 및 _tasks.vs.js_와 같은 _json_ 파일입니다.

작업 영역 설정의 기능은 작업 영역 내에서 간단히 경로 인 "범위"를 중심으로 합니다. 소비자가를 호출 하면 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> 요청 된 경로와 설정 형식이 포함 된 모든 범위가 집계 됩니다. 범위 집계 우선 순위는 다음과 같습니다.

1. "로컬 설정"-일반적으로 작업 영역 루트의 `.vs` 디렉터리입니다.
1. 요청 된 경로 자체입니다.
1. 요청 된 경로의 부모 디렉터리입니다.
1. 작업 영역 루트까지 포함 하는 모든 부모 디렉터리입니다.
1. "전역 설정"은 사용자 디렉터리에 있습니다.

결과는의 인스턴스입니다 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> . 이 개체는 특정 형식에 대 한 설정을 포함 하 고로 저장 된 키 이름을 설정 하기 위해 쿼리할 수 있습니다 `string` . <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A>메서드 및 <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> 확장 메서드는 호출자가 요청 된 설정 값의 형식을 알고 있다고 간주 합니다. 대부분의 설정 파일이 _. json_ 파일로 유지 되므로 많은 호출은 `string` ,, `bool` `int` 및 이러한 형식의 배열을 사용 합니다. 개체 형식도 지원 됩니다. 이러한 경우 자체를 형식 인수로 사용할 수 있습니다 `IWorkspaceSettings` . 예를 들면 다음과 같습니다.

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

이러한 설정이 사용자의 _VSWorkspaceSettings.js_에 있는 경우 다음과 같이 데이터에 액세스할 수 있습니다.

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>이러한 설정 Api는 네임 스페이스에서 사용할 수 있는 Api와 관련이 없습니다 `Microsoft.VisualStudio.Settings` . 작업 영역 설정은 호스트와는 관계가 없으며 작업 영역 특정 설정 파일 또는 동적 설정 공급자를 사용 합니다.

### <a name="providing-dynamic-settings"></a>동적 설정 제공

확장 프로그램은를 제공할 수 있습니다 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> . 이러한 메모리 내 공급자는 확장을 사용 하 여 설정을 추가 하거나 다른 사용자를 재정의할 수 있습니다.

내보내기는 `IWorkspaceSettingsProvider` 다른 작업 영역 공급자와는 다릅니다. 팩터리가이 아니고 `IWorkspaceProviderFactory` 특수 특성 유형이 없습니다. 대신을 구현 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> 하 고를 사용 `[Export(typeof(IWorkspaceSettingsProviderFactory))]` 합니다.

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>을 반환 하는 메서드를 구현 하는 경우 `IWorkspaceSettingsSource` (예: `IWorkspaceSettingsProvider.GetSingleSettings` )가 아닌의 인스턴스를 반환 `IWorkspaceSettings` `IWorkspaceSettingsSource` 합니다. `IWorkspaceSettings` 일부 설정 집계 중에 유용할 수 있는 자세한 정보를 제공 합니다.

### <a name="settings-related-apis"></a>설정 관련 Api

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> 작업 영역에 대 한 설정을 읽고 집계 합니다.
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A>`IWorkspaceSettingsManager`작업 영역에 대 한를 가져옵니다.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> 모든 겹치는 범위에서 집계 된 지정 된 범위에 대 한 설정을 가져옵니다.
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> 특정 범위에 대 한 설정을 포함 합니다.

## <a name="workspace-suggested-practices"></a>작업 영역 제안 방법

- `IWorkspaceProviderFactory.CreateProvider`생성 시 컨텍스트를 기억할 유사한 api 또는에서 개체를 반환 `Workspace` 합니다. 이 개체가 생성 될 때까지 공급자 인터페이스가 작성 됩니다.
- 작업 영역에 대 한 "로컬 설정" 경로에 작업 영역 관련 캐시 또는 설정을 저장 합니다. `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder`Visual Studio 2017 버전 15.6 이상에서를 사용 하 여 파일에 대 한 경로를 만듭니다. 버전 15.6 이전 버전의 경우 다음 코드 조각을 사용 합니다.

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>솔루션 이벤트 및 패키지 자동 로드

로드 된 패키지는 `IVsSolutionEvents7` 을 구현 하 고 호출할 수 있습니다 `IVsSolution.AdviseSolutionEvents` . Visual Studio에서 폴더 열기 및 닫기에 대 한 이벤트를 포함 합니다.

UI 컨텍스트를 사용 하 여 패키지를 자동으로 로드할 수 있습니다. 값이 `4646B819-1AE0-4E79-97F4-8A8176FDD664`입니다.

## <a name="troubleshooting"></a>문제 해결

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage 패키지가 제대로 로드 되지 않았습니다.

작업 영역 확장성은 MEF 기반 이며 컴퍼지션 오류로 인해 열린 폴더를 호스팅하는 패키지가 로드 되지 않습니다. 예를 들어, 확장이를 사용 하 여 형식을 내보내고 `ExportFileContextProviderAttribute` 형식이를 구현 하는 경우 `IWorkspaceProviderFactory<IFileContextActionProvider>` Visual Studio에서 폴더를 열려고 하면 오류가 발생 합니다.

::: moniker range="vs-2017"

오류 세부 정보는 _%localappdata%\microsoft\visualstudio\15.0_id \componentmodelcache\microsoft.visualstudio.default.err_에서 찾을 수 있습니다. 확장 프로그램에서 구현 하는 형식에 대 한 모든 오류를 해결 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

오류 세부 정보는 _%localappdata%\microsoft\visualstudio\16.0_id \componentmodelcache\microsoft.visualstudio.default.err_에서 찾을 수 있습니다. 확장 프로그램에서 구현 하는 형식에 대 한 모든 오류를 해결 합니다.

::: moniker-end

## <a name="next-steps"></a>다음 단계

* [파일](workspace-file-contexts.md) 컨텍스트-파일 컨텍스트 공급자는 열린 폴더 작업 영역에 대 한 코드 인텔리전스를 가져옵니다.
* [인덱싱](workspace-indexing.md) -작업 영역 인덱싱은 작업 영역에 대 한 정보를 수집 하 고 유지 합니다.
