---
title: TableAdapter 만들기 및 구성
ms.date: 09/01/2017
ms.topic: how-to
helpviewer_keywords:
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 90dcc8e623f258721c71ef02082500a0736764e4
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282676"
---
# <a name="create-and-configure-tableadapters"></a>TableAdapter 만들기 및 구성

Tableadapter는 응용 프로그램과 데이터베이스 간의 통신을 제공 합니다. 데이터베이스에 연결 하 여 쿼리 또는 저장 프로시저를 실행 하 고 새 데이터 테이블을 반환 하거나 반환 된 데이터가 있는 기존를 채웁니다 <xref:System.Data.DataTable> . Tableadapter는 응용 프로그램에서 업데이트 된 데이터를 다시 데이터베이스로 보낼 수도 있습니다.

Tableadapter는 다음 작업 중 하나를 수행할 때 생성 됩니다.

- **서버 탐색기** 에서 **데이터 세트 디자이너**으로 데이터베이스 개체를 끌어 옵니다.

- 데이터 소스 구성 마법사를 실행 하 고 **데이터베이스** 또는 **웹 서비스** 데이터 원본 유형 중 하나를 선택 합니다.

   ![Visual Studio의 데이터 소스 구성 마법사](media/data-source-configuration-wizard.png)

또한 **도구 상자** 에서 tableadapter를 **데이터 세트 디자이너** 화면의 빈 영역으로 끌어서 새 tableadapter를 만들고 데이터 소스를 사용 하 여 구성할 수 있습니다.

Tableadapter에 대 한 소개는 [tableadapter를 사용 하 여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)를 참조 하세요.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>TableAdapter 구성 마법사 사용

**Tableadapter 구성 마법사** 를 실행 하 여 tableadapter 및 연결 된 datatable을 만들거나 편집 합니다. **데이터 세트 디자이너**에서 기존 TableAdapter를 마우스 오른쪽 단추로 클릭 하 여 구성할 수 있습니다.

![raddata Table 어댑터 구성 마법사](../data-tools/media/raddata-table-adapter-configuration-wizard.png)

**데이터 세트 디자이너** 포커스가 있을 때 도구 상자에서 새 TableAdapter를 끌면 마법사가 시작 되 고 TableAdapter가 연결 해야 하는 데이터 소스를 지정 하 라는 메시지가 표시 됩니다. 다음 페이지에서 마법사는 데이터베이스와 통신 하는 데 사용 해야 하는 명령의 종류 (SQL 문 또는 저장 프로시저)를 묻는 메시지를 표시 합니다. 데이터 원본에 이미 연결 된 TableAdapter를 구성 하는 경우에는이 내용이 표시 되지 않습니다.

- 데이터베이스에 대 한 올바른 사용 권한이 있는 경우 기본 데이터베이스에 새 저장 프로시저를 만들 수 있는 옵션이 있습니다. 이러한 권한이 없는 경우에는이 옵션을 사용할 수 없습니다.

- TableAdapter의 **SELECT**, **INSERT**, **UPDATE**및 **DELETE** 명령에 대해 기존 저장 프로시저를 실행 하도록 선택할 수도 있습니다. 예를 들어 **Update** 명령에 할당 된 저장 프로시저는 메서드가 호출 될 때 실행 됩니다 `TableAdapter.Update()` .

선택한 저장 프로시저에서 데이터 테이블의 해당 열로 매개 변수를 매핑합니다. 예를 들어 저장 프로시저가 테이블의 열에 전달 하는 이라는 매개 변수를 허용 하는 경우 `@CompanyName` `CompanyName` 매개 변수의 **원본 열** 을로 설정 `@CompanyName` `CompanyName` 합니다.

> [!NOTE]
> SELECT 명령에 할당 되는 저장 프로시저는 마법사의 다음 단계에서 이름을 지정 하는 TableAdapter의 메서드를 호출 하 여 실행 합니다. 기본 메서드는 이므로 `Fill` SELECT 프로시저를 실행 하는 데 일반적으로 사용 되는 코드는 `TableAdapter.Fill(tableName)` 입니다. 에서 기본 이름을로 변경 하는 경우 사용자가 `Fill` `Fill` 할당 한 이름으로 대체 하 고 "tableadapter"를 TableAdapter의 실제 이름 (예:)으로 바꿉니다 `CustomersTableAdapter` .

- 업데이트를 **데이터베이스에 직접 보내는 메서드 만들기** 옵션을 선택 하는 것은 속성을 true로 설정 하는 것과 같습니다 `GenerateDBDirectMethods` . 원래 SQL 문에서 충분한 정보를 제공하지 않거나 쿼리가 업데이트할 수 없는 쿼리인 경우에는 이 옵션을 사용할 수 없습니다. 예를 들어 **조인** 쿼리와 단일 (스칼라) 값을 반환 하는 쿼리에서 이러한 상황이 발생할 수 있습니다.

마법사의 **고급 옵션** 을 사용 하 여 다음 작업을 수행할 수 있습니다.

- **SQL 문 생성** 페이지에 정의 된 SELECT 문을 기반으로 INSERT, UPDATE 및 DELETE 문을 생성 합니다.
- 낙관적 동시성 사용
- INSERT 및 UPDATE 문을 실행 한 후 데이터 테이블을 새로 고칠지 여부를 지정 합니다.

## <a name="configure-a-tableadapters-fill-method"></a>TableAdapter의 Fill 메서드 구성

