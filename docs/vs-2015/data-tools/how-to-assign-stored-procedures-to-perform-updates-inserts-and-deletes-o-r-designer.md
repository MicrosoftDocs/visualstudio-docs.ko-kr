---
title: '방법: 저장 프로시저를 할당 하 여 업데이트, 삽입 및 삭제 수행 (O-R 디자이너) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2054a55f0633d5d4add51fee2e933d9f4d829fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609977"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>방법: 저장 프로시저를 할당하여 업데이트, 삽입 및 삭제 수행(O/R 디자이너)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

저장 프로시저를 O/R 디자이너에 추가하여 일반적인 <xref:System.Data.Linq.DataContext> 메서드로 실행할 수 있습니다. 또한 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 엔터티 클래스의 변경 내용을 데이터베이스에 저장 하는 경우 (예: 메서드를 호출 하는 경우) 삽입, 업데이트 및 삭제를 수행 하는 기본 런타임 동작을 재정의 하는 데 사용할 수 있습니다 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .

> [!NOTE]
> 클라이언트로 다시 보내야 하는 값(예: 저장 프로시저에서 계산된 값)을 저장 프로시저에서 반환하는 경우 저장 프로시저에 출력 매개 변수를 만듭니다. 출력 매개 변수를 사용할 수 없는 경우 O/R 디자이너에서 생성된 재정의를 사용하지 말고 부분 메서드(Partial Method) 구현을 작성합니다. 데이터베이스에서 생성된 값에 매핑되는 멤버는 INSERT 또는 UPDATE 작업이 성공적으로 완료된 후 적절한 값으로 설정되어야 합니다. 자세한 내용은 [기본 동작 재정의에서 개발자의 책임](https://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1)을 참조 하세요.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]은 identity(자동 증분), rowguidcol(데이터베이스에서 생성된 GUID) 및 timestamp 열에 대해 데이터베이스에서 생성된 값을 자동으로 처리합니다. 데이터베이스에서 생성된 값이 다른 형식의 열에 있으면 null 값이라는 예기치 않은 결과가 발생합니다. 데이터베이스에서 생성된 값을 반환하려면 수동으로 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>를 `true`로 설정하고 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>를 <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> 또는 <xref:System.Data.Linq.Mapping.AutoSync> 중 하나로 설정해야 합니다.

## <a name="configuring-the-update-behavior-of-an-entity-class"></a>엔터티 클래스의 업데이트 동작 구성
 기본적으로 삽입, 업데이트 및 삭제와 같은 데이터베이스를 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 엔터티 클래스의 데이터에 대한 변경 내용으로 업데이트하는 논리가 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 런타임에서 제공됩니다. 런타임에서는 테이블의 스키마 (열 및 기본 키 정보)를 기반으로 기본 Insert, Update 및 Delete 명령을 만듭니다. 기본 동작을 원하지 않는 경우 테이블의 데이터를 조작 하는 데 필요한 삽입, 업데이트 및 삭제를 수행 하기 위한 특정 저장 프로시저를 할당 하 여 업데이트 동작을 구성할 수 있습니다. 엔터티 클래스가 뷰에 매핑되는 때와 같이 기본 동작이 생성되지 않은 경우에도 이렇게 할 수 있습니다. 또한 저장 프로시저를 통해 데이터베이스의 테이블에 액세스해야 하는 경우에 기본 업데이트 동작을 재정의할 수 있습니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>저장 프로시저를 지정하여 엔터티 클래스의 기본 동작을 재정의하려면

1. 디자이너에서 **LINQ to SQL** 파일을 엽니다. (**솔루션 탐색기**에서 .dbml 파일을 두 번 클릭합니다.)

2. **서버 탐색기** / **데이터베이스 탐색기**에서 **저장 프로시저** 를 확장 하 고 엔터티 클래스의 삽입, 업데이트 및/또는 삭제 명령에 사용할 저장 프로시저를 찾습니다.

3. 저장 프로시저를 O/R 디자이너로 끌어 놓습니다.

     저장 프로시저는 메서드 창에 <xref:System.Data.Linq.DataContext> 메서드로 추가됩니다. 자세한 내용은 [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)를 참조 하세요.

4. 업데이트 수행을 위해 저장 프로시저를 사용하려는 엔터티 클래스를 선택합니다.

5. **속성** 창에서 재정의할 **삽입**, **업데이트** 또는 **삭제** 명령을 선택합니다.

6. **런타임 사용** 옆의 줄임표(...)를 클릭하여 **동작 구성** 대화 상자를 엽니다.

7. **사용자 지정**을 선택합니다.

8. **사용자 지정** 목록에서 원하는 저장 프로시저를 선택합니다.

9. **메서드 인수** 및 **클래스 속성** 목록을 살펴보고 **메서드 인수**가 적절한 **클래스 속성**에 매핑되어 있는지 확인합니다. 업데이트 및 삭제 명령을 위해 원래 메서드 인수 (Original_*Argumentname*)를 원래 속성 (*PropertyName* (original))에 매핑합니다.

    > [!NOTE]
    > 기본적으로 메서드 인수는 이름이 일치하는 경우 클래스 속성에 매핑됩니다. 속성 이름이 변경되어서 더 이상 테이블과 엔터티 클래스 간에 일치하지 않으면 디자이너에서 올바른 매핑을 결정할 수 없는 경우 매핑할 해당 클래스 속성을 선택해야 합니다.

10. **확인** 또는 **적용**을 클릭합니다.

    > [!NOTE]
    > 계속해서 클래스/동작 조합을 변경한 후 **적용**을 클릭하여 해당하는 각 조합에 대한 동작을 구성할 수 있습니다. **적용**을 클릭 하기 전에 클래스 또는 동작을 변경한 경우 변경 내용을 적용할 수 있는 경고 대화 상자가 표시 됩니다.

     업데이트에 대 한 기본 런타임 논리를 사용 하도록 되돌리려면 **속성** 창에서 삽입, 업데이트 또는 삭제 명령 옆에 있는 줄임표를 클릭 한 다음 **동작 구성** 대화 상자에서 **런타임 사용** 을 선택 합니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [DataContext 메서드의 LINQ to SQL 도구 (o/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md) [연습: LINQ to SQL 클래스 만들기 (o-r 디자이너)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [삽입, 업데이트 및 삭제 작업](https://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)
