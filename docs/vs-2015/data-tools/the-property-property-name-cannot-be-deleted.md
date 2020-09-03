---
title: 속성 &lt; 속성 이름을 &gt; 삭제할 수 없습니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aca36919cb4c82d6ca76e0f3eecbbacd48cde768
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667250"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>속성 &lt; 속성 이름을 &gt; 삭제할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

속성이 \<property name> 및 간의 상속에 대 한 판별자 속성으로 설정 되어 있으므로 삭제할 수 없습니다. \<class name>\<class name>

 선택한 속성이 오류 메시지에 표시된 클래스 간 상속의 **판별자 속성**으로 설정되었습니다. 속성이 데이터 클래스 간 상속 구성에 참여 중인 경우에는 해당 속성을 삭제할 수 없습니다.

 **판별자 속성**을 데이터 클래스의 다른 속성으로 설정하면 원하는 속성을 삭제할 수 있습니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. O/R 디자이너에서 오류 메시지에 표시된 데이터 클래스를 연결하는 상속 선을 선택합니다.

2. **판별자** 속성을 다른 속성으로 설정합니다.

3. 속성 삭제를 다시 한 번 시도합니다.

## <a name="see-also"></a>관련 항목
 [방법: o/r 디자이너를 사용 하 여 상속 구성](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) [데이터 클래스 상속 (o/r 디자이너)](../data-tools/data-class-inheritance-o-r-designer.md) [연습: 단일 테이블 상속을 사용 하 여 LINQ to SQL 클래스 만들기 (o/r 디자이너)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
