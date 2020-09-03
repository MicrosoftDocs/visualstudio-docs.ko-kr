---
title: 데이터 세트 만들기 및 구성
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
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c84105387c708fa16e0b1d5c3294ef909466524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631200"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Visual Studio에서 데이터 세트 만들기 및 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 *집합* 은 데이터베이스의 데이터를 메모리에 저장 하 고 변경 내용 추적을 지원 하 여 데이터베이스에 항상 연결 되어 있지 않아도 해당 데이터에 대 한 CRUD (만들기, 읽기, 업데이트 및 삭제) 작업을 가능 하 게 하는 개체 집합입니다. 데이터 집합은 데이터 비즈니스 응용 프로그램에 대 한 간단한 *양식을* 위해 설계 되었습니다. 새 응용 프로그램의 경우 Entity Framework를 사용 하 여 메모리에 데이터를 저장 하 고 모델링 하는 것이 좋습니다. 데이터 집합을 사용 하려면 데이터베이스 개념에 대 한 기본 지식이 있어야 합니다.

 <xref:System.Data.DataSet>디자인 타임에 **데이터 소스 구성 마법사**를 사용 하 여 Visual Studio에서 형식화 된 클래스를 만듭니다. 데이터 집합을 프로그래밍 방식으로 만드는 방법에 대 한 자세한 내용은 [데이터 집합 만들기](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc)를 참조 하세요.

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>데이터 소스 구성 마법사를 사용 하 여 새 데이터 집합 만들기

1. **프로젝트** 메뉴에서 **새 데이터 소스 추가** 를 클릭 하 여 **데이터 소스 구성 마법사**를 시작 합니다.

2. 연결할 데이터 원본의 유형을 선택 합니다.

     ![데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png "데이터 소스 구성 마법사")

3. 데이터베이스에서 데이터 집합에 대 한 데이터 원본으로 사용할 데이터베이스를 선택 합니다.

     ![데이터 원본 연결 선택](../data-tools/media/data-source-choose-a-connection.png "데이터 원본 연결 선택")

4. 데이터 집합에 표시할 테이블 (또는 개별 열), 저장 프로시저, 함수 및 뷰를 데이터베이스에서 선택 합니다.

     ![데이터베이스 개체 선택](../data-tools/media/raddata-chose-objects.png "raddata 선택 개체")

5. **마침**을 클릭합니다.

6. 데이터 집합은 **솔루션 탐색기**노드로 표시 됩니다.

     ![솔루션 탐색기의 데이터 집합](../data-tools/media/dataset-in-solution-explorer.png "솔루션 탐색기의 데이터 집합")

     해당 노드를 클릭 하면 데이터 집합 **디자이너**에 데이터 집합이 표시 됩니다. 데이터 집합의 각 테이블에는 맨 아래에 표시 되는 연결 된 TableAdapter 개체가 있습니다. 테이블 어댑터는 데이터 집합을 채우는 데 사용 되며 필요에 따라 데이터베이스에 명령을 보낼 수 있습니다.

     ![데이터 세트 디자이너](../data-tools/media/dataset-designer.png "데이터 세트 디자이너")

7. 테이블을 연결 하는 관계 선은 데이터베이스에 정의 된 테이블 관계를 나타냅니다. 기본적으로 데이터베이스의 foreign key 제약 조건은 업데이트 및 삭제 규칙이 없음으로 설정 된 관계로만 표시 됩니다. 일반적으로 원하는 것입니다. 그러나 해당 줄을 클릭 하 여 **관계** 대화 상자를 표시할 수 있습니다 .이 대화 상자에서 계층적 업데이트의 동작을 변경할 수 있습니다. 자세한 내용은 [데이터 집합의 관계](../data-tools/relationships-in-datasets.md) 및 [계층적 업데이트](../data-tools/hierarchical-update.md)를 참조 하세요.

     ![데이터 집합 관계 대화 상자](../data-tools/media/raddata-relation-dialog.png "raddata 관계 대화 상자")

8. 테이블에서 테이블, 테이블 어댑터 또는 열 이름을 클릭 하 여 **속성** 창에서 해당 속성을 확인 합니다. 여기에서 일부 값을 수정할 수 있습니다. 원본 데이터베이스가 아니라 데이터 집합을 수정 하는 것만 명심 하세요.

     ![데이터 집합 열 속성](../data-tools/media/dataset-column-properties.png "데이터 집합 열 속성")

9. 새 테이블 또는 테이블 어댑터를 데이터 집합에 추가 하거나, 기존 테이블 어댑터에 대 한 새 쿼리를 추가 하거나, **도구 상자** 탭에서 해당 항목을 끌어 테이블 간에 새 관계를 지정할 수 있습니다. 이 탭은 **데이터 집합 디자이너** 에 포커스가 있을 때 나타납니다.

     ![데이터 집합 도구 상자](../data-tools/media/raddata-dataset-toolbox.png "raddata 데이터 집합 도구 상자")

10. 그런 다음 데이터를 사용 하 여 데이터 집합을 채우는 방법을 지정 하는 것이 좋습니다. 이렇게 하려면 **TableAdapter 구성 마법사**를 사용 합니다. 자세한 내용은 [tableadapter를 사용 하 여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md) 를 참조 하세요.

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>기존 데이터 집합에 데이터베이스 테이블 또는 기타 개체 추가
 이 절차에서는 데이터 집합을 처음 만들 때 사용한 것과 동일한 데이터베이스에서 테이블을 추가 하는 방법을 보여 줍니다.

1. **솔루션 탐색기** 에서 데이터 집합 노드를 클릭 하 여 데이터 집합 디자이너를 포커스로 가져옵니다.

2. Visual Studio의 왼쪽 여백에 있는 **데이터 원본** 탭을 클릭 하거나 빠른 시작 `Data Sources` 을 **QuickLaunch**입력 합니다.

3. 데이터 집합 노드를 마우스 오른쪽 단추로 클릭 하 고 **마법사를 사용 하 여 데이터 원본 구성** 을 선택 합니다.

     ![데이터 소스 상황에 맞는 메뉴](../data-tools/media/data-source-context-menu.png "데이터 소스 상황에 맞는 메뉴")

4. 마법사를 사용 하 여 데이터 집합에 추가할 추가 테이블, 저장 프로시저 또는 기타 데이터베이스 개체를 지정 합니다.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>데이터 집합에 독립 실행형 데이터 테이블 추가

1. **데이터 세트 디자이너**에서 데이터 세트를 엽니다.

2. <xref:System.Data.DataTable> **도구 상자** 의 **데이터 집합** 탭에서 **데이터 세트 디자이너**로 클래스를 끌어 옵니다.

3. 열을 추가 하 여 데이터 테이블을 정의 합니다. 자세한 내용은 [방법: DataTable에 열 추가](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)를 참조 하세요.

4. 독립 실행형 테이블은 `Fill` 데이터를 채울 수 있도록 독립 실행형 테이블에서 논리를 구현 해야 합니다. 독립 실행형 데이터 테이블을 채우는 방법에 대 한 자세한 내용은 [DataAdapter에서 데이터 집합 채우기](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153)를 참조 하세요.
