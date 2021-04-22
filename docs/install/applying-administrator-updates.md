---
title: Microsoft Endpoint Configuration Manager를 사용하여 Visual Studio에 관리자 업데이트 적용
titleSuffix: ''
description: Visual Studio에 관리자 업데이트를 적용하는 방법을 알아봅니다.
ms.date: 04/16/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 9a3fdb28-db3d-4970-bc17-7417a985f0fb
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d7d2950b9495846693d5edee7790b8611cbca170
ms.sourcegitcommit: 367a2d9df789aa617abaa09b0cd0a18db7357d0c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107800797"
---
# <a name="applying-administrator-updates-that-use-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager를 사용하는 관리자 업데이트 적용

이 문서에서는 Visual Studio 관리자 업데이트의 다양한 유형 및 특징을 설명합니다. 아래에서는 조직 전체에 배포해야 하는 시기 및 방법, 사용 가능한 구성 옵션, 보고서를 확인하고 문제를 해결하는 방법에 대한 정보를 찾을 수 있습니다. 관리자 업데이트를 사용하기 위한 필수 구성 요소에 대한 자세한 내용은 [관리자 업데이트 사용](../install/enabling-administrator-updates.md)을 참조하세요. 관리자 업데이트는 컴퓨터에 Visual Studio가 이미 설치되어 있다고 가정합니다. 관리자 업데이트를 적용해도 새 설치가 시작되지는 않습니다.

## <a name="understanding-visual-studio-administrator-updates"></a>Visual Studio 관리자 업데이트 이해 

Microsoft 카탈로그 및 WSUS에서 사용하도록 Microsoft 업데이트에 게시되는 Visual Studio 관리자 업데이트 패키지에는 Configuration Manager가 Visual Studio 업데이트를 다운로드하고 클라이언트 머신에 배포하는 데 필요한 정보가 포함되어 있습니다. 또한 IT 관리자가 조직 전체에 배포할 업데이트를 결정하는 데 필요한 정보가 포함되어 있습니다. 이 패키지를 사용하여 네트워크 레이아웃을 쉽게 유지 관리할 수도 있습니다. Visual Studio 관리자 업데이트 패키지에는 제품을 새로 설치하는 데 충분한 정보가 포함되어 있지 않으며, Content Delivery Network에 게시된 실제 제품 이진 파일이 포함되지 않습니다. Visual Studio 관리자 업데이트는 일반 Visual Studio 업데이트와 마찬가지로 누적됩니다. 제품 버전 번호가 더 높고 릴리스 날짜가 더 늦은 Visual Studio 업데이트는 더 빠르고 더 낮은 버전의 상위 집합이라고 가정할 수 있습니다. 

Visual Studio 관리자 업데이트는 지원되는 Visual Studio 서비스 버전에 적용됩니다. 특정 기간 동안 지원되는 Visual Studio 서비스 기준에 대한 자세한 내용은 [Visual Studio 제품 수명 주기 및 서비스](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)를 참조하세요. 지원되는 Visual Studio 서비스 기준은 모두 안전하게 유지됩니다.  

## <a name="types-and-characteristics-of-administrator-updates"></a>관리자 업데이트의 유형 및 특징 

Visual Studio에는 다음과 같은 세 가지 유형의 관리자 업데이트가 있습니다.

