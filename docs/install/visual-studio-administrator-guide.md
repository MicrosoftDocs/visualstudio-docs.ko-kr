---
title: Visual Studio 관리자 가이드
titleSuffix: ''
description: 엔터프라이즈 환경에 Visual Studio를 배포하는 방법을 자세히 알아봅니다.
ms.date: 07/29/2020
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: db1e57097b492a8847be6d96719054a6b917e4bd
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425409"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio 관리자 가이드

엔터프라이즈 환경에서는 일반적으로 시스템 관리자가 네트워크 공유 또는 시스템 관리 소프트웨어를 사용하여 최종 사용자에게 설치를 배포합니다. Visual Studio 설치 엔진은 엔터프라이즈 배포를 지원하여 시스템 관리자가 네트워크 설치 위치를 만들고, 설치 기본값을 미리 구성하고, 설치 프로세스에서 제품 키를 배포하고, 출시 후 제품 업데이트를 관리하도록 구성되었습니다.

이 관리자 가이드에서는 네트워크 환경의 엔터프라이즈 배포에 대한 시나리오 기반 지침을 제공합니다.

## <a name="before-you-begin"></a>시작하기 전 주의 사항

조직 전체에 Visual Studio를 배포하기 전에 몇 가지 결정할 사항과 완료할 작업이 있습니다.

::: moniker range="vs-2019"

* 각 대상 컴퓨터가 [최소 설치 요구 사항](/visualstudio/releases/2019/system-requirements/)을 충족하는지 확인합니다.

* 서비스 요구 사항을 결정합니다.

  회사가 어떤 기능 집합을 오래 유지해야 하지만 정기 서비스 업데이트도 받고자 하는 경우 서비스 기준선의 사용을 계획합니다. 자세한 내용은 [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) 페이지의 **** Enterprise 및 Professional 고객용 지원 옵션 섹션 및 [서비스 기준선에서 Visual Studio 업데이트](update-servicing-baseline.md) 페이지를 참조하세요.

  누적 기능 업데이트와 함께 서비스 업데이트를 적용할 계획인 경우 최신 정보를 선택할 수 있습니다.

* 업데이트 모델을 결정합니다.

  업데이트를 가져오려면 개별 클라이언트 컴퓨터를 어디에 두어야 할까요? 특히 업데이트를 인터넷에서 가져올지 아니면 회사 전체 로컬 공유에서 가져올지 결정합니다. 그런 다음, 로컬 공유 사용을 선택한 경우 개별 사용자가 자신의 고유한 클라이언트를 업데이트할 수 있는지 아니면 관리자가 프로그램에 의해 클라이언트를 업데이트할지 결정합니다.

  최신 제품 업데이트를 사용하여 Visual Studio의 네트워크 설치 레이아웃을 업데이트할 수 있으므로, 해당 레이아웃을 Visual Studio의 최신 업데이트에 대한 설치 지점으로 사용하거나 이미 클라이언트 워크스테이션에 배포된 설치를 유지 관리하는 데 사용할 수 있습니다. 자세한 내용은 [Visual Studio의 네트워크 기반 설치 업데이트](../install/update-a-network-installation-of-visual-studio.md)를 참조하세요.

  인터넷에 연결되지 않은 컴퓨터의 경우 최소 레이아웃을 만드는 것이 오프라인 Visual Studio 인스턴스를 업데이트하는 가장 쉽고 빠른 방법입니다. 자세한 내용은 [최소 오프라인 레이아웃을 사용하여 Visual Studio 업데이트](update-minimal-layout.md)를 참조하세요.

* 회사에 필요한 [워크로드 및 구성 요소](workload-and-component-ids.md?view=vs-2019)를 결정합니다.

* [응답 파일](automated-installation-with-response-file.md?view=vs-2019)(스크립트 파일의 세부 정보 관리를 단순하게 해주는)을 사용할지 여부를 결정합니다.

* 그룹 정책을 사용할지 여부 및 개별 컴퓨터에 대한 고객 피드백을 사용하지 않도록 Visual Studio를 구성할지 여부를 결정합니다.

::: moniker-end

::: moniker range="vs-2017"

* 각 대상 컴퓨터가 [최소 설치 요구 사항](/visualstudio/productinfo/vs2017-system-requirements-vs/)을 충족하는지 확인합니다.

* 서비스 요구 사항을 결정합니다.

  회사가 어떤 기능 집합을 오래 유지해야 하지만 정기 서비스 업데이트도 받고자 하는 경우 서비스 기준선의 사용을 계획합니다. 자세한 내용은 [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) 페이지의 **** 이전 버전의 Visual Studio 지원 섹션 및 [서비스 기준선에서 Visual Studio 업데이트](update-servicing-baseline.md) 페이지를 참조하세요.

  누적 기능 업데이트와 함께 서비스 업데이트를 적용할 계획인 경우 최신 정보를 선택할 수 있습니다.

