---
title: 속성이 연결에 참여하고 있으므로 이 속성을 삭제할 수 없음
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: aab2d2e3151786b45889262680d2f0815f684b6a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535384"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>&lt;property name&gt; 속성은 &lt;association name&gt; 연결에 참여하고 있으므로 삭제할 수 없음

선택한 속성이 오류 메시지에 표시된 클래스 간 연결의 **연결 속성**으로 설정되었습니다. 속성이 데이터 클래스 간 연결에 참여 중인 경우에는 해당 속성을 삭제할 수 없습니다.

**연결 속성**을 데이터 클래스의 다른 속성으로 설정하면 원하는 속성을 삭제할 수 있습니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. **O/R 디자이너** 에서 오류 메시지에 표시 된 데이터 클래스를 연결 하는 연결 선을 선택 합니다.

2. 해당 선을 두 번 클릭하여 **연결 편집기** 대화 상자를 엽니다.

3. **연결 속성**에서 속성을 제거합니다.

4. 속성 삭제를 다시 한 번 시도합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)