---
title: 로컬 컴퓨터의 방화벽 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.firewall.localmachine
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
ms.openlocfilehash: d5f3e57bbac1d2c293c5a9f910beca5484db06cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871595"
---
# <a name="error-firewall-on-local-machine"></a>오류: 로컬 머신의 방화벽
Visual Studio 폼을 실행하고 있는 컴퓨터인 로컬 컴퓨터의 인터넷 연결 방화벽이 원격 디버깅을 허용하도록 설정되어 있지 않습니다. 기본 전송을 사용하는 관리 또는 네이티브 원격 디버깅의 경우 DCOM 트래픽에 대해 TCP 135 포트를 열어야 합니다. 파일 및 프린터 공유가 열려 있어야 하고 devenv.exe가 예외 목록에 추가되어야 합니다. 일부 IPSEC 포트를 열어야 할 수도 있습니다.

 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.