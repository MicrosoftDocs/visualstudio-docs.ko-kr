---
title: '오류: 사이트에서 IP 주소 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46eace1c566a2810c5914a49654f8393f425fdee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155746"
---
# <a name="error-site-uses-ip-address"></a>오류: 사이트에서 IP 주소 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 오류는 디버거에서 IP 주소를 사용하는 웹 애플리케이션에 자동으로 연결하려고 할 때 발생합니다. IIS에서 **웹 사이트 확인**을 **특정 IP 주소 사용**으로 변경하는 경우 이 오류가 발생합니다.  
  
 자동 연결이 제대로 동작하기 위해서는 컴퓨터 이름뿐 아니라 특정 IP 주소도 함께 사용하여 프로젝트를 만들어야 합니다. 그렇지 않으면 디버거에서 컴퓨터 이름을 localhost로 변경하므로 DEBUG 동사를 IIS로 보낼 수 없게 됩니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1. 디버그 메뉴에서 **프로세스에 연결**을 선택하여 자동 연결 대신 수동 연결을 사용합니다.  
  
     또는  
  
2. **IIS 웹 사이트 확인** 설정을 변경합니다.  
  
## <a name="see-also"></a>관련 항목  
 [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