* 업데이트 모델을 결정합니다.

  업데이트를 가져오려면 개별 클라이언트 컴퓨터를 어디에 두어야 할까요? 특히 업데이트를 인터넷에서 가져올지 아니면 회사 전체 로컬 공유에서 가져올지 결정합니다. 그런 다음, 로컬 공유 사용을 선택한 경우 개별 사용자가 자신의 고유한 클라이언트를 업데이트할 수 있는지 아니면 관리자가 프로그램에 의해 클라이언트를 업데이트할지 결정합니다.

  최신 제품 업데이트를 사용하여 Visual Studio의 네트워크 설치 레이아웃을 업데이트할 수 있으므로, 해당 레이아웃을 Visual Studio의 최신 업데이트에 대한 설치 지점으로 사용하거나 이미 클라이언트 워크스테이션에 배포된 설치를 유지 관리하는 데 사용할 수 있습니다. 자세한 내용은 [Visual Studio의 네트워크 기반 설치 업데이트](../install/update-a-network-installation-of-visual-studio.md)를 참조하세요.

  인터넷에 연결되지 않은 컴퓨터의 경우 최소 레이아웃을 만드는 것이 오프라인 Visual Studio 인스턴스를 업데이트하는 가장 쉽고 빠른 방법입니다. 자세한 내용은 [최소 오프라인 레이아웃을 사용하여 Visual Studio 업데이트](update-minimal-layout.md)를 참조하세요.

* 회사에 필요한 [워크로드 및 구성 요소](workload-and-component-ids.md?view=vs-2017)를 결정합니다.

* [응답 파일](automated-installation-with-response-file.md?view=vs-2017)(스크립트 파일의 세부 정보 관리를 단순하게 해주는)을 사용할지 여부를 결정합니다.

* 그룹 정책을 사용할지 여부 및 개별 컴퓨터에 대한 고객 피드백을 사용하지 않도록 Visual Studio를 구성할지 여부를 결정합니다.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>1단계 - Visual Studio 제품 파일 다운로드

* 설치하려는 [워크로드 및 구성 요소를 선택](workload-and-component-ids.md?view=vs-2019)합니다.

