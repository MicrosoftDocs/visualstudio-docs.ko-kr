---
title: '방법: Finder 메서드 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], get entities
- Business Data Connectivity service [SharePoint development in Visual Studio], return entities
- BDC [SharePoint development in Visual Studio], return entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Finder method
- Business Data Connectivity service [SharePoint development in Visual Studio], get entities
- BDC [SharePoint development in Visual Studio], Finder method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fa8f8eb34943cc17bc6cabca8e93ea7569a7ba6
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016729"
---
# <a name="how-to-add-a-finder-method"></a>방법: Finder 메서드 추가
  BDC (비즈니스 데이터 연결) 서비스를 사용 하 여 웹 파트 또는 목록의 엔터티 목록을 표시 하려면 *Finder* 메서드를 만들어야 합니다. Finder 메서드는 엔터티 인스턴스의 컬렉션을 반환 하는 특수 메서드입니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

### <a name="to-create-a-finder-method"></a>Finder 메서드를 만들려면

1. **BDC 디자이너**에서 엔터티를 선택 합니다.

    자세한 내용은 [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)를 참조 하세요.

2. 메뉴 모음에서 **View**  >  **다른 Windows**  >  **BDC 메서드 세부 정보**보기를 선택 합니다.

    **BDC 메서드 세부 정보** 창이 열립니다. **Bdc 메서드 세부** 정보 창에 대 한 자세한 내용은 [bdc 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)를 참조 하세요.

3. **메서드 추가** 목록에서 **Finder 메서드 만들기**를 선택 합니다.

    Visual Studio는 메서드, 반환 매개 변수 및 형식 설명자를 추가 합니다.

4. 형식 설명자를 엔터티 컬렉션 형식 설명자로 구성 합니다. 엔터티 컬렉션 형식 설명자를 만드는 방법에 대 한 자세한 내용은 [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)를 참조 하세요.

   > [!NOTE]
   > 엔터티에 특정 Finder 메서드를 추가한 경우에는이 단계를 수행할 필요가 없습니다. Visual Studio는 특정 Finder 메서드에서 정의한 형식 설명자를 사용 합니다.

5. **솔루션 탐색기**에서 엔터티에 대해 생성 된 서비스 코드 파일의 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다. 서비스 코드 파일에 대 한 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조 하세요.

6. Finder 메서드에 코드를 추가 합니다. 이 코드는 다음 작업을 수행합니다.

   - 데이터 소스에서 데이터를 검색 합니다.

   - BDC 서비스에 대 한 엔터티 목록을 반환 합니다.

     다음 예에서는 `Contact` SQL Server에 대 한 AdventureWorks 예제 데이터베이스의 데이터를 사용 하 여 엔터티 컬렉션을 반환 합니다.

   > [!NOTE]
   > 필드의 값을 `ServerName` 서버의 이름으로 바꿉니다.

    [!code-csharp[SP_BDC#2](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#2)]
    [!code-vb[SP_BDC#2](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#2)]

## <a name="see-also"></a>참고 항목
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [방법: 메서드에 매개 변수 추가](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
