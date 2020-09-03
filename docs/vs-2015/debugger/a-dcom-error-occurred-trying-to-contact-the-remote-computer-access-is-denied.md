---
title: 원격 컴퓨터에 접속하려고 시도하는 동안 DCOM 오류가 발생했습니다. 액세스가 거부되었습니다. | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0157b1ade2c38a2c10920b9674d7c9a58ac036b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156526"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>원격 컴퓨터에 접속하려고 시도하는 동안 DCOM 오류가 발생했습니다. 액세스가 거부되었습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

원격 디버깅은 다음과 같은 상황에서 원격 컴퓨터와 로컬 컴퓨터 간의 통신에 DCOM을 사용합니다.  
  
- 디버거는 **도구/옵션/디버깅** 페이지에서 **네이티브 호환성 모드로** 설정 되거나 관리 되는 **호환성 모드가** 선택 됩니다.  
  
- 관리되는 C++(C++/CLI) 코드를 디버깅하는 경우  
  
- Visual Studio 2013에서 **도구/옵션/디버깅** 페이지에서 **네이티브 편집 하며 계속 하기 사용** 을 선택 하는 경우  
  
- 일부 타사 디버깅 시나리오  
  
  이 오류는 Visual Studio 프로세스가 DCOM을 통해 원격 디버거 프로세스에 자신을 인증할 수 없는 경우(또는 제공된 자격 증명이 불충분한 것으로 간주되는 경우) 발생합니다. 다음 해결 방법 중 하나 이상으로 문제를 해결할 수 있습니다.  
  
- **기본 호환성 모드** 및 **관리되는 호환성 모드**를 해제합니다.  
  
- Visual Studio 2013에서 **네이티브 편집하며 계속하기 사용**을 해제합니다.  
  
- 두 컴퓨터를 다시 부팅합니다.  
  
- 원격 디버깅을 수행하려면 자격 증명을 입력해야 하는 경우 자격 증명을 저장하는 옵션을 선택합니다.  
  
## <a name="see-also"></a>관련 항목  
 [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
