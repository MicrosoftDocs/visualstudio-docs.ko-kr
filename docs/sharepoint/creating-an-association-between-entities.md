---
title: 엔터티 간 연결 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
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
ms.openlocfilehash: ee767ded0687baa09653bd82785b68bee7fa0ebd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72981088"
---
# <a name="create-an-association-between-entities"></a>엔터티 간 연결 만들기
  연결을 만들어 BDC (비즈니스 데이터 연결) 모델의 엔터티 간 관계를 정의할 수 있습니다. Visual Studio는 모델의 소비자에 게 각 연결에 대 한 정보를 제공 하는 메서드를 생성 합니다. 이러한 메서드는 SharePoint 웹 파트, 목록 또는 사용자 지정 애플리케이션에서 사용되어 UI(사용자 인터페이스)에 데이터 관계를 표시할 수 있습니다.

## <a name="create-an-association"></a>연결 만들기
 Visual Studio **도구 상자**에서 **연결** 컨트롤을 선택 하 고, 첫 번째 엔터티 (원본 엔터티)를 선택한 다음, 두 번째 엔터티 (대상 엔터티)를 선택 하 여 연결을 만듭니다. 연결 **편집기**에서 연결의 세부 정보를 정의할 수 있습니다. 자세한 내용은 [방법: 엔터티 간 연결 만들기](../sharepoint/how-to-create-an-association-between-entities.md)를 참조 하세요.

## <a name="association-methods"></a>연결 메서드
 SharePoint 비즈니스 데이터 웹 파트와 같은 응용 프로그램은 엔터티의 서비스 클래스에서 메서드를 호출 하 여 연결을 사용 합니다. **연결 편집기**에서 엔터티를 선택 하 여 엔터티의 서비스 클래스에 메서드를 추가할 수 있습니다.

 기본적으로 **연결 편집기** 는 소스 및 대상 엔터티에 연결 탐색 메서드를 추가 합니다. 소비자는 소스 엔터티의 연결 탐색 메서드를 사용 하 여 대상 엔터티 목록을 검색할 수 있습니다. 대상 엔터티의 Association 탐색 메서드를 사용 하면 소비자가 대상 엔터티와 관련 된 소스 엔터티를 검색할 수 있습니다.

 이러한 각 메서드에 코드를 추가 하 여 적절 한 정보를 반환 해야 합니다. 다른 형식의 메서드를 추가 하 여 고급 시나리오를 지원할 수도 있습니다. 이러한 각 방법에 대 한 자세한 내용은 [지원 되는 작업](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14))을 참조 하세요.

## <a name="types-of-associations"></a>연결 유형
 BDC 디자이너에서 외래 키 기반 연결 및 외래 키가 없는 연결 이라는 두 가지 유형의 연결을 만들 수 있습니다.

### <a name="foreign-key-based-association"></a>외래 키 기반 연결
 원본 엔터티의 식별자와 대상 엔터티에 정의 된 형식 설명자를 연결 하 여 외래 키 기반 연결을 만들 수 있습니다. 이 관계를 통해 모델의 소비자는 사용자에 게 향상 된 UI를 제공할 수 있습니다. 예를 들어 사용자가 드롭다운 목록에서 고객을 표시할 수 있는 판매 주문을 만들 수 있도록 하는 Outlook의 양식입니다. 또는 사용자가 고객에 대 한 프로필 페이지를 열 수 있는 SharePoint의 판매 주문 목록입니다.

 외래 키 기반 연결을 만들려면 동일한 이름과 형식을 공유 하는 식별자와 형식 설명자를 관련 시킵니다. 예를 들어 엔터티와 엔터티 간에 외래 키 기반 연결을 만들 수 있습니다 `Contact` `SalesOrder` . `SalesOrder`엔터티는 `ContactID` Finder 또는 특정 finder 메서드의 반환 매개 변수 일부로 형식 설명자를 반환 합니다. 두 형식 설명자가 모두 **연결 편집기**에 표시 됩니다. 엔터티와 엔터티 간에 외래 키 기반 관계를 만들려면 `Contact` `SalesOrder` `ContactID` 이러한 각 필드 옆에 있는 식별자를 선택 합니다.

 대상 엔터티 컬렉션을 반환 하는 소스 엔터티의 Association Navigator 메서드에 코드를 추가 합니다. 다음 예에서는 연락처에 대 한 판매 주문을 반환 합니다.

 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]

 소스 엔터티를 반환 하는 대상 엔터티의 Association Navigator 메서드에 코드를 추가 합니다. 다음 예에서는 판매 주문과 관련 된 연락처를 반환 합니다.

 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]

### <a name="foreign-keyless-association"></a>외부 키가 없는 연결
 식별자를 필드 형식 설명자에 매핑하지 않고 연결을 만들 수 있습니다. 원본 엔터티가 대상 엔터티와 직접 관계가 없는 경우 이러한 종류의 연결을 만듭니다. 예를 들어 테이블 `SalesOrderDetail` 에는 테이블의 기본 키에 매핑되는 외래 키가 없습니다 `Contact` .

 와 관련 된 정보를 테이블에 표시 하려는 경우 `SalesOrderDetail` `Contact` 엔터티와 엔터티 간에 외래 키가 없는 연결을 만들 수 있습니다 `Contact` `SalesOrderDetail` .

 엔터티의 연결 탐색 메서드에서 `Contact` `SalesOrderDetail` 테이블을 조인 하거나 저장 프로시저를 호출 하 여 엔터티를 반환 합니다.

 다음 예에서는 테이블을 조인 하 여 모든 판매 주문에 대 한 세부 정보를 반환 합니다.

 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]

 엔터티의 연결 탐색 메서드에서 `SalesOrderDetail` 관련 된을 반환 합니다 `Contact` . 다음은 이에 대한 예입니다.

 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]

## <a name="see-also"></a>추가 정보
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: 엔터티 간 연결 만들기](../sharepoint/how-to-create-an-association-between-entities.md)
