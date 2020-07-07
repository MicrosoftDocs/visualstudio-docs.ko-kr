---
title: '방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한 지정 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a87cc8a3eb8f98ea19a87e93c37aae5303151ecf
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015403"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한 지정
  리소스 파일을 사용하여 지역화된 이름을 제공하고, 속성을 정의하고, BDC(비즈니스 데이터 연결) 모델에 정의된 개체에 대한 사용 권한을 적용할 수 있습니다. 이 정보를 지정 하려면 비즈니스 **데이터 연결 모델** 항목을 포함 하는 프로젝트에 **비즈니스 데이터 연결 리소스** 항목을 추가 합니다. 그런 다음 리소스 파일의 XML을 편집하여 이름, 속성 및 사용 권한을 지정합니다.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>SharePoint 프로젝트에 BDC 리소스 파일을 추가 하려면

1. **솔루션 탐색기**에서 SharePoint 프로젝트에 대 한 폴더를 확장 하 고 BDC 모델이 포함 된 폴더를 선택 합니다.

2. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

3. **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

4. **새 항목 추가** 대화 상자에서 **비즈니스 데이터 연결 리소스 항목**을 선택 합니다.

5. **이름** 상자에서 리소스 파일의 이름을 지정한 다음 **추가** 단추를 선택 합니다.

     확장명이 .bdcr인 리소스 파일이 프로젝트에 추가되고 편집할 수 있도록 열립니다.

6. XML을 추가하여 BDC 모델을 적용할 지역화된 이름, 속성 및 사용 권한을 정의합니다.

     이러한 요소를 정의 하는 방법에 대 한 자세한 내용은 [모델 및 리소스 파일](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14))을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
- [방법: BDC 모델 만들기](../sharepoint/how-to-create-a-bdc-model.md)
- [방법: BDC 기능에 사용자 지정 어셈블리 포함](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)
