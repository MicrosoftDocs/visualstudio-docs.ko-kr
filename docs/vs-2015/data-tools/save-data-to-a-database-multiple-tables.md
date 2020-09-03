---
title: 데이터베이스에 데이터 저장 (여러 테이블) | Microsoft Docs
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5c4d5fc73660c97bcb69957a93d2ff08f64e31c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655455"
---
# <a name="save-data-to-a-database-multiple-tables"></a>데이터베이스에 데이터 저장(여러 테이블)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

애플리케이션 개발에서 가장 일반적인 시나리오는 Windows 애플리케이션의 폼에 데이터를 표시하고 데이터를 편집한 다음 업데이트된 데이터를 데이터베이스로 다시 보내는 것입니다. 이 연습에서는 두 관련 테이블의 데이터를 표시하는 폼을 만들고, 레코드를 편집한 다음 변경 내용을 데이터베이스에 다시 저장하는 방법을 보여줍니다. 이 예에서는 Northwind 샘플 데이터베이스의 `Customers` 및 `Orders` 테이블을 사용합니다.

 TableAdapter의 `Update` 메서드를 호출하여 애플리케이션의 데이터를 데이터베이스에 다시 저장할 수 있습니다. **데이터 소스** 창에서 폼으로 테이블을 끌어다 놓으면 데이터를 저장 하는 데 필요한 코드가 자동으로 추가 됩니다. 양식에 추가 된 추가 테이블에는이 코드를 수동으로 추가 해야 합니다. 이 연습에서는 둘 이상의 테이블에서 업데이트를 저장하는 코드를 추가하는 방법을 보여줍니다.

> [!NOTE]
> 표시 되는 대화 상자와 메뉴 명령은 사용 중인 활성 설정 또는 버전에 따라 도움말에 설명 된 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

 이 연습에서 설명하는 작업은 다음과 같습니다.

- 새 **Windows 응용 프로그램** 프로젝트를 만듭니다.

- [데이터 소스 구성 마법사](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)를 사용 하 여 응용 프로그램에서 데이터 소스를 만들고 구성 합니다.

- [데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)에서 항목의 컨트롤을 설정 합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

- **데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만듭니다.

- 데이터 집합의 각 테이블에서 몇 개의 레코드를 수정 합니다.

- 데이터 세트의 업데이트된 데이터를 데이터베이스로 다시 보내도록 코드를 수정합니다.

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 완료하려면 다음 사항이 필요합니다.

- Northwind 샘플 데이터베이스에 대한 액세스.

## <a name="create-the-windows-application"></a>Windows 응용 프로그램 만들기
 첫 번째 단계는 **Windows 응용 프로그램**을 만드는 것입니다. 이 단계에서 프로젝트에 이름을 할당 하는 작업은 선택 사항 이지만 나중에 저장할 계획 이므로 이름을 지정 합니다.

#### <a name="to-create-the-new-windows-application-project"></a>새 Windows 응용 프로그램 프로젝트를 만들려면

1. **파일** 메뉴에서 새 프로젝트를 만듭니다.

2. 프로젝트 이름을 `UpdateMultipleTablesWalkthrough`로 지정합니다.

3. **Windows 응용 프로그램**을 선택 하 고 **확인**을 선택 합니다. 자세한 내용은 [클라이언트 응용 프로그램](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)을 참조 하세요.

     **UpdateMultipleTablesWalkthrough** 프로젝트가 만들어져 **솔루션 탐색기**에 추가됩니다.

## <a name="create-the-data-source"></a>데이터 원본 만들기
 이 단계에서는 **데이터 원본 구성 마법사**를 사용하여 Northwind 데이터베이스에서 데이터 원본을 만듭니다. 연결을 만들려면 Northwind 샘플 데이터베이스에 액세스해야 합니다.

#### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면

1. **데이터** 메뉴에서**데이터 소스 표시**를 선택 합니다.

2. **데이터** 소스 창에서**새 데이터 소스 추가** 를 선택 하 여 **데이터 소스 구성 마법사**를 시작 합니다.

3. **데이터 소스 형식 선택**화면에서 **데이터베이스**를 선택 하 고 **다음**을 선택 합니다.

4. **데이터 연결 선택**화면에서 다음 중 하나를 수행 합니다.

    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

         또는

    - **새 연결**을 선택하여 **연결 추가 또는 수정** 대화 상자를 엽니다.

5. 데이터베이스에 암호가 필요 하면 중요 한 데이터를 포함 하는 옵션을 선택 하 고 **다음**을 선택 합니다.

6. **응용 프로그램 구성 파일에 연결 문자열 저장**에서 **다음**을 선택 합니다.

7. **데이터베이스 개체 선택**화면에서 **테이블** 노드를 확장 합니다.

8. **Customers** 및 **Orders** 테이블을 선택한 다음 **마침**을 선택 합니다.

     **NorthwindDataSet**가 프로젝트에 추가되고 테이블이 **데이터 원본** 창에 나타납니다.

