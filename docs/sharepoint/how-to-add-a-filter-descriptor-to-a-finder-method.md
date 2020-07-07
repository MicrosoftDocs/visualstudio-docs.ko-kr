---
title: '방법: Finder 메서드에 필터 설명자 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 228afb2f49f4d528fa9b806e9bf8d2531f7de901
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016735"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>방법: Finder 메서드에 필터 설명자 추가
  필터 설명자를 사용 하면 모델의 소비자가 실행 되기 전에 메서드에 값을 전달할 수 있습니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

 한 가지 일반적인 시나리오는 SharePoint의 사용자가 특정 조건에 맞는 외부 콘텐츠 형식의 인스턴스를 검색 하는 것입니다. Finder 메서드에 필터 설명자를 추가 하 여이 시나리오를 지원할 수 있습니다.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Finder 메서드에 필터 설명자를 추가 하려면

1. **BDC 메서드 세부 정보** 창에서 Finder 메서드의 노드를 확장 하 고 **매개 변수** 노드를 확장 한 다음 입력 매개 변수를 추가 합니다. 자세한 내용은 [방법: 메서드에 매개 변수 추가](../sharepoint/how-to-add-a-parameter-to-a-method.md)를 참조 하세요.

2. **메서드 세부 정보** 창에서 매개 변수의 형식 설명자를 선택 합니다.

3. 메뉴 모음에서 **보기**  >  **속성 창**을 선택 합니다.

4. **속성** 창에서 **유형 이름** 속성을 필터에 적합 한 데이터 형식으로 설정 합니다.

     예를 들어 필터는 주문 날짜를 사용 하 여 메서드에서 반환 되는 판매 주문 수를 제한할 수 있습니다. 해당 필터를 지원 하려면 형식 설명자의 **형식 이름** 속성이 **system.object**로 설정 되어야 합니다.

5. **메서드 세부 정보** 창에서 **필터 설명자** 노드를 확장 합니다.

6. **필터 설명자 추가** 목록에서 **필터 설명자 만들기**를 선택 합니다.

     새 필터 설명자가 **필터 설명자** 노드 아래에 나타납니다.

7. 메뉴 모음에서 **보기**  >  **속성 창**을 선택 합니다.

8. **속성** 창에서 **형식** 속성을 선택 합니다.

9. **유형** 속성에 대해 표시 되는 목록에서 원하는 필터링 패턴을 선택 합니다.

     예를 들어 주문 날짜를 사용 하 여 Finder 메서드에서 반환 되는 판매 주문 수를 제한 하는 필터를 만들려면 **비교**를 선택 합니다. 비교 필터를 사용 하면 finder 메서드가 특정 조건에 맞는 인스턴스만 반환 합니다. 각 필터링 패턴에 대 한 자세한 내용은 [BDC에서 지 원하는 필터 유형](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14))을 참조 하세요.

10. **속성** 창에서 **연결 된 형식 설명자** 속성을 선택 합니다.

11. **연결 된 형식 설명자** 속성에 대해 표시 되는 목록에서이 절차의 앞부분에서 만든 형식 설명자를 선택 합니다. 이는 필터와 Finder 메서드의 입력 매개 변수를 연결 합니다.

12. 데이터를 반환 하는 Finder 메서드에 코드를 추가 합니다. 입력 매개 변수를 select 쿼리에서 조건으로 사용할 수 있습니다.

     다음 예에서는 지정 된 주문 날짜의 판매 주문을 반환 합니다.

    > [!NOTE]
    > 필드의 값을 `ServerName` 서버의 이름으로 바꿉니다.

     [!code-csharp[SP_BDC#11](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#11)]

## <a name="see-also"></a>참고 항목
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
- [방법: 메서드에 매개 변수 추가](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)
