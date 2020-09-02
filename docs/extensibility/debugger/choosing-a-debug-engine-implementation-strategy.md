---
title: 디버그 엔진 구현 전략 선택 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739133"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>디버그 엔진 구현 전략 선택
런타임 아키텍처를 사용 하 여 DE (디버그 엔진) 구현 전략을 결정 합니다. 디버깅 중인 프로그램에 대 한 디버그 엔진을 in-process로 만들 수 있습니다. Visual Studio 세션 디버그 관리자 (SDM)에 대해 in-process로 디버그 엔진을 만듭니다. 또는 둘 다에서 디버그 엔진을 out-of-process로 만듭니다. 다음 지침은 이러한 세 가지 전략 중 하나를 선택 하는 데 도움이 됩니다.

## <a name="guidelines"></a>지침
 디버깅 중인 SDM 및 프로그램 모두에 대 한 out-of-process를 수행할 수는 있지만 일반적으로이 작업을 수행할 이유가 없습니다. 프로세스 경계를 넘어 호출 하는 것은 상대적으로 느립니다.

 디버그 엔진은 Win32 네이티브 런타임 환경 및 공용 언어 런타임 환경에 대해 이미 제공 됩니다. 두 환경에 대 한 DE를 교체 해야 하는 경우 SDM을 사용 하 여 DE-DE를 만들어야 합니다.

 그렇지 않은 경우에는 디버깅 중인 프로그램에 대해 SDM 또는 in-process로의 in-process를 만듭니다. DE의 식 계산기에서 프로그램 기호 저장소에 자주 액세스 해야 하는지 여부를 고려해 야 합니다. 빠른 액세스를 위해 기호 저장소를 메모리에 로드할 수 있는 경우 또는입니다. 또한 다음과 같은 방법을 고려해 야 합니다.

- 식 계산기와 기호 저장소 사이에 많은 호출이 없거나 기호 저장소를 SDM 메모리 공간으로 읽을 수 있는 경우 SDM에 대해 in-process를 만듭니다. 프로그램에 연결 되 면 디버그 엔진의 CLSID를 SDM에 반환 해야 합니다. SDM은이 CLSID를 사용 하 여 DE-DE의 in-process 인스턴스를 만듭니다.

- DE가 프로그램을 호출 하 여 기호 저장소에 액세스 해야 하는 경우 프로그램을 사용 하 여 DE-DE를 만듭니다. 이 경우 프로그램은 DE의 인스턴스를 만듭니다.

## <a name="see-also"></a>추가 정보
- [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
