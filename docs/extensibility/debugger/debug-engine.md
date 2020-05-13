---
title: 디버그 엔진 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4cb00796f8db23a43cd81a06d80d0fac40f075e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739058"
---
# <a name="debug-engine"></a>디버그 엔진
DE(디버그 엔진)는 인터프리터 또는 운영 체제와 협력하여 실행 제어, 중단점 및 식 평가와 같은 디버깅 서비스를 제공합니다. DE는 디버깅되는 프로그램의 상태를 모니터링할 책임이 있습니다. 이를 위해 DE는 CPU또는 런타임에서 제공하는 API등 지원되는 런타임에서 사용할 수 있는 메서드를 사용합니다.

 예를 들어 공통 언어 런타임(CLR)은 ICorDebugXXX 인터페이스를 통해 실행 중인 프로그램을 모니터링하는 메커니즘을 제공합니다. CLR을 지원하는 DE는 적절한 ICorDebugXXX 인터페이스를 사용하여 디버깅중인 관리 되는 코드 프로그램을 추적합니다. 그런 다음 상태 변경 사항을 세션 디버그 관리자(SDM)에 전달하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 이러한 정보를 IDE로 전달합니다.

> [!NOTE]
> 디버그 엔진은 특정 런타임, 즉 디버깅 중인 프로그램이 실행되는 시스템을 대상으로 합니다. CLR은 관리 코드의 런타임이며 Win32 런타임은 네이티브 Windows 응용 프로그램에 대한 것입니다. 만드는 언어가 이러한 두 런타임 중 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 하나를 대상으로 할 수 있는 경우 이미 필요한 디버그 엔진을 제공합니다. 구현하기만 하면 식 계산기만 있으면 됩니다.

## <a name="debug-engine-operation"></a>디버그 엔진 작동
 모니터링 서비스는 DE 인터페이스를 통해 구현되며 디버그 패키지가 서로 다른 운영 모드 간에 전환될 수 있습니다. 자세한 내용은 [작동 모드를](../../extensibility/debugger/operational-modes.md)참조하십시오. 일반적으로 런타임 환경당 하나의 DE 구현만 있습니다.

> [!NOTE]
> Transact-SQL 및 [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)], VBScript에 대한 별도의 [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] DE 구현이 있지만 단일 DE를 공유합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버깅을 사용하면 디버그 엔진이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 셸과 동일한 프로세스또는 디버깅 중인 대상 프로그램과 동일한 프로세스의 두 가지 방법 중 하나를 실행할 수 있습니다. 후자의 형식은 일반적으로 디버깅되는 프로세스가 실제로 인터프리터에서 실행되는 스크립트일 때 발생합니다. 디버그 엔진은 스크립트를 모니터링하기 위해 인터프리터에 대한 친밀한 지식을 가지고 있어야 합니다. 이 경우 인터프리터는 실제로 런타임입니다. 디버그 엔진은 특정 런타임 구현을 위한 것입니다. 또한 단일 DE구현은 프로세스 및 컴퓨터 경계(예: 원격 디버깅)로 분할할 수 있습니다.

 DE는 디버깅 인터페이스를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 노출합니다. 모든 통신은 COM을 통해입니다. DE가 프로세스 중, 프로세스 외 또는 다른 컴퓨터에서 로드되든 관계없이 구성 요소 통신에는 영향을 주지 않습니다.

 DE는 식 계산기 구성 요소와 함께 작동하여 특정 런타임에 대한 DE가 식구문을 이해할 수 있도록 합니다. DE는 또한 언어 컴파일러에서 생성된 기호 디버그 정보에 액세스하기 위해 기호 처리기 구성 요소와 함께 작동합니다. 자세한 내용은 [식 계산기](../../extensibility/debugger/expression-evaluator.md) 및 [기호 공급자를](../../extensibility/debugger/symbol-provider.md)참조하십시오.

## <a name="see-also"></a>참조
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
- [식 계산기](../../extensibility/debugger/expression-evaluator.md)
- [기호 공급자](../../extensibility/debugger/symbol-provider.md)
