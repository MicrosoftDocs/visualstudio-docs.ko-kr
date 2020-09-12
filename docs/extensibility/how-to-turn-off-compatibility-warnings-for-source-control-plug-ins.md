---
title: 소스 제어 플러그 인에 대 한 경고 해제
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 406d063bd2df6dd1d831c3a8220d8d513596a79a
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037187"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>방법: 소스 제어 플러그 인에 대 한 호환성 경고 해제

에서 소스 제어를 사용 하는 경우 사용자에 게 여러 호환성 경고가 표시 될 수 있습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . 표시 되는 경고는 원본 제어 플러그 인의 기능에 따라 다르며 여기에 설명 된 대로 사용 하지 않도록 설정할 수 있습니다.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>경고를 사용 하지 않도록 설정 하려면: "Visual Studio와의 최적화 된 소스 제어 통합을 확인 하려면"

- 다음 레지스트리 항목을 설정 합니다 (필요한 경우 값 추가).

   **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword: 00000001**

   이 경고는 모든 비 플러그 인에 대해 표시 됩니다 [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] .

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>"설치 된 원본 제어 공급자가 일부 기능을 지원 하지 않습니다." 경고를 사용 하지 않도록 설정 하려면

- 다음 두 레지스트리 값을 설정 합니다 (필요한 경우 값 추가).

     **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword: 00000000**

    **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword: 00000001**

     이 경고는 소스 제어 플러그 인에서 여러 프로젝트에 대해 재진입을 명시적으로 지원 하지 않는 경우 (즉, 한 번에 하나의 파일 및 프로젝트만 체크 인할 수 있는 경우)에 표시 됩니다.

     재진입 (기능)을 지 원하는 것이 가장 좋습니다. 이렇게 `SCC_CAP_REENTRANT` 하면이 경고가 제거 됩니다. 그러나이 지원을 사용할 수 없는 경우 이러한 레지스트리 항목을 설정할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [기능 플래그](../extensibility/capability-flags.md)
