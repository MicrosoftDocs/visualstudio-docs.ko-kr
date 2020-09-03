---
title: '방법: O-R 디자이너를 사용 하 여 상속 구성 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f8c08546fdf96c755b3adb80021ab7269509739
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654699"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>방법: O/R 디자이너를 사용하여 상속 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)])는 관계형 시스템에서 주로 구현되는 단일 테이블 상속 개념을 지원합니다. 단일 테이블 상속에서는 부모 정보와 자식 정보에 대한 필드를 모두 포함하는 데이터베이스 테이블이 하나 있습니다. 관계형 데이터의 경우 판별자 열에는 해당 레코드가 어느 클래스에 속해 있는지를 판별하는 값이 포함됩니다.

 예를 들어 회사에 고용되어 있는 모든 사람들이 포함되어 있는 Persons 테이블을 생각해 봅시다. 어떤 사람들은 사원이고 어떤 사람들은 관리자입니다. Persons 테이블에는 관리자의 경우 1 값이 들어 있고 사원의 경우 2 값이 들어 있는 `EmployeeType`이라는 열이 있으며 이 열이 판별자 열입니다. 이 시나리오에서는 직원 서브클래스를 만든 후 `EmployeeType` 값이 2인 레코드로만 클래스를 채울 수 있습니다. 각 클래스에서 적용되지 않는 열은 제거할 수도 있습니다.

 상속을 사용하고 관계형 데이터에 대응하는 개체 모델을 만드는 것은 조금 복잡할 수 있습니다. 다음 절차에서는 O/R 디자이너를 사용하여 상속을 구성하는 데 필요한 단계를 요약한 것입니다. 기존 테이블과 열을 참조하지 않고 일반 단계를 따르는 것이 어려울 수 있으므로 데이터를 사용하는 연습이 제공되었습니다. 를 사용 하 여 상속을 구성 하는 자세한 단계별 지침은 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] [연습: 단일 테이블 상속을 사용 하 여 LINQ to SQL 클래스 만들기 (O/R 디자이너)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)를 참조 하세요.

### <a name="to-create-inherited-data-classes"></a>상속된 데이터 클래스를 만들려면

1. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]기존 Visual Basic 또는 c # 프로젝트에 **LINQ to SQL 클래스** 항목을 추가 하 여를 엽니다.

2. 기본 클래스로 사용할 테이블을 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]로 끌어 옵니다.

3. 두 번째 테이블 복사본을 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]로 끌어 와서 이름을 바꿉니다. 이것을 파생 클래스 또는 서브클래스라고 합니다.

4. **도구 상자**의 **개체 관계형 디자이너** 탭에서 **상속**을 클릭한 다음, 서브클래스(이름을 바꾼 테이블)를 클릭하고 이를 기본 클래스에 연결합니다.

    > [!NOTE]
    > **도구 상자**에서 **상속** 항목을 클릭한 다음, 마우스 단추를 놓고 3단계에서 만든 클래스의 두 번째 복사본을 클릭한 다음, 2단계에서 만든 첫 번째 클래스를 클릭합니다. 상속 선의 화살표가 첫 번째 클래스를 가리킵니다.

5. 각 클래스에서 연결에 사용되지 않으므로 표시하지 않을 개체 속성을 모두 삭제합니다. 연결에 사용 되는 개체 속성을 삭제 하려고 하면 오류가 표시 됩니다. [속성은 \<property name> 연결 \<association name> 에 참여 하 고 있으므로 삭제할 수 없습니다 ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > 파생 클래스는 기본 클래스에 정의된 속성을 상속하므로 각 클래스에 동일한 열은 정의할 수 없습니다. 열은 속성으로 구현 됩니다. 기본 클래스의 속성에 상속 한정자를 설정 하 여 파생 클래스에서 열 만들기를 사용 하도록 설정할 수 있습니다. 자세한 내용은 [빌드에 없음: 속성 및 메서드 재정의](https://msdn.microsoft.com/2167e8f5-1225-4b13-9ebd-02591ba90213)를 참조 하세요.

6. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에서 상속 선을 선택합니다.

7. **속성** 창에서 **판별자 속성** 을 클래스의 레코드를 구분 하는 데 사용 되는 열 이름으로 설정 합니다.

8. **Derived Class Discriminator Value** 속성을 해당 레코드를 상속된 형식으로 지정한 데이터베이스의 값으로 설정합니다. 이는 판별자 열에 저장된 값이며 상속된 클래스를 지정하는 데 사용되는 값입니다.

9. **Base Class Discriminator Value** 속성을 해당 레코드를 기본 형식으로 지정한 값으로 설정합니다. 이는 판별자 열에 저장된 값이며 기본 클래스를 지정하는 데 사용되는 값입니다.

10. 선택적으로 **Inheritance Default** 속성을 사용하여 정의된 상속 코드와 일치하지 않는 행을 로드할 때 사용되는 상속 계층 구조에서 형식을 지정할 수 있습니다. 즉, 레코드의 판별자 열에 **파생 클래스 판별자 값** 또는 **기본 클래스 판별자 값** 속성의 값과 일치 하지 않는 값이 있으면 해당 레코드는 **상속 기본값으로**지정 된 형식으로 로드 됩니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [연습: LINQ to SQL 클래스 만들기 (O-R 디자이너)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [PAVE Visual Studio에서 데이터 응용 프로그램 개발에 대 한 새로운 기능 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1) [visual STUDIO에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [연습: 빌드에 없는 단일 테이블 상속 (O/R 디자이너)을 사용 하 여 LINQ to SQL 클래스 만들기](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [: Visual Basic 상속의 상속](https://msdn.microsoft.com/e5e6e240-ed31-4657-820c-079b7c79313c) [Inheritance](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)
