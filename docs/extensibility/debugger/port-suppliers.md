---
title: 포트 공급자 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738307"
---
# <a name="port-suppliers"></a>포트 공급자
디버거 아키텍처에서 *포트 공급자*는 다음과 같습니다.

- 는 서버에 포함 되어 있으며 해당 서버에 대 한 요청에 포트를 제공 합니다.

- 포함 하는 서버에서 포트를 추가 하 고 제거할 수 있습니다.

- 는 서버에 제공 된 모든 포트를 열거할 수 있습니다.

- 는 레지스트리를 통해 Visual Studio에 등록 된 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스로 표시 됩니다. 이 인터페이스는 [Getportsupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)를 호출 하 여 가져올 수 있습니다.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 기본 포트 공급자와 기본 포트를 제공 합니다. 사용자 지정 포트를 구현 해야 하는 경우 해당 사용자 지정 포트를 제공 하기 위해 사용자 지정 포트 공급자도 구현 해야 합니다.

## <a name="see-also"></a>추가 정보
- [서버](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Ports](../../extensibility/debugger/ports.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
