---
title: 사용자 지정 프로젝트의 버전 인식 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 0b29728cffc962b5d09a5adc45f8cac2093b020a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825682"
---
# <a name="making-custom-projects-version-aware"></a>사용자 지정 프로젝트의 버전 인식 설정
사용자 지정 프로젝트 시스템에서 해당 형식의 프로젝트가 여러 버전의 Visual Studio에서 로드되도록 할 수 있습니다. 또한 이전 버전의 Visual Studio에서 해당 형식의 프로젝트를 로드할 수 없도록 방지할 수도 있습니다. 프로젝트를 복구, 변환 또는 사용 중단해야 하는 경우 자신을 이후 버전으로 식별하도록 해당 프로젝트를 설정할 수 있습니다.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>프로젝트가 여러 버전에서 로드되도록 허용  
 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 이상 버전에서 만들어진 프로젝트는 대부분 여러 버전에서 작동하도록 수정할 수 있습니다.  
  
 Visual Studio는 프로젝트를 로드하기 전에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> 메서드를 호출하여 프로젝트를 업그레이드할 수 있는지 여부를 확인합니다. 프로젝트를 업그레이드할 수 있는 경우 `UpgradeProject_CheckOnly` 메서드는 나중에 프로젝트를 업그레이드하기 위해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 메서드를 호출하도록 플래그를 설정합니다. 호환되지 않는 프로젝트는 업그레이드할 수 없기 때문에 `UpgradeProject_CheckOnly` 는 제일 먼저 이전 섹션에서 설명한 대로 프로젝트 호환성을 확인해야 합니다.  
  
 프로젝트 시스템 작성자는 `UpgradeProject_CheckOnly` 인터페이스에서 `IVsProjectUpgradeViaFactory4` 를 구현하여 프로젝트 시스템 사용자에게 업그레이드 검사를 제공합니다. 사용자가 프로젝트를 열면 이 메서드가 호출되어 로드하기 전에 프로젝트를 복구해야 하는지 여부를 확인합니다. 가능한 업그레이드 요구 사항은 `VSPUVF_REPAIRFLAGS`에 열거되며 여기에는 다음과 같은 요구 사항이 포함됩니다.  
  
1. `SPUVF_PROJECT_NOREPAIR`: 복구할 필요가 없습니다.  
  
2. `VSPUVF_PROJECT_SAFEREPAIR`: 이전 버전의 제품에서 발생했던 문제 없이 프로젝트가 이전 버전과 호환됩니다.  
  
3. `VSPUVF_PROJECT_UNSAFEREPAIR`: 프로젝트가 이전 버전과 호환되지만 이전 버전의 제품에서 발생했던 일부 문제가 발생합니다. 예를 들어 프로젝트가 다른 SDK 버전에 의존하는 경우에는 호환되지 않습니다.  
  
4. `VSPUVF_PROJECT_ONEWAYUPGRADE`: 프로젝트가 이전 버전과 호환되지 않습니다.  
  
5. `VSPUVF_PROJECT_INCOMPATIBLE`: 현재 버전이 이 프로젝트를 지원하지 않습니다.  
  
6. `VSPUVF_PROJECT_DEPRECATED`: 이 프로젝트가 더 이상 지원되지 않습니다.  
  
