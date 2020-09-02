---
title: '오류: RPC에 인증 필요 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62535738"
---
# <a name="error-rpc-requires-authentication"></a>오류: RPC에 인증 필요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 디버거에서 원격 컴퓨터에 연결할 수 없습니다. 로컬 컴퓨터에서 RPC 정책을 사용하도록 설정되어 있어 원격 디버깅을 수행할 수 없습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1. `\`*windir*`\system32\regedt32.exe`를 실행합니다.  
  
2. `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`를 찾아서 삭제합니다.  
  
3. 컴퓨터를 다시 시작하여 레지스트리 변경 내용을 적용합니다.  
  
4. 문제가 지속 되 면 컴퓨터 구성에 대해 도메인 관리자에 게 문의 하십시오. **>관리 템플릿->시스템->원격 프로시저 호출-인증 되지 않은 RPC 클라이언트에 대 한 >제한** 그룹 정책 설정입니다.
