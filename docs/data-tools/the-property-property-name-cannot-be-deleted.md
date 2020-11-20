---
title: 속성을 삭제할 수 없음
description: 속성을 삭제할 수 없습니다. 이 Visual Studio 개체 관계형 디자이너 (O/R 디자이너) 메시지에 대 한 정보를 봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bdca9758116c551604b5f75f141c15107c1fc890
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998362"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>\<property name> 속성을 삭제할 수 없습니다.

속성이 \<property name> 및 간의 상속에 대 한 **판별자 속성** 으로 설정 되어 있으므로 삭제할 수 없습니다. \<class name>\<class name>

선택한 속성이 오류 메시지에 표시된 클래스 간 상속의 **판별자 속성** 으로 설정되었습니다. 속성이 데이터 클래스 간 상속 구성에 참여 중인 경우에는 해당 속성을 삭제할 수 없습니다.

**판별자 속성** 을 데이터 클래스의 다른 속성으로 설정하면 원하는 속성을 삭제할 수 있습니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. **O/R 디자이너** 에서 오류 메시지에 표시 된 데이터 클래스를 연결 하는 상속 선을 선택 합니다.

2. **판별자** 속성을 다른 속성으로 설정합니다.

3. 속성 삭제를 다시 한 번 시도합니다.

## <a name="see-also"></a>추가 정보

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)