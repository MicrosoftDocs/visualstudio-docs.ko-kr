---
title: 데이터 세트 디자이너에서 DataTable 만들기
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7dd762c6df5eebc9ebbf142a3ad7dfe430800802
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036771"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>연습: 데이터 세트 디자이너에서 DataTable 만들기

이 연습에서는 <xref:System.Data.DataTable> **데이터 세트 디자이너**를 사용 하 여 (TableAdapter가 없는)를 만드는 방법을 설명 합니다. Tableadapter를 포함 하는 데이터 테이블을 만드는 방법에 대 한 자세한 내용은 [Tableadapter 만들기 및 구성](../data-tools/create-and-configure-tableadapters.md)을 참조 하세요.

## <a name="create-a-new-windows-forms-application"></a>새 Windows Forms 애플리케이션 만들기

1. Visual Studio의 **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다.

2. 왼쪽 창에서 **Visual c #** 또는 **Visual Basic** 을 확장 한 다음 **Windows 데스크톱**을 선택 합니다.

3. 가운데 창에서 **Windows Forms 앱** 프로젝트 형식을 선택 합니다.

4. 프로젝트 이름을 **DataTableWalkthrough**로 지정한 다음 **확인**을 선택 합니다.

     **DataTableWalkthrough** 프로젝트가 만들어지고 **솔루션 탐색기**에 추가 됩니다.

## <a name="add-a-new-dataset-to-the-application"></a>응용 프로그램에 새 데이터 집합 추가

1. **프로젝트** 메뉴에서 **새 항목 추가**를 선택합니다.

     **새 항목 추가** 대화 상자가 나타납니다.

2. 왼쪽 창에서 **데이터**를 선택한 다음 가운데 창에서 데이터 **집합** 을 선택 합니다.

3. **추가**를 선택합니다.

     Visual Studio에서 **DataSet1** 라는 파일을 프로젝트에 추가 하 고 **데이터 세트 디자이너**에서 엽니다.

## <a name="add-a-new-datatable-to-the-dataset"></a>데이터 집합에 새 DataTable 추가

1. **도구 상자** 의 **데이터 집합** 탭에서 **데이터 세트 디자이너**로 **DataTable** 을 끌어 옵니다.

     **DataTable1** 이라는 테이블이 데이터 집합에 추가 됩니다.

2. **DataTable1** 의 제목 표시줄을 클릭 하 고 이름을 바꿉니다 `Music` .

## <a name="add-columns-to-the-datatable"></a>DataTable에 열 추가

1. **Music** 테이블을 마우스 오른쪽 단추로 클릭 합니다. **추가**를 가리킨 다음 **열**을 클릭 합니다.

2. 열의 이름을로 `SongID` 합니다.

3. **속성** 창에서 <xref:System.Data.DataColumn.DataType%2A> 속성을 <xref:System.Int16?displayProperty=fullName>로 설정합니다.

4. 이 프로세스를 반복 하 고 다음 열을 추가 합니다.

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>테이블에 대 한 기본 키 설정

모든 데이터 테이블에는 기본 키가 있어야 합니다. 기본 키는 데이터 테이블의 특정 레코드를 고유 하 게 식별 합니다.

기본 키를 설정 하려면 **SongID** 열을 마우스 오른쪽 단추로 클릭 한 다음 **기본 키 설정**을 클릭 합니다. 키 아이콘이 **SongID** 열 옆에 표시 됩니다.

## <a name="save-your-project"></a>프로젝트 저장

**DataTableWalkthrough** 프로젝트를 저장 하려면 **파일** 메뉴에서 **모두 저장**을 선택 합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 데이터 세트 만들기 및 구성](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)
