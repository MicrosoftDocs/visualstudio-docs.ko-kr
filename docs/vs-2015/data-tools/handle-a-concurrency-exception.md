---
title: 동시성 예외 처리 | Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b3f9bdaf5107f805100b938212128d42c0263dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670033"
---
# <a name="handle-a-concurrency-exception"></a>동시성 예외 처리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동시성 예외 ( <xref:System.Data.DBConcurrencyException> )는 두 사용자가 동시에 데이터베이스의 동일한 데이터를 변경 하려고 할 때 발생 합니다. 이 연습에서는를 catch 하 고 <xref:System.Data.DBConcurrencyException> , 오류를 일으킨 행을 찾고,이를 처리 하는 방법에 대 한 전략을 파악 하는 방법을 보여 주는 Windows 응용 프로그램을 만듭니다.

 이 연습에서는 다음 프로세스를 수행 합니다.

1. 새 **Windows 응용 프로그램** 프로젝트를 만듭니다.

2. Northwind 테이블을 기반으로 새 데이터 집합을 만듭니다 `Customers` .

3. 를 사용 하 여 폼을 만들어 <xref:System.Windows.Forms.DataGridView> 데이터를 표시 합니다.

4. Northwind 데이터베이스에 있는 테이블의 데이터로 데이터 집합을 채웁니다 `Customers` .

5. Visual Studio의 [Visual Database Tools](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) 를 사용 하 여 데이터 테이블에 직접 액세스 하 `Customers` 고 레코드를 변경 합니다.

6. 동일한 레코드를 다른 값으로 변경 하 고, 데이터 집합을 업데이트 하 고, 변경 내용을 데이터베이스에 쓰려고 시도 하 여 동시성 오류가 발생 합니다.

7. 오류를 파악 한 다음 레코드의 다른 버전을 표시 하 여 사용자가 계속 해 서 데이터베이스를 업데이트 하거나 업데이트를 취소할지 여부를 결정할 수 있도록 합니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음 사항이 필요합니다.

- 업데이트를 수행할 수 있는 권한을 사용 하 여 Northwind 샘플 데이터베이스에 액세스 합니다.

> [!NOTE]
> 표시 되는 대화 상자와 메뉴 명령은 사용 중인 활성 설정 또는 버전에 따라 도움말에 설명 된 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 새 Windows 응용 프로그램을 만들어 연습을 시작 합니다.

#### <a name="to-create-a-new-windows-application-project"></a>새 Windows 응용 프로그램 프로젝트를 만들려면

1. **파일** 메뉴에서 새 프로젝트를 만듭니다.

2. **프로젝트 형식** 창에서 프로그래밍 언어를 선택 합니다.

3. **템플릿** 창에서 **Windows 애플리케이션**을 선택합니다.

4. 프로젝트 이름을 `ConcurrencyWalkthrough` 로 지정한 다음 **확인**을 선택 합니다.

     Visual Studio는 **솔루션 탐색기** 에 프로젝트를 추가 하 고 디자이너에 새 폼을 표시 합니다.

## <a name="create-the-northwind-dataset"></a>Northwind 데이터 집합 만들기
 이 섹션에서는 라는 데이터 집합을 만듭니다 `NorthwindDataSet` .

#### <a name="to-create-the-northwinddataset"></a>NorthwindDataSet를 만들려면

1. **데이터** 메뉴에서 **새 데이터 소스 추가**를 선택 합니다.

     [데이터 원본 구성](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) 마법사가 열립니다.

2. **데이터 소스 형식 선택**화면에서 **데이터베이스**를 선택 합니다.

3. 사용 가능한 연결 목록에서 Northwind 샘플 데이터베이스에 대 한 연결을 선택 합니다. 연결 목록에서 연결을 사용할 수 없는 경우**새 연결** 을 선택 합니다.

    > [!NOTE]
    > 로컬 데이터베이스 파일에 연결 하는 경우 프로젝트에 파일을 추가할지 묻는 메시지가 표시 되 면 **아니요** 를 선택 합니다.

4. **응용 프로그램 구성 파일에 연결 문자열 저장**화면에서 **다음**을 선택 합니다.