> [!NOTE]
> 혼동을 줄 수 있으니 업그레이드 플래그를 설정할 때는 서로 결합하지 마세요. 예를 들어 `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED`처럼 모호한 업그레이드 상태를 만들지 마세요.  
  
 프로젝트 버전을 통해 `UpgradeProjectFlavor_CheckOnly` 인터페이스에서 `IVsProjectFlavorUpgradeViaFactory2` 함수를 구현할 수 있습니다. 이 함수가 작동하게 하려면 앞에서 언급한 `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` 구현에서 이 함수를 호출해야 합니다. 이 호출은 Visual Basic 또는 C# 기본 프로젝트 시스템에서 이미 구현되어 있습니다. 이 함수를 사용하면 프로젝트 버전을 통해 기본 프로젝트 시스템에서 확인한 사항 및 프로젝트의 업그레이드 요구 사항을 파악할 수 있습니다. 호환성 대화 상자에 가장 중요한 두 가지 요구 사항이 표시됩니다.  
  
 Visual Studio가 업그레이드 검사를 수행할 때 이전 버전의 Visual Studio에서와 달리 NULL 값 대신 로거를 제공합니다. 로거를 사용하면 프로젝트 시스템 및 버전을 통해 이전 프로젝트를 올바르게 로드하는 데 필요한 변경의 특성을 이해할 수 있습니다. 대화 상자 대신 로거를 사용하여 추가 정보를 제공하는 것이 좋습니다. 자세한 내용은 이 항목 뒷부분의 [The Upgrade Logger](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) 를 참조하세요.  
  
 관리되는 구현의 경우 Microsoft.VisualStudio.Shell.Interop.11.0.dll interop 어셈블리에서 프로젝트 업그레이드 인터페이스를 사용할 수 있습니다.  
  
 `UpgradeProject` 메서드는 변경으로 인해 이전 버전의 Visual Studio에서 프로젝트가 로드되는 것이 금지되는지 확인할 수 있습니다. 이 경우 메서드가 프로젝트를 호환되지 않음으로 표시합니다. 프로젝트가 호환되지 않음으로 표시되는 방법을 이해하려면 이 항목 앞부분의 [Marking a Project as Incompatible](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) 를 참조하세요. 이 대화 상자를 두 번 표시할 필요가 없으므로 `IVsAppCompat.BreakAssetCompatibility` 메서드를 먼저 호출하는 대신 이 대화 상자가 나타난 다음 `IVsAppCompat.AskForUserConsentToBreakAssetCompat` 메서드를 직접 호출하여 프로젝트를 호환되지 않음으로 표시하는 것이 좋습니다.  
  
 호환성 사용자 환경을 요약하려면 다음 예제를 참조하세요. 프로젝트가 이전 버전에서 만들어졌고 현재 버전에서 업그레이드가 필요하다고 판단한 경우 사용자에게 변경 권한이 있는지 묻는 대화 상자가 표시됩니다. 사용자가 동의하는 경우 프로젝트가 수정 후 로드됩니다. 그런 다음 솔루션을 닫고 이전 버전에서 다시 열면 단방향으로 업그레이드된 프로젝트는 호환되지 않아 로드되지 않습니다. 프로젝트에 업그레이드가 아닌 복구만 필요한 경우 복구된 프로젝트는 두 버전 모두에서 열립니다.  
  
## <a name="marking-a-project-as-incompatible"></a><a name="BKMK_Incompat"></a> 프로젝트를 호환 되지 않음으로 표시  
 프로젝트를 이전 버전의 Visual Studio와 호환되지 않음으로 표시할 수 있습니다.  예를 들어 .NET Framework 4.5 기능을 사용하는 프로젝트를 만든다고 가정합니다. 이 프로젝트는 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]에서 빌드할 수 없으므로 해당 버전에서 로드할 수 없도록 호환되지 않음으로 표시할 수 있습니다.  
  
 호환되지 않는 기능을 추가하는 구성 요소는 프로젝트를 호환되지 않음으로 표시합니다. 구성 요소는 원하는 프로젝트를 나타내는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 인터페이스에 대한 권한이 있어야 합니다.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>프로젝트를 호환되지 않음으로 표시하려면  
  
1. 구성 요소에서 글로벌 서비스 SVsSolution의 `IVsAppCompat` 인터페이스를 가져옵니다.  
  
     자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>를 참조하세요.  
  
