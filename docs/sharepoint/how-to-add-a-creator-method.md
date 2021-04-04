---
title: '방법: Creator 메서드 추가 | Microsoft Docs'
description: SharePoint의 BDC (비즈니스 데이터 연결) 서비스에서 엔터티의 데이터 원본에 새 데이터를 추가 하는 Creator 메서드를 추가 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], Creator
- BDC [SharePoint development in Visual Studio], adding entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], adding entity instances
- BDC [SharePoint development in Visual Studio], adding entities
- Business Data Connectivity service [SharePoint development in Visual Studio], Creator
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 950745a533fbea8d360c8bea6d839a304dd6e0d7
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216412"
---
# <a name="how-to-add-a-creator-method"></a>방법: Creator 메서드 추가
  Creator 메서드는 엔터티의 데이터 원본에 새 데이터를 추가 합니다. BDC (비즈니스 데이터 연결) 서비스는 사용자가 모델을 기반으로 하는 목록 **리본** 에서 **새 항목** 단추를 선택할 때이 메서드를 호출 합니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조하세요.

### <a name="to-add-a-creator-method"></a>Creator 메서드를 추가 하려면

1. **BDC 디자이너** 에서 엔터티를 선택 합니다.

2. 메뉴 모음에서   >  **다른 Windows**  > **BDC 메서드 세부 정보** 보기를 선택 합니다.

    **BDC 메서드 세부 정보** 창이 열립니다. 해당 창에 대 한 자세한 내용은 [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)를 참조 하세요.

3. **메서드 추가** 목록에서 **Creator 메서드 만들기** 를 선택 합니다.

    Visual Studio에서는 다음 요소를 모델에 추가 하 고 이러한 요소는 **BDC 메서드 세부 정보** 창에 표시 됩니다.

   - **Create** 라는 메서드

   - 메서드에 대 한 입력 매개 변수입니다.

   - 메서드의 반환 매개 변수입니다.

   - 매개 변수에 대 한 형식 설명자입니다.

   - 메서드에 대 한 메서드 인스턴스입니다.

     자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조하세요.

4. **솔루션 탐색기** 에서 엔터티에 대해 생성 된 서비스 코드 파일의 바로 가기 메뉴를 열고 **코드 보기** 를 선택 합니다.

    엔터티 서비스 코드 파일이 코드 편집기에서 열립니다. 엔터티 서비스 코드 파일에 대 한 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조 하세요.

5. 데이터 소스에 데이터를 추가 하는 작성자 메서드에 코드를 추가 합니다. 다음 예에서는 SQL Server에 대 한 AdventureWorks 예제 데이터베이스에 연락처를 추가 합니다.

   > [!NOTE]
   > 필드의 값을 `ServerName` 서버의 이름으로 바꿉니다.

    :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet4":::
    :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet4":::

## <a name="see-also"></a>참고 항목
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [BDC 모델 디자인 도구 개요](../sharepoint/bdc-model-design-tools-overview.md)
- [방법: 메서드에 매개 변수 추가](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [방법: 메서드 인스턴스 정의](../sharepoint/how-to-define-a-method-instance.md)
