---
title: '방법: 소스 제어 플러그인 설치 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c0ac87aec3d6ac2532909772238e020e33bf78f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707988"
---
# <a name="how-to-install-a-source-control-plug-in"></a>방법: 소스 제어 플러그인 설치
소스 제어 플러그인을 만들려면 다음 세 단계가 포함됩니다.

1. 이 설명서의 소스 제어 플러그인 API 참조 섹션에 정의된 함수를 사용하여 DLL을 만듭니다.

2. 소스 제어 플러그인 API 정의 함수를 구현합니다. 호출할 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 플러그인에서 인터페이스와 대화 상자를 사용할 수 있도록 합니다.

3. 적절한 레지스트리 항목을 만들어 DLL을 등록합니다.

## <a name="integration-with-visual-studio"></a>Visual Studio와의 통합
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]는 소스 제어 플러그인 API를 준수하는 소스 제어 플러그인을 지원합니다.

### <a name="register-the-source-control-plug-in"></a>소스 제어 플러그인 등록
 실행 중인 통합 개발 환경(IDE)이 소스 제어 시스템에 호출하려면 먼저 API를 내보내는 소스 제어 플러그인 DLL을 찾아야 합니다.

#### <a name="to-register-the-source-control-plug-in-dll"></a>소스 제어 플러그인 DLL을 등록하려면

1. 회사 이름 하위 키를 지정하는 **SOFTWARE** 하위 키의 **HKEY_LOCAL_MACHINE** 키 아래에 제품 이름 하위 키 다음에 두 개의 항목을 추가합니다. 패턴은 **HKEY_LOCAL_MACHINE\SOFTWARE\\\<회사 \\ \<이름>\\ \<제품 이름>항목>**  =  *값입니다.* 두 항목을 항상 **SCCServerName** 및 **SCCServerPath.** 각각은 일반 문자열입니다.

    예를 들어 회사 이름이 Microsoft이고 소스 제어 제품이름이 SourceSafe인 경우 이 레지스트리 경로는 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SourceSafe**입니다. 이 하위 키에서 첫 번째 항목인 **SCCServerName은**제품 이름을 지정하는 사용자가 읽을 수 있는 문자열입니다. 두 번째 항목인 **SCCServerPath는**IDE가 연결해야 하는 소스 제어 플러그인 DLL의 전체 경로입니다. 다음은 샘플 레지스트리 항목을 제공합니다.

   |샘플 레지스트리 항목|샘플 값|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\소프트웨어\마이크로소프트\소스세이프\SCCServerName|Microsoft Visual SourceSafe|
   |HKEY_LOCAL_MACHINE\소프트웨어\마이크로소프트\소스세이프\SCCServerPath|*c:\vss\win32\sscc.dll*|

   > [!NOTE]
   > SCCServerPath는 SourceSafe 플러그인의 전체 경로입니다. 소스 제어 플러그인은 다른 회사 및 제품 이름을 사용하지만 동일한 레지스트리 입력 경로를 사용합니다.

