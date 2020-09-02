---
title: BDC 모델 디자인 도구 개요 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7a2531f1cc6352a03acf0b3d6af82c35e47c2743
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64827947"
---
# <a name="bdc-model-design-tools-overview"></a>BDC 모델 디자인 도구 개요
  Bdc 디자이너, **Bdc 메서드 세부 정보** 창 및 **bdc 탐색기**를 사용 하 여 Bdc (비즈니스 데이터 연결) 모델을 디자인할 수 있습니다.

 **BDC 탐색기** 를 사용 하 여 모델을 찾아보고, 모델을 검색 하 고, 형식 설명자를 정의할 수 있습니다.

## <a name="bdc-designer"></a>BDC 디자이너
 BDC 디자이너를 사용 하면 모델의 엔터티를 정의 하 고 서로 관계를 시각적으로 정렬할 수 있습니다. BDC 디자이너를 사용 하 여 다음 작업을 수행할 수 있습니다.

- 모델에 엔터티를 추가 합니다.

- 모델에서 엔터티를 제거 합니다.

- 엔터티 간의 관계를 정의 합니다.

  BDC 디자이너를 열려면 프로젝트에서 모델 파일을 두 번 클릭 하거나 모델 파일에 대 한 바로 가기 메뉴를 연 다음 **열기**를 선택 합니다. **도구 상자** 에서 디자이너로 **엔터티** 를 끌거나 복사 하 여 모델에 엔터티를 추가 합니다. 두 엔터티 간의 연결을 만들려면 **도구 상자**에서 **연결** 컨트롤을 선택 하 고 첫 번째 엔터티를 선택한 다음 두 번째 엔터티를 선택 합니다.

## <a name="bdc-method-details-window"></a>BDC 메서드 세부 정보 창
 **BDC 메서드 세부 정보** 창을 사용 하 여 메서드의 매개 변수, 인스턴스 및 필터 설명자를 정의 합니다.

 **BDC 메서드 세부 정보** 창에서 Finder, 특정 Finder, Creator, 업데이트 및 Deleter 메서드를 신속 하 게 생성할 수 있습니다. 이러한 메서드를 생성 하는 경우 Visual Studio는 매개 변수, 인스턴스 및 형식 설명자와 같은 메타 데이터를 메서드에 추가 합니다. 특정 시나리오를 충족 하도록이 메타 데이터를 수정할 수 있습니다.

 **BDC 메서드 세부 정보** 창을 열려면 메뉴 모음에서 **View**  >  **다른 Windows**  >  **BDC 메서드 세부 정보**보기를 선택 합니다.

 **Bdc 메서드 세부 정보** 창에서 메서드를 보려면 bdc 디자이너에서 엔터티를 선택 합니다. 선택한 엔터티의 메서드는 **BDC 메서드 세부 정보** 창에 표시 됩니다. BDC 디자이너에서 엔터티를 선택 하지 않으면 **Bdc 메서드 세부 정보** 창에 정보가 표시 되지 않습니다.

 **BDC 메서드 세부 정보** 창에서 노드를 확장 하거나 축소 하 여 매개 변수, 인스턴스 및 필터 설명자를 정의 합니다. **BDC 탐색기** 를 사용 하 여 형식 설명자를 정의 합니다.

## <a name="bdc-explorer"></a>BDC 탐색기
 **BDC 탐색기** 에는 모델을 구성 하는 요소가 표시 됩니다. **Bdc 탐색기**를 열려면 메뉴 모음에서 **View**  >  **다른 Windows**  >  **BDC 탐색기**보기를 선택 합니다. 모델을 찾아보려면 **BDC 탐색기**에서 노드를 확장 합니다. 각 노드는 모델 파일의 XML에 있는 요소를 나타냅니다.

 **BDC 탐색기**에서 노드를 선택 하면 선택한 각 노드의 속성이 **속성** 창에 표시 됩니다. 이러한 속성 중 대부분은 모델 파일의 특성에 해당 합니다. **BDC 탐색기**맨 위에 있는 검색 상자를 사용 하 여 모델을 검색할 수 있습니다.

> [!NOTE]
> **BDC 탐색기** 에는 식별자, 사용자 지정 속성, 지역화 된 문자열, 연결 그룹, 동작, 필터 설명자, 동작 제어 목록 및 기본 매개 변수 값이 표시 되지 않습니다.

### <a name="define-type-descriptors"></a>형식 설명자 정의
 **BDC 탐색기** 를 사용 하 여 형식 설명자를 정의 합니다. BDC 탐색기를 사용 하면 형식 설명자를 한 번 정의한 후 모델의 다른 위치에서 해당 형식 설명자를 다시 사용할 수 있습니다. 이를 수행 하려면 형식 설명자를 복사 하 고 다른 매개 변수 또는 형식 설명자에 붙여넣습니다.

> [!NOTE]
> 원래 형식 설명자를 변경 해도 해당 형식 설명자의 복사본에는 영향을 주지 않습니다.

 자세한 내용은 [방법: 매개 변수의 형식 설명자 정의](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: BDC 모델 만들기](../sharepoint/how-to-create-a-bdc-model.md)
- [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [방법: Finder 메서드 추가](../sharepoint/how-to-add-a-finder-method.md)
- [방법: 특정 Finder 메서드 추가](../sharepoint/how-to-add-a-specific-finder-method.md)
- [방법: Creator 메서드 추가](../sharepoint/how-to-add-a-creator-method.md)
- [방법: Deleter 메서드 추가](../sharepoint/how-to-add-a-deleter-method.md)
- [방법: 업데이트 프로그램 메서드 추가](../sharepoint/how-to-add-an-updater-method.md)
- [엔터티 간 연결 만들기](../sharepoint/creating-an-association-between-entities.md)
- [연습: 비즈니스 데이터를 사용 하 여 SharePoint에서 외부 목록 만들기](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)
- [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
