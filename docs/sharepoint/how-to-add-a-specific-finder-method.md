---
title: '방법: 특정 Finder 메서드 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 403213b6dcd87251df0b24333c759c8de8720afd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014813"
---
# <a name="how-to-add-a-specific-finder-method"></a>방법: 특정 Finder 메서드 추가
  *특정 Finder* 메서드를 만들어 단일 엔터티 인스턴스를 반환할 수 있습니다. 사용자가 비즈니스 데이터 웹 파트 또는 외부 목록에서 엔터티를 선택 하면 BDC (비즈니스 데이터 연결) 서비스가 특정 Finder 메서드를 실행 합니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

### <a name="to-create-a-specific-finder-method"></a>특정 Finder 메서드를 만들려면

1. **BDC 디자이너**에서 엔터티를 선택 합니다.

    Visual Studio에서 **BDC 디자이너** 에 엔터티를 추가 하는 방법에 대 한 자세한 내용은 [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)를 참조 하세요.

2. 메뉴 모음에서 **보기**  >  **다른 창**, **BDC 메서드 세부 정보**를 선택 합니다.

    **BDC 메서드 세부 정보** 창이 열립니다. 해당 창에 대 한 자세한 내용은 [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)를 참조 하세요.

3. **메서드 추가** 목록에서 **특정 Finder 메서드 만들기**를 선택 합니다.

    Visual Studio에서는 다음 요소를 모델에 추가 합니다. 이러한 요소는 **BDC 메서드 세부 정보** 창에 표시 됩니다.

   - 메서드

   - 메서드에 대 한 입력 매개 변수입니다.

   - 메서드의 반환 매개 변수입니다.

   - 각 매개 변수에 대 한 형식 설명자입니다.

   - 메서드에 대 한 메서드 인스턴스입니다.

     자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

4. Visual Studio **속성** 창을 엽니다.

5. 반환 매개 변수의 형식 설명자를 엔터티 형식 설명자로 구성 합니다. 엔터티 형식 설명자를 만드는 방법에 대 한 자세한 내용은 [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)를 참조 하세요.

   > [!NOTE]
   > 엔터티에 Finder 메서드를 추가한 경우에는이 단계를 수행할 필요가 없습니다. Visual Studio는 Finder 메서드에서 정의한 형식 설명자를 사용 합니다.

   > [!NOTE]
   > 엔터티 형식의 식별자 필드가 자동으로 생성 되는 데이터베이스 테이블의 필드를 나타내는 경우에는 식별자 필드의 **읽기** 전용 속성을 **True**로 설정 합니다.

6. **메서드 세부 정보** 창에서 메서드의 메서드 인스턴스를 선택 합니다.

7. **속성 창**에서 **반환 매개 변수 이름** 속성을 메서드의 반환 매개 변수 이름으로 설정 합니다. 메서드 인스턴스 속성에 대 한 자세한 내용은 [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14))를 참조 하십시오.

8. **솔루션 탐색기**에서 엔터티에 대해 생성 된 서비스 코드 파일의 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다.

    엔터티 서비스 코드 파일이 코드 편집기에서 열립니다. 엔터티 서비스 코드 파일에 대 한 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조 하세요.

9. 특정 Finder 메서드에 코드를 추가 합니다. 이 코드는 다음 작업을 수행합니다.

   - 데이터 원본에서 레코드를 검색 합니다.

   - 엔터티를 BDC 서비스에 반환 합니다.

     다음 예에서는 SQL Server에 대 한 AdventureWorks 예제 데이터베이스의 연락처를 반환 합니다.

     > [!NOTE]
     > 필드의 값을 `ServerName` 서버의 이름으로 바꿉니다.

     [!code-csharp[SP_BDC#3](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#3)]

## <a name="see-also"></a>추가 정보
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [방법: 메서드에 매개 변수 추가](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
