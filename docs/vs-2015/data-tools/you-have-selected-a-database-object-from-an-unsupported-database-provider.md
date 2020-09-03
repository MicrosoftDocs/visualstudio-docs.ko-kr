---
title: 지원 되지 않는 데이터베이스 공급자에서 데이터베이스 개체를 선택 했습니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 05a4407eba52ec3940b70ffab220ef354af90e9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657786"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>지원되지 않는 데이터베이스 공급자에서 데이터베이스 공급자를 선택했습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] )는 SQL Server에 대 한 .NET Framework Data Provider ()만 지원 <xref:System.Data.SqlClient> 합니다. **확인**을 클릭하고 지원되지 않은 데이터베이스 공급자의 개체를 사용하여 계속 작업을 할 수 있지만 런타임에 예상치 못한 동작이 발생할 수도 있습니다.

> [!NOTE]
> .NET Framework Data Provider for SQL Server를 사용하는 데이터 연결만 지원됩니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

- **확인**을 클릭하여 지원되지 않는 데이터베이스 공급자를 사용하는 연결에 매핑할 엔터티 클래스를 계속 디자인합니다. 지원되지 않는 데이터베이스 공급자를 사용하면 예상치 못한 동작이 발생할 수도 있습니다.

     또는

- **취소**를 클릭합니다.

     작업이 중지됩니다. .NET Framework Provider for SQL Server를 사용하는 데이터 연결을 만들거나 사용합니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [.NET Framework 데이터 공급자](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)