---
title: 연결 연결 이름을 만들 수 없습니다. &lt; &gt; 속성은 두 번 나열 됩니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e4a1d20b5c341c1643836ae30e5de6243f35454
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662555"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>&lt;association name&gt; 연결을 만들 수 없습니다. - 속성이 두 번 나열된 경우
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

연결을 만들 수 없습니다 \<association name> . 동일한 속성이 두 번 이상 나열 \<property name> 됩니다.

 연결이 **연결 편집기** 대화 상자에서 선택한 **연결 속성**에 의해 정의되었습니다. 속성은 연결의 각 클래스에 대해 한 번만 나열될 수 있습니다.

 메시지의 속성은 부모 또는 자식 클래스의 **연결 속성**에 한 번을 초과해 나타납니다.

### <a name="to-resolve-this-condition"></a>이 문제를 해결하려면

- 메시지를 검사하여 메시지에 지정된 속성을 기록합니다.

- **확인**을 클릭하여 메시지 상자를 닫습니다.

- **연결 속성**을 검사하여 중복된 엔트리를 제거합니다.

- **확인**을 클릭합니다.

## <a name="see-also"></a>참고 항목
 [Visual Studio의 LINQ to SQL 도구](https://msdn.microsoft.com/library/a57e82d5-f7e4-4894-8add-3d9ba4fce186) [방법: LINQ to SQL 클래스 간 연결 (관계) 만들기 (o/r 디자이너)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [연습: LINQ to SQL 클래스 만들기 (o-r 디자이너)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
