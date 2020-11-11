---
title: 속성 형식이 일치 하지 않습니다.
description: 연결을 만들 수 없습니다. 속성 형식이 일치 하지 않습니다. 이 Visual Studio 개체 관계형 디자이너 (O/R 디자이너) 메시지에 대 한 정보를 봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8413ffd8b5bf2af4c4d7272173a9cb4d0fbf6cbc
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518468"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>&lt;association name&gt; 연결을 만들 수 없습니다. - 속성 형식이 일치하지 않는 경우

연결을 만들 수 없습니다 \<association name> . 속성 형식이 일치 하지 않습니다. 속성에 일치 하는 형식이 없습니다 \<property names> .

연결이 **연결 편집기** 대화 상자에서 선택한 **연결 속성** 에 의해 정의되었습니다. 연결의 각 측에 대한 속성은 동일한 데이터 형식이어야 합니다.

메시지에 나열된 속성은 동일한 데이터 형식을 갖지 않습니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 메시지를 검사하여 메시지에서 호출된 속성을 기록합니다.

2. **확인** 을 클릭하여 대화 상자를 닫습니다.

3. **연결 속성** 을 검사하고 동일한 데이터 형식의 속성을 선택합니다.

4. **확인** 을 클릭합니다.

## <a name="see-also"></a>참조

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [방법: LINQ to SQL 클래스 간의 연결 만들기 (O/R 디자이너)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)