2. 구성 요소에서 `IVsAppCompat.AskForUserConsentToBreakAssetCompat`을 호출하고 원하는 프로젝트를 나타내는 `IVsHierarchy` 인터페이스 배열로 전달합니다.  
  
     이 메서드의 서명은 다음과 같습니다.  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     이 코드를 구현하는 경우 프로젝트 호환성 대화 상자가 표시됩니다. 대화 상자에서 사용자에게 지정된 모든 프로젝트를 호환되지 않음으로 표시할 권한이 있는지 묻습니다. 사용자가 동의한 경우 `AskForUserConsentToBreakAssetCompat` 이 `S_OK`를 반환하고 그렇지 않은 경우 `AskForUserConsentToBreakAssetCompat` 은 `OLE_E_PROMPTSAVECANCELLED`를 반환합니다.  
  
    > [!WARNING]
    > 가장 일반적인 시나리오에서는 `IVsHierarchy` 배열에 항목이 하나만 포함됩니다.  
  
3. `AskForUserConsentToBreakAssetCompat` 이 `S_OK`를 반환한 경우 구성 요소는 호환성을 차단하는 변경 내용을 수행하거나 적용합니다.  
  
4. 구성 요소에서 호환되지 않음으로 표시할 각 프로젝트에 대해 `IVsAppCompat.BreakAssetCompatibility` 메서드를 호출합니다. Visual Studio가 레지스트리에서 현재 버전 문자열을 찾게 하는 대신 구성 요소가 매개 변수 `lpszMinimumVersion` 의 값을 특정 최소 버전으로 설정할 수 있습니다. 이 방법을 사용하면 현재 레지스트리 설정을 기준으로 나중에 구성 요소에 대해 실수로 높은 값을 설정하는 위험을 최소화할 수 있습니다. 해당 값이 높게 설정된 경우 Visual Studio에서 프로젝트를 열 수 없습니다.  
  
     이 메서드의 서명은 다음과 같습니다.  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     구성 요소에서 `lpszMinimumVersion` 을 NULL로 설정한 경우 `BreakAssetCompatibility` 메서드가 `IVsAppCompat.GetCurrentDesignTimeCompatVersion` 메서드를 호출하여 Visual Studio의 현재 버전을 나타내는 문자열을 가져옵니다.  
  
     이 메서드의 서명은 다음과 같습니다.  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     그런 다음 BreakAssetCompatibility 메서드는 `IVsHierarchy.SetProperty` 메서드를 호출하여 루트 `VSHPROPID_MinimumDesignTimeCompatVersion` 속성을 이전 단계에서 얻은 버전 문자열 값으로 설정합니다.  
  
     자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>를 참조하세요.  
  
> [!IMPORTANT]
> 프로젝트를 호환됨 또는 호환되지 않음으로 표시하려면 `VSHPROPID_MinimumDesignTimeCompatVersion` 속성을 구현해야 합니다. 예를 들어 프로젝트 시스템에서 MSBuild 프로젝트 파일을 사용하는 경우 프로젝트 파일에 해당 `<MinimumVisualStudioVersion>` 속성 값과 동일한 값을 갖는 `VSHPROPID_MinimumDesignTimeCompatVersion` 빌드 속성을 추가합니다.  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>프로젝트가 호환되지 않는지 확인  
 Visual Studio의 현재 버전과 호환되지 않는 프로젝트는 로드하지 않아야 합니다. 또한 호환되지 않는 프로젝트는 업그레이드하거나 복구할 수 없습니다. 따라서 업그레이드 또는 복구를 고려할 때 한 번, 로드하기 전에 한 번 프로젝트의 호환성을 두 번 확인해야 합니다.  
  
 프로젝트의 비호환성을 탐지하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 메서드를 구현해야 합니다. 프로젝트가 호환되지 않는 경우 `UpgradeProject_CheckOnly` 는 성공 코드 `VS_S_INCOMPATIBLEPROJECT`를 반환하고, `CreateProject` 는 오류 코드 `VS_E_INCOMPATIBLEPROJECT`를 반환해야 합니다. 버전이 지정된 프로젝트의 경우 `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` 대신 `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly`를 구현해야 합니다.  
  
 프로젝트 시스템에 웹, Office(VSTO), Silverlight 또는 이를 기반으로 하는 기타 프로젝트 형식이 있는 경우 버전이 지정된 것으로 간주합니다. 이미 `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` 를 구현한 이전 프로젝트 시스템 및 이미 `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` 를 구현한 버전이 지정된 프로젝트 시스템은 계속 지원됩니다. 이전 버전의 `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` 에는 다음 구현 서명이 있습니다.  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 이 메서드가 `pUpgradeRequired` 를 TRUE로 설정하고 `S_OK`를 반환한 경우 메서드가 업그레이드 플래그를 `VSPUVF_PROJECT_ONEWAYUPGRADE`값으로 설정한 것처럼 결과가 "업그레이드"로 간주됩니다. 자세한 내용은 이 항목 뒷부분에서 설명합니다. 다음 반환 값은 이 이전 메서드를 사용하여 지원되지만 `pUpgradeRequired` 가 TRUE로 설정된 경우에만 가능합니다.  
  