## <a name="set-the-controls-to-be-created"></a>만들 컨트롤 설정
 이 연습에서 테이블의 데이터는 `Customers` 개별 컨트롤에 데이터가 표시 되는 **세부 정보** 레이아웃에 있습니다. 테이블의 데이터는 `Orders` 컨트롤에 표시 되는 **그리드** 레이아웃에 <xref:System.Windows.Forms.DataGridView> 있습니다.

#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>데이터 소스 창에서 항목에 대한 삭제 유형을 설정하려면

1. **데이터 소스** 창에서 **Customers** 노드를 확장 합니다.

2. **Customers** 노드의 컨트롤 목록에서 **세부 정보** 를 선택 하 여 **customers** 테이블의 컨트롤을 개별 컨트롤로 변경 합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

## <a name="create-the-data-bound-form"></a>데이터 바인딩된 폼 만들기
 **데이터 소스** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다.

#### <a name="to-create-data-bound-controls-on-the-form"></a>폼에서 데이터 바인딩된 컨트롤을 만들려면

1. 주 **Customers** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어서 놓습니다.

     설명 레이블이 있는 데이터 바인딩된 컨트롤이 레코드 탐색을 위한 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>와 함께 폼에 나타납니다. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> 및 <xref:System.Windows.Forms.BindingNavigator>가 구성 요소 트레이에 나타납니다.

2. 관련 **Orders** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어 옵니다.

    > [!NOTE]
    > **Fax** 열 아래에 있는 관련 **Orders** 노드는 **Customers** 노드의 자식 노드입니다.

     <xref:System.Windows.Forms.DataGridView> 컨트롤과 레코드 탐색에 사용되는 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>가 폼에 나타납니다. OrdersTableAdapter가 <xref:System.Windows.Forms.BindingSource> 구성 요소 트레이에 표시 됩니다.

## <a name="addcode-to-update-the-database"></a>데이터베이스 업데이트를 위한 addcode
 **Customers** 및 **Orders** TableAdapters의 `Update` 메서드를 호출하여 데이터베이스를 업데이트할 수 있습니다. 기본적으로의 **저장** 단추에 대 한 이벤트 처리기는 <xref:System.Windows.Forms.BindingNavigator> 데이터베이스에 업데이트를 보내기 위해 폼의 코드에 추가 됩니다. 이 절차에서는 업데이트를 올바른 순서로 보내도록 코드를 수정 합니다. 이렇게 하면 참조 무결성 오류가 발생 하는 가능성이 없어집니다. 또한 이 코드는 try-catch 블록에서 업데이트 호출을 래핑하여 오류 처리를 구현합니다. 애플리케이션의 요구 사항에 맞게 코드를 수정할 수 있습니다.

> [!NOTE]
> 명확 하 게 하기 위해이 연습에서는 트랜잭션을 사용 하지 않습니다. 그러나 두 개 이상의 관련 테이블을 업데이트 하는 경우에는 트랜잭션 내의 모든 업데이트 논리를 포함 합니다. 트랜잭션은 변경 내용을 커밋하기 전에 데이터베이스의 모든 관련 변경 내용이 성공 하도록 하는 프로세스입니다. 자세한 내용은 [트랜잭션 및 동시성](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b)을 참조 하세요.

#### <a name="to-add-update-logic-to-the-application"></a>애플리케이션에 업데이트 논리를 추가하려면

1. 에서 **저장** 단추를 선택 합니다 <xref:System.Windows.Forms.BindingNavigator> . 그러면 이벤트 처리기에 대 한 코드 편집기가 열립니다 `bindingNavigatorSaveItem_Click` .

2. 관련 TableAdapter의 `Update` 메서드를 호출하도록 이벤트 처리기의 코드를 바꿉니다. 다음 코드는 먼저 각 <xref:System.Data.DataRowState>(<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> 및 <xref:System.Data.DataRowState>)에 대해 업데이트된 정보를 저장할 3개 임시 데이터 테이블을 만듭니다. 그런 다음 업데이트를 올바른 순서로 실행 합니다. 이 코드는 다음과 같습니다.

     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]

## <a name="test-the-application"></a>애플리케이션 테스트

#### <a name="to-test-the-application"></a>애플리케이션을 테스트하려면

1. **F5 키**를 선택 합니다.

2. 각 테이블에 포함된 레코드 하나 이상의 데이터를 변경해 봅니다.

3. **저장** 단추를 선택합니다.

4. 데이터베이스의 값을 점검하여 변경 내용이 저장되었는지 확인합니다.

## <a name="next-steps"></a>다음 단계
 응용 프로그램 요구 사항에 따라 Windows 응용 프로그램에서 데이터 바인딩된 폼을 만든 후 몇 단계를 더 수행 해야 할 수도 있습니다. 이 연습에서 보완할 수 있는 사항은 다음과 같습니다.

- 폼에 검색 기능을 추가합니다. 자세한 내용은 [방법: Windows Forms 응용 프로그램에 매개 변수가 있는 쿼리 추가](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)를 참조 하세요.

- 데이터 소스를 편집하여 데이터베이스 개체를 추가하거나 편집합니다. 자세한 내용은 [방법: 데이터 집합 편집](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
