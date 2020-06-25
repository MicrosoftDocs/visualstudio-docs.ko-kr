---
title: '방법: 엔터티 클래스에 유효성 검사 추가'
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5d408c67b2e54fecd6404bac93d93ecfb35de162
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282347"
---
# <a name="how-to-add-validation-to-entity-classes"></a>방법: 엔터티 클래스에 유효성 검사 추가
엔터티 클래스의 *유효성 검사*는 데이터 개체에 입력된 값이 개체의 스키마 제약 조건과 애플리케이션에 대해 설정된 규칙을 따르는지 확인하는 과정입니다. 업데이트를 내부 데이터베이스에 보내기 전에 데이터의 유효성을 검사하면 오류를 줄일 수 있습니다. 또한 애플리케이션과 데이터베이스 간에 발생할 수 있는 잠재적 라운드트립 횟수를 줄일 수 있습니다.

[Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md) 는 사용자가 전체 엔터티를 삽입, 업데이트 및 삭제 하는 동안 실행 되는 디자이너 생성 코드와 개별 열이 변경 되는 동안 및 그 후에 실행 되는 디자이너 생성 코드를 확장할 수 있는 부분 메서드를 제공 합니다.

> [!NOTE]
> 이 항목에서는 **O/R 디자이너**를 사용 하 여 엔터티 클래스에 유효성 검사를 추가 하는 기본 단계를 제공 합니다. 특정 엔터티 클래스를 참조 하지 않고 이러한 일반 단계를 수행 하기 어려울 수 있기 때문에 실제 데이터를 사용 하는 연습이 제공 됩니다.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>특정 열의 값에 대 한 변경 내용에 대 한 유효성 검사 추가
이 절차는 열의 값이 변경될 때 데이터의 유효성을 검사하는 방법을 보여 줍니다. 유효성 검사는 사용자 인터페이스 대신 클래스 정의 내에서 수행되기 때문에 값에 대한 유효성 검사가 실패하면 예외가 throw됩니다. 애플리케이션에서 열 값을 변경하려고 하는 코드에 대한 오류 처리를 구현하세요.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>열의 값을 변경하는 동안 데이터의 유효성을 검사하려면

1. **O/R 디자이너**에서 새 LINQ to SQL 클래스 파일 (**.dbml** 파일)을 열거나 만듭니다. (**솔루션 탐색기**에서 **.dbml** 파일을 두 번 클릭합니다.)

2. **O/R 디자이너**에서 유효성 검사를 추가할 클래스를 마우스 오른쪽 단추로 클릭한 다음, **코드 보기**를 클릭합니다.

     선택한 엔터티 클래스의 partial 클래스와 함께 코드 편집기가 열립니다.

3. 커서를 partial 클래스에 놓습니다.

4. Visual Basic 프로젝트의 경우

    1. **메서드 이름** 목록을 확장합니다.

    2. 유효성 검사를 추가할 열에 대해 **OnCOLUMNNAMEChanging** 메서드를 찾습니다.

    3. `OnCOLUMNNAMEChanging` 메서드가 partial 클래스에 추가됩니다.

    4. 다음 코드를 추가하여 입력된 값을 먼저 확인한 다음 열에 입력된 값이 애플리케이션에서 허용되는지 확인합니다. 다음 `value` 인수는 제안된 값을 포함하고 있으므로 이를 유효한 값으로 확인하는 논리를 추가합니다.

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    C# 프로젝트의 경우:

    C # 프로젝트는 이벤트 처리기를 자동으로 생성 하지 않으므로 IntelliSense를 사용 하 여 열 변경 부분 메서드를 만들 수 있습니다. `partial`을 입력한 다음 사용 가능한 부분 메서드에 액세스하기 위한 공간을 입력합니다. 유효성 검사를 추가할 열에 대해 열 변경 메서드를 클릭합니다. 다음 코드는 열 변경 부분 메서드를 선택할 때 생성 되는 코드와 비슷합니다.

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>엔터티 클래스의 업데이트에 대 한 유효성 검사 추가
변경하는 동안 값을 검사하는 작업 이외에도 전체 엔터티 클래스에 대해 업데이트를 시도할 때 데이터의 유효성을 검사할 수도 있습니다. 비즈니스 규칙에서 여러 열의 값에 대한 비교를 요구하는 경우 업데이트를 시도하는 동안 유효성 검사가 해당 작업을 수행합니다. 다음 절차는 전체 엔터티 클래스를 업데이트하려고 할 때 유효성을 검사하는 방법을 보여 줍니다.

> [!NOTE]
> 전체 엔터티 클래스 업데이트에 대한 유효성 검사 코드는 특정 엔터티 클래스의 partial 클래스가 아니라 partial <xref:System.Data.Linq.DataContext> 클래스에서 실행됩니다.

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>엔터티 클래스에 대한 업데이트 동안 데이터의 유효성을 검사하려면

1. **O/R 디자이너**에서 새 LINQ to SQL 클래스 파일 (**.dbml** 파일)을 열거나 만듭니다. (**솔루션 탐색기**에서 **.dbml** 파일을 두 번 클릭합니다.)

2. **O/R 디자이너**에서 마우스 오른쪽 단추로 빈 영역을 클릭하고 **코드 보기**를 클릭합니다.

     `DataContext`의 partial 클래스와 함께 코드 편집기가 열립니다.

3. 커서를 `DataContext`의 partial 클래스에 놓습니다.

4. Visual Basic 프로젝트의 경우

    1. **메서드 이름** 목록을 확장합니다.

    2. **UpdateENTITYCLASSNAME**를 클릭합니다.

    3. `UpdateENTITYCLASSNAME` 메서드가 partial 클래스에 추가됩니다.

    4. 다음 코드에 표시된 것과 같은 `instance` 인수를 사용하여 개별 열 값에 액세스합니다.

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    C# 프로젝트의 경우:

    C # 프로젝트는 이벤트 처리기를 자동으로 생성 하지 않으므로 IntelliSense를 사용 하 여 부분 메서드를 만들 수 있습니다 `UpdateCLASSNAME` . `partial`을 입력한 다음 사용 가능한 부분 메서드에 액세스하기 위한 공간을 입력합니다. 유효성 검사를 추가 하려는 클래스의 업데이트 메서드를 클릭 합니다. 다음 코드는 부분 메서드를 선택할 때 생성 되는 코드와 비슷합니다 `UpdateCLASSNAME` .

    ```csharp
    partial void UpdateCLASSNAME(CLASSNAME instance)
    {
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
        {
            string ErrorMessage = "Invalid data!";
            throw new System.Exception(ErrorMessage);
        }
    }
    ```

## <a name="see-also"></a>참조

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
