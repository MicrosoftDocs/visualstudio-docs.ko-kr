---
title: 엔터프라이즈 배포에 대한 기본값 설정
description: Visual Studio의 엔터프라이즈 배포에 대한 도메인 정책 및 기타 구성 작업에 대해 알아봅니다.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d03912eecd7b3cfa3563fc095453fee3ddf9b163
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114287"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Visual Studio의 엔터프라이즈 배포에 대한 기본값 설정

Visual Studio의 배포에 영향을 주는 레지스트리 정책을 설정할 수 있습니다. 이러한 정책은 새 설치 관리자에 전체적으로 적용되고 다음에 영향을 줍니다.

- 다른 버전 또는 인스턴스와 공유되는 일부 패키지가 설치되는 경우
- 패키지가 캐시되는 경우
- 모든 패키지가 캐시되는지 여부

[명령줄 옵션](use-command-line-parameters-to-install-visual-studio.md)을 사용하여 이러한 일부 정책을 설정하거나, 컴퓨터에서 레지스트리 값을 설정하거나, 조직에서 그룹 정책을 사용하여 해당 값을 배포할 수 있습니다.

## <a name="registry-keys"></a>레지스트리 키

그룹 정책을 통해 또는 레지스트리에서 직접 제어를 사용할 수 있도록 여러 위치에서 엔터프라이즈 기본값을 설정할 수 있습니다. Visual Studio에서는 엔터프라이즈 정책이 설정되었는지 순차적으로 확인하고, 정책 값이 아래 순서대로 발견되면 즉시 나머지 키가 무시됩니다.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup`(64비트 운영 체제)

> [!IMPORTANT]
> `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` 키를 설정하지 않은 대신 다른 키 중에 하나를 설치한 경우 64비트 운영 체제에서 다를 키를 둘 다 설정해야 합니다. 이 문제는 향후 제품 업데이트에서 해결됩니다.

일부 레지스트리 값은 처음 사용될 때 자동으로 설정됩니다(설정되어 있지 않은 경우). 이 연습을 통해 이후 설치에 같은 값이 사용됩니다. 이러한 값은 두 번째 레지스트리 키 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`에 저장됩니다.

다음 레지스트리 값을 설정할 수 있습니다.

| **이름** | **형식** | **기본값** | **설명** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` 또는 `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | 패키지가 매니페스트되고 필요한 경우 페이로드가 저장되는 디렉터리입니다. 자세한 내용은 [패키지 캐시를 사용하지 않도록 설정 또는 이동](disable-or-move-the-package-cache.md) 페이지를 참조하세요. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | 설치된 후에도 패키지 페이로드를 유지합니다. 언제든지 값을 변경할 수 있습니다. 정책을 사용하지 않도록 설정하면 복구하거나 수정하는 인스턴스에 대한 캐시된 패키지 페이로드가 모두 제거됩니다. 자세한 내용은 [패키지 캐시를 사용하지 않도록 설정 또는 이동](disable-or-move-the-package-cache.md) 페이지를 참조하세요. |
| `SharedInstallationPath` | `REG_SZ` 또는 `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | 여러 버전의 Visual Studio 인스턴스에 걸쳐 공유되는 일부 패키지가 설치되는 디렉터리입니다. 언제든지 값을 변경할 수 있지만 이후 설치에만 영향을 줍니다. 이전 위치에 이미 설치된 모든 제품은 이동되지 않거나 제대로 작동하지 않을 수 있습니다. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | 설치된 모든 Visual Studio 제품에 대한 업데이트를 자동으로 다운로드하지 않습니다. 언제든지 값을 변경할 수 있습니다. |

> [!IMPORTANT]
> 설치 후 `CachePath` 레지스트리 정책을 변경할 경우 기존 패키지 캐시를 새 위치로 이동하고 `SYSTEM` 및 `Administrators`에 모든 권한을 부여하고 `Everyone`에 읽기 권한을 부여하여 해당 캐시가 보호되도록 해야 합니다.
> 기존 캐시를 이동하거나 보호하지 못하면 이후 설치에 관련된 문제가 발생할 수 있습니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

- [Visual Studio 설치](install-visual-studio.md)
- [패키지 캐시를 사용하지 않도록 설정 또는 이동](disable-or-move-the-package-cache.md)
- [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
