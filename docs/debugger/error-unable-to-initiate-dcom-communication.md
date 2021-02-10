---
title: DCOM 통신을 시작할 수 없음 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ddae1685935cbb5267d3cc4f994c16e99a542da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870924"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>오류: DCOM 통신을 초기화할 수 없음
로컬 컴퓨터에서 원격 컴퓨터와 통신을 시도하는 동안 DCOM 오류가 발생했습니다. 원격 서버의 방화벽 때문이거나 원격 컴퓨터의 Windows 인증이 손상되었기 때문일 수 있습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- 원격 머신에서 Windows 방화벽을 사용하는 경우에 로컬 디버깅을 위해 방화벽을 구성하는 방법에 관한 지침은 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.

- Windows 인증을 복원하려면 두 컴퓨터를 모두 다시 부팅합니다. 로컬 컴퓨터와 원격 컴퓨터에서 이벤트 로그를 검사하여 Kerberos 오류가 있는지 확인하고 알려진 문제가 있는지 도메인 관리자에게 문의합니다.

## <a name="see-also"></a>참조
- [Remote Debugging](../debugger/remote-debugging.md)