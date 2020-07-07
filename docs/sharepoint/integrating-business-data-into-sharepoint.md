---
title: SharePoint에 비즈니스 데이터 통합 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4bbfb681a0dac0825bf7af4f1f27ab1c1b50053
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016315"
---
# <a name="integrate-business-data-into-sharepoint"></a>SharePoint에 비즈니스 데이터 통합
  비즈니스 데이터를 SharePoint에 통합할 수 있습니다. 비즈니스 데이터는, Siebel, SAP 등의 백 엔드 서버 응용 프로그램 또는 웹 서비스에서 가져올 수 있습니다 [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)] . 사용자는 SharePoint에서 외부 목록 또는 비즈니스 데이터 웹 파트를 사용 하 여 비즈니스 데이터를 확인, 추가, 업데이트 또는 삭제할 수 있습니다.  사용자는 Microsoft Outlook과 같은 Microsoft Office 응용 프로그램에서이 데이터를 오프 라인으로 액세스할 수도 있습니다. 자세한 내용은 [외부 데이터를 표시할 수 있는 위치](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14))를 참조 하세요.

 데이터를 SharePoint에 통합 하려면 BDC (비즈니스 데이터 연결) 서비스용 모델을 만듭니다. BDC 서비스는 비즈니스 응용 프로그램의 데이터에 대 한 정보를 저장 하는 SharePoint의 응용 프로그램입니다. 자세한 내용은 [BDC (비즈니스 데이터 연결) 서비스](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14))를 참조 하세요.

## <a name="models-in-visual-studio"></a>Visual Studio의 모델
 Visual Studio의 모델을 사용 하 여 백 엔드 데이터 원본에서 데이터를 검색 하 고 업데이트 하는 사용자 지정 코드를 작성할 수 있습니다. 여러 데이터 원본의 데이터를 집계할 수도 있습니다. 예를 들어 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] 데이터베이스 및 웹 서비스의 데이터를 포함 하는 고객의 목록을 표시할 수 있습니다.

 SharePoint에 이미 배포 된 모델을 가져올 수도 있습니다. 모델을 가져온 후에는 사용자 지정 코드를 추가 하거나 Visual Studio를 사용 하 여 여러 SharePoint 서버 팜에 모델을 패키지 하 고 배포할 수 있습니다. 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조 하세요.

## <a name="design-a-model-in-visual-studio"></a>Visual Studio에서 모델 디자인
 디자이너와 여러 도구 창을 사용 하 여 모델을 디자인할 수 있습니다. 모델을 디자인할 때 Visual Studio에서 모델 XML을 생성 합니다. 자세한 내용은 [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)를 참조 하세요.

 모델에는 엔터티와 메서드가 포함 됩니다.

### <a name="entities"></a>엔터티
 엔터티는 필드의 컬렉션을 설명 합니다. 예를 들어 엔터티는 데이터베이스의 테이블을 나타낼 수 있습니다. 엔터티는 SharePoint에서 외부 콘텐츠 형식으로 표시 됩니다. 외부 콘텐츠 형식에 대 한 자세한 내용은 [외부 콘텐츠 형식 이란?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14)) 을 참조 하세요.

### <a name="methods"></a>메서드
 메서드를 사용 하면 외부 콘텐츠 형식의 소비자가 엔터티의 필드에 대해 작업을 수행할 수 있습니다. 예를 들어 업데이트 프로그램 메서드를 사용 하 여 사용자가 주소를 변경 하 고 `Address` 및 `BirthDate` 가 엔터티의 필드인 고객의 생년월일을 변경할 수 있습니다 `Customer` .

 Visual Studio는 모델의 각 엔터티에 대 한 서비스 코드 파일을 생성 합니다. 모델에 메서드를 추가 하면 Visual Studio에서 서비스 코드 파일에 해당 메서드를 생성 합니다. 각 메서드에 코드를 추가 하 여 적절 한 작업을 수행 합니다. 예를 들어 작성자 메서드를 모델에 추가 하는 경우 Visual Studio는 서비스 코드 파일에 Creator 메서드를 생성 합니다. 사용자가 모델을 기반으로 하는 목록에서 **새 항목** 단추를 클릭 하면 BDC 서비스에서이 메서드를 호출 합니다. 따라서 데이터 원본에 새 데이터를 추가 하는 Creator 메서드에 코드를 추가 합니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)|새 모델을 만들거나 SharePoint에서 내보내는 모델을 가져오는 방법을 보여 줍니다.|
|[비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)|Visual Studio 디자인 도구를 사용 하 여 모델의 요소를 디자인 하는 방법을 설명 합니다.|
|[BCS를 사용 하 여 솔루션을 빌드할 때 SharePoint 디자이너 및 Visual Studio를 사용 하는 경우](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Visual Studio를 사용할지 아니면 SharePoint Designer를 사용 하 여 BDC에 대 한 모델을 만들지를 결정할 수 있습니다.|
