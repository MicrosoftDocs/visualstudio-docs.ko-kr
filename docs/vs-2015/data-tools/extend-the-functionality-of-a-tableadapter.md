---
title: TableAdapter의 기능 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19367f812a87d6aa585e123100f1d08144c57ff9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672365"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>TableAdapter의 기능 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter의 partial 클래스 파일에 코드를 추가 하 여 TableAdapter의 기능을 확장할 수 있습니다.

 Tableadapter를 정의 하는 코드는 **데이터 세트 디자이너**에서 tableadapter가 변경 되거나 마법사에서 tableadapter의 구성을 수정할 때 다시 생성 됩니다. TableAdapter를 다시 생성 하는 동안 코드가 삭제 되지 않도록 하려면 TableAdapter의 partial 클래스 파일에 코드를 추가 합니다.

 Partial 클래스를 사용 하면 특정 클래스에 대 한 코드를 여러 물리적 파일 간에 분할할 수 있습니다. 자세한 내용은 [부분](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) 또는 [부분 (형식)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)을 참조 하세요.

## <a name="locate-tableadapters-in-code"></a>코드에서 Tableadapter 찾기
 Tableadapter는 **데이터 세트 디자이너**를 사용 하 여 디자인 되었지만 생성 된 tableadapter 클래스는의 중첩 클래스가 아닙니다 <xref:System.Data.DataSet> . Tableadapter는 TableAdapter의 연결 된 데이터 집합 이름을 기반으로 하는 네임 스페이스에 있습니다. 예를 들어 응용 프로그램에 라는 데이터 집합이 포함 된 경우 `HRDataSet` tableadapter는 네임 스페이스에 있습니다 `HRDataSetTableAdapters` . 명명 규칙은 다음 패턴을 따릅니다. *DatasetName*  +  `TableAdapters` )

 다음 예제에서는 라는 TableAdapter가를 `CustomersTableAdapter` 사용 하는 프로젝트에 있다고 가정 합니다 `NorthwindDataSet` .

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>TableAdapter의 partial 클래스를 만들려면

1. **프로젝트** 메뉴로 이동 하 고**클래스 추가**를 선택 하 여 프로젝트에 새 클래스를 추가 합니다.

2. 클래스 `CustomersTableAdapterExtended` 이름을 지정합니다.

3. **추가**를 선택합니다.

4. 다음과 같이 코드를 프로젝트의 올바른 네임 스페이스 및 partial 클래스 이름으로 바꿉니다.

     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]

## <a name="see-also"></a>관련 항목
 [TableAdapters를 사용하여 데이터 세트 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)
