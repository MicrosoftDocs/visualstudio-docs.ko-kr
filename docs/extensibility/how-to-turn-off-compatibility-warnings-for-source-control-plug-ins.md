---
title: 소스 제어 플러그인에 대한 호환성 경고 끄기 | 마이크로 소프트 문서
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
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710720"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>방법: 소스 제어 플러그인에 대한 호환성 경고 끄기
에서 소스 컨트롤을 사용할 때 여러 호환성 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]경고가 표시될 수 있습니다. 표시되는 경고는 소스 제어 플러그인의 기능에 따라 다르며 여기에 자세히 설명된 대로 비활성화할 수 있습니다.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>경고를 사용하지 않도록 설정하려면: "Visual Studio와 최적의 소스 제어 통합을 보장합니다."

- 다음 레지스트리 항목을 설정합니다(필요한 경우 값 추가)

   **HKEY_CURRENT_USER\소프트웨어\마이크로소프트\비주얼 스튜디오\8.0\소스 제어\돈트디스플레이체크넷호환 = dword:00000001**

   이 경고는 모든 비[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 플러그인에 대해 표시됩니다.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>경고를 사용하지 않도록 설정하려면: "설치된 소스 제어 공급자가 모든 기능을 지원하지 않습니다."

- 다음 두 레지스트리 값을 설정합니다(필요한 경우 값 추가).

     **HKEY_CURRENT_USER\소프트웨어\마이크로소프트\비주얼 스튜디오\8.0\소스 제어\경고OldMSSCCI공급자 = dword:00000000**

    **HKEY_CURRENT_USER\소프트웨어\마이크로소프트\비주얼 스튜디오\8.0\소스 제어\UseOldSCC = dword:0000001**

     이 경고는 소스 제어 플러그인이 여러 프로젝트에 대한 재진입을 명시적으로 지원하지 않는 경우(즉, 한 번에 하나의 파일과 프로젝트만 체크 인할 수 있는 경우)에 표시됩니다.

     재진입 (기능)을`SCC_CAP_REENTRANT` 지원하는 것이 가장 좋습니다. 이렇게 하면 이 경고가 제거됩니다. 그러나 이 지원이 불가능한 경우 이러한 레지스트리 항목을 설정할 수 있습니다.

## <a name="see-also"></a>참조
- [기능 플래그](../extensibility/capability-flags.md)
