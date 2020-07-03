---
title: 오류 - RPC에 인증 필요 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e98daf3697c86eec7767135c9ad85d67cd6e958a
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460587"
---
# <a name="error-rpc-requires-authentication"></a>오류: RPC에 인증 필요
Visual Studio 디버거에서 원격 컴퓨터에 연결할 수 없습니다. 로컬 컴퓨터에서 RPC 정책을 사용하도록 설정되어 있어 원격 디버깅을 수행할 수 없습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. `\`*windir*`\system32\regedt32.exe`를 실행합니다.

2. `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`를 찾아서 삭제합니다.

3. 컴퓨터를 다시 시작하여 레지스트리 변경 내용을 적용합니다.

4. 문제가 지속되면 **컴퓨터 구성 > 관리 템플릿 > 시스템 > 원격 프로시저 호출 > 인증되지 않은 RPC 클라이언트 제한** 그룹 정책 설정에 대해 도메인 관리자에게 문의하세요.