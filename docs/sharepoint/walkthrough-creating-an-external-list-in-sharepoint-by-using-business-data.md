---
title: 비즈니스 데이터를 사용 하 여 SharePoint에서 외부 목록 만들기
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], external list
- Business Data Connectivity service [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a SharePoint list
- BDC [SharePoint development in Visual Studio], business data in a Web Part
- BDC [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], entity backed list
- Business Data Connectivity service [SharePoint development in Visual Studio], external list
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 29f6c4e170bce8ae7bacfc7178ebd9386f2d4416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015826"
---
# <a name="walkthrough-create-an-external-list-in-sharepoint-by-using-business-data"></a>연습: 비즈니스 데이터를 사용 하 여 SharePoint에서 외부 목록 만들기

BDC (비즈니스 데이터 연결) 서비스를 사용 하면 SharePoint에서 백 엔드 서버 응용 프로그램, 웹 서비스 및 데이터베이스의 비즈니스 데이터를 표시할 수 있습니다.

이 연습에서는 샘플 데이터베이스의 연락처에 대 한 정보를 반환 하는 BDC 서비스용 모델을 만드는 방법을 보여 줍니다. 그런 다음이 모델을 사용 하 여 SharePoint에서 외부 목록을 만듭니다.

이 연습에서는 다음 작업을 수행합니다.

- 프로젝트 만들기
- 모델에 엔터티 추가
- Finder 메서드 추가
- 특정 Finder 메서드 추가
- 프로젝트를 테스트 합니다.

## <a name="prerequisites"></a>필수 구성 요소

이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 지원 되는 버전의 Windows 및 SharePoint

- AdventureWorks 샘플 데이터베이스에 액세스 합니다. AdventureWorks 데이터베이스를 설치 하는 방법에 대 한 자세한 내용은 [SQL Server 예제 데이터베이스](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)를 참조 하세요.

## <a name="create-a-project-that-contains-a-bdc-model"></a>BDC 모델을 포함 하는 프로젝트 만들기

1. Visual Studio의 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트**를 선택 합니다.

     **새 프로젝트** 대화 상자가 열립니다.

2. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 항목을 선택 합니다.

3. **템플릿** 창에서 **SharePoint 2010 프로젝트**를 선택 하 고 프로젝트 이름을 **AdventureWorksTest**로 지정한 다음 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다. 이 마법사에서는 프로젝트를 디버그 하 고 솔루션의 신뢰 수준을 설정 하는 데 사용할 사이트를 지정할 수 있습니다.

4. **팜 솔루션으로 배포** 옵션 단추를 선택 하 여 신뢰 수준을 설정 합니다.

5. **마침** 단추를 선택 하 여 기본 로컬 SharePoint 사이트를 적용 합니다.

6. **솔루션 탐색기**에서 SharePoint 프로젝트 노드를 선택 합니다.

7. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

     **새 항목 추가** 대화 상자가 열립니다.

8. **템플릿** 창에서 **비즈니스 데이터 연결 모델 (팜 솔루션에만 해당)** 을 선택 하 고 프로젝트 이름을 **AdventureWorksContacts**로 지정한 다음 **추가** 단추를 선택 합니다.

## <a name="add-data-access-classes-to-the-project"></a>프로젝트에 데이터 액세스 클래스 추가

1. 메뉴 모음에서 **도구**  >  **데이터베이스에 연결**을 선택 합니다.

     **연결 추가** 대화 상자가 열립니다.

2. SQL Server AdventureWorks 예제 데이터베이스에 대 한 연결을 추가 합니다.

     자세한 내용은 [연결 추가/수정 (Microsoft SQL Server)](https://msdn.microsoft.com/fa400910-26c3-4df7-b9d1-115e688b4ea3)을 참조 하세요.

3. **솔루션 탐색기**에서 프로젝트 노드를 선택합니다.

4. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

5. **설치 된 템플릿** 창에서 **데이터** 노드를 선택 합니다.

6. **템플릿** 창에서 **LINQ to SQL 클래스**를 선택 합니다.

7. **이름** 상자에서 **AdventureWorks**를 지정 하 고 **추가** 단추를 선택 합니다.

     .dbml 파일이 프로젝트에 추가되고 O/R 디자이너(개체 관계형 디자이너)가 열립니다.

8. 메뉴 모음에서 서버 탐색기 **보기**를 선택  >  **Server Explorer**합니다.

9. **서버 탐색기**에서 AdventureWorks 예제 데이터베이스를 나타내는 노드를 확장 한 다음 **테이블** 노드를 확장 합니다.

10. O/R 디자이너에 **Contact (Person)** 테이블을 추가 합니다.

     엔터티 클래스가 만들어져 디자인 화면에 표시됩니다. 엔터티 클래스에는 Contact (Person) 테이블의 열에 매핑되는 속성이 있습니다.

## <a name="remove-the-default-entity-from-the-bdc-model"></a>BDC 모델에서 기본 엔터티 제거

**비즈니스 데이터 연결 모델** 프로젝트는 Entity1 이라는 기본 엔터티를 모델에 추가 합니다. 이 엔터티를 제거 합니다. 나중에 새 엔터티를 추가 합니다. 빈 모델로 시작 하면 연습을 완료 하는 데 필요한 단계 수를 줄일 수 있습니다.

1. **솔루션 탐색기**에서 **BdcModel1** 노드를 확장 하 고 *BdcModel1* 파일을 엽니다.

2. 비즈니스 데이터 연결 모델 파일이 BDC 디자이너에서 열립니다.

3. 디자이너에서 **Entity1**에 대 한 바로 가기 메뉴를 열고 **삭제**를 선택 합니다.

4. **솔루션 탐색기**에서 *Entity1* (Visual Basic) 또는 *Entity1.cs* (c #)의 바로 가기 메뉴를 연 다음 **삭제**를 선택 합니다.

5. *Entity1Service* (Visual Basic) 또는 *Entity1Service.cs* (c #)의 바로 가기 메뉴를 열고 **삭제**를 선택 합니다.

## <a name="add-an-entity-to-the-model"></a>모델에 엔터티 추가

모델에 엔터티를 추가 합니다. Visual Studio **도구 상자** 의 엔터티를 BDC 디자이너에 추가할 수 있습니다.

1. 메뉴 모음에서 **View**  >  **도구 상자**보기를 선택 합니다.

2. **도구 상자**의 **BusinessDataConnectivity** 탭에서 **엔터티** 를 BDC 디자이너에 추가 합니다.

     새 엔터티가 디자이너에 표시 됩니다. Visual Studio는 *Entityservice .vb* (Visual Basic) 또는 *EntityService.cs* (c #의 경우) 라는 파일을 프로젝트에 추가 합니다.

3. 메뉴 모음에서 **보기**  >  **속성**  >  **창**을 선택 합니다.

4. **속성** 창에서 **이름** 속성 값을 **Contact**로 설정 합니다.

5. 디자이너에서 엔터티에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **식별자**를 선택 합니다.

     엔터티에 새 식별자가 나타납니다.

6. **속성** 창에서 식별자의 이름을 **ContactID**로 변경 합니다.

7. **형식 이름** 목록에서 **system.object**를 선택 합니다.

## <a name="add-a-specific-finder-method"></a>특정 Finder 메서드 추가

BDC 서비스에서 특정 연락처를 표시 하도록 하려면 특정 Finder 메서드를 추가 해야 합니다. 사용자가 목록에서 항목을 선택한 다음 리본 메뉴에서 **항목 보기** 단추를 선택 하면 BDC 서비스에서 특정 Finder 메서드를 호출 합니다.

**BDC 메서드 세부 정보** 창을 사용 하 여 연락처 엔터티에 특정 Finder 메서드를 추가 합니다. 특정 엔터티를 반환 하려면 메서드에 코드를 추가 합니다.

1. BDC 디자이너에서 **Contact** 엔터티를 선택 합니다.

2. 메뉴 모음에서 **View**  >  **다른 Windows**  >  **BDC 메서드 세부 정보**보기를 선택 합니다.

     BDC 메서드 세부 정보 창이 열립니다.

3. **메서드 추가** 목록에서 **특정 Finder 메서드 만들기**를 선택 합니다.

     Visual Studio에서는 다음 요소를 모델에 추가 합니다. 이러한 요소는 **BDC 메서드 세부 정보** 창에 표시 됩니다.

    - ReadItem 이라는 메서드입니다.

    - 메서드에 대 한 입력 매개 변수입니다.

    - 메서드의 반환 매개 변수입니다.

    - 각 매개 변수에 대 한 형식 설명자입니다.

    - 메서드에 대 한 메서드 인스턴스입니다.

4. **BDC 메서드 세부 정보** 창에서 **연락처** 유형 설명자에 대해 표시 되는 목록을 연 다음 **편집**을 선택 합니다.

     **BDC 탐색기** 가 열리고 모델의 계층 뷰가 제공 됩니다.

5. **속성** 창에서 **TypeName** 속성 옆에 있는 목록을 열고 **현재 프로젝트** 탭을 선택한 후 **Contact** 속성을 선택 합니다.

6. **BDC 탐색기**에서 **연락처**의 바로 가기 메뉴를 열고 **형식 설명자 추가**를 선택 합니다.

     **TypeDescriptor1** 라는 새 형식 설명자가 **BDC 탐색기**에 나타납니다.

7. **속성** 창에서 **이름** 속성 값을 **ContactID**로 설정 합니다.

8. **TypeName** 속성 옆에 있는 목록을 열고 **Int32**를 선택 합니다.

9. **식별자** 속성 옆에 있는 목록을 열고 **ContactID**를 선택 합니다.

10. 6 단계를 반복 하 여 다음 각 필드에 대 한 형식 설명자를 만듭니다.

    |Name|유형 이름|
    |----------|---------------|
    |FirstName|System.String|
    |LastName|System.String|
    |전화|System.String|
    |EmailAddress|System.String|
    |EmailPromotion|System.Int32|
    |NameStyle|System.Boolean|
    |PasswordHash|System.String|
    |PasswordSalt|System.String|

11. BDC 디자이너의 **Contact** 엔터티에서 **readitem** 메서드를 엽니다.

     Contact service 코드 파일이 코드 편집기에서 열립니다.

12. 클래스에서 `ContactService` `ReadItem` 메서드를 다음 코드로 바꿉니다. 이 코드는 다음 작업을 수행합니다.

    - AdventureWorks 데이터베이스의 Contact 테이블에서 레코드를 검색 합니다.

    - 연락처 엔터티를 BDC 서비스로 반환 합니다.

    > [!NOTE]
    > 필드의 값을 `ServerName` 서버의 이름으로 바꿉니다.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="add-a-finder-method"></a>Finder 메서드 추가

BDC 서비스에서 연락처를 목록에 표시할 수 있도록 하려면 Finder 메서드를 추가 해야 합니다. **BDC 메서드 세부 정보** 창을 사용 하 여 Contact 엔터티에 Finder 메서드를 추가 합니다. 엔터티 컬렉션을 BDC 서비스로 반환 하려면 메서드에 코드를 추가 합니다.

1. BDC 디자이너에서 **Contact** 엔터티를 선택 합니다.

2. **BDC 메서드 세부 정보** 창에서 **readitem** 노드를 축소 합니다.

3. **Readlist** 메서드 아래의 **메서드 추가** 목록에서 **Finder 메서드 만들기**를 선택 합니다.

     Visual Studio는 메서드, 반환 매개 변수 및 형식 설명자를 추가 합니다.

4. BDC 디자이너의 **Contact** 엔터티에서 **readlist** 메서드를 엽니다.

     코드 편집기에서 Contact 서비스의 코드 파일이 열립니다.

5. 클래스에서 `ContactService` `ReadList` 메서드를 다음 코드로 바꿉니다. 이 코드는 다음 작업을 수행합니다.

   - AdventureWorks 데이터베이스의 Contacts 테이블에서 데이터를 검색 합니다.

   - BDC 서비스에 대 한 연락처 엔터티 목록을 반환 합니다.

     > [!NOTE]
     > 필드의 값을 `ServerName` 서버의 이름으로 바꿉니다.

     [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="test-the-project"></a>프로젝트 테스트

프로젝트를 실행 하면 SharePoint 사이트가 열리고 Visual Studio에서 비즈니스 데이터 연결 서비스에 모델을 추가 합니다. SharePoint에서 Contact 엔터티를 참조 하는 외부 목록을 만듭니다. AdventureWorks 데이터베이스의 연락처에 대 한 데이터가 목록에 표시 됩니다.

> [!NOTE]
> 솔루션을 디버깅 하려면 먼저 SharePoint에서 보안 설정을 수정 해야 할 수 있습니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

1. **F5** 키를 선택합니다.

     SharePoint 사이트가 열립니다.

2. **사이트 작업** 메뉴에서 **기타 옵션** 명령을 선택 합니다.

3. **만들기** 페이지에서 **외부 목록** 템플릿을 선택한 다음 **만들기** 단추를 선택 합니다.

4. 사용자 지정 목록에 **연락처**이름을 지정 합니다.

5. **외부 콘텐츠 형식** 필드 옆에 있는 찾아보기 단추를 선택 합니다.

6. **외부 콘텐츠 형식 선택** 대화 상자에서 **AdventureWorksContacts** 항목을 선택 하 고 **만들기** 단추를 선택 합니다.

     SharePoint에서 AdventureWorks 샘플 데이터베이스의 연락처를 포함하는 외부 목록을 만듭니다.

7. SpecificFinder 메서드를 테스트하려면 목록에서 연락처를 선택합니다.

8. 리본 메뉴에서 **항목** 탭을 선택 하 고 **항목 보기** 명령을 선택 합니다.

     선택한 연락처의 세부 정보가 폼에 나타납니다.

## <a name="next-steps"></a>다음 단계

다음 항목에서 SharePoint의 BDC 서비스에 대 한 모델을 디자인 하는 방법에 대해 자세히 알아볼 수 있습니다.

- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)

## <a name="see-also"></a>추가 정보

[비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md) 
 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md) 
 [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md) 
 [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)
