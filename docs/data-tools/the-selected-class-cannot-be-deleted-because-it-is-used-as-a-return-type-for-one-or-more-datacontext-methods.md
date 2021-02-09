---
title: 선택한 클래스를 삭제할 수 없습니다.
description: 선택한 클래스가 하나 이상의 DataContext 메서드의 반환 형식으로 사용되므로 해당 클래스를 삭제할 수 없습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a9948df37df4faf7cc5349b2729ca4f648d973cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866387"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>선택한 클래스가 하나 이상의 DataContext 메서드의 반환 형식으로 사용되므로 해당 클래스를 삭제할 수 없습니다.

하나 이상의 <xref:System.Data.Linq.DataContext> 메서드 반환 형식은 선택한 엔터티 클래스입니다. 메서드의 반환 형식으로 사용 되는 엔터티 클래스를 삭제 <xref:System.Data.Linq.DataContext> 하면 프로젝트 컴파일이 실패 합니다. 선택한 엔터티 클래스를 삭제하려면 해당 엔터티 클래스를 사용하는 <xref:System.Data.Linq.DataContext> 메서드를 식별하고 해당 메서드의 반환 형식을 서로 다른 엔터티 클래스로 설정합니다.

<xref:System.Data.Linq.DataContext> 메서드의 반환 형식을 원래 자동으로 생성된 형식으로 되돌리려면 우선 **메서드** 창에서 <xref:System.Data.Linq.DataContext> 메서드를 삭제한 다음, 개체를 **서버 탐색기**/**데이터베이스 탐색기** 에서 **O/R 디자이너** 로 다시 끌어 옵니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. **메서드** 창에서 <xref:System.Data.Linq.DataContext> 메서드를 선택하고 **속성** 창에서 **반환 형식** 속성을 검사하여 엔터티 클래스를 반환 형식으로 사용하는 <xref:System.Data.Linq.DataContext> 메서드를 식별합니다.

2. **반환 형식** 을 서로 다른 엔터티 클래스로 설정하거나 메서드 창에서 <xref:System.Data.Linq.DataContext> 메서드를 삭제합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
