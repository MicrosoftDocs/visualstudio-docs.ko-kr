---
title: 디버깅 없이 Transact-SQL 실행이 중지됨 | Microsoft Docs
ms.date: 11/08/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_sql_executed_but_not_debugged
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66a1f60673d1bdfb58b1a101bd1571637c41f556
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851530"
---
# <a name="error-transact-sql-execution-ended-without-debugging"></a>오류: 디버깅 없이 Transact-SQL 실행이 중지됨

이 오류는 Transact-SQL 또는 SQLCLR 프로시저를 디버그하려 할 때 디버거가 SQL Server에서 디버깅 메시지를 받지 못하는 경우에 발생합니다.

이 문제는 네트워크 문제나 SQL Server와 관련된 문제가 원인일 수도 있지만 대부분의 경우는 권한 문제 때문입니다.

다음 두 가지 계정과 관련이 있습니다.

- 애플리케이션 계정은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]가 실행되는 사용자 계정입니다.

- 연결 계정은 SQL Server에 연결하는 데 사용되는 ID입니다. 연결에서 SQL 인증을 사용하는 경우에는 이 계정이 Visual Studio가 실행되는 ID와 달라도 무방합니다.

  SQL 디버깅을 수행하려면 애플리케이션 계정이 연결 계정과 일치하거나 sysadmin이어야 합니다.

  sa와 같은 SQL 계정 이름을 사용하는 경우 애플리케이션 계정이 SQL Server에 sysadmin으로 설정되어야 합니다. 기본적으로 SQL Server가 실행되고 있는 컴퓨터의 관리자는 SQL Server sysadmin입니다.

  이 오류를 해결하려면 다음 작업을 수행해야 합니다.

  - 권한 설정을 확인합니다. 자세한 내용은 [방법: 디버깅을 위한 SQL Server 권한 설정](/previous-versions/w1bhybwz(v=vs.100))을 참조하세요.

  - SQL 디버깅이 올바르게 설정되어 있는지 확인합니다.

  - 네트워크 또는 데이터베이스 관리자에게 문의합니다.

## <a name="see-also"></a>참조

- [SQL 디버깅 설정](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100))
- [방법: 디버깅을 위한 SQL Server 권한 설정](/previous-versions/w1bhybwz(v=vs.100))
- [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)
- [Remote Debugging](../debugger/remote-debugging.md)