5. **테이블 노드를** 확장 하 고 테이블을 선택 `Customers` 합니다. 데이터 집합의 기본 이름은 이어야 합니다 `NorthwindDataSet` .

6. **마침** 을 선택 하 여 프로젝트에 데이터 집합을 추가 합니다.

## <a name="create-a-data-bound-datagridview-control"></a>데이터 바인딩된 DataGridView 컨트롤 만들기
 이 섹션에서는 <xref:System.Windows.Forms.DataGridView> **데이터 소스** 창에서 Windows Form으로 **Customers** 항목을 끌어를 만듭니다.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Customers 테이블에 바인딩된 DataGridView 컨트롤을 만들려면

1. **데이터 메뉴에서** **데이터 소스 표시** 를 선택 하 여 **데이터 소스 창을**엽니다.

2. **데이터 소스** 창에서 **NorthwindDataSet** 노드를 확장 한 다음 **Customers** 테이블을 선택 합니다.

3. 테이블 노드에서 아래쪽 화살표를 선택 하 고 드롭다운 목록에서 **DataGridView** 를 선택 합니다.

4. 테이블을 폼의 빈 영역으로 끕니다.

     이라는 <xref:System.Windows.Forms.DataGridView> 컨트롤과 라는 컨트롤은에 `CustomersDataGridView` <xref:System.Windows.Forms.BindingNavigator> `CustomersBindingNavigator` 바인딩된 폼에 추가 됩니다 <xref:System.Windows.Forms.BindingSource> . 이에 있는는의 테이블에 바인딩됩니다 `Customers` `NorthwindDataSet` .

## <a name="test-the-form"></a>양식 테스트
 이제 폼을 테스트 하 여이 시점까지 예상 대로 동작 하는지 확인할 수 있습니다.

#### <a name="to-test-the-form"></a>폼을 테스트 하려면

1. 응용 프로그램을 실행 하려면 **F5 키** 를 선택 합니다.

     <xref:System.Windows.Forms.DataGridView>이 폼에는 테이블의 데이터로 채워진 컨트롤이 표시 됩니다 `Customers` .

2. **디버그** 메뉴에서**디버깅 중지**를 선택 합니다.

## <a name="handleconcurrency-errors"></a>Handleconcurrency 오류
 오류를 처리 하는 방법은 응용 프로그램을 제어 하는 특정 비즈니스 규칙에 따라 다릅니다. 이 연습에서는 동시성 오류를 처리 하는 방법에 대 한 예제로 다음 전략을 사용 합니다.

 Applicationpresents 세 가지 버전의 레코드를 사용자에 게 제공 합니다.

- 데이터베이스의 현재 레코드

- 데이터 집합에 로드 된 원본 레코드

- 데이터 집합에서 제안 된 변경 내용

  그런 다음 사용자는 데이터베이스를 제안 된 버전으로 덮어쓰거나 업데이트를 취소 하 고 데이터베이스의 새 값을 사용 하 여 데이터 집합을 새로 고칠 수 있습니다.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>동시성 오류 처리를 사용 하도록 설정 하려면

1. 사용자 지정 오류 처리기를 만듭니다.

2. 사용자에 게 선택 항목을 표시 합니다.

3. 사용자의 응답을 처리 합니다.

4. 업데이트를 다시 보내거나 데이터 집합의 데이터를 다시 설정 합니다.

### <a name="addcode-to-handle-the-concurrency-exception"></a>동시성 예외를 처리 하는 addcode
 업데이트를 수행 하려고 할 때 예외가 발생 하면 일반적으로 발생 한 예외에 의해 제공 된 정보를 사용 하 여 작업을 수행 하려고 합니다.

 이 섹션에서는 데이터베이스 업데이트를 시도 하는 코드를 추가 합니다. 또한 <xref:System.Data.DBConcurrencyException> 발생할 수 있는 모든 예외 및 기타 예외를 처리 합니다.

> [!NOTE]
> `CreateMessage`및 `ProcessDialogResults` 메서드는이 연습의 뒷부분에서 추가 됩니다.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>동시성 오류에 대 한 오류 처리를 추가 하려면

