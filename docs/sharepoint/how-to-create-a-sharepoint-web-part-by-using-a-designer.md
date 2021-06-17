---
title: '방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기 | Microsoft Docs'
titleSuffix: ''
description: 비주얼 웹 파트 항목을 SharePoint 프로젝트에 추가 하 여 웹 파트를 만듭니다. 그러면 visual Studio에서 visual Web Developer designer가 열립니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cbbb290af0029329910a23a71f68024ee0e5e5f4
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112388"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기

  모든 SharePoint 프로젝트에 **시각적 웹 파트** 항목을 추가 하 여 웹 파트를 만들 수 있습니다. 그러면 웹 파트에 컨트롤과 코드를 추가할 수 있는 visual Studio의 Visual Web Developer designer가 열립니다. 비주얼 웹 파트는 웹 파트와 동일한 방식으로 작동 합니다. 유일한 차이점은 Visual web Developer 디자이너에서 비주얼 웹 파트를 디자인 하는 것입니다.

## <a name="to-create-a-project-for-visual-web-parts"></a>시각적 웹 파트에 대 한 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** >**새로 만들기** > **프로젝트** 를 선택합니다.
::: moniker range="=vs-2017"

2. **새 프로젝트** 대화 상자의 **Visual c #** 또는 **Visual Basic** 에서 **Office/Sharepoint** 노드를 확장 한 다음 **SharePoint 솔루션** 범주를 선택 합니다.

3. 프로젝트 템플릿 목록에서 **SharePoint 2013-비주얼 웹 파트** 를 선택한 다음 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다.
::: moniker-end
::: moniker range=">=vs-2019"
2. **새 프로젝트 만들기** 대화 상자에서 설치 된 sharepoint의 특정 버전에 대해 *Sharepoint 비주얼 웹 파트**를 선택 합니다. 예를 들어 SharePoint 2019을 설치한 경우 **sharepoint 2019-비주얼 웹 파트** 템플릿을 선택 합니다.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. 원하는 경우 프로젝트 이름을 변경한 다음 **만들기** 단추를 선택 합니다.

::: moniker-end
4. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 로컬 컴퓨터에 있는 SharePoint 사이트의 URL을 지정한 다음 **마침** 단추를 선택 합니다.

     **솔루션 탐색기** 웹 파트가 표시 됩니다. Visual Web Developer designer에서 웹 파트를 디자인 한 후에는 지정한 사이트에서 웹 파트를 테스트 합니다.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>기존 SharePoint 프로젝트에 비주얼 웹 파트를 추가 하려면

1. 메뉴 모음에서 **프로젝트** > **새 항목 추가** 를 선택합니다.

2. **새 항목 추가** 대화 상자에서 **Office/SharePoint** 노드를 선택 합니다.

3. 프로젝트 템플릿 목록에서 **비주얼 웹 파트** 를 선택 하 고 이름을 지정한 다음 **추가** 단추를 선택 합니다.

     **솔루션 탐색기** 웹 파트가 표시 됩니다. Visual Web Developer designer에서 웹 파트를 디자인 한 후에는 지정한 사이트에서 웹 파트를 테스트 합니다.

## <a name="see-also"></a>참조

- [SharePoint용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)
- [방법: SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [연습: SharePoint용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [연습: 디자이너를 사용하여 SharePoint용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
