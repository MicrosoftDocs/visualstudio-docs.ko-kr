---
title: 엔터프라이즈 배포에 대한 기본값 설정
description: Visual Studio의 엔터프라이즈 배포에 대한 도메인 정책 및 기타 구성 작업에 대해 알아봅니다.
ms.date: 04/13/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b32c56e418631bfc8f5435d0eb113c9da2296ae9
ms.sourcegitcommit: 3985d0ae8d6332f4682c82a10897763173d52961
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2021
ms.locfileid: "107386009"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Visual Studio의 엔터프라이즈 배포에 대한 기본값 설정

Visual Studio의 배포에 영향을 주는 레지스트리 정책을 설정할 수 있습니다. 해당 정책은 머신 전체에 적용되고 다음에 영향을 줍니다.

- 다른 버전 또는 인스턴스와 공유되는 일부 패키지가 설치되는 경우
- 패키지 위치 및 캐시되는지 여부
- 관리자 업데이트를 적용하는 방법

[명령줄 옵션](use-command-line-parameters-to-install-visual-studio.md)을 사용하여 이러한 일부 정책을 설정하거나, 컴퓨터에서 레지스트리 값을 설정하거나, 조직에서 그룹 정책을 사용하여 해당 값을 배포할 수 있습니다.

## <a name="registry-keys"></a>레지스트리 키

그룹 정책을 통해 또는 레지스트리에서 직접 제어를 사용할 수 있도록 여러 위치에서 엔터프라이즈 기본값을 설정할 수 있습니다. Visual Studio에서는 엔터프라이즈 정책이 설정되었는지 순차적으로 확인하고, 정책 값이 아래 순서대로 발견되면 즉시 나머지 키가 무시됩니다.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup`(64비트 운영 체제)

일부 레지스트리 값은 처음 사용될 때 자동으로 설정됩니다(설정되어 있지 않은 경우). 이 연습을 통해 이후 설치에 같은 값이 사용됩니다. 이러한 값은 두 번째 레지스트리 키 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`에 저장됩니다.

다음 레지스트리 값을 설정할 수 있습니다.

::: moniker range="vs-2017"
| **이름** | **형식** | **기본값** | **설명** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` 또는 `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | 패키지가 매니페스트되고 필요한 경우 페이로드가 저장되는 디렉터리입니다. 자세한 내용은 [패키지 캐시를 사용하지 않도록 설정 또는 이동](disable-or-move-the-package-cache.md) 페이지를 참조하세요. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | 설치된 후에도 패키지 페이로드를 유지합니다. 언제든지 값을 변경할 수 있습니다. 정책을 사용하지 않도록 설정하면 복구하거나 수정하는 인스턴스에 대한 캐시된 패키지 페이로드가 모두 제거됩니다. 자세한 내용은 [패키지 캐시를 사용하지 않도록 설정 또는 이동](disable-or-move-the-package-cache.md) 페이지를 참조하세요. |
| `SharedInstallationPath` | `REG_SZ` 또는 `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | 여러 버전의 Visual Studio 인스턴스에 걸쳐 공유되는 일부 패키지가 설치되는 디렉터리입니다. 언제든지 값을 변경할 수 있지만 이후 설치에만 영향을 줍니다. 이전 위치에 이미 설치된 모든 제품은 이동되지 않거나 제대로 작동하지 않을 수 있습니다. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 0 | 설치된 모든 Visual Studio 제품에 대한 업데이트를 자동으로 다운로드하지 않습니다. 언제든지 값을 변경할 수 있습니다. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 0 | 관리자 업데이트를 클라이언트 컴퓨터에 적용할 수 있습니다. 이 값이 없거나 0으로 설정된 경우 관리자 업데이트가 차단됩니다. 이 값은 관리 용도로 사용됩니다. 자세한 내용은 [관리자 업데이트 사용](enabling-administrator-updates.md)을 참조하세요. | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 0 | 사용자가 Visual Studio에 대한 관리자 업데이트를 받지 않으려는 것을 나타냅니다. 이 레지스트리 키가 없거나 설정된 값이 0이면 Visual Studio 사용자가 Visual Studio에 대한 관리자 업데이트를 받으려는 것입니다. 이는 클라이언트 컴퓨터에 대한 관리자 권한이 있는 개발자 사용자를 위한 것입니다. 자세한 내용은 [관리자 업데이트 적용](../install/applying-administrator-updates.md#understanding-configuration-options)을 참조하세요. | 
| `UpdateConfigurationFile` | `REG_SZ` 또는 `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | 관리자 업데이트를 구성하기 위한 파일 경로입니다. 자세한 내용은 [관리자 업데이트 구성 방법](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)을 참조하세요. | 
::: moniker-end

