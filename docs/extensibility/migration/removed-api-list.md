---
title: Visual Studio 2022 미리 보기에서 제거된 API
description: 확장 작성자가 Visual Studio 2022 미리 보기에서 작동하도록 확장을 업데이트하기 위해 Visual Studio 2022 미리 보기에서 제거된 VS SDK API에 대해 알아봅니다.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: bed8d0a261f70acb5e842ebeaf0059faae3fc478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308583"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>Visual Studio 2022 SDK에서 API 제거

[!INCLUDE [preview-note](../includes/preview-note.md)]

아래 API는 Visual Studio SDK에서 제거되었으며 더 이상 사용할 수 없습니다. 코드를 업데이트하는 방법에 대한 자세한 내용은 각 섹션을 참조하세요.

* [`IVsImageService`](#ivsimageservice)
* [`IBlockContextProvider`](#iblockcontextprovider)
* [`IToolTipProvider`](#itooltipprovider)
* [`IVsTextScanner` 및 `IVsFullTextScanner`](#ivstextscanner-and-ivsfulltextscanner)
* [비동기 솔루션 로드 및 경량 솔루션 로드](#asynchronous-solution-load-and-lightweight-solution-load)
* [`IVsDummy`](#ivsdummy)
* [`Microsoft.VisualStudio.Shell.Task`](#microsoftvisualstudioshelltask)
* [원본 안전에서 열기](#open-from-source-safe)
* [.NET Framework 대한 새 WPF XAML 디자이너](#new-wpf-xaml-designer-for-net-framework)

## <a name="ivsimageservice"></a>IVsImageService

`IVsImageService`는 2022년 Visual Studio 제거됩니다. 의 모든 사용자는 `IVsImageService` 대신 로 이동해야 `IVsImageService2` 합니다.

### <a name="recommended-updates"></a>권장 업데이트

를 사용하는 경우 `IVsImageService` 해당 메서드에 대한 호출을 에서 해당하는 메서드에 대한 호출로 대체합니다. `IVsImageService2`

| **IVsImageService 메서드** | **동등한 IVsImageService2 메서드** |
|----------------------------|----------------------------------------|
| 추가                        | AddCustomImage                         |
| 가져오기                        | GetImage                               |
| GetIconForFile             | GetImageMonikerForFile                 |
| GetIconForFileEx           | GetImageMonikerForFile                 |

`IVsImageService`의 Add 및 Get 메서드는 모니커가 아닌 이름(문자열)으로 사용자 지정 이미지를 참조합니다.  모니커만 사용하여 사용자 지정 이미지를 참조하도록 코드를 전환하는 것이 좋지만, 비실용적인 것으로 입증되는 경우 `IVsImageService2` 이름을 모니커와 연결할 수 있는 몇 가지 메서드가 있습니다.

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

이러한 두 가지 방법을 사용하여 이름으로 이미지를 계속 참조할 수 있습니다.

## <a name="iblockcontextprovider"></a>IBlockContextProvider

`IBlockContextProvider`및 관련 형식은 Visual Studio 2022에서 제거됩니다. 의 모든 사용자는 `IBlockContextProvider` 대신 로 이동해야 `IStructureContextSourceProvider` 합니다.

### <a name="recommended-updates"></a>권장 업데이트

의 사용자는 `IBlockContextProvider` `IStructureContextSourceProvider` 대신 ([설명서](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider))를 사용해야 합니다.

## <a name="itooltipprovider"></a>IToolTipProvider

`IToolTipProvider`및 관련 형식은 Visual Studio 2022에서 제거됩니다. 의 모든 사용자는 `IToolTipProvider` 대신 로 이동해야 `IToolTipService` 합니다.

### <a name="recommended-updates"></a>권장 업데이트

의 사용자는 `IToolTipProvider` `IToolTipService` 대신 ([설명서](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice))를 사용해야 합니다.

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>IVsTextScanner 및 IVsFullTextScanner

`IVsTextScanner`및 `IVsFullTextScanner` 는 2022년 Visual Studio 제거됩니다. 또는 의 모든 사용자는 `IVsTextScanner` `IVsFullTextScanner` 대신 로 이동해야 `IVsTextLines` 합니다.

### <a name="recommended-updates"></a>권장 업데이트

또는 의 사용자는 `IVsTextScanner` `IVsFullTextScanner` 를 대신 사용해야 `IVsTextLines` 합니다([설명서](/dotnet/apimicrosoft.visualstudio.textmanager.interop.ivstextlines.getlinetext)).

## <a name="asynchronous-solution-load-and-lightweight-solution-load"></a>비동기 솔루션 로드 및 경량 솔루션 로드

ASL(비동기 솔루션 로드) 및 LSL(경량 솔루션 로드) 기능은 2022년 Visual Studio 제거되고 있습니다. 따라서 다음 메서드가 제거됩니다.

### <a name="interfaces"></a>인터페이스

* `IVsSolution4` - 메서드: `IsBackgroundSolutionLoadEnabled` , `EnsureProjectsAreLoaded` , `EnsureProjectIsLoaded` , `EnsureSolutionIsLoaded`
* `IVsSolutionLoadEvents` - 메서드: `OnBeforeBackgroundSolutionLoadBegins` , `OnQueryBackgroundLoadProjectBatch` , `OnBeforeLoadProjectBatch` , `OnAfterLoadProjectBatch`
* `IVsSolutionLoadManagerSupport` - 전체 인터페이스
* `IVsSolutionLoadManager` - 전체 인터페이스
* `IVsSccManager3`  - 전체 인터페이스
* `IVsAsynchronousProjectCreate` - 전체 인터페이스
* `IVsAsynchronousProjectCreateUI` - 전체 인터페이스

### <a name="enums-properties-and-ui-contexts"></a>열거형, 속성 및 UI 컨텍스트

* `VSHPROPID_ProjectUnloadStatus` - 열거형: `UNLOADSTATUS_LoadPendingIfNeeded`
* `VSHPROPID_DemandLoadDependencies`
* `VSHPROPID_IsProjectProvisioned`
* `VSPROPID_IsInBackgroundIdleLoadProjectBatch`
* `VSPROPID_IsInSyncDemandLoadProjectBatch`
* `VSPROPID_ActiveSolutionLoadManager`
* `UICONTEXT_BackgroundProjectLoad`

### <a name="recommended-updates"></a>권장 업데이트

없음

## <a name="ivsdummy"></a>IVsDummy

`IVsDummy`는 2022년 Visual Studio 제거되며 대체되지 않습니다. 

### <a name="recommended-updates"></a>권장 업데이트

없음 그러나 API가 아무 것도 하지 않았기 때문에 아무 영향도 미치지 않아야 합니다.

## <a name="microsoftvisualstudioshelltask"></a>Microsoft.VisualStudio.Shell.Task

`Microsoft.VisualStudio.Shell.Task`클래스는 매우 인기 `Microsoft.VisualStudio.Shell.TaskListItem` 있는 클래스와 충돌하지 않도록 로 이름이 `System.Threading.Tasks.Task` 변경되었습니다.

## <a name="open-from-source-safe"></a>원본 안전에서 열기

다음 메서드, 이벤트 및 상수를 제거하는 등 소스로부터 안전한 솔루션을 열기 위한 지원이 제거되고 있습니다.

## <a name="interfaces"></a>인터페이스

* `IVsSCCProvider3` - 전체 인터페이스

### <a name="recommended-updates"></a>권장 업데이트

없음

## <a name="new-wpf-xaml-designer-for-net-framework"></a>.NET Framework 대한 새 WPF XAML 디자이너

.NET Framework 대한 현재 WPF XAML 디자이너 더 이상 사용되지 않으며 .NET(.NET Core)용 WPF XAML 디자이너 사용되는 것과 동일한 아키텍처에 따라 .NET Framework 새 WPF XAML 디자이너 대체됩니다. 즉, WPF .NET Framework .design.dll 기반의 확장성 모델을 제어하고 Microsoft.Windows.Design.Extensibility는 더 이상 지원되지 않습니다. .NET Framework 대한 새 WPF XAML 디자이너 .NET(.NET Core)용 WPF XAML 디자이너 동일한 확장성 모델을 제공합니다. .NET용 .designtools.dll 확장(.NET Core)을 이미 만든 경우 .NET Framework 새 WPF XAML 디자이너 동일한 확장이 작동합니다. WPF 플랫폼(.NET Framework 및 .NET Core) 및 UWP 플랫폼의 새로운 확장성 모델로 마이그레이션하는 방법에 대한 자세한 내용은 아래 마이그레이션 링크를 참조하세요. 

### <a name="recommended-updates"></a>권장 업데이트

[XAML 디자이너 확장성 마이그레이션을](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md)참조하세요.
