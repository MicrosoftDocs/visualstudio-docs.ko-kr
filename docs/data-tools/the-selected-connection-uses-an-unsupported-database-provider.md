---
title: 지원 되지 않는 데이터베이스 공급자
description: 선택한 연결에서 지원되지 않는 데이터베이스 공급자를 사용합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c8fa073b47927f673914156c586bf27a121e53ea
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037571"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>선택한 연결에서 지원되지 않는 데이터베이스 공급자를 사용합니다.

이 메시지는 SQL Server에 대 한 .NET Framework Data Provider를 사용 하지 않는 항목을 **서버 탐색기** 또는 **데이터베이스 탐색기** 에서 [Visual Studio의 LINQ to SQL 도구로](../data-tools/linq-to-sql-tools-in-visual-studio2.md)끌 때 나타납니다.

**O/R 디자이너** 는 SQL Server에 대해 .NET Framework 공급자를 사용 하는 데이터 연결만 지원 합니다. Microsoft SQL Server 또는 Microsoft SQL Server 데이터베이스 파일에 대한 연결만 유효합니다.

이 오류를 해결 하려면 SQL Server에 대 한 .NET Framework Data Provider를 사용 하는 데이터 연결의 항목만 **O/R 디자이너**에 추가 합니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Data.SqlClient>
- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
