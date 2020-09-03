---
title: '방법: 업데이트 프로그램 메서드 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], updating data
- BDC [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating data
- Business Data Connectivity service [SharePoint development in Visual Studio], Updater
- Business Data Connectivity service [SharePoint development in Visual Studio], updating entity instances
- BDC [SharePoint development in Visual Studio], updating entity instances
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c76373c710908a8ae7edc49c4e26ff7e94336a6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014988"
---
# <a name="how-to-add-an-updater-method"></a>방법: 업데이트 프로그램 메서드 추가
  사용자가 *업데이트 프로그램 메서드를 만들어* SharePoint 외부 목록의 비즈니스 데이터를 업데이트할 수 있도록 설정할 수 있습니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

### <a name="to-create-an-updater-method"></a>업데이트 프로그램 메서드를 만들려면

1. BDC 디자이너에서 엔터티를 선택 합니다.

2. 메뉴 모음에서 **View**  >  **다른 Windows**  >  **BDC 메서드 세부 정보**보기를 선택 합니다.

    BDC 메서드 세부 정보 창이 열립니다. 이 창에 대 한 자세한 내용은 [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)를 참조 하세요.

3. **메서드 추가** 목록에서 **업데이트 프로그램 메서드 만들기**를 선택 합니다.

    Visual Studio에서는 다음 요소를 모델에 추가 합니다. 이러한 요소는 BDC 메서드 세부 정보 창에 표시 됩니다.

   - 이름이 **Update**인 메서드입니다.

   - 메서드에 대 한 입력 매개 변수입니다.

   - 매개 변수에 대 한 형식 설명자입니다. 기본적으로 Visual Studio는 Finder 메서드에 대해 정의한 엔터티 형식 설명자를 사용 합니다 (예: Contact).

   - 메서드에 대 한 메서드 인스턴스입니다.

     자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

   > [!NOTE]
   > 엔터티 형식의 식별자가 자동으로 생성 되지 않은 데이터베이스 테이블의 필드를 나타내는 경우 **사전 업데이트 필드** 속성을 **True**로 설정 합니다.

4. **솔루션 탐색기**에서 엔터티에 대해 생성 된 서비스 코드 파일의 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다.

    엔터티 서비스 코드 파일이 **코드 편집기**에서 열립니다. 해당 파일에 대 한 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조 하세요.

5. 업데이트 메서드에 코드를 추가 하 여 데이터를 업데이트 합니다. 다음 예에서는 SQL Server에 대 한 AdventureWorks 예제 데이터베이스의 연락처에 대 한 정보를 업데이트 합니다.

   > [!NOTE]
   > 필드의 값을 `ServerName` 서버의 이름으로 바꿉니다.

    [!code-csharp[SP_BDC#5](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#5)]
    [!code-vb[SP_BDC#5](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#5)]

## <a name="see-also"></a>참조
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [방법: 메서드에 매개 변수 추가](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
