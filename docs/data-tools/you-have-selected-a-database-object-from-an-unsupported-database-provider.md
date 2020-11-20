---
title: 지원 되지 않는 공급자의 개체
description: 지원 되지 않는 데이터베이스 공급자에서 데이터베이스 개체를 선택 했습니다. 이 Visual Studio (O/R 디자이너) 메시지에 대 한 정보를 봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f4f4a24e085cf4d268512ca90e5d1b3205abc9fe
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998164"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>지원되지 않는 데이터베이스 공급자에서 데이터베이스 공급자를 선택했습니다.

**O/R 디자이너** 는 SQL Server에 대 한 .NET Framework Data Provider ()만 지원 <xref:System.Data.SqlClient> 합니다. **확인** 을 클릭하고 지원되지 않은 데이터베이스 공급자의 개체를 사용하여 계속 작업을 할 수 있지만 런타임에 예상치 못한 동작이 발생할 수도 있습니다.

> [!NOTE]
> .NET Framework Data Provider for SQL Server를 사용하는 데이터 연결만 지원됩니다.

## <a name="options"></a>옵션

- **확인** 을 클릭하여 지원되지 않는 데이터베이스 공급자를 사용하는 연결에 매핑할 엔터티 클래스를 계속 디자인합니다. 지원되지 않는 데이터베이스 공급자를 사용하면 예상치 못한 동작이 발생할 수도 있습니다.

- 작업을 중지 하려면 **취소** 를 클릭 합니다. SQL Server에 대 한 .NET Framework 공급자를 사용 하는 다른 데이터 연결을 만들거나 사용 합니다.

## <a name="see-also"></a>추가 정보

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