1. `VS_S_PROJECT_SAFEREPAIRREQUIRED`. 이 반환 값은 `pUpgradeRequired` 값을 `VSPUVF_PROJECT_SAFEREPAIR`와 동일한 TRUE로 변환합니다. 자세한 내용은 이 항목의 뒷부분에서 설명합니다.  
  
2. `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. 이 반환 값은 `pUpgradeRequired` 값을 `VSPUVF_PROJECT_UNSAFEREPAIR`와 동일한 TRUE로 변환합니다. 자세한 내용은 이 항목의 뒷부분에서 설명합니다.  
  
3. `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. 이 반환 값은 `pUpgradeRequired` 값을 `VSPUVF_PROJECT_ONEWAYUPGRADE`와 동일한 TRUE로 변환합니다. 자세한 내용은 이 항목의 뒷부분에서 설명합니다.  
  
   `IVsProjectUpgradeViaFactory4` 및 `IVsProjectFlavorUpgradeViaFactory2` 의 새 구현을 사용하면 마이그레이션 형식을 보다 정확하게 지정할 수 있습니다.  
  
> [!NOTE]
> `UpgradeProject_CheckOnly` 에 대한 후속 호출에서 사용할 수 있도록 `CreateProject`메서드를 통한 호환성 검사 결과를 캐시할 수 있습니다.  
  
 예를 들어 `UpgradeProject_CheckOnly` SP1 프로젝트 시스템용으로 작성된 `CreateProject` 및 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 메서드가 프로젝트 파일을 검사하여 `<MinimumVisualStudioVersion>` 빌드 속성이 "11.0"인 것을 발견한 경우 Visual Studio 2010 SP1에서 프로젝트를 로드하지 않습니다. 또한 **솔루션 탐색기** 에 프로젝트가 "호환되지 않음"으로 표시되며 로드되지 않습니다.  
  
## <a name="the-upgrade-logger"></a><a name="BKMK_UpgradeLogger"></a> 업그레이드로 거  
 `IVsProjectUpgradeViaFactory::UpgradeProject` 에 대한 호출에는 `IVsUpgradeLogger` 로거가 포함되어 있으며 이 로거는 프로젝트 시스템 및 버전에서 문제 해결을 위한 자세한 업그레이드 추적을 제공하는 데 사용됩니다. 경고나 오류가 기록된 경우 Visual Studio는 업그레이드 보고서를 표시합니다.  
  
 업그레이드 로거를 작성할 때는 다음 지침을 고려합니다.  
  
- Visual Studio는 모든 프로젝트 업그레이드를 완료한 후 플러시를 호출합니다. 프로젝트 시스템에서 호출하지 마세요.  
  
- LogMessage 함수에는 다음 ErrorLevel이 있습니다.  
  
  - 0 - 추적하려는 모든 정보  

  - 1 - 경고  

  - 2 - 오류  

  - 3 - 보고서 포맷터 프로젝트가 업그레이드되면 "Converted"라는 단어(지역화되지 않음)가 한 번 기록됩니다.  
  
- 프로젝트에 복구 또는 업그레이드가 필요하지 않은 경우 Visual Studio는 UpgradeProject_CheckOnly 또는 UpgradeProjectFlavor_CheckOnly 메서드 실행 중 프로젝트 시스템에서 경고 또는 오류를 기록한 경우에만 로그 파일을 생성합니다.