::: moniker range="vs-2019"
| **이름** | **형식** | **기본값** | **설명** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` 또는 `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | 패키지가 매니페스트되고 필요한 경우 페이로드가 저장되는 디렉터리입니다. 자세한 내용은 [패키지 캐시를 사용하지 않도록 설정 또는 이동](disable-or-move-the-package-cache.md) 페이지를 참조하세요. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | 설치된 후에도 패키지 페이로드를 유지합니다. 언제든지 값을 변경할 수 있습니다. 정책을 사용하지 않도록 설정하면 복구하거나 수정하는 인스턴스에 대한 캐시된 패키지 페이로드가 모두 제거됩니다. 자세한 내용은 [패키지 캐시를 사용하지 않도록 설정 또는 이동](disable-or-move-the-package-cache.md) 페이지를 참조하세요. |
| `SharedInstallationPath` | `REG_SZ` 또는 `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | 여러 버전의 Visual Studio 인스턴스에 걸쳐 공유되는 일부 패키지가 설치되는 디렉터리입니다. 언제든지 값을 변경할 수 있지만 이후 설치에만 영향을 줍니다. 이전 위치에 이미 설치된 모든 제품은 이동되지 않거나 제대로 작동하지 않을 수 있습니다. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 0 | 설치된 모든 Visual Studio 제품에 대한 업데이트를 자동으로 다운로드하지 않습니다. 언제든지 값을 변경할 수 있습니다. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 0 | 관리자 업데이트를 클라이언트 컴퓨터에 적용할 수 있습니다. 이 값이 없거나 0으로 설정된 경우 관리자 업데이트가 차단됩니다. 이 값은 관리 용도로 사용됩니다. 자세한 내용은 [관리자 업데이트 사용](enabling-administrator-updates.md)을 참조하세요. | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 0 | 사용자가 Visual Studio에 대한 관리자 업데이트를 받지 않으려는 것을 나타냅니다. 이 레지스트리 키가 없거나 설정된 값이 0이면 Visual Studio 사용자가 Visual Studio에 대한 관리자 업데이트를 받으려는 것입니다. 이는 클라이언트 컴퓨터에 대한 관리자 권한이 있는 개발자 사용자를 위한 것입니다. 자세한 내용은 [관리자 업데이트 적용](../install/applying-administrator-updates.md#understanding-configuration-options)을 참조하세요. | 
| `UpdateConfigurationFile` | `REG_SZ` 또는 `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | 관리자 업데이트를 구성하기 위한 파일 경로입니다. 자세한 내용은 [관리자 업데이트 구성 방법](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)을 참조하세요. | 
| `BaselineStickinessVersions2019` | `REG_SZ` 또는 `REG_EXPAND_SZ` | `16.7.0` | 클라이언트가 있어야 하는 서비스 기준 부 버전입니다. 자세한 내용은 [관리자 업데이트 적용](../install/applying-administrator-updates.md#understanding-configuration-options) 페이지를 참조하세요. | 
::: moniker-end

> [!IMPORTANT]
> 설치 후 `CachePath` 레지스트리 정책을 변경할 경우 기존 패키지 캐시를 새 위치로 이동하고 `SYSTEM` 및 `Administrators`에 모든 권한을 부여하고 `Everyone`에 읽기 권한을 부여하여 해당 캐시가 보호되도록 해야 합니다.
> 기존 캐시를 이동하거나 보호하지 못하면 이후 설치에 관련된 문제가 발생할 수 있습니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

- [Visual Studio 설치](install-visual-studio.md)
- [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
- [관리자 업데이트 적용](applying-administrator-updates.md)
- [패키지 캐시를 사용하지 않도록 설정 또는 이동](disable-or-move-the-package-cache.md)
- [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