* **보안 업데이트** 는 모든 Visual Studio 버전(예: Enterprise, Professional, Community 등)에 적용할 수 있으며, 구체적으로 대상이 지정되고 호환되는 서비스 수준 변경 내용을 포함합니다. 보안 업데이트는 클라이언트를 더 높은 부 버전으로 업데이트하지 않습니다. 이미 특정 부 버전 수준에 있는 클라이언트에게 보안 취약성에 대한 수정을 제공하도록 설계된 것입니다. 보안 업데이트에는 하나 이상의 보안 수정이 있지만 보안 수정 사항은 클라이언트 컴퓨터에 설치된 구성 요소 또는 워크로드에 있을 수도 있고 그렇지 않을 수도 있습니다. 예를 들어 .NET 구성 요소의 보안 취약성을 수정할 수 있으며, 업데이트가 보안 업데이트로 레이블이 지정될 수 있지만 C++ 구성 요소만 설치된 클라이언트 컴퓨터에는 실제로 의미 있는 영향을 주지 않습니다. 보안 업데이트에 다른 안정성 수정 또는 기타 필수 구성 요소 업데이트가 포함될 수도 있습니다. 보안 업데이트는 [MUC(Microsoft 업데이트 카탈로그)](https://www.catalog.update.microsoft.com/Home.aspx) 및 [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) 모두에 게시되고 ‘보안 업데이트’로 분류됩니다.
 
* **기능 업데이트** 를 사용하면 IT 관리자가 조직의 컴퓨터를 더 최신 부 버전의 Visual Studio 2019로 업데이트할 수 있습니다. 기능 업데이트는 Enterprise, Professional, Build Tools SKU와 같이 일반적으로 엔터프라이즈에서 사용되는 Visual Studio 버전에만 적용됩니다. 모든 기능 업데이트는 Microsoft 업데이트 카탈로그에 ‘기능 팩’으로 게시되며, 필요한 경우 수동으로 [Microsoft 업데이트 카탈로그에서 Configuration Manager로 가져올](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog) 수 있습니다. 기능 업데이트는 누적되며 추가 품질 수정 및 이전 보안 수정을 포함합니다. 서비스 기준을 유지하도록 클라이언트 컴퓨터를 구성하고 기능 업데이트가 특정 클라이언트에 배달되지 않도록 구성하는 방법에 대한 지침은 아래 [구성 옵션 섹션](#understanding-configuration-options)을 참조하세요. 

* **품질 업데이트** 는 일반적으로 엔터프라이즈에서 사용되는 Visual Studio 버전에만 적용되며, 구체적으로 대상이 지정되고 호환되는 서비스 수준 변경 내용을 포함합니다. 품질 업데이트는 클라이언트를 더 높은 부 버전으로 업데이트하지 않습니다. 이미 특정 부 버전 수준에 있는 클라이언트에 성능 및 안정성 수정 또는 기타 필수 구성 요소 업데이트를 제공하도록 설계된 것입니다. 품질 업데이트는 보안 업데이트와 함께 누적되므로 보안 수정이 이미 별도로 릴리스된 경우에만 보안 수정이 포함됩니다. 품질 업데이트는 Microsoft 업데이트 카탈로그에 ‘업데이트’로 게시되며 필요에 따라 수동으로 [Configuration Manager로 가져올](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog) 수도 있습니다.

### <a name="decoding-the-titles-of-administrator-updates"></a>관리자 업데이트 제목 해석

각 관리자 업데이트의 제목에는 적용 가능한 버전 범위와 업데이트의 결과 버전이 모두 설명되어 있습니다.예제:

::: moniker range="vs-2017"

* “보안 업데이트”로 분류된 **Visual Studio 2017 버전 15.9.0~15.9.35 업데이트** 는 클라이언트에서 모든 Visual Studio 2017 에디션의 버전 15.9.0~15.9.35에 적용되며 해당 클라이언트 에디션을 버전 15.9.35로 업데이트합니다.

* “기능 팩”으로 분류된 **Visual Studio 2017 버전 15.0.0~15.9.0 업데이트** 는 클라이언트에서 엔터프라이즈용으로 허가된 Visual Studio 2017 에디션의 전체 제품 버전 범위 15.0.0~15.9.0에 적용되며 해당 클라이언트 에디션을 버전 15.9.0으로 업데이트합니다. 이 기능 팩을 적용하면 기본적으로 클라이언트에서 보안 업데이트를 받을 수 있습니다. 

* 단순히 “업데이트”로 분류된 **Visual Studio 2017 버전 15.9.0~15.9.37 업데이트** 는 클라이언트에서 엔터프라이즈용으로 허가된 Visual Studio 2017 에디션의 버전 15.9.0~15.9.37에 적용되며 해당 클라이언트 에디션을 버전 15.9.37로 업데이트합니다. 

::: moniker-end

::: moniker range="vs-2019"

* “보안 업데이트”로 분류된 **Visual Studio 2019 버전 16.7.0~16.7.12 업데이트** 는 클라이언트에서 모든 Visual Studio 2019 에디션의 버전 16.7.0~16.7.12에 적용되며 해당 클라이언트 에디션을 버전 16.7.12로 업데이트합니다.  

* “기능 팩”으로 분류된 **Visual Studio 2019 버전 16.0.0~16.9.0 업데이트** 는 클라이언트에서 엔터프라이즈용으로 허가된 Visual Studio 2019 에디션의 전체 제품 버전 범위 16.0.0~16.9.0에 적용되며 이전 서비스 기준을 유지하도록 구성되지 않은 클라이언트 에디션을 버전 16.9.0으로 업데이트합니다. 

* 단순히 “업데이트”로 분류된 **Visual Studio 2019 버전 16.8.0~16.8.7 업데이트** 는 클라이언트에서 엔터프라이즈용으로 허가된 Visual Studio 2019 에디션의 버전 16.8.0~16.8.7에 적용되며 해당 클라이언트 에디션을 버전 16.8.7로 업데이트합니다. 

::: moniker-end

## <a name="using-configuration-manager-to-deploy-visual-studio-updates"></a>Configuration Manager를 사용하여 Visual Studio 업데이트 배포

### <a name="understanding-configuration-options"></a>구성 옵션 이해

Visual Studio 관리자 업데이트를 조직의 배포 기본 설정 및 요구 사항에 부합하도록 설정하는 데 사용할 수 있는 몇 가지 구성 옵션이 있습니다. 가장 일반적인 구성 옵션은 다음과 같습니다. 지원되는 모든 관리자 업데이트 동작의 전체 목록은 [명령줄 매개 변수를 사용하여 Visual Studio 설치](../install/use-command-line-parameters-to-install-visual-studio.md)를 참조하고 “업데이트” 작업에 해당하는 동작에만 주목하세요.

* **[관리자 업데이트 옵트인](../install/enabling-administrator-updates.md#encoding-administrator-intent-on-the-client-machines)** : 클라이언트 머신에서 관리자 업데이트를 받으려면 이 레지스트리 키가 필요합니다. 이것은 시스템 수준 키입니다. 즉, 시스템에 설치된 Visual Studio의 모든 인스턴스에 적용됩니다. 
 
* **Visual Studio 사용자 옵트아웃**: Visual Studio 사용자는 수신하는 Visual Studio 관리자 업데이트의 ‘옵트아웃’에 대한 별도의 머신 전체의 **AdministratorUpdatesOptOut** 레지스트리 키를 사용할 수 있습니다. 이 키의 목적은 Visual Studio 사용자가 머신에 업데이트를 자동으로 적용하는 것을 제어할 수 있도록 하는 것입니다. 클라이언트 컴퓨터에서 관리자 업데이트를 차단하도록 구성하려면 **AdministratorUpdatesOptOut** REG_DWORD 키를 **1** 로 설정합니다. 이 키가 없거나 설정된 값이 **0** 이면 Visual Studio 사용자가 Visual Studio에 대한 관리자 업데이트를 받으려는 것입니다.

    사용자 기본 설정을 인코딩하는  **AdministratorUpdatesOptOut** 키는 IT 관리자 의도를 인코딩하는  **AdministratorUpdatesEnabled** 키보다 우선 적용됩니다.  **AdministratorUpdatesOptOut** 을  **1** 로 설정하면  **AdministratorUpdatesEnabled** 키도 **1** 로 설정된 경우에도 업데이트는 클라이언트에서 차단됩니다.이 작업은 IT 관리자가 개발자에 의해 옵트아웃된 항목을 액세스 및 모니터링하고 두 당사자가 누구의 요구 사항이 더 중요한지 논의할 수 있다고 가정합니다.IT 관리자는 필요한 경우 언제든지 키를 변경할 수 있습니다.
 
* **업데이트된 제품 비트의 위치**: 대부분의 경우 클라이언트 컴퓨터는 인터넷을 사용하여 Microsoft CDN을 통해 업데이트된 제품 비트를 다운로드합니다. 이 시나리오에서는 클라이언트 컴퓨터가 인터넷에 액세스할 수 있어야 합니다. 그러나 일부 기업은 클라이언트 컴퓨터가 내부 네트워크 레이아웃 위치에서만 비트를 설치하고 업데이트하도록 제한합니다. 내부 네트워크 위치에 있는 업데이트된 비트를 사용하여 관리자 업데이트를 적용할 수 있도록 하려면 관리자 업데이트를 성공적으로 배포하기 전에 다음 조건이 충족되어야 합니다. 

  - 클라이언트 머신은 특정 시점에 해당 네트워크 레이아웃 위치에서 부트스트래퍼를 이미 실행했어야 합니다. 이상적으로 원래 클라이언트 설치는 네트워크 레이아웃의 부트스트래퍼를 사용하여 발생하지만, 동일한 네트워크 위치에서 업데이트된 부트스트래퍼를 사용하여 업데이트를 설치할 수도 있습니다. 이러한 작업 중 하나는 클라이언트 머신에서 해당 특정 레이아웃 위치와의 연결을 포함합니다.   
  - 네트워크 레이아웃 위치(클라이언트가 연결되는 위치)는 관리자 업데이트를 배포하려는 [업데이트된 제품 비트를 포함하도록 업데이트](../install/update-a-network-installation-of-visual-studio.md)해야 합니다. 

::: moniker range="vs-2019"

* **서비스 기준 유지**: 위에서 설명한 대로 관리자 기능 업데이트는 Visual Studio 설치를 더 최신 부 버전의 제품으로 업데이트합니다. 그러나 Visual Studio 개발자가 안정적이고 안전한 서비스 기준 수준을 유지해야 하고 머신을 더 최신 부 버전으로 업데이트하는 시기를 제어하기를 원하는 경우도 있습니다. 서비스 기준을 유지하고 전송된 원치 않는 관리자 기능 업데이트를 무시하도록 클라이언트 머신을 구성하려면 **BaselineStickinessVersions2019** Reg_SZ 데이터 값을 만들어 클라이언트 머신이 맞추고 유지해야 하는 기본 설정 기준을 나타내는 문자열로 설정해야 합니다. 이 문자열은 **16.7.0** 과 같은 허용되는 서비스 기준 버전을 포함할 수 있습니다.  

     `BaselineStickinessVersions2019` 레지스트리 값의 형식이 잘못된 경우 모든 관리자 기능 업데이트가 머신에 설치되지 않도록 차단됩니다. [Visual Studio 기능 업데이트 지원 기간](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)에 주의하세요. 또한 `BaselineStickinessVersions2019` 키의 존재 여부 또는 이 키의 값과 관계없이 기술적으로는 수명 주기 끝에 도달한 관리자 기능 업데이트를 적용할 수 있지만, 지원이 종료되어 안전하지 않을 수 있으므로 권장되지 않습니다.

::: moniker-end

* **Visual Studio가 사용 중인 경우에도 업데이트를 강제로 실행**: 업데이트를 설치하기 전에 Visual Studio를 닫아야 합니다. Visual Studio가 열려 있거나 사용 중인 경우 업데이트 설치가 중단됩니다. Visual Studio를 닫도록 하는 간편한 방법 한 가지는 컴퓨터를 다시 부팅한 후 즉시 업데이트를 적용하도록 확인 관리자를 구성하는 것입니다. `--force` 매개 변수를 사용하여 Visual Studio를 강제로 종료할 수도 있습니다. Visual Studio를 강제로 닫으면 작업이 손실될 수 있으므로 주의해서 사용해야 합니다. 기본 시스템 컨텍스트에서 관리자 업데이트를 실행하면 `–-force` 플래그가 무시되므로 사용자 컨텍스트에서 실행되도록 관리자 업데이트를 구성해야 합니다.

### <a name="methods-for-configuring-an-administrator-update"></a>관리자 업데이트를 구성하는 방법

관리자 업데이트를 구성하는 세 가지 주요 방법으로는 레지스트리 키, 클라이언트 컴퓨터의 구성 파일, Configuration Manager 배포 패키지 자체의 수정이 있습니다.   

* **레지스트리 키**: 관리자 업데이트는 [엔터프라이즈 배포에 대한 기본값 설정](../install/set-defaults-for-enterprise-deployments.md)에 설명된 대로 표준 Visual Studio 위치 중 하나에서 특정 레지스트리 키를 찾습니다. 레지스트리 키로 제어되는 옵션은 **AdministratorUpdatesOptOut** Reg_DWORD, **AdministratorUpdatesOptOut** Reg_DWORD, **BaselineStickinessVersions2019** Reg_SZ와 같은 항목입니다. 레지스트리 키를 만들고 값을 설정하려면 클라이언트 컴퓨터에 대한 관리자 액세스 권한이 필요합니다. 
 
* **구성 파일**: 일부 설정은 클라이언트 컴퓨터에서 선택적 구성 파일에 보존될 수 있으며, 이 파일을 한 번만 설정하면 이후의 모든 관리자 업데이트에 적용될 수 있습니다. 구성 파일 접근 방식은 레지스트리 키와 같이 작동하며 컴퓨터 수준에서 적용됩니다. 즉, 클라이언트 컴퓨터에 설치된 모든 Visual Studio 설치에 적용됩니다. 구성 파일의 표준 위치는 `C:\ProgramData\Microsoft\VisualStudio\updates.config`입니다. 그러나 다른 위치를 사용하여 파일을 저장하려는 경우 **UpdateConfigurationFile** 이라는 Reg_SZ 레지스트리 키를 만들고 값을 구성 파일의 경로로 설정하면 됩니다. 이 레지스트리 키는 [엔터프라이즈 배포에 대한 기본값 설정](../install/set-defaults-for-enterprise-deployments.md)에 설명된 Visual Studio 레지스트리 위치 중 하나에 배치할 수 있습니다. 사용자 지정 구성 파일 위치에 대한 레지스트리 값을 추가하면 레지스트리가 해당 파일을 찾습니다. 파일이 없으면 예외가 throw되고 업데이트가 실패합니다.    
 
     구성 파일(JSON 형식)은 Visual Studio 설치 관리자에 전달할 수 있는 더 많은 스위치를 지정하는 쉼표로 구분된 문자열의 배열인 `installerUpdateArgs` 옵션을 지원합니다. 파일의 내용에 잘못된 필드 또는 지원되지 않는 옵션이 포함되어 있으면 업데이트가 실패합니다. 자세한 내용은 [명령줄 매개 변수를 사용하여 Visual Studio 설치](../install/use-command-line-parameters-to-install-visual-studio.md)를 참조하세요.
 
   다음은 구성 파일 예제입니다. 

   ```
   “installerUpdateArgs” : [“--quiet”, “--noWeb”], 

   “checkPendingReboot” :  “true” 
   ```

* **SCCM에서 수동으로 관리자 업데이트 패키지 업데이트**: SCCM의 개별 관리자 업데이트 패키지에 대한 명령줄 매개 변수를 수동으로 수정할 수도 있습니다.

## <a name="verification-reports-and-troubleshooting-error-codes"></a>확인, 보고서 및 오류 코드 문제 해결

### <a name="determining-that-visual-studio-was-updated"></a>Visual Studio가 업데이트되었는지 확인

다음 방법 중 하나를 사용하여 관리자 업데이트가 올바르게 설치되었는지 확인할 수 있습니다. 

* 클라이언트 컴퓨터에서 Visual Studio 2019를 시작하고  **도움말** > **정보** 를 선택하여 버전 번호가 원하는 업데이트 제목의 마지막 숫자와 일치하는지 확인합니다. 

* 클라이언트 컴퓨터의 **vswhere** 도구를 사용하여 컴퓨터에 설치된 다양한 Visual Studio 버전을 식별합니다. 자세한 내용은 [Visual Studio 인스턴스 검색 및 관리 도구](../install/tools-for-managing-visual-studio-instances.md)를 참조하세요. 

* 각 관리 업데이트 시도마다 클라이언트 컴퓨터의 `%temp%` 디렉터리에 업데이트 작업의 진행 상태를 캡처하는 여러 로그 파일이 생성됩니다.폴더를 날짜 기준으로 정렬하여 관리 업데이트, 부트스트래퍼, Visual Studio 설치 관리자 및 설치 엔진 각각에 대해  `dd_updatedriver`, `dd_bootstrapper`, `dd_client`,  `dd_setup` 으로 시작하는 파일을 찾습니다.이러한 로그 파일에 업데이트가 성공적으로 적용되었음을 나타내는 0이 포함되어 있는지 확인합니다. 이러한 로그 파일을 사용하여 구성 파일이 사용되고 있는지 확인할 수도 있습니다. 자세한 내용은 [Visual Studio 로그 수집 도구](https://www.microsoft.com/download/details.aspx?id=12493)를 참조하세요.     

### <a name="error-codes-and-conditions"></a>오류 코드 및 조건

>[!IMPORTANT]
> 업데이트를 설치하기 전에 반드시 Visual Studio를 닫아야 합니다. Visual Studio가 열려 있거나 사용 중인 경우 업데이트 설치가 취소됩니다.

관리 업데이트는 다음과 같은 반환 코드를 반환할 수 있습니다.  

| 오류 코드 | 정의 |
|--|:-|
| 0 | 관리 업데이트가 설치되었습니다. |
| 1001 | Visual Studio 설치 관리자 또는 관련 설치 프로세스가 실행 중입니다. 업데이트가 적용되지 않았습니다. |
| 1002 | Visual Studio 설치 관리자가 일시 중지되었습니다. 업데이트가 적용되지 않았습니다. |
| 1003 | Visual Studio가 실행 중입니다. 업데이트가 적용되지 않았습니다. 이 조건은 `--force` 플래그를 사용하여 재정의할 수 있습니다. |
| 1004 | 인터넷이 검색되지 않습니다.업데이트가 업데이트된 파일이 저장되어 있는 인터넷 위치에 연결할 수 없습니다. 업데이트가 적용되지 않았습니다. |
| 1005 |  **AdministratorUpdatesEnabled** 레지스트리 값이 **0** 으로 설정되었거나 설정된 값이 없습니다. 업데이트가 적용되지 않았습니다. |
| 1006 |  **AdministratorUpdatesOptOut** 레지스트리 값이 **1** 로 설정되어 있습니다. 업데이트가 적용되지 않았습니다. 이 키는 관리자가 업데이트하지 않아야 하는 클라이언트 컴퓨터를 위한 것입니다. |
| 1007 | Visual Studio 설치 관리자가 설치되어 있지 않습니다. |
| 1008 | **BaselineStickinessVersions2019** 레지스트리 값이 읽을 수 있는 형식이 아닙니다. 이 레지스트리 값은 **All** 또는 빌드 번호가 0으로 설정된 유효한 버전(예: X.Y.0)을 포함해야 합니다. |
| 3010 | 시스템을 다시 부팅해야 합니다.업데이트가 적용되었을 수도 있고 적용되지 않았을 수도 있습니다. 컴퓨터를 다시 부팅하고 업데이트를 다시 시도하세요. |
| 기타 | 업데이트를 적용하는 동안 오류가 발생했습니다.업데이트가 적용되지 않았습니다. |

클라이언트 오류 코드의 전체 목록은 [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)를 참조하세요. 

## <a name="feedback-and-support"></a>피드백 및 지원
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

다음 방법을 사용하여 Visual Studio 관리자 업데이트에 대한 피드백을 제공하거나 업데이트에 영향을 주는 문제를 보고할 수 있습니다.
* [Visual Studio 설치 및 업그레이드 문제 해결](../install/troubleshooting-installation-issues.md) 참고 자료를 참조합니다.
* [Visual Studio 설치 Q&A 포럼](https://docs.microsoft.com/answers/topics/vs-setup.html)에서 커뮤니티에 질문하세요.
* [Visual Studio 지원 페이지](https://visualstudio.microsoft.com/vs/support/)로 이동하여 문제가 FAQ에 등록되어 있는지 확인합니다.  채팅 도움말의 [지원 링크](https://visualstudio.microsoft.com/vs/support/#talktous) 단추를 선택할 수도 있습니다.
* 관리자 업데이트 적용 경험에 대해 Visual Studio 팀에 [기능 피드백을 제공하거나 문제를 보고](https://aka.ms/vs/wsus/feedback)하세요.
* 조직의 Microsoft 담당 기술 계정 관리자에게 문의합니다.

## <a name="see-also"></a>참조
* [관리자 업데이트 사용](../install/enabling-administrator-updates.md)    
* [Visual Studio 관리자 가이드](../install/visual-studio-administrator-guide.md)
* [Visual Studio 제품 수명 주기 및 서비스](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Visual Studio 2019 릴리스 정보](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Visual Studio 2017 릴리스 정보](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio 설치](../install/install-visual-studio.md)
* [명령줄 매개 변수를 사용하여 Visual Studio 설치](../install/use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 인스턴스 검색 및 관리 도구](../install/tools-for-managing-visual-studio-instances.md)
* [Visual Studio의 네트워크 설치 만들기](../install/create-a-network-installation-of-visual-studio.md)
* [지시 파일에서 설정을 정의하는 방법](../install/automated-installation-with-response-file.md)
* [네트워크 기반 Visual Studio 배포에 대한 업데이트 제어](../install/controlling-updates-to-visual-studio-deployments.md)
* [Microsoft 업데이트 카탈로그 FAQ](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager(SCCM) 설명서](https://docs.microsoft.com/mem/configmgr)
* [Microsoft 카탈로그에서 Configuration Manager로 업데이트 가져오기](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [WSUS(Windows Server Update Services) 설명서](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
