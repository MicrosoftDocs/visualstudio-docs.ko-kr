---
title: 트랜잭션에 데이터 저장 | Microsoft Docs
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671082"
---
# <a name="save-data-in-a-transaction"></a>트랜잭션에 데이터 저장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 네임 스페이스를 사용 하 여 트랜잭션에 데이터를 저장 하는 방법을 보여 줍니다 <xref:System.Transactions> . 이 예에서는 Northwind 샘플 데이터베이스의 `Customers` 및 `Orders` 테이블을 사용합니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 진행하려면 Northwind 샘플 데이터베이스에 액세스해야 합니다.

## <a name="create-a-windows-application"></a>Windows 응용 프로그램 만들기
 첫 번째 단계는 **Windows 응용 프로그램**을 만드는 것입니다.

#### <a name="to-create-the-new-windows-project"></a>새 Windows 프로젝트를 만들려면

1. Visual Studio의 **파일** 메뉴에서 새 **프로젝트**를 만듭니다.

2. 프로젝트 이름을 **SavingDataInATransactionWalkthrough**로 합니다.

3. **Windows 응용 프로그램**을 선택 하 고 **확인**을 선택 합니다. 자세한 내용은 [클라이언트 응용 프로그램](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)을 참조 하세요.

     **SavingDataInATransactionWalkthrough** 프로젝트가 만들어져 **솔루션 탐색기**에 추가됩니다.

## <a name="create-a-database-data-source"></a>데이터베이스 데이터 원본 만들기
 이 단계에서는 [데이터 소스 구성 마법사](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) 를 사용 하 여 `Customers` `Orders` Northwind 샘플 데이터베이스의 및 테이블을 기반으로 데이터 원본을 만듭니다.

#### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면

1. **데이터** 메뉴에서**데이터 소스 표시**를 선택 합니다.

2. **데이터** 소스 창에서 **새 데이터 소스 추가** 를 선택 하 여 **데이터 소스 구성 마법사**를 시작 합니다.

3. **데이터 소스 형식 선택**화면에서 **데이터베이스**를 선택 하 고 **다음**을 선택 합니다.

4. **데이터 연결 선택**화면에서 다음 중 하나를 수행 합니다.

    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

         또는

    - **새 연결**을 선택하여 **연결 추가/수정** 대화 상자를 시작하고 Northwind 데이터베이스에 대한 연결을 만듭니다.

5. 데이터베이스에 암호가 필요 하면 중요 한 데이터를 포함 하는 옵션을 선택 하 고 **다음**을 선택 합니다.

6. **응용 프로그램 구성 파일에 연결 문자열 저장** 화면에서 **다음**을 선택 합니다.

7. **데이터베이스 개체 선택** 화면에서 **테이블** 노드를 확장 합니다.

8. `Customers`및 테이블을 선택 하 고 `Orders` **마침**을 선택 합니다.

     **NorthwindDataSet** 가 프로젝트에 추가 되 고 `Customers` 및 `Orders` 테이블이 **데이터 소스** 창에 표시 됩니다.

## <a name="addcontrols-to-the-form"></a>폼에 컨트롤 추가
 **데이터 소스** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Windows form에서 데이터 바인딩된 컨트롤을 만들려면

- **데이터 소스** 창에서 **Customers** 노드를 확장 합니다.

- 주 **Customers** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어서 놓습니다.

     <xref:System.Windows.Forms.DataGridView> 컨트롤과 레코드 탐색에 사용되는 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>가 폼에 나타납니다. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> 및 <xref:System.Windows.Forms.BindingNavigator>가 구성 요소 트레이에 나타납니다.

- 관련 **Orders** 노드 (주 **주문** 노드가 아닌, **Fax** 열 아래의 관련 자식 테이블 노드)를 **customersdatagridview**아래에 있는 폼으로 끕니다.

     <xref:System.Windows.Forms.DataGridView>가 폼에 나타납니다. OrdersTableAdapter가 <xref:System.Windows.Forms.BindingSource> 구성 요소 트레이에 표시 됩니다.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>시스템 트랜잭션 어셈블리에 대 한 참조 추가
 트랜잭션은 <xref:System.Transactions> 네임스페이스를 사용합니다. 시스템 트랜잭션 어셈블리에 대 한 프로젝트 참조는 기본적으로 추가 되지 않으므로 수동으로 추가 해야 합니다.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System.Transactions DLL 파일에 대한 참조를 추가하려면

1. **프로젝트** 메뉴에서**참조 추가**를 선택 합니다.

2. **.Net** 탭에서 **시스템 트랜잭션**을 선택 하 고 **확인**을 선택 합니다.

     **System.Transactions**에 대한 참조가 프로젝트에 추가됩니다.

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator의 SaveItem 단추에 코드 Modifythe
 폼에 끌어 놓은 첫 번째 테이블의 경우 코드는 기본적으로의 저장 단추에 대 한 이벤트에 추가 됩니다 `click` <xref:System.Windows.Forms.BindingNavigator> . 추가 테이블을 업데이트하려면 코드를 수동으로 추가해야 합니다. 이 연습에서는 저장 단추의 click 이벤트 처리기에서 기존 저장 코드를 리팩터링 합니다. 또한 행을 추가 하거나 삭제 해야 하는지 여부에 따라 특정 업데이트 기능을 제공 하는 몇 가지 메서드를 추가로 만들 수 있습니다.

#### <a name="to-modify-the-auto-generated-save-code"></a>자동으로 생성된 저장 코드를 수정하려면

1. **Customersbindingnavigator** 에서 **저장** 단추 (플로피 디스크 아이콘이 있는 단추)를 선택 합니다.

2. `CustomersBindingNavigatorSaveItem_Click` 메서드를 다음 코드로 바꿉니다.

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   관련 데이터의 변경을 조정하는 순서는 다음과 같습니다.

- 자식 레코드를 삭제 합니다. 이 경우 테이블에서 레코드를 삭제 `Orders` 합니다.

- 부모 레코드를 삭제 합니다. 이 경우 테이블에서 레코드를 삭제 `Customers` 합니다.

- 부모 레코드를 삽입 합니다. (이 경우 테이블에 레코드를 삽입 `Customers` 합니다.)

- 자식 레코드를 삽입 합니다. (이 경우 테이블에 레코드를 삽입 `Orders` 합니다.)

#### <a name="to-delete-existing-orders"></a>기존 주문을 삭제하려면

- 다음 `DeleteOrders` 메서드를 **Form1**에 추가합니다.

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>기존 고객을 삭제하려면

- 다음 `DeleteCustomers` 메서드를 **Form1**에 추가합니다.

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>새 고객을 추가하려면

- 다음 `AddNewCustomers` 메서드를 **Form1**에 추가합니다.

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>새 주문을 추가하려면

- 다음 `AddNewOrders` 메서드를 **Form1**에 추가합니다.

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>애플리케이션 실행

#### <a name="to-run-the-application"></a>애플리케이션을 실행하려면

- **F5 키** 를 선택 하 여 응용 프로그램을 실행 합니다.

## <a name="see-also"></a>관련 항목
 [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
