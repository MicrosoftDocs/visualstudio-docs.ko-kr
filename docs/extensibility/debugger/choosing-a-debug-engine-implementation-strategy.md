---
title: 디버그 엔진 구현 전략 선택 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739133"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>디버그 엔진 구현 전략 선택
런타임 아키텍처를 사용하여 DE(디버그 엔진) 구현 전략을 결정합니다. 디버깅하는 프로그램에 프로세스 내 디버그 엔진을 만들 수 있습니다. 프로세스 내 디버그 엔진을 SDM(Visual Studio 세션 디버그 관리자)에 만듭니다. 또는 둘 다에 대해 디버그 엔진을 프로세스 에서 벗어나도록 만듭니다. 다음 지침은 이 세 가지 전략 중에서 선택하는 데 도움이 됩니다.

## <a name="guidelines"></a>지침
 DE가 SDM과 디버깅하는 프로그램 모두에 대해 프로세스가 불가능할 수 있지만 일반적으로 그렇게 할 이유가 없습니다. 프로세스 경계를 가로지르는 호출은 상대적으로 느립니다.

 Debug 엔진은 Win32 네이티브 런타임 환경과 공통 언어 런타임 환경에 이미 제공됩니다. 두 환경 중 하나에 대해 DE를 교체해야 하는 경우 프로세스 내 DE를 SDM으로 만들어야 합니다.

 그렇지 않으면 SDM에 대한 DE 프로세스를 만들거나 디버깅하는 프로그램에 대한 프로세스 를 만듭니다. DE의 식 평가자가 프로그램 기호 저장소에 자주 액세스해야 하는지 고려해야 합니다. 또는, 심볼 저장소를 빠른 액세스를 위해 메모리에 로드할 수 있는 경우. 또한 다음 방법을 고려하십시오.

- 식 계산기와 기호 저장소 간에 호출이 많지 않거나 심볼 저장소를 SDM 메모리 공간으로 읽을 수 있는 경우 SDM에 대한 DE 프로세스를 만듭니다. 디버그 엔진의 CLSID를 프로그램에 연결할 때 SDM에 반환해야 합니다. SDM은 이 CLSID를 사용하여 DE의 프로세스 내 인스턴스를 만듭니다.

- DE가 심볼 저장소에 액세스하기 위해 프로그램을 호출해야 하는 경우 프로그램을 사용하여 DE 프로세스를 만듭니다. 이 경우 프로그램은 DE의 인스턴스를 만듭니다.

## <a name="see-also"></a>참조
- [비주얼 스튜디오 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