1. 메서드 아래에 다음 코드를 추가 합니다 `Form1_Load` .

     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]

2. 메서드를 `CustomersBindingNavigatorSaveItem_Click` 호출 하 여 메서드를 `UpdateDatabase` 다음과 같이 바꿉니다.

     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]

### <a name="displaychoices-to-the-user"></a>사용자에 게 displaychoices를 선택 합니다.
 방금 작성 한 코드는 프로시저를 호출 `CreateMessage` 하 여 사용자에 게 오류 정보를 표시 합니다. 이 연습에서는 메시지 상자를 사용 하 여 레코드의 다른 버전을 사용자에 게 표시 합니다. 이를 통해 사용자는 레코드를 변경 내용으로 덮어쓸지 아니면 편집을 취소할지를 선택할 수 있습니다. 사용자가 메시지 상자에서 단추를 클릭 하 여 옵션을 선택 하면 응답은 메서드에 전달 됩니다 `ProcessDialogResult` .

##### <a name="to-create-the-message-to-display-to-the-user"></a>사용자에 게 표시할 메시지를 만들려면

- **코드 편집기**에 다음 코드를 추가 하 여 메시지를 만듭니다. 메서드 아래에이 코드를 입력 `UpdateDatabase` 합니다.

     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]

### <a name="process-the-users-response"></a>사용자의 응답을 처리 합니다.
 또한 메시지 상자에 대 한 사용자의 응답을 처리 하는 코드도 필요 합니다. 옵션은 데이터베이스의 현재 레코드를 제안 된 변경 내용으로 덮어쓰거나 로컬 변경 내용을 취소 하 고 현재 데이터베이스에 있는 레코드를 사용 하 여 데이터 테이블을 새로 고치는 것입니다. 사용자가 예를 선택 하면 <xref:System.Data.DataTable.Merge%2A> *preserveChanges* 인수를로 설정 하 여 메서드가 호출 됩니다 `true` . 그러면 레코드의 원래 버전이 데이터베이스의 레코드와 일치 하기 때문에 업데이트에 성공 하 게 됩니다.

##### <a name="to-process-the-user-input-from-the-message-box"></a>메시지 상자에서 사용자 입력을 처리 하려면

- 이전 섹션에서 추가 된 코드 아래에 다음 코드를 추가 합니다.

     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]

## <a name="test-the-form"></a>양식 테스트
 이제 폼을 테스트 하 여 예상 대로 동작 하는지 확인할 수 있습니다. 동시성 위반을 시뮬레이트하려면 NorthwindDataSet을 채운 후 데이터베이스에서 데이터를 변경 해야 합니다.

#### <a name="to-test-the-form"></a>폼을 테스트 하려면

1. **F5 키** 를 선택 하 여 응용 프로그램을 실행 합니다.

2. 양식이 표시 되 면 실행을 그대로 유지 하 고 Visual Studio IDE로 전환 합니다.

3. **보기** 메뉴에서 **서버 탐색기**를 선택합니다.

4. **서버 탐색기**에서 응용 프로그램이 사용 하는 연결을 확장 한 다음 **테이블** 노드를 확장 합니다.

5. **Customers** 테이블을 마우스 오른쪽 단추로 클릭 한 다음 **테이블 데이터 표시**를 선택 합니다.

6. 첫 번째 레코드 ( `ALFKI` )에서 `ContactName` 를로 변경 `Maria Anders2` 합니다.

    > [!NOTE]
    > 다른 행으로 이동 하 여 변경 내용을 커밋합니다.

7. `ConcurrencyWalkthrough`실행 중인 폼으로 전환 합니다.

8. 폼의 첫 번째 레코드 ()에서 `ALFKI` `ContactName` 를로 변경 `Maria Anders1` 합니다.

9. **저장** 단추를 선택합니다.

     동시성 오류가 발생 하 고 메시지 상자가 나타납니다.

10. **아니요** 를 선택 하면 업데이트를 취소 하 고 현재 데이터베이스에 있는 값으로 데이터 집합을 업데이트 합니다. **예** 를 선택 하면 데이터베이스에 제안 된 값이 기록 됩니다.

## <a name="see-also"></a>관련 항목

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)