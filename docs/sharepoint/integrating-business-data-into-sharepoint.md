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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016315"
---
# <a name="integrate-business-data-into-sharepoint"></a>SharePoint에 비즈니스 데이터 통합
  SharePoint에 비즈니스 데이터를 통합할 수 있습니다. 비즈니스 데이터는 [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel, SAP 등의 백 엔드 서버 애플리케이션 또는 웹 서비스에서 가져올 수 있습니다. 사용자는 SharePoint에서 외부 목록 또는 비즈니스 데이터 웹 파트를 사용하여 비즈니스 데이터를 표시, 추가, 업데이트 또는 삭제할 수 있습니다.  사용자는 Microsoft Outlook과 같은 Microsoft Office 애플리케이션에서 오프라인으로 이 데이터에 액세스할 수도 있습니다. 자세한 내용은 [외부 데이터를 표시할 수 있는 위치](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14))를 참조하세요.

 SharePoint에 데이터를 통합하려면 BDC(비즈니스 데이터 연결) 서비스용 모델을 만듭니다. BDC 서비스는 비즈니스 애플리케이션의 데이터 정보를 저장하는 SharePoint의 애플리케이션입니다. 자세한 내용은 [BDC(비즈니스 데이터 연결) 서비스](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14))를 참조하세요.

## <a name="models-in-visual-studio"></a>Visual Studio의 모델
 Visual Studio의 모델을 사용하여 백 엔드 데이터 소스에서 데이터를 검색하고 업데이트하는 사용자 지정 코드를 작성할 수 있습니다. 여러 데이터 소스의 데이터를 집계할 수도 있습니다. 예를 들어 [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] 데이터베이스와 웹 서비스의 데이터를 포함하는 고객 목록을 표시할 수 있습니다.

 SharePoint에 이미 배포된 모델을 가져올 수도 있습니다. 모델을 가져온 후 사용자 지정 코드를 추가하거나, Visual Studio를 사용하여 모델을 패키지하고 여러 SharePoint Server 팜에 배포할 수 있습니다. 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조하세요.

## <a name="design-a-model-in-visual-studio"></a>Visual Studio에서 모델 디자인
 디자이너와 여러 도구 창을 사용하여 모델을 디자인할 수 있습니다. 모델을 디자인하면 Visual Studio에서 모델 XML을 생성합니다. 자세한 내용은 [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)를 참조하세요.

 모델에는 엔터티와 메서드가 포함되어 있습니다.

### <a name="entities"></a>엔터티
 엔터티는 필드 컬렉션을 설명합니다. 예를 들어 엔터티는 데이터베이스의 테이블을 나타낼 수 있습니다. 엔터티는 SharePoint에서 외부 콘텐츠 형식으로 표시됩니다. 외부 콘텐츠 형식에 대한 자세한 내용은 [외부 콘텐츠 형식이란?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))을 참조하세요.

### <a name="methods"></a>메서드
 메서드를 사용하면 외부 콘텐츠 형식의 소비자가 엔터티의 필드에 대해 작업을 수행할 수 있습니다. 예를 들어 업데이트 프로그램 메서드를 사용하면 사용자가 `Address` 및 `BirthDate`가 `Customer` 엔터티의 필드인 고객의 주소 및 생년월일을 변경할 수 있습니다.

 Visual Studio에서 모델의 각 엔터티에 대한 서비스 코드 파일을 생성합니다. 모델에 메서드를 추가하면 Visual Studio에서 서비스 코드 파일에 해당 메서드를 생성합니다. 각 메서드에 코드를 추가하여 적절한 작업을 수행합니다. 예를 들어 모델에 Creator 메서드를 추가하면 Visual Studio에서 서비스 코드 파일에 Creator 메서드를 생성합니다. 이 메서드는 사용자가 모델 기반 목록에서 **새 항목** 단추를 클릭할 때 BDC 서비스에서 호출됩니다. 따라서 데이터 소스에 새 데이터를 추가하는 코드를 Creator 메서드에 추가합니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조하세요.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)|새 모델을 만들거나 SharePoint에서 내보낸 모델을 가져오는 방법을 보여 줍니다.|
|[비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)|Visual Studio 디자인 도구를 사용하여 모델의 요소를 디자인하는 방법을 설명합니다.|
|[BCS를 사용하여 솔루션을 빌드할 때 SharePoint Designer 대 Visual Studio를 사용해야 하는 경우](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Visual Studio를 사용하여 BDC 모델을 만들지 또는 SharePoint Designer를 사용하여 BDC 모델을 만들지 결정하는 데 도움이 됩니다.|
