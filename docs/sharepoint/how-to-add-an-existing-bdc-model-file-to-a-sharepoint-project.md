---
title: '방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 92063b5aeaf4f86919b9eabf783b102a9f5b8f34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016516"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가
  Visual Studio를 사용 하 여 모델 파일 (*. bdcm*)을 SharePoint 팜 프로젝트에 추가 하 여 BDC (비즈니스 데이터 연결) 모델을 사용자 지정 하 고 패키지 하 고 재배포할 수 있습니다. 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조 하세요.

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>SharePoint 프로젝트에 BDC 모델 파일을 추가 하려면

1. **솔루션 탐색기**에서 SharePoint 프로젝트에 대 한 폴더를 선택 합니다.

2. 메뉴 모음에서 **프로젝트**  >  **기존 항목 추가**를 선택 합니다.

3. **기존 항목 추가** 대화 상자에서 프로젝트에 추가 하려는 모델 정의 파일의 위치로 이동 하 여 파일을 선택한 다음 **추가** 단추를 선택 합니다.

    모델이 *.net 어셈블리 형식의 LOB (기간 업무) 시스템*을 정의 하지 않는 경우 **.Net 어셈블리 추가 LobSystem** 대화 상자가 열립니다.

4. 대화 상자가 표시 되 면 다음 단계 중 하나를 수행 합니다.

   - 사용자 지정 코드를 작성 하 고 디자이너를 사용 하 여 가져온 모델에 대 한 메타 데이터를 정의 하려면 **예** 단추를 선택 하 고 시스템 이름을 지정한 다음 **확인** 단추를 선택 합니다.

   - 그렇지 않으면 **아니요** 단추를 선택 하 고 **확인** 단추를 선택 합니다.

     **비즈니스 데이터 연결 모델** 항목이 프로젝트에 추가 됩니다.

## <a name="see-also"></a>추가 정보
- [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
- [방법: BDC 모델 만들기](../sharepoint/how-to-create-a-bdc-model.md)
- [방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한 지정](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [방법: BDC 기능에 사용자 지정 어셈블리 포함](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)
