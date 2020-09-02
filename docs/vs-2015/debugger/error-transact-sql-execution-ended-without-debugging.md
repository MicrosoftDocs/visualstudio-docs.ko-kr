---
title: '오류: 디버깅 없이 Transact-SQL 실행이 중지됨 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 7a4d4999-3973-4339-ba6a-f0d19bcb1d4a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cdfcaa42c55f87711b0889c6a67d1a4799b84fed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681069"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>오류: 디버깅 없이 Transact-SQL 실행이 중지됨
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 오류는 Transact-SQL 또는 SQLCLR 프로시저를 디버깅하려 할 때 디버거가 SQL Server에서 디버깅 메시지를 받지 못하는 경우에 발생합니다.  
  
 이 오류는 네트워크 문제나 SQL Server와 관련된 문제가 원인일 수도 있지만 대부분의 경우는 권한 문제 때문입니다.  
  
 다음 두 가지 계정과 관련이 있습니다.  
  
- 애플리케이션 계정은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]가 실행되는 사용자 계정입니다.  
  
- 연결 계정은 SQL Server에 연결하는 데 사용되는 ID입니다. 연결에서 SQL 인증을 사용하는 경우에는 이 ID가 Visual Studio가 실행되는 ID와 달라도 무방합니다.  
  
  SQL 디버깅을 수행하려면 애플리케이션 계정이 연결 계정과 일치하거나 sysadmin이어야 합니다.  
  
  sa 같은 SQL 로그인을 사용하는 경우 애플리케이션 계정은 SQL Server에서 sysadmin으로 설정되어 있어야 합니다. 기본적으로 SQL Server가 실행되고 있는 컴퓨터의 관리자는 SQL Server sysadmin입니다.  
  
  이 오류를 해결하려면 다음 작업을 수행해야 합니다.  
  
- 권한 설정을 확인합니다. 자세한 내용은 [방법: 디버깅을 위한 SQL Server 권한 설정](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)을 참조하세요.  
  
- SQL 디버깅이 올바르게 설정되어 있는지 확인합니다.  
  
- 네트워크 또는 데이터베이스 관리자에게 문의합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL 디버깅 설정](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)   
 [방법: 디버깅을 위한 SQL Server 권한 설정](https://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