TableAdapter의 테이블 스키마를 변경 해야 하는 경우가 있습니다. 이렇게 하려면 TableAdapter의 기본 메서드를 수정 합니다 `Fill` . Tableadapter는 `Fill` 연결 된 데이터 테이블의 스키마를 정의 하는 기본 메서드를 사용 하 여 생성 됩니다. 기본 `Fill` 방법은 TableAdapter를 처음 구성할 때 입력 한 쿼리 또는 저장 프로시저를 기반으로 합니다. 데이터 집합 디자이너의 데이터 테이블 아래에 있는 첫 번째 (최상위) 메서드입니다.

![쿼리가 여러 개 포함된 TableAdapter](../data-tools/media/tableadapter.gif)

TableAdapter의 main 메서드에 대 한 모든 변경 내용은 `Fill` 연결 된 데이터 테이블의 스키마에 반영 됩니다. 예를 들어 main 메서드의 쿼리에서 열을 제거 하면 `Fill` 연결 된 데이터 테이블 에서도 해당 열이 제거 됩니다. 또한 주 메서드에서 열을 제거 하면 `Fill` 해당 TableAdapter에 대 한 추가 쿼리에서 해당 열이 제거 됩니다.

TableAdapter 쿼리 구성 마법사를 사용 하 여 TableAdapter에 대 한 추가 쿼리를 만들고 편집할 수 있습니다. 이러한 추가 쿼리는 스칼라 값을 반환 하는 경우를 제외 하 고 테이블 스키마를 준수 해야 합니다.  각 추가 쿼리에는 지정 된 이름이 있습니다.

다음 예제에서는 이라는 추가 쿼리를 호출 하는 방법을 보여 줍니다 `FillByCity` .

`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")`

### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>새 쿼리를 사용 하 여 TableAdapter 쿼리 구성 마법사를 시작 하려면

1. **데이터 세트 디자이너**에서 데이터 세트를 엽니다.

2. 새 쿼리를 만드는 경우 **도구 상자** 의 **데이터 집합** 탭에서 **쿼리** 개체를로 끌어 오거나 <xref:System.Data.DataTable> TableAdapter의 바로 가기 메뉴에서 **쿼리 추가** 를 선택 합니다. 연결 된 없이 TableAdapter를 만드는 **데이터 세트 디자이너**의 빈 영역으로 **쿼리** 개체를 끌어올 수도 있습니다 <xref:System.Data.DataTable> . 이러한 쿼리는 단일 (스칼라) 값만 반환 하거나 데이터베이스에 대해 UPDATE, INSERT 또는 DELETE 명령을 실행할 수 있습니다.

3. **데이터 연결 선택** 화면에서 쿼리에서 사용할 연결을 선택 하거나 만듭니다.

    > [!NOTE]
    > 이 화면은 디자이너에서 사용할 적절 한 연결을 결정할 수 없는 경우 나 사용할 수 있는 연결이 없는 경우에만 표시 됩니다.

4. **명령 유형 선택** 화면에서 데이터베이스에서 데이터를 가져오는 다음 방법 중에서 선택 합니다.

    - **Sql 문을 사용** 하 여 데이터베이스에서 데이터를 선택 하는 sql 문을 입력할 수 있습니다.

    - **새 저장 프로시저 만들기** 를 사용 하면 마법사에서 지정 된 SELECT 문을 기반으로 데이터베이스에 새 저장 프로시저를 만들 수 있습니다.

    - **기존 저장 프로시저를 사용** 하면 쿼리를 실행할 때 기존 저장 프로시저를 실행할 수 있습니다.

### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>기존 쿼리에서 TableAdapter 쿼리 구성 마법사를 시작 하려면

- 기존 TableAdapter 쿼리를 편집 하는 경우 쿼리를 마우스 오른쪽 단추로 클릭 한 다음 바로 가기 메뉴에서 **구성** 을 선택 합니다.

    > [!NOTE]
    > TableAdapter의 주 쿼리를 마우스 오른쪽 단추로 클릭 하면 TableAdapter와 스키마를 다시 <xref:System.Data.DataTable> 만듭니다. 그러나 TableAdapter에서 추가 쿼리를 마우스 오른쪽 단추로 클릭 하면 선택한 쿼리만 구성 됩니다. Tableadapter **구성 마법사** 는 tableadapter 정의를 다시 구성 하는 반면 **Tableadapter 쿼리 구성 마법사** 는 선택한 쿼리를 다시 구성 합니다.

### <a name="to-add-a-global-query-to-a-tableadapter"></a>TableAdapter에 전역 쿼리를 추가 하려면

- 전역 쿼리는 단일 (스칼라) 값을 반환 하거나 값을 반환 하지 않는 SQL 쿼리입니다. 일반적으로 전역 함수는 삽입, 업데이트 및 삭제와 같은 데이터베이스 작업을 수행 합니다. 또한 테이블의 고객 수 또는 특정 주문의 모든 항목에 대 한 총 요금 같은 정보를 집계 합니다.

     **도구 상자** 의 **데이터 집합** 탭에서 **데이터 세트 디자이너**의 빈 영역으로 **쿼리** 개체를 끌어서 전역 쿼리를 추가 합니다.

- 원하는 작업을 수행 하는 쿼리를 제공 합니다 (예:) `SELECT COUNT(*) AS CustomerCount FROM Customers` .

    > [!NOTE]
    > **쿼리** 개체를 **데이터 세트 디자이너** 직접 끌면 스칼라 (단일) 값만 반환 하는 메서드가 만들어집니다. 선택한 쿼리나 저장 프로시저가 둘 이상의 값을 반환할 수 있지만 마법사로 만든 메서드는 단일 값만 반환 합니다. 예를 들어 쿼리는 반환 된 데이터에서 첫 번째 행의 첫 번째 열을 반환할 수 있습니다.

## <a name="see-also"></a>참조

- [TableAdapters를 사용하여 데이터 세트 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)