* [Visual Studio 제품 파일에 대한 네트워크 공유를 만듭니다](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>2단계 - 설치 스크립트를 빌드

* [명령줄 매개 변수](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019)를 사용하여 설치를 제어하는 설치 스크립트를 빌드합니다.

  >[!NOTE]
  > [응답 파일](automated-installation-with-response-file.md?view=vs-2019)을 사용하여 스크립트를 단순화할 수 있습니다. 반드시 기본 설치 옵션이 포함된 응답 파일을 만들어야 합니다.

* (선택 사항) 사용자가 소프트웨어를 별도로 활성화할 필요가 없도록 설치 스크립트의 일부로 [볼륨 라이선스 제품 키를 적용](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019)합니다.

* (선택 사항) 네트워크 레이아웃을 업데이트하여 [제품 업데이트가 최종 사용자에게 전달되는 시점 및 위치를 제어](controlling-updates-to-visual-studio-deployments.md?view=vs-2019)합니다.

* (선택 사항) 다른 버전 또는 인스턴스와 공유되는 일부 패키지를 설치하는 위치, [패키지를 캐시하는 위치](set-defaults-for-enterprise-deployments.md?view=vs-2019) 또는 [패키지를 캐시하는지 여부](disable-or-move-the-package-cache.md?view=vs-2019) 등 Visual Studio의 배포에 영향을 미치는 레지스트리 정책을 설정합니다.

* (선택 사항) 그룹 정책을 설정합니다. 개별 컴퓨터에서 [고객 피드백을 사용하지 앟도록 Visual Studio를 구성](../ide/visual-studio-experience-improvement-program.md)할 수도 있습니다.

## <a name="step-3---deploy"></a>3단계 - 배포

* 선택한 배포 기술을 사용하여 대상 개발자 워크스테이션에서 스크립트를 실행합니다.

## <a name="step-4---deploy-updates"></a>4단계 - 업데이트 배포

* 1단계에서 사용한 명령을 정기적으로 실행하여 업데이트된 구성 요소를 추가하는 방법으로 [네트워크 위치를 최신 업데이트로 갱신](update-a-network-installation-of-visual-studio.md?view=vs-2019)합니다.

  업데이트 스크립트를 사용하여 Visual Studio를 업데이트할 수 있습니다. [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) 명령줄 매개 변수를 사용하면 됩니다.

## <a name="step-5---optional-use-visual-studio-tools"></a>5단계 - (선택 사항) Visual Studio 도구 사용

클라이언트 컴퓨터에 [설치된 Visual Studio 인스턴스를 검색 및 관리](tools-for-managing-visual-studio-instances.md?view=vs-2019)하는 데 사용할 수 있는 여러 가지 도구가 있습니다.

## <a name="advanced-configuration"></a>고급 구성

기본적으로 Visual Studio 설치에서는 Bing 검색에 오류 목록 F1 및 코드 링크로부터 사용자 지정 유형을 포함할 수 있습니다. 정책에 따라 다음 레지스트리 키의 값을 변경하여 검색 메커니즘이 사용자 지정 사용자 유형을 포함하지 못하도록 Visual Studio를 구성할 수 있습니다.

**“PutCustomTypeInBingSearch” DWORD 0**

레지스트리는 프라이빗 레지스트리 하이브의 *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics\* 디렉터리에 있습니다. 레지스트리 하이브를 여는 방법에 대한 지침은 [Visual Studio 인스턴스용으로 레지스트리 편집](tools-for-managing-visual-studio-instances.md?view=vs-2019#editing-the-registry-for-a-visual-studio-instance)을 참조하세요.

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>1단계 - Visual Studio 제품 파일 다운로드

* 설치하려는 [워크로드 및 구성 요소를 선택](workload-and-component-ids.md?view=vs-2017)합니다.

* [Visual Studio 제품 파일에 대한 네트워크 공유를 만듭니다](create-a-network-installation-of-visual-studio.md?view=vs-2017).

## <a name="step-2---build-an-installation-script"></a>2단계 - 설치 스크립트를 빌드

* [명령줄 매개 변수](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017)를 사용하여 설치를 제어하는 설치 스크립트를 빌드합니다.

  >[!NOTE]
  > [응답 파일](automated-installation-with-response-file.md?view=vs-2017)을 사용하여 스크립트를 단순화할 수 있습니다. 반드시 기본 설치 옵션이 포함된 응답 파일을 만들어야 합니다.

* (선택 사항) 사용자가 소프트웨어를 별도로 활성화할 필요가 없도록 설치 스크립트의 일부로 [볼륨 라이선스 제품 키를 적용](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017)합니다.

* (선택 사항) 네트워크 레이아웃을 업데이트하여 [제품 업데이트가 최종 사용자에게 전달되는 시점 및 위치를 제어](controlling-updates-to-visual-studio-deployments.md?view=vs-2017)합니다.

* (선택 사항) 다른 버전 또는 인스턴스와 공유되는 일부 패키지를 설치하는 위치, [패키지를 캐시하는 위치](set-defaults-for-enterprise-deployments.md?view=vs-2019) 또는 [패키지를 캐시하는지 여부](disable-or-move-the-package-cache.md?view=vs-2017) 등 Visual Studio의 배포에 영향을 미치는 레지스트리 정책을 설정합니다.

* (선택 사항) 그룹 정책을 설정합니다. 개별 컴퓨터에서 [고객 피드백을 사용하지 앟도록 Visual Studio를 구성](../ide/visual-studio-experience-improvement-program.md)할 수도 있습니다.

## <a name="step-3---deploy"></a>3단계 - 배포

* 선택한 배포 기술을 사용하여 대상 개발자 워크스테이션에서 스크립트를 실행합니다.

## <a name="step-4---deploy-updates"></a>4단계 - 업데이트 배포

* 1단계에서 사용한 명령을 정기적으로 실행하여 업데이트된 구성 요소를 추가하는 방법으로 [네트워크 위치를 최신 업데이트로 갱신](update-a-network-installation-of-visual-studio.md?view=vs-2017)합니다.

  업데이트 스크립트를 사용하여 Visual Studio를 업데이트할 수 있습니다. [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) 명령줄 매개 변수를 사용하면 됩니다.

## <a name="step-5---optional-use-visual-studio-tools"></a>5단계 - (선택 사항) Visual Studio 도구 사용

클라이언트 컴퓨터에 [설치된 Visual Studio 인스턴스를 검색 및 관리](tools-for-managing-visual-studio-instances.md?view=vs-2017)하는 데 사용할 수 있는 여러 가지 도구가 있습니다.

## <a name="advanced-configuration"></a>고급 구성

기본적으로 Visual Studio 설치에서는 Bing 검색에 오류 목록 F1 및 코드 링크로부터 사용자 지정 유형을 포함할 수 있습니다. 정책에 따라 다음 레지스트리 키의 값을 변경하여 검색 메커니즘이 사용자 지정 사용자 유형을 포함하지 못하도록 Visual Studio를 구성할 수 있습니다.

**“PutCustomTypeInBingSearch” DWORD 0**

레지스트리는 프라이빗 레지스트리 하이브의 *Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\* 디렉터리에 있습니다. 레지스트리 하이브를 여는 방법에 대한 지침은 [Visual Studio 인스턴스용으로 레지스트리 편집](tools-for-managing-visual-studio-instances.md?view=vs-2017#editing-the-registry-for-a-visual-studio-instance)을 참조하세요.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

* [명령줄 매개 변수 예](command-line-parameter-examples.md)
* [Visual Studio 오프라인 설치에 필요한 인증서 설치](install-certificates-for-visual-studio-offline.md)
* [설치 구성 가져오기 또는 내보내기](import-export-installation-configurations.md)
* [Visual Studio 설치 보관](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/releases/2019/servicing/)
* [동기 자동 로드 설정](../extensibility/synchronously-autoloaded-extensions.md)
