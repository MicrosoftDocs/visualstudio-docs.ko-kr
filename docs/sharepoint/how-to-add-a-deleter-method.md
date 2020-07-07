---
title: '방법: Deleter 메서드 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dd97d28936e9f0cc50e9064fdc1a6a64bb20fc77
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017034"
---
# <a name="how-to-add-a-deleter-method"></a>방법: Deleter 메서드 추가
  모델에 Deleter 메서드를 추가 하 여 최종 사용자가 SharePoint 사이트의 외부 목록에서 데이터 레코드를 삭제할 수 있도록 설정할 수 있습니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

### <a name="to-create-a-deleter-method"></a>Deleter 메서드를 만들려면

1. **BDC 디자이너**에서 엔터티를 선택 합니다.

2. 메뉴 모음에서 **View**  >  **다른 Windows**  >  **BDC 메서드 세부 정보**보기를 선택 합니다.

    **BDC 메서드 세부 정보** 창이 열립니다. 이 창에 대 한 자세한 내용은 [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)를 참조 하세요.

3. **메서드 추가** 목록에서 **Deleter 메서드 만들기**를 선택 합니다.

    Visual Studio에서는 다음 요소를 모델에 추가 합니다. 이러한 요소는 **BDC 메서드 세부 정보** 창에 표시 됩니다.

   - **Delete**라는 메서드입니다.

   - 메서드에 대 한 입력 매개 변수입니다.

   - 매개 변수에 대 한 형식 설명자입니다.

   - 메서드에 대 한 메서드 인스턴스입니다.

     자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

4. **솔루션 탐색기**에서 엔터티에 대해 생성 된 서비스 코드 파일의 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다.

    엔터티 서비스 코드 파일이 코드 편집기에서 열립니다. 엔터티 서비스 코드 파일에 대 한 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조 하세요.

5. Deleter 메서드에 코드를 추가 하 여 레코드를 삭제 합니다. 다음 예에서는 SQL Server에 대 한 AdventureWorks 예제 데이터베이스를 사용 하 여 판매 주문에서 품목을 삭제 합니다.

   > [!NOTE]
   > 이 예제의 메서드는 두 개의 입력 매개 변수를 사용 합니다.

   > [!NOTE]
   > 필드의 값을 `ServerName` 서버의 이름으로 바꿉니다.

    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]

## <a name="see-also"></a>참고 항목
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [방법: 메서드에 매개 변수 추가](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
