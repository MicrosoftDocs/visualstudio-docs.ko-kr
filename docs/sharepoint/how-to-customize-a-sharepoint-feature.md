---
title: '방법: SharePoint 기능 사용자 지정 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
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
ms.openlocfilehash: a330f3c4cbe1e410ddc6a1612796c92eeda281b8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016893"
---
# <a name="how-to-customize-a-sharepoint-feature"></a>방법: SharePoint 기능 사용자 지정
  Visual Studio의 기능 디자이너를 사용 하 여 SharePoint 기능을 만들고 사용자 지정할 수 있습니다. 예를 들어 기능 범위를 설정 하 고 다른 기능을 종속성으로 추가할 수 있습니다. 기본적으로 솔루션 탐색기 또는 SharePoint 패키지 탐색기에서 새 기능을 추가 하면 기능 디자이너가 열립니다.

## <a name="opening-the-feature-designer"></a>기능 디자이너 열기
 기능 디자이너를 사용 하 여 기능에 SharePoint 프로젝트 항목을 추가 하거나 제거할 수 있습니다.

#### <a name="to-open-the-feature-designer"></a>기능 디자이너를 열려면

1. **솔루션 탐색기**에서 **기능**을 확장 합니다.

2. *Feature1* 항목을 두 번 클릭 하거나 *Feature1* 항목에 대 한 바로 가기 메뉴를 연 다음 **뷰 디자이너**를 선택 합니다.

## <a name="view-the-packaged-manifest-file"></a>패키지 된 매니페스트 파일 보기
 기능 디자이너를 사용 하 여 기능에 대 한 패키지 된 매니페스트 파일 (*feature.xml*)을 수정 하 고 생성할 수 있습니다. 그런 다음 Visual Studio에서이 파일에 대 한 XML 코드를 볼 수 있습니다.

#### <a name="to-view-the-packaged-manifest-file"></a>패키지 된 매니페스트 파일을 보려면

1. **기능 디자이너**에서 **매니페스트** 탭을 선택 합니다.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>솔루션 탐색기를 사용 하 여 패키지 된 매니페스트 파일을 보려면

1. **솔루션 탐색기**에서 **모든 파일 표시** 아이콘을 선택 합니다.

2. 기능, FeatureName, FeatureName를 차례로 확장 한 다음 * \<FeatureName>.Template.xml* 파일을 엽니다.

    > [!NOTE]
    > 기능 템플릿 매니페스트 XML 파일을 열면 파일의 유효성이 자동으로 검사 되 고 오류 목록 창에 표시 되는 경고는 무시 될 수 있습니다.

## <a name="change-the-manifest-template"></a>매니페스트 템플릿 변경
 Visual Studio XML 편집기나 매니페스트 템플릿 창에서 기능 매니페스트 파일의 XML 코드를 변경할 수 있습니다. XML 코드에 대 한 모든 변경 내용은 해당 기능에 대 한 패키지 된 매니페스트 파일에 병합 됩니다. 예를 들어 기능 속성을 사용자 지정 하기 위해 매니페스트 템플릿을 변경할 수 있습니다.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML 편집기를 사용 하 여 매니페스트 템플릿을 변경 하려면

1. **기능 디자이너**에서 **매니페스트** 탭을 선택 하 고 **편집 옵션** 노드를 확장 한 다음 **XML 편집기에서 열기** 링크를 선택 합니다.

     XML에 대 한 변경 내용은 패키지 된 매니페스트 파일로 병합 됩니다.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>매니페스트 템플릿 창을 사용 하 여 매니페스트 템플릿을 변경 하려면

1. **기능 디자이너**에서 **매니페스트** 탭을 선택 하 고 **편집 옵션** 노드를 확장 한 다음 매니페스트 템플릿 창에 표시 되는 XML을 변경 합니다.

     XML에 대 한 변경 내용은 **패키지 된 매니페스트 창 미리 보기** 에 나타납니다.

## <a name="overwrite-the-packaged-manifest-file"></a>패키지 된 매니페스트 파일 덮어쓰기
 기능 디자이너를 사용 하지 않도록 설정 하 고 *feature.xml* 파일을 수동으로 만들 수 있습니다. 이 절차를 처음 수행 하면 기능 디자이너의 현재 설정이 기능 템플릿 XML 파일에 저장 됩니다. 그런 다음 XML 코드를 수정 하거나 덮어쓸 수 있습니다.

> [!NOTE]
> 기능 디자이너를 사용 하지 않도록 설정 하는 동안 XML 파일에서 SharePoint 프로젝트 항목을 추가 하거나 제거 하는 경우 이러한 프로젝트 항목은 패키지 되지 않습니다.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>디자이너를 사용 하지 않도록 설정 하 여 패키지 된 매니페스트 파일을 덮어쓰려면

1. **기능 디자이너**에서 **매니페스트** 탭을 선택 합니다.

2. **편집 옵션** 노드를 확장 하 고 **xml 편집기에서 생성 된 xml 덮어쓰기 및 매니페스트 편집** 링크를 선택한 다음 **예** 단추를 선택 합니다.

     템플릿이 현재 패키지 된 매니페스트 파일로 업데이트 됩니다.

## <a name="enable-the-feature-designer"></a>기능 디자이너 사용
 기능 디자이너를 다시 사용 하도록 설정 하 여 *feature.xml* 파일을 사용자 지정할 수 있습니다.

#### <a name="to-re-enable-the-designer"></a>디자이너를 다시 사용 하도록 설정 하려면

1. **기능 디자이너**에서 **매니페스트 편집 취소를 선택 하 고 디자이너를 다시 사용 하도록 설정한** 후 **예** 단추를 선택 합니다.

2. 원래 텍스트를 사용 하 여 템플릿을 새로 고치면 XML의 모든 변경 내용이 손실 됩니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
