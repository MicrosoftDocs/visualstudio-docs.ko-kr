---
title: '방법: 모델에 엔터티 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b80f39494b98014a75d4265f228906be2ff45188
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016670"
---
# <a name="how-to-add-an-entity-to-a-model"></a>방법: 모델에 엔터티 추가
  엔터티를 만들려면 Visual Studio **도구 상자** 의 엔터티 컨트롤을 BDC (비즈니스 데이터 연결) 디자이너에 추가 합니다.

### <a name="to-add-an-entity-to-the-model"></a>모델에 엔터티를 추가 하려면

1. BDC 프로젝트를 만들거나 기존 BDC 프로젝트를 엽니다. 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조 하세요.

2. **도구 상자**의 **BusinessDataCatalog** 그룹에서 **엔터티** 컨트롤을 디자이너에 추가 합니다.

     새 엔터티가 디자이너에 표시 됩니다. Visual Studio `<Entity>` 에서 프로젝트의 BDC 모델 파일의 XML에 요소를 추가 합니다. 엔터티 요소의 특성에 대 한 자세한 내용은 [엔터티](/previous-versions/office/developer/sharepoint-2010/ee558325(v=office.14))를 참조 하세요.

3. 디자이너에서 엔터티에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 다음 **식별자**를 선택 합니다.

     엔터티에 새 식별자가 나타납니다.

    > [!NOTE]
    > **속성** 창에서 엔터티 이름 및 식별자를 변경할 수 있습니다.

4. 클래스에서 엔터티 필드를 정의 합니다. 프로젝트에 새 클래스를 추가 하거나 개체 관계형 디자이너 (O/R 디자이너)와 같은 다른 도구를 사용 하 여 만든 기존 클래스를 사용할 수 있습니다. 다음 예제에서는 Contact 라는 엔터티 클래스를 보여 줍니다.

     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]

## <a name="see-also"></a>참고 항목
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
