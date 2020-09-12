---
title: 지원 방법을 삭제할 수 없음
description: 이 관련 메서드는 다음과 같은 기본 삽입, 업데이트 및 삭제 메서드를 지원하는 메서드입니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 66acc8486bcb261bb97a1611ff0c6753caa65dee
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037558"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>이 관련 메서드는 다음과 같은 기본 삽입, 업데이트 및 삭제 메서드를 지원하는 메서드입니다.

이 관련 메서드는 다음과 같은 기본 `Insert` , 또는 메서드에 대 한 지원 메서드입니다 `Update` `Delete` . 이 관련 메서드를 삭제하면 이러한 메서드도 삭제됩니다. 계속하시겠습니까?

선택한 `DataContext` 메서드는 현재 `Insert` `Update` `Delete` **O/R 디자이너**의 엔터티 클래스 중 하나에 대 한, 또는 메서드 중 하나로 사용 됩니다. 선택한 메서드를 삭제 하면이 메서드를 사용 하는 엔터티 클래스가 업데이트 중에 삽입, 업데이트 또는 삭제를 수행 하는 기본 런타임 동작으로 되돌아갑니다.

## <a name="selected-method-options"></a>선택한 메서드 옵션

- 선택한 메서드를 삭제 하 여 엔터티 클래스가 런타임 업데이트를 사용 하도록 하려면 **예**를 클릭 합니다.

   선택한 메서드가 삭제 되 고이 메서드를 사용 하 여 업데이트 동작을 재정의 하는 모든 클래스가 기본 LINQ to SQL 런타임 동작을 사용 하 여 되돌립니다.

- 선택한 메서드를 변경 하지 않고 메시지 상자를 닫으려면 **아니요**를 클릭 합니다.

   메시지 상자가 닫히고 변경되지 않습니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)