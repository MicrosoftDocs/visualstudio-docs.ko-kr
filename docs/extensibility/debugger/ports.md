---
title: 포트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b42e7fa97c12afa07923e99d8b084840ee7ccad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738312"
---
# <a name="ports"></a>포트
디버거 아키텍처에서 *포트:*

- 서버에서 실행되는 프로세스 집합에 대한 컨테이너입니다. 예를 들어 포트는 직렬 케이블또는 네트워크로 관리되지 않는 DCOM 컴퓨터에 대한 Windows CE 기반 장치에 대한 연결을 나타낼 수 있습니다. 로컬 포트라고 하는 하나의 특수 포트에는 로컬 컴퓨터에서 실행되는 모든 프로세스가 포함됩니다.

- 이름 또는 식별자로 자신을 식별할 수 있습니다.

- 포트에서 실행 중인 모든 프로세스를 열거하고 이러한 프로세스를 시작하고 종료할 수 있습니다.

- [AddPort에 IDebugPortRequest2](../../extensibility/debugger/reference/idebugport2.md) 인수를 전달 하 여 생성 되는 [IDebugPort2](../../extensibility/debugger/reference/idebugportrequest2.md) 인터페이스에 의해 표시 됩니다. [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]기본 및 관리되는 모든 Windows 기반 프로세스를 처리하는 기본 포트를 제공합니다. Windows 기반이 아닌 외부 장치와의 연결을 위해 사용자 지정 포트를 설정해야 합니다. 이러한 사용자 지정 포트를 제공 하려면 사용자 지정 포트 공급자도 설정 해야 합니다.

## <a name="see-also"></a>참조
- [서버](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [프로세스](../../extensibility/debugger/processes.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