2. 다음 선택적 레지스트리 항목을 사용하여 소스 제어 플러그인의 동작을 수정할 수 있습니다. 이러한 항목은 **SccServerName** 및 **SccServerPath**.

   - 소스 제어 플러그 인이 **의 플러그인 선택 목록에** 나타나지 않도록 하려면 **HideInVisualStudio레지스트리** 항목을 사용할 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]수 있습니다. 이 항목은 소스 제어 플러그인으로의 자동 전환에도 영향을 미칩니다. 이 항목에 사용할 수 있는 한 가지 방법은 소스 제어 플러그인을 대체하는 소스 제어 패키지를 제공하지만 사용자가 소스 제어 플러그인을 사용하여 소스 제어 패키지로 쉽게 마이그레이션할 수 있도록 하려는 경우입니다. 소스 제어 패키지를 설치하면 이 레지스트리 항목을 설정하여 플러그인을 숨깁니다.

      **HideInVisualStudio는** DWORD 값이며 플러그인을 숨기기 위해 *1로* 설정하거나 *0으로* 설정되어 플러그인을 표시합니다. 레지스트리 항목이 나타나지 않으면 기본 동작은 플러그인을 표시하는 것입니다.

   - **DisableSccManager** 레지스트리 항목을 사용 하 고 비활성화 하거나 일반적으로 **파일** > **소스** 제어 하위 메뉴 아래에 나타나는 **시작 \<소스 제어 서버>** 메뉴 옵션을 숨길 수 있습니다. 이 메뉴 옵션을 선택하면 [SccRunScc](../../extensibility/sccrunscc-function.md) 함수가 호출됩니다. 소스 제어 플러그인은 외부 프로그램을 지원하지 않을 수 있으므로 **시작** 메뉴 옵션을 사용하지 않도록 설정하거나 숨길 수도 있습니다.

      **DisableSccManager는** DWORD 값이며 ** \<시작 소스 제어 서버>** 메뉴 옵션을 활성화하고 메뉴 옵션을 비활성화하려면 *1로* 설정하고 메뉴 옵션을 숨기려면 *2로* 설정합니다. *0* 이 레지스트리 항목이 나타나지 않으면 기본 동작은 메뉴 옵션을 표시하는 것입니다.

   | 샘플 레지스트리 항목 | 샘플 값 |
   | - |--------------|
   | HKEY_LOCAL_MACHINE\소프트웨어\마이크로소프트\소스세이프\하이데인비주얼스튜디오 | 1 |
   | HKEY_LOCAL_MACHINE\SOFTWARE\마이크로소프트\소스 세이프\비활성화SccManager | 1 |

3. **소프트웨어** 하위 키의 **HKEY_LOCAL_MACHINE** 키 아래에 하위 키인 **SourceCodeControlProvider를**추가합니다.

    이 하위 키에서 레지스트리 항목 **ProviderRegKey는** 1 단계에서 레지스트리에 배치 한 하위 키를 나타내는 문자열로 설정 됩니다. 패턴은 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\ProviderRegKey** = *\\ SOFTWARE<\> \\ 회사\>이름<제품 이름입니다.*

    다음은 이 하위 키에 대한 샘플 콘텐츠입니다.

   |레지스트리 항목|샘플 값|
   |--------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\소스코드제어제공자\공급자RegKey|소프트웨어\마이크로소프트\소스 세이프|

   > [!NOTE]
   > 소스 제어 플러그인은 동일한 하위 키 및 항목 이름을 사용하지만 값은 다릅니다.

4. **SourceCodeControlProvider** 하위 키 아래에 **InstalledSCCProvider라는** 하위 키를 만든 다음 해당 하위 키 아래에 하나의 항목을 배치합니다.

    이 항목의 이름은 공급자의 사용자가 읽을 수 있는 이름(SCCServerName 항목에 대해 지정된 값과 동일)이며 값은 다시 한 번 1단계에서 만든 하위 키입니다. 패턴은 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControlProvider\InstalledSCC<\\ 표시\>이름** = *\\ 소프트웨어\> \\<회사\>이름<제품 이름*.

    다음은 그 예입니다.

   |샘플 레지스트리 항목|샘플 값|
   |---------------------------|------------------|
   |HKEY_LOCAL_MACHINE\SOFTWARE\소스코드제어제공자\설치SCC제공자\마이크로소프트 비주얼 소스세이프|소프트웨어\마이크로소프트\소스 세이프|

   > [!NOTE]
   > 이러한 방식으로 여러 소스 제어 플러그인이 등록될 수 있습니다. 이렇게 하면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 설치된 모든 소스 제어 플러그인 API 기반 플러그인을 찾습니다.

## <a name="how-an-ide-locates-the-dll"></a>IDE가 DLL을 찾는 방법
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에는 소스 제어 플러그인 DLL을 찾는 두 가지 방법이 있습니다.

