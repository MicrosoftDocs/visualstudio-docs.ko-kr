---
title: n 계층 애플리케이션에서 TableAdapter에 코드 추가
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3ea451ac60de971677ee2f7910b28b334c67dff3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283101"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>n 계층 애플리케이션에서 TableAdapter에 코드 추가
TableAdapter의 partial 클래스 파일을 만들고 코드를 추가 ( *DatasetName* 파일에 코드를 추가 하는 대신) 하 여 tableadapter의 기능을 확장할 수 있습니다. Partial 클래스를 사용 하면 특정 클래스에 대 한 코드를 여러 물리적 파일로 분할할 수 있습니다. 자세한 내용은 [부분](/dotnet/visual-basic/language-reference/modifiers/partial) 또는 [부분 (형식)](/dotnet/csharp/language-reference/keywords/partial-type)을 참조 하세요.

TableAdapter를 정의 하는 코드는 데이터 집합에서 TableAdapter가 변경 될 때마다 생성 됩니다. 이 코드는 TableAdapter의 구성을 수정 하는 마법사를 실행 하는 동안 변경 된 경우에도 생성 됩니다. TableAdapter를 다시 생성 하는 동안 코드가 삭제 되지 않도록 하려면 TableAdapter의 partial 클래스 파일에 코드를 추가 합니다.

데이터 집합 및 TableAdapter 코드를 분리 한 후에는 기본적으로 각 프로젝트의 불연속 클래스 파일이 생성 됩니다. 원본 프로젝트에는 TableAdapter 코드를 포함 하는 *DatasetName* (또는 *DatasetName.Designer.cs*) 라는 파일이 있습니다. **데이터 집합 프로젝트** 속성에 지정 된 프로젝트에는 데이터 집합 코드를 포함 하는 *DatasetName* (또는 *DatasetName.DataSet.Designer.cs*) 라는 파일이 있습니다.

> [!NOTE]
> **데이터 세트 프로젝트** 속성을 설정하여 데이터 세트와 TableAdapters를 분리할 때는 프로젝트의 기존 부분 데이터 세트 클래스가 자동으로 이동되지 않습니다. 기존 부분 데이터 집합 클래스는 데이터 집합 프로젝트로 수동으로 이동 해야 합니다.

> [!NOTE]
> 데이터 집합은 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 유효성 검사가 필요할 때 및 이벤트 처리기를 생성 하는 기능을 제공 합니다. 자세한 내용은 [n 계층 데이터 집합에 유효성 검사 추가](../data-tools/add-validation-to-an-n-tier-dataset.md)를 참조 하세요.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>N 계층 응용 프로그램에서 TableAdapter에 사용자 코드를 추가 하려면

1. *.Xsd* 파일이 포함 된 프로젝트를 찾습니다.

2. *.Xsd* 파일을 두 번 클릭 하 여 **데이터 세트 디자이너**을 엽니다.

3. 코드를 추가할 TableAdapter를 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 선택 합니다.

     Partial 클래스가 만들어지고 코드 편집기에서 열립니다.

4. Partial 클래스 선언 내에 코드를 추가 합니다.

5. 다음 예제에서는에서에 코드를 추가할 위치를 보여 줍니다 `CustomersTableAdapter` `NorthwindDataSet` .

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>추가 정보

- [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md)
- [n 계층 애플리케이션에서 데이터 세트에 코드 추가](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [TableAdapter 만들기 및 구성](create-and-configure-tableadapters.md)
- [계층적 업데이트 개요](hierarchical-update.md)
