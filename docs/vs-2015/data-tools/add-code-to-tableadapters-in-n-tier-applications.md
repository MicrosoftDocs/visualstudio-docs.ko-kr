---
title: N 계층 응용 프로그램에서 Tableadapter에 코드 추가 | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673098"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>n 계층 애플리케이션에서 TableAdapter에 코드 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`TableAdapter` `TableAdapter` *DatasetName*에 코드를 추가 하는 대신,에 대 한 partial 클래스 파일을 만들고 코드를 추가 하 여의 기능을 확장할 수 있습니다. 데이터 집합 디자이너 파일). Partial 클래스를 사용 하면 특정 클래스에 대 한 코드를 여러 물리적 파일로 분할할 수 있습니다. 자세한 내용은 [부분](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) 또는 [부분 (형식)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334)을 참조 하세요.

 을 정의 하는 코드는가 변경 될 때마다 `TableAdapter` 생성 됩니다 `TableAdapter` . 이 코드는의 구성을 수정 하는 마법사를 실행 하는 동안 변경 된 경우에도 생성 됩니다 `TableAdapter` . 를 다시 생성 하는 동안 코드가 삭제 되지 않도록 하려면 `TableAdapter` 의 partial 클래스 파일에 코드를 추가 `TableAdapter` 합니다.

 기본적으로 데이터 집합 및 코드를 분리 한 후 `TableAdapter` 결과는 각 프로젝트의 불연속 클래스 파일입니다. 원본 프로젝트에는 이름이 *DatasetName*인 파일이 있습니다. 디자이너 .vb (또는 *DatasetName*. Designer.cs)를 포함 하는 코드를 포함 `TableAdapter` 합니다. **데이터 집합 프로젝트** 속성에 지정 된 프로젝트에는 이름이 *DatasetName*인 파일이 있습니다. 데이터 집합. .vb 또는 *DatasetName*. DataSet.Designer.cs)를 포함 하는 데이터 집합 코드를 포함 합니다.

> [!NOTE]
> `TableAdapter` **데이터 집합 프로젝트** 속성을 설정 하 여 데이터 집합 및를 분리 하는 경우 프로젝트의 기존 부분 데이터 집합 클래스는 자동으로 이동 되지 않습니다. 기존 데이터 집합 partial 클래스는 데이터 집합 프로젝트로 수동으로 이동 해야 합니다.

> [!NOTE]
> 데이터 집합 디자이너는 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 유효성 검사가 필요할 때 및 이벤트 처리기를 생성 하는 기능을 제공 합니다. 자세한 내용은 [n 계층 데이터 집합에 유효성 검사 추가](../data-tools/add-validation-to-an-n-tier-dataset.md)를 참조 하세요.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>N 계층 응용 프로그램에서 TableAdapter에 사용자 코드를 추가 하려면

1. .Xsd 파일 (데이터 집합)을 포함 하는 프로젝트를 찾습니다.

2. **.Xsd** 파일을 두 번 클릭 하 여 데이터 집합을 엽니다.

3. 코드를 추가할를 마우스 오른쪽 단추로 클릭 한 `TableAdapter` 다음**코드 보기**를 선택 합니다.

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

## <a name="see-also"></a>관련 항목
 [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md) [n 계층 응용 프로그램의 데이터 집합에 코드 추가](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [Tableadapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) [TableAdapterManager 개요](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650) [계층적 업데이트 개요](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)