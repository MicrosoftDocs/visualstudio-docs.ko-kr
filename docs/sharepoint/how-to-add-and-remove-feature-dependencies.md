---
title: '방법: 기능 종속성 추가 및 제거 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c318a7dc4672a10e993d0149ec77e7f94679d465
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014775"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>방법: 기능 종속성 추가 및 제거
  SharePoint 기능은 기능이 나 데이터의 다른 기능에 따라 달라질 수 있습니다. 이러한 경우에는 기능에 대 한 종속성으로 이러한 다른 기능을 표시할 수 있습니다. 이러한 방식으로 SharePoint 서버는 기능이 활성화 되기 전에 종속 기능이 활성화 되도록 합니다.

## <a name="add-dependencies"></a>종속성 추가
 솔루션의 다른 기능을 종속성으로 추가할 수 있습니다. 이렇게 하면 기능을 설치 하기 전에 필수 기능이 설치 되 고 활성화 되도록 할 수 있습니다.

#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>솔루션의 기능에 대 한 종속성을 추가 하려면

1. 기능 디자이너를 열고 **기능 활성화 종속성** 노드를 확장 한 다음 **추가** 단추를 선택 합니다.

2. **기능 활성화 종속성 추가** 대화 상자에서 **솔루션의 기능에 대 한 종속성 추가** 옵션 단추를 선택 하 고 종속성으로 추가할 기능의 제목을 선택한 다음 **추가** 단추를 선택 합니다.

     **Ctrl** 키를 선택 하는 동안 여러 제목을 선택 하 여 둘 이상의 기능을 추가할 수 있습니다.

## <a name="addi-custom-dependencies"></a>Addi 사용자 지정 종속성
 SharePoint 서버에 이미 배포 된 기능을 종속성으로 추가할 수 있습니다. 이러한 방식으로 SharePoint 활성화 프로세스는 기능을 설치 하기 전에 모든 종속 기능이 활성화 되는지 확인 합니다.

#### <a name="to-add-a-dependency-by-the-feature-id"></a>기능 ID를 기준으로 종속성을 추가 하려면

1. 기능 디자이너를 열고 **기능 활성화 종속성** 노드를 확장 한 다음 **추가** 단추를 선택 합니다.

2. **기능 활성화 종속성 추가** 대화 상자에서 **사용자 지정 종속성 추가** 옵션 단추를 선택 합니다.

3. **기능 ID** 텍스트 상자에 활성화 종속성으로 표시 하려는 기능의 GUID를 입력 한 다음 **추가** 단추를 선택 합니다.

## <a name="edit-custom-dependencies"></a>사용자 지정 종속성 편집
 이전에 추가한 사용자 지정 종속성을 편집할 수 있습니다. 그러나 솔루션에 있는 종속 기능은 제거할 수만 있고 편집할 수는 없습니다.

#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>솔루션의 기능에 대 한 종속성을 변경 하려면

1. 기능 디자이너를 열고 **기능 활성화 종속성** 노드를 확장 합니다.

2. 편집 하려는 기능의 이름을 선택 하 고 **편집** 단추를 선택 합니다.

3. **사용자 지정 기능 활성화 종속성 편집** 대화 상자에서 제목, 기능 ID 또는 설명을 변경한 후 **제출** 단추를 선택 합니다.

## <a name="remove-dependencies"></a>종속성 제거

#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>솔루션의 기능에 대 한 종속성을 제거 하려면

1. 기능 디자이너에서 **기능 활성화 종속성** 노드를 확장 하 고 제거할 기능의 이름을 선택한 다음 **제거** 단추를 선택 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 기능 만들기](../sharepoint/creating-sharepoint-features.md)
- [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [방법: SharePoint 기능에 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
