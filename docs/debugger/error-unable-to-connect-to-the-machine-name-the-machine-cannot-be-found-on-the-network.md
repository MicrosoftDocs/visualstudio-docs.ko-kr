---
title: '오류: 컴퓨터 &lt;이름&gt;에 연결할 수 없습니다. 네트워크에서 컴퓨터를 찾을 수 없습니다. | Microsoft 문서'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d0f820156714a726d506d8871d4e42a8dc12a23
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736831"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>오류: 컴퓨터 &lt;이름&gt;에 연결할 수 없습니다. 네트워크에서 컴퓨터를 찾을 수 없습니다.
이 오류는 다음과 같은 경우에 발생합니다.

- 원격 컴퓨터에 대한 연결이 끊어진 경우

- 원격 컴퓨터의 사용자 계정이 비활성화된 경우

- 원격 컴퓨터의 암호가 만료된 경우

### <a name="to-resolve-this-behavior"></a>이 동작을 해결하려면

- 로컬 컴퓨터와 원격 컴퓨터가 동일한 네트워크에 있는지 확인합니다. 이를 확인하려면 Microsoft Windows 탐색기(또는 파일 탐색기)를 사용하여 원격 컴퓨터에 액세스해 봅니다.

     — 및 —

- 원격 컴퓨터에 연결하는 데 사용 중인 사용자 계정이 활성화되어 있는지 확인합니다.

     — 및 —

- 원격 컴퓨터에 연결하는 데 사용 중인 암호가 유효하고 만료되지 않았는지 확인합니다.

## <a name="see-also"></a>참조
- [Remote Debugging](../debugger/remote-debugging.md)
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)