- 기본 소스 제어 플러그인을 찾아 자동으로 연결합니다.

- 사용자가 선택한 모든 등록된 소스 제어 플러그인을 찾습니다.

  첫 번째 방법으로 DLL을 찾으려면 IDE는 항목 **providerRegKey에**대한 **HKEY_LOCAL_MACHINE\Software\SourceCodeControl 공급자** 하위 키 에서 찾습니다. 이 항목의 값은 다른 하위 키를 가리킵니다. 그런 다음 IDE는 **HKEY_LOCAL_MACHINE**아래의 두 번째 하위 키에서 **SccServerPath라는** 항목을 찾습니다. 이 항목의 값은 IDE를 DLL로 가리킵니다.

> [!NOTE]
> IDE는 상대 경로(예: *.\NewProvider.DLL)에서*DLL을 로드하지 않습니다. DLL에 대한 전체 경로를 지정해야 합니다(예: *c:\Providers\NewProvider.DLL).* 이렇게 하면 무단 또는 가장된 플러그인 DLL의 로드를 방지하여 IDE의 보안이 강화됩니다.

 두 번째 방법으로 DLL을 찾으려면 IDE는 모든 항목에 대해 **HKEY_LOCAL_MACHINE\Software\SourceCodeControlProvider\InstalledSCCProviders** 하위 키 아래에 표시됩니다. 각 항목에는 이름과 값이 있습니다. IDE는 사용자에게 이러한 이름 목록을 표시합니다. 사용자가 이름을 선택하면 IDE는 하위 키를 가리키는 선택한 이름의 값을 찾습니다. IDE는 **HKEY_LOCAL_MACHINE**아래의 하위 키에서 **SccServerPath라는** 항목을 찾습니다. 해당 항목의 값은 IDE를 올바른 DLL로 가리킵니다.

 소스 제어 플러그인은 DLL을 찾는 두 가지 방법을 모두 지원해야 하며, 따라서 **공급자RegKey를**설정하여 이전 설정을 덮어쓰기합니다. 더 중요한 것은 사용자가 사용할 소스 제어 플러그인을 선택할 수 있도록 **InstalledSccProviders** 목록에 자신을 추가해야 한다는 것입니다.

> [!NOTE]
> **HKEY_LOCAL_MACHINE** 키가 사용되므로 지정된 컴퓨터에서 기본 소스 제어 플러그인으로 하나의 소스 제어 플러그인만 등록할 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 수 있습니다(그러나 사용자가 특정 솔루션에 실제로 사용할 소스 제어 플러그인을 결정할 수 있음). 설치 과정에서 소스 제어 플러그인이 이미 설정되어 있는지 확인합니다. 그렇다면 사용자에게 새 소스 제어 플러그인을 기본값으로 설정할지 여부를 물어봅니다. 제거 하는 동안 **HKEY_LOCAL_MACHINE\SOFTWARE\SourceCodeControl.의**모든 소스 제어 플러그인에 공통된 다른 레지스트리 하위 키를 제거 하지 마십시오. 특정 SCC 하위 키만 제거합니다.

## <a name="how-the-ide-detects-version-1213-support"></a>IDE가 버전 1.2/1.3 지원을 감지하는 방법
 플러그인이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어 플러그인 API 버전 1.2 및 1.3 기능을 지원하는지 여부를 어떻게 감지합니까? 고급 기능을 선언하려면 소스 제어 플러그인이 해당 기능을 구현해야 합니다.

 먼저 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [SccGetVersion을](../../extensibility/sccgetversion-function.md)호출하여 반환되는 값을 확인합니다. 1.2보다 크거나 같아야 합니다.

 다음으로 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] `lpSccCaps` [SccInitialize에서](../../extensibility/sccinitialize-function.md)인수를 검사하여 특정 새 기능이 지원되는지 여부를 결정합니다.

 이러한 조건이 모두 충족되면 버전 1.2 및 1.3에서 지원되는 새 함수를 호출할 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 시작](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
