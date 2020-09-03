---
title: '방법: 메서드에 매개 변수 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], adding a method to a parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter
- BDC [SharePoint development in Visual Studio], adding a method to a parameter
- BDC [SharePoint development in Visual Studio], parameter
- Business Data Connectivity service [SharePoint development in Visual Studio], method parameters
- BDC [SharePoint development in Visual Studio], method parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6d0496d0fd6a347683d56630990e50af585520ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016710"
---
# <a name="how-to-add-a-parameter-to-a-method"></a>방법: 메서드에 매개 변수 추가
  매개 변수를 사용 하 여 메서드에 정보를 전달 하거나 메서드에서 정보를 반환 합니다. 모든 메서드에는 매개 변수가 하나 이상 있어야 합니다. 만들려는 메서드 유형을 지 원하는 매개 변수를 디자인 하는 방법에 대 한 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

 메서드에 매개 변수를 추가 하면 Visual Studio에서 프로젝트의 모델 파일에 있는 XML에 매개 변수 요소를 추가 합니다. Parameter 요소의 특성에 대 한 자세한 내용은 [매개 변수](/previous-versions/office/developer/sharepoint-2010/ee557705(v=office.14))를 참조 하세요.

### <a name="to-add-a-parameter-to-a-method"></a>메서드에 매개 변수를 추가하려면

1. 엔터티에 메서드를 추가 합니다.

2. 메뉴 모음에서 **View**  >  **다른 Windows**  >  **BDC 메서드 세부 정보**보기를 선택 합니다.

     **BDC 메서드 세부 정보** 창이 열립니다. 자세한 내용은 [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)를 참조 하세요.

3. **BDC 메서드 세부 정보** 창에서 메서드의 노드를 확장 한 다음 **매개 변수** 노드를 확장 합니다.

4. **매개 변수 추가** 목록에서 **매개 변수 만들기**를 선택 합니다.

     새 매개 변수가 **매개 변수** 노드 아래에 나타납니다.

5. 메뉴 모음에서 **보기**  >  **속성 창**을 선택 합니다.

6. **속성** 창에서 **이름** 속성을 적절 한 이름으로 설정 합니다. 예를 들어 메서드가 고객을 반환 하는 경우 메서드 이름을 **GetCustomers**로 할 수 있습니다.

7. **BDC 메서드 세부 정보** 창에서 매개 변수 방향에 대해 표시 되는 목록을 연 다음 **In**, **InOut**, **Out**또는 **Return**을 선택 합니다.

     만들려는 유형 메서드에 대해 선택할 방향에 대 한 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

8. 매개 변수의 형식 설명자를 수정 합니다. 자세한 내용은 [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
