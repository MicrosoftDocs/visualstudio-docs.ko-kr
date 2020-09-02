---
title: n 계층 애플리케이션에서 데이터 세트에 코드 추가
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending DataSets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a57a05ddb8317ea31b852ded369ad7ef69d40bd0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283088"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>n 계층 애플리케이션에서 데이터 세트에 코드 추가

*DatasetName*에 코드를 추가 하는 대신 데이터 집합에 대 한 partial 클래스 파일을 만들고 코드를 추가 하 여 데이터 집합의 기능을 확장할 수 있습니다. 데이터 집합 디자이너 파일). Partial 클래스를 사용 하면 특정 클래스에 대 한 코드를 여러 물리적 파일로 분할할 수 있습니다. 자세한 내용은 [partial](/dotnet/visual-basic/language-reference/modifiers/partial) 또는 [partial 클래스 및 메서드](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)를 참조 하세요.

데이터 집합을 정의 하는 코드는 형식화 된 데이터 집합에서 데이터 집합 정의가 변경 될 때마다 생성 됩니다. 이 코드는 데이터 집합의 구성을 수정 하는 마법사를 실행 하는 동안 변경 작업을 수행할 때도 생성 됩니다. 데이터 집합을 다시 생성 하는 동안 코드가 삭제 되지 않도록 하려면 데이터 집합의 partial 클래스 파일에 코드를 추가 합니다.

데이터 집합 및 TableAdapter 코드를 분리 한 후에는 기본적으로 각 프로젝트의 불연속 클래스 파일이 생성 됩니다. 원본 프로젝트에는 TableAdapter 코드를 포함 하는 *DatasetName* (또는 *DatasetName.Designer.cs*) 라는 파일이 있습니다. **데이터 집합 프로젝트** 속성에 지정 된 프로젝트에는 이름이 *DatasetName* (또는 *DatasetName.DataSet.Designer.cs*) 인 파일이 있습니다. 이 파일에는 데이터 집합 코드가 포함 됩니다.

> [!NOTE]
> **데이터 집합 프로젝트** 속성을 설정 하 여 데이터 집합 및 tableadapter를 분리 하는 경우 프로젝트의 기존 부분 데이터 집합 클래스는 자동으로 이동 되지 않습니다. 기존 데이터 집합 partial 클래스는 데이터 집합 프로젝트로 수동으로 이동 해야 합니다.

> [!NOTE]
> 유효성 검사 코드를 추가 해야 하는 경우 형식화 된 데이터 집합은 <xref:System.Data.DataTable.ColumnChanging> 및 이벤트 처리기를 생성 하는 기능을 제공 합니다 <xref:System.Data.DataTable.RowChanging> . 자세한 내용은 [n 계층 데이터 집합에 유효성 검사 추가](../data-tools/add-validation-to-an-n-tier-dataset.md)를 참조 하세요.

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>N 계층 응용 프로그램의 데이터 집합에 코드를 추가 하려면

1. *.Xsd* 파일이 포함 된 프로젝트를 찾습니다.

2. **.Xsd** 파일을 선택 하 여 데이터 집합을 엽니다.

3. 코드를 추가 하려는 데이터 테이블 (제목 표시줄의 테이블 이름)을 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 선택 합니다.

     Partial 클래스가 만들어지고 코드 편집기에서 열립니다.

4. Partial 클래스 선언 내에 코드를 추가 합니다.

     다음 예제에서는 NorthwindDataSet의 CustomersDataTable에 코드를 추가할 위치를 보여 줍니다.

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```

    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>추가 정보

- [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md)
- [n 계층 애플리케이션에서 TableAdapter에 코드 추가](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [TableAdapter 만들기 및 구성](create-and-configure-tableadapters.md)
- [계층적 업데이트 개요](hierarchical-update.md)
- [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)
