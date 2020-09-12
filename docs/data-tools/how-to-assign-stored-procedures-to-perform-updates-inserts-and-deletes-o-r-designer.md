---
title: LINQ to SQL의 저장 프로시저를 사용 하 여 데이터 업데이트
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3f8b2f783d6ae449a6124afe5d8e25dd836f0f8e
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036316"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>방법: 저장 프로시저를 할당하여 업데이트, 삽입 및 삭제 수행(O/R 디자이너)

저장 프로시저를 **O/R 디자이너**에 추가하여 일반적인 <xref:System.Data.Linq.DataContext> 메서드로 실행할 수 있습니다. 또한 엔터티 클래스의 변경 내용을 데이터베이스에 저장 하는 경우 (예: 메서드를 호출 하는 경우) 삽입, 업데이트 및 삭제를 수행 하는 기본 LINQ to SQL 런타임 동작을 재정의 하는 데 사용할 수 있습니다 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .

> [!NOTE]
> 클라이언트로 다시 보내야 하는 값(예: 저장 프로시저에서 계산된 값)을 저장 프로시저에서 반환하는 경우 저장 프로시저에 출력 매개 변수를 만듭니다. 출력 매개 변수를 사용할 수 없는 경우 O/R 디자이너에서 생성된 재정의를 사용하지 말고 부분 메서드(Partial Method) 구현을 작성합니다. 데이터베이스에서 생성된 값에 매핑되는 멤버는 INSERT 또는 UPDATE 작업이 성공적으로 완료된 후 적절한 값으로 설정되어야 합니다. 자세한 내용은 [기본 동작 재정의에서 개발자의 책임](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior)을 참조 하세요.

> [!NOTE]
> LINQ to SQL은 id (자동 증분), rowguidcol (데이터베이스에서 생성 된 GUID) 및 timestamp 열에 대해 데이터베이스에서 생성 된 값을 자동으로 처리 합니다. 데이터베이스에서 생성된 값이 다른 형식의 열에 있으면 null 값이라는 예기치 않은 결과가 발생합니다. 데이터베이스에서 생성 된 값을 반환 하려면 수동으로를 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> **true** 로 설정 하 고 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> [AutoSync](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync, OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)또는 [AutoSync](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>)중 하나로 설정 해야 합니다.

## <a name="configure-the-update-behavior-of-an-entity-class"></a>엔터티 클래스의 업데이트 동작 구성

기본적으로 LINQ to SQL 엔터티 클래스의 데이터에 적용 된 변경 내용으로 데이터베이스를 업데이트 (삽입, 업데이트 및 삭제) 하는 논리는 LINQ to SQL 런타임에서 제공 됩니다. 런타임에서는 열 및 기본 키 정보와 같은 테이블 스키마를 기반으로 기본 INSERT, UPDATE 및 DELETE 명령을 만듭니다. 기본 동작을 원하지 않는 경우 테이블의 데이터를 조작 하는 데 필요한 삽입, 업데이트 및 삭제를 수행 하기 위한 특정 저장 프로시저를 할당 하 여 업데이트 동작을 구성할 수 있습니다. 엔터티 클래스가 뷰에 매핑되는 때와 같이 기본 동작이 생성되지 않은 경우에도 이렇게 할 수 있습니다. 또한 저장 프로시저를 통해 데이터베이스의 테이블에 액세스해야 하는 경우에 기본 업데이트 동작을 재정의할 수 있습니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>저장 프로시저를 지정하여 엔터티 클래스의 기본 동작을 재정의하려면

1. 디자이너에서 **LINQ to SQL** 파일을 엽니다. (**솔루션 탐색기**에서 **.dbml** 파일을 두 번 클릭합니다.)

2. **서버 탐색기** 또는 **데이터베이스 탐색기**에서 **저장 프로시저**를 확장하여 엔터티 클래스의 삽입, 업데이트 및/또는 삭제 명령에 사용할 저장 프로시저를 찾습니다.

3. 저장 프로시저를 **O/R 디자이너**로 끌어 놓습니다.

     저장 프로시저는 메서드 창에 <xref:System.Data.Linq.DataContext> 메서드로 추가됩니다. 자세한 내용은 [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)를 참조 하세요.

4. 업데이트 수행을 위해 저장 프로시저를 사용하려는 엔터티 클래스를 선택합니다.

5. **속성** 창에서 재정의할 **삽입**, **업데이트** 또는 **삭제** 명령을 선택합니다.

6. **런타임 사용** 옆의 줄임표(...)를 클릭하여 **동작 구성** 대화 상자를 엽니다.

7. **사용자 지정**을 선택합니다.

8. **사용자 지정** 목록에서 원하는 저장 프로시저를 선택합니다.

9. **메서드 인수** 및 **클래스 속성** 목록을 살펴보고 **메서드 인수**가 적절한 **클래스 속성**에 매핑되어 있는지 확인합니다. 원래 메서드 인수 ( `Original_<ArgumentName>` )를 및 명령의 원래 속성 ()에 매핑합니다 `<PropertyName> (Original)` `Update` `Delete` .

    > [!NOTE]
    > 기본적으로 메서드 인수는 이름이 일치하는 경우 클래스 속성에 매핑됩니다. 속성 이름이 변경되어서 더 이상 테이블과 엔터티 클래스 간에 일치하지 않으면 디자이너에서 올바른 매핑을 결정할 수 없는 경우 매핑할 해당 클래스 속성을 선택해야 합니다.

10. **확인** 또는 **적용**을 클릭합니다.

    > [!NOTE]
    > 각 변경을 수행한 후에 **적용** 을 클릭 하면 각 클래스 및 동작 조합의 동작을 계속 구성할 수 있습니다. **적용**을 클릭 하기 전에 클래스 또는 동작을 변경 하면 경고 대화 상자가 표시 되 고 변경 내용을 적용할 수 있는 기회가 제공 됩니다.

업데이트의 기본 런타임 논리 사용으로 되돌아가려면 **속성** 창에서 **삽입**, **업데이트** 또는 **삭제** 명령 옆의 줄임표를 클릭한 다음, **동작 구성** 대화 상자에서 **런타임 사용**을 선택합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext 메서드](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL(.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [삽입, 업데이트 및 삭제 작업 (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
