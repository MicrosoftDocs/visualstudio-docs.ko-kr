---
title: 속성이 두 번 나열 됨
description: 연결을 만들 수 없습니다. 속성은 두 번 나열 됩니다. 이 Visual Studio 개체 관계형 디자이너 (O/R 디자이너) 메시지에 대 한 정보를 봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4466515f390db2ac3c03d302fd6ffb8da3a6176f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867349"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>&lt;association name&gt; 연결을 만들 수 없습니다. - 속성이 두 번 나열된 경우

연결을 만들 수 없습니다 \<association name> . 동일한 속성이 두 번 이상 나열 \<property name> 됩니다.

연결이 **연결 편집기** 대화 상자에서 선택한 **연결 속성** 에 의해 정의되었습니다. 속성은 연결의 각 클래스에 대해 한 번만 나열될 수 있습니다.

메시지의 속성은 부모 또는 자식 클래스의 **연결 속성** 에 한 번을 초과해 나타납니다.

## <a name="to-resolve-this-condition"></a>이 문제를 해결하려면

- 메시지를 검사하여 메시지에 지정된 속성을 기록합니다.

- **확인** 을 클릭하여 메시지 상자를 닫습니다.

- **연결 속성** 을 검사하여 중복된 엔트리를 제거합니다.

- **확인** 을 클릭합니다.

## <a name="see-also"></a>참조

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [방법: LINQ to SQL 클래스 간의 연결 만들기 (O/R 디자이너)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)