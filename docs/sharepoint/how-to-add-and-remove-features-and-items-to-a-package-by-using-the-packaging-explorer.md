---
title: '패키징 탐색기: 패키지에 항목 & 기능을 추가 & 제거 합니다.'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9bc4546d598a2fcca822f1921f778034fb768c2b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585591"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>방법: 패키징 탐색기를 사용 하 여 패키지에 기능과 항목 추가 및 제거
  SharePoint 항목 및 기능을 배포 하도록 패키지를 구성 하려면 패키징 탐색기를 사용할 수 있습니다. .Wsp 파일 내에서 SharePoint 프로젝트 항목 및 기능을 조정할 수 있습니다.

 또는 패키징 디자이너를 사용 하 여 기능을 확인 하 고 다시 정렬 하 여 활성화 순서를 변경할 수 있습니다. 자세한 내용은 [방법: 패키지 디자이너를 사용 하 여 패키지에 기능 및 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)를 참조 하세요.

## <a name="open-the-packaging-explorer"></a>패키징 탐색기 열기
 Visual Studio 솔루션에 SharePoint 프로젝트가 하나 이상 있는 경우 다음 절차를 사용 하 여 패키징 탐색기를 열 수 있습니다. 또는 기능 또는 패키지 디자이너를 볼 때 패키징 탐색기가 자동으로 열립니다. 모든 기능 및 패키지 디자이너를 닫은 후에는 패키징 탐색기도 닫힙니다.

#### <a name="to-open-the-packaging-explorer"></a>패키징 탐색기를 열려면

1. 메뉴 모음에서 **보기**  >  **다른 Windows**  >  **패키징 탐색기**를 선택 합니다.

     **패키징 탐색기** 가 **도구 상자**에 나타납니다.

## <a name="adding-a-feature-to-a-package"></a>패키지에 기능 추가
 패키징 탐색기를 사용 하 여 패키지에 새 기능 및 기존 기능을 추가할 수 있습니다.

#### <a name="to-add-a-sharepoint-feature"></a>SharePoint 기능을 추가 하려면

1. **패키징 탐색기**를 열고 프로젝트에 대 한 바로 가기 메뉴를 연 다음 **기능 추가**를 선택 합니다.

#### <a name="to-move-an-existing-sharepoint-feature"></a>기존 SharePoint 기능을 이동 하려면

1. **패키징 탐색기**를 열고 다음 단계 중 하나를 수행 합니다.

    - 한 프로젝트에서 다른 프로젝트로 **기능** 을 끌어 옵니다.

    - 기능에 대 한 바로 가기 메뉴를 열고, **잘라내기**를 선택 하 고, 기능을 이동 하려는 프로젝트의 바로 가기 메뉴를 연 다음 **붙여넣기**를 선택 합니다.

    > [!NOTE]
    > 솔루션에 SharePoint 프로젝트가 두 개 이상 있는 경우 이 절차를 사용합니다.

## <a name="validate-a-feature-or-package"></a>기능 또는 패키지의 유효성 검사
 파일의 유효성을 검사 하 여 SharePoint 기능 및 패키지의 잠재적 문제를 식별할 수 있습니다. 경고 및 오류는 출력 창 및 오류 목록 창에 표시 됩니다.

#### <a name="to-validate-a-sharepoint-feature-or-package"></a>SharePoint 기능 또는 패키지의 유효성을 검사 하려면

1. **패키징 탐색기**를 엽니다.

2. 기능 또는 패키지에 대 한 바로 가기 메뉴를 열고 **유효성 검사**를 선택 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 패키지 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
