---
title: '방법: 엔터티 간 연결 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 75d4fcc9b99c9c5e2960e152eb5dac1da1343109
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016931"
---
# <a name="how-to-create-an-association-between-entities"></a>방법: 엔터티 간 연결 만들기
  연결을 만들어 BDC (비즈니스 데이터 연결) 모델의 엔터티 간 관계를 정의할 수 있습니다. Visual Studio는 모델의 소비자에 게 각 연결에 대 한 정보를 제공 하는 메서드를 생성 합니다. 이러한 메서드는 SharePoint 웹 파트, 목록 또는 사용자 지정 애플리케이션에서 사용되어 UI(사용자 인터페이스)에 데이터 관계를 표시할 수 있습니다.

 BDC 디자이너에서 외래 키 기반 연결 및 외래 키가 없는 연결 이라는 두 가지 유형의 연결을 만들 수 있습니다. 자세한 내용은 [엔터티 간 연결 만들기](../sharepoint/creating-an-association-between-entities.md)를 참조 하세요.

### <a name="to-create-an-association-between-entities"></a>엔터티 간 연결을 만들려면

1. **도구 상자**의 **BusinessDataConnectivity** 탭에서 **연결** 항목을 선택 합니다.

2. BDC 디자이너에서 소스 엔터티를 선택한 다음 대상 엔터티를 선택합니다.

     **연결 편집기** 가 표시 됩니다.

3. 외래 키 기반 연결을 만들려면 **외래 키 연결** 확인란을 선택 합니다.

    1. **식별자 매핑** 테이블의 **원본 ID** 열에서 **필드** 열에 표시 되는 일치 하는 각 형식 설명자 옆의 식별자를 선택 합니다.

         예를 들어 **원본 ID** 열에서 `ContactID` `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` 형식 설명자와 형식 설명자 옆에 있는를 선택 합니다 `ReadItem.salesOrder.SalesOrder.ContactID` .

4. 외래 키가 없는 연결을 만들려면 **외래 키 연결** 확인란의 선택을 취소 합니다.

5. **확인** 단추를 선택합니다.

6. BDC 디자이너에서 연결을 나타내는 줄은 소스 엔터티와 대상 엔터티 사이에 표시 됩니다.

     Visual Studio는 대상 엔터티의 서비스 클래스와 원본 엔터티의 서비스 클래스에 연결 탐색기 메서드를 추가 합니다. 연결 탐색 메서드에 대 한 자세한 내용은 [지원 되는 작업](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14))을 참조 하세요.

7. 원본 엔터티의 Association Navigator 메서드에서 대상 엔터티의 컬렉션을 반환 하는 코드를 추가 합니다.

8. 대상 엔터티의 Association Navigator 메서드에서 관련 된 소스 엔터티를 반환 하는 코드를 추가 합니다.

     연결 탐색기 메서드의 예는 [엔터티 간 연결 만들기](../sharepoint/creating-an-association-between-entities.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [엔터티 간 연결 만들기](../sharepoint/creating-an-association-between-entities.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [방법: 메서드에 매개 변수 추가](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
- [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [연습: 비즈니스 데이터를 사용 하 여 SharePoint에서 외부 목록 만들기](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
