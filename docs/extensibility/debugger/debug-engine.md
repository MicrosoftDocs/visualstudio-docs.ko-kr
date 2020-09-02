---
title: 디버그 엔진 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739058"
---
# <a name="debug-engine"></a>디버그 엔진
DE (디버그 엔진)는 인터프리터 또는 운영 체제와 함께 작동 하 여 실행 제어, 중단점 및 식 평가와 같은 디버깅 서비스를 제공 합니다. DE는 디버깅 중인 프로그램의 상태를 모니터링 하는 일을 담당 합니다. 이 작업을 수행 하기 위해 DE는 CPU 또는 런타임에서 제공 하는 Api의 지원 되는 런타임에서 사용할 수 있는 모든 메서드를 사용 합니다.

 예를 들어 CLR (공용 언어 런타임)은 ICorDebugXXX 인터페이스를 통해 실행 중인 프로그램을 모니터링 하는 메커니즘을 제공 합니다. CLR을 지 원하는 DE는 적절 한 ICorDebugXXX 인터페이스를 사용 하 여 디버깅 중인 관리 코드 프로그램을 추적 합니다. 그런 다음 해당 정보를 IDE에 전달 하는 SDM (세션 디버그 관리자)에 상태 변경 내용을 전달 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다.

> [!NOTE]
> 디버그 엔진은 특정 런타임, 즉 디버깅 중인 프로그램이 실행 되는 시스템을 대상으로 합니다. CLR은 관리 코드에 대 한 런타임 이며 Win32 런타임은 네이티브 Windows 응용 프로그램을 위한 것입니다. 만든 언어가 이러한 두 런타임 중 하나를 대상으로 할 수 있는 경우는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 이미 필요한 디버그 엔진을 제공 합니다. 구현 해야 하는 것은 모두 식 계산기입니다.

## <a name="debug-engine-operation"></a>디버그 엔진 작업
 모니터링 서비스는 DE 인터페이스를 통해 구현 되며 디버그 패키지가 여러 작업 모드 간에 전환 될 수 있습니다. 자세한 내용은 [운영 모드](../../extensibility/debugger/operational-modes.md)를 참조 하세요. 일반적으로 런타임 환경 마다 하나의 DE-DE 구현이 있습니다.

> [!NOTE]
> Transact-sql 및 VBScript에 대 한 별도의 DE 구현이 있지만 [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] 단일 de를 공유 합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅을 사용 하면 디버그 엔진이 셸과 동일한 프로세스 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 또는 디버깅 대상 프로그램과 동일한 프로세스에서 두 가지 방법 중 하나를 실행할 수 있습니다. 후자 형식은 일반적으로 디버그 중인 프로세스가 인터프리터에서 실행 되는 스크립트인 경우에 발생 합니다. 디버그 엔진은 스크립트를 모니터링 하기 위해 인터프리터에 대 한 지식이 있어야 합니다. 이 경우 인터프리터는 실제로 런타임입니다. 디버그 엔진은 특정 런타임 구현을 위한 것입니다. 또한 단일 DE의 구현은 프로세스 및 컴퓨터 경계 (예: 원격 디버깅) 간에 분할 될 수 있습니다.

 DE는 디버깅 인터페이스를 노출 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 모든 통신은 COM을 통해 진행 됩니다. DE가 in-process로 로드 되는지, out-of-process로 로드 되는지, 다른 컴퓨터에 로드 되는지는 구성 요소 통신에 영향을 주지 않습니다.

 DE는 식 계산기 구성 요소와 함께 작동 하 여 특정 런타임에서 식의 구문을 이해할 수 있도록 합니다. 또한 DE는 기호 처리기 구성 요소와 함께 작동 하 여 언어 컴파일러에서 생성 된 기호화 된 디버그 정보에 액세스 합니다. 자세한 내용은 [식 계산기](../../extensibility/debugger/expression-evaluator.md) 및 [기호 공급자](../../extensibility/debugger/symbol-provider.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
- [식 계산기](../../extensibility/debugger/expression-evaluator.md)
- [기호 공급자](../../extensibility/debugger/symbol-provider.md)
