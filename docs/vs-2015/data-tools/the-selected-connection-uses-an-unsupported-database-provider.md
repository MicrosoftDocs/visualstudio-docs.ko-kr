---
title: 선택한 연결에서 지원 되지 않는 데이터베이스 공급자를 사용 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e79d8408fba54cf192d51f9d2ead8c0ffafe1f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667186"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>선택한 연결에서 지원되지 않는 데이터베이스 공급자를 사용합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 메시지는 **서버 탐색기**SQL Server에 대 한 .NET Framework Data Provider를 사용 하지 않는 항목을 / **Database Explorer** [Visual Studio의 데이터베이스 탐색기 도구로](../data-tools/linq-to-sql-tools-in-visual-studio2.md)끌 때 나타납니다.

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에서는 .NET Framework Provider for SQL Server를 사용하는 데이터 연결만 지원합니다. Microsoft SQL Server 또는 Microsoft SQL Server 데이터베이스 파일에 대한 연결만 유효합니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- .NET Framework Data Provider for SQL Server를 사용하는 데이터 연결의 항목만 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에 추가합니다.

## <a name="see-also"></a>관련 항목
 <xref:System.Data.SqlClient>[.NET Framework 데이터 공급자](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) [연습: LINQ to SQL 클래스 만들기 (O-R 디자이너)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)