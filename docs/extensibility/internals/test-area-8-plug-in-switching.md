---
title: '테스트 영역 8: 플러그인 스위칭 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704396"
---
# <a name="test-area-8-plug-in-switching"></a>테스트 영역 8: 플러그 인 전환
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합 개발 환경(IDE)에는 현재 소스 제어 플러그인을 변경하는 사용자 인터페이스(UI)가 있다. 이 테스트 영역은 솔루션 소스 제어에 사용할 플러그인을 선택하는 프로세스에 대한 테스트 사례를 제공합니다.

## <a name="command-menu-access"></a>명령 메뉴 액세스
 다음 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합 개발 환경 메뉴 경로는 테스트 사례에 사용됩니다.

- 현재 소스 제어 플러그인: **도구** -> **옵션** -> **소스 제어** -> **플러그인 선택.**

- 소스 제어 바인딩 변경: **파일** -> **소스 제어** -> **변경 소스 제어...**

## <a name="common-expected-behavior"></a>일반적인 예상 동작
 Visual Studio를 종료하거나 솔루션을 다시 로드하지 않고도 솔루션에 대한 소스 제어 플러그인을 변경할 수 있습니다. 또한 현재 소스 제어 플러그인은 해당 솔루션이 로드될 때 솔루션에서 사용하는 플러그인으로 자동으로 변경됩니다.

## <a name="test-cases"></a>테스트 사례
 다음은 플러그인 스위칭 테스트 영역에 대한 특정 테스트 사례입니다.

### <a name="case-8a-automatic-change"></a>케이스 8a: 자동 변경

#### <a name="expected-behavior"></a>예상되는 동작
 사용자가 소스 제어하에 있는 솔루션을 로드하면 솔루션이 자동으로 로드되고 적절한 소스 제어 플러그인이 현재로 선택됩니다.

| 작업 | 테스트 단계 | 확인할 예상 결과 |
| - | - | - |
| 자동 소스 제어 플러그인 변경 | 1. 현재로 테스트에서 플러그인을 선택 **(도구** -> **옵션** -> **소스 제어** -> **플러그인 선택.)**<br />2. 새 프로젝트를 만듭니다.<br />3. 소스 제어에 솔루션을 추가합니다.<br />4. 다른 플러그인(예: [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)])을 선택합니다.<br />5. 언로딩 솔루션 프롬프트를 수락합니다.<br />6. 디스크에서 솔루션을 다시 엽니다. | 솔루션이 열립니다.<br /><br /> 테스트 중인 플러그인은 현재 소스 제어 플러그인입니다. |

### <a name="case-8b-solution-based-change"></a>사례 8b: 솔루션 기반 변경

#### <a name="expected-behavior"></a>예상되는 동작
 솔루션에 연결된 소스 제어 플러그인이 변경될 수 있습니다.

| 작업 | 테스트 단계 | 확인할 예상 결과 |
|----------------------------------| - | - |
| 솔루션용 플러그인 변경 | 1. 테스트 중인 플러그인을 현재(도구**Tools** -> **옵션** -> **소스 제어 플러그** -> **인 선택)로 선택합니다.**<br />2. 새 프로젝트 및 솔루션을 만듭니다.<br />3. 소스 제어에 솔루션을 추가합니다.<br />4. 소스 제어 변경 **대화** 상자 사용)에서 솔루션을 바인딩 해제합니다.<br />5. 다른 플러그인(예: [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)])을 선택합니다.<br />6. 언로드된 경우 디스크에서 솔루션을 다시 로드합니다.<br />7. 소스 제어에 솔루션을 추가합니다.<br />8. 소스 제어 변경 **대화** 상자 사용)에서 솔루션을 바인딩 해제합니다.<br />9. 테스트 중인 플러그인을 다시 선택합니다.<br />10. 언로드된 경우 디스크에서 솔루션을 다시 로드합니다.<br />11. **원본 제어** 변경 대화 상자를 사용하여 솔루션을 원래 위치에 바인딩합니다. | 선택한 플러그인을 사용하여 소스 제어에 솔루션이 추가됩니다. |

## <a name="see-also"></a>참조
- [소스 제어 플러그 인에 대한 테스트 가이드](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
