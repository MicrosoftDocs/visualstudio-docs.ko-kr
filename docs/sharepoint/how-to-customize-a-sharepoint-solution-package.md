---
title: '방법: SharePoint 솔루션 패키지 사용자 지정 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
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
ms.openlocfilehash: 77b66160d489f711b5588fdcdd024d13769d734f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016870"
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>방법: SharePoint 솔루션 패키지 사용자 지정
  패키지 디자이너를 사용 하 여 패키지 (*.wsp*)를 만들고 사용자 지정할 수 있습니다. 예를 들어 SharePoint 프로젝트 항목 및 기능을 추가 하 고, 솔루션이 배포 될 때 웹 서버가 다시 설정 되는지 여부를 지정 하 고, 배포 서버 유형을 설정할 수 있습니다.

## <a name="open-the-package-designer"></a>패키지 디자이너 열기

#### <a name="to-open-the-package-designer"></a>패키지 디자이너를 열려면

- **솔루션 탐색기**에서 **패키지**를 두 번 클릭 하거나 **패키지**의 바로 가기 메뉴에서 **뷰 디자이너** 를 선택 합니다.

## <a name="view-the-packaged-manifestffile"></a>패키지 된 manifestfFile 보기
 패키지 디자이너를 사용 하 여 패키지 된 매니페스트 파일을 수정 하 고 생성할 수 있습니다. 그런 다음 Visual Studio에서이 파일에 대 한 XML 코드를 볼 수 있습니다.

#### <a name="to-view-the-xml-source-file"></a>XML 원본 파일을 보려면

1. **패키지 디자이너**에서 **매니페스트**를 선택 합니다.

#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>솔루션 탐색기를 사용 하 여 패키지 된 매니페스트 파일을 보려면

1. **솔루션 탐색기**에서 **모든 파일 표시**를 선택합니다.

2. 패키지를 확장 하 고 패키지를 확장 한 다음 *Package.Template.xml* 파일을 엽니다.

    > [!NOTE]
    > 패키지 템플릿에 대 한 매니페스트 XML 파일을 열면 파일의 유효성이 자동으로 검사 되 고 오류 목록 창에 표시 되는 경고는 무시 해도 됩니다.

## <a name="change-the-manifest-template"></a>매니페스트 템플릿 변경
 Visual Studio XML 편집기나 매니페스트 템플릿 창에서 패키지 된 매니페스트 파일의 XML 코드를 변경할 수 있습니다. XML 코드에 대 한 모든 변경 내용은 패키지의 패키지 된 매니페스트 파일에 병합 됩니다.

#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>XML 편집기를 사용 하 여 매니페스트 템플릿을 변경 하려면

1. **패키지 디자이너**에서 **매니페스트** 탭을 선택 하 고 **편집 옵션** 노드를 확장 한 다음 **XML 편집기에서 열기** 링크를 선택 합니다.

     XML에 대 한 변경 내용은 패키지 된 매니페스트 파일로 병합 됩니다.

#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>매니페스트 템플릿 창을 사용 하 여 매니페스트 템플릿을 변경 하려면

1. **패키지 디자이너**에서 **매니페스트** 탭을 선택 하 고 **편집 옵션** 노드를 확장 한 다음 매니페스트 템플릿 창에 표시 되는 XML을 변경 합니다.

     XML에 대 한 변경 내용은 **패키지 된 매니페스트 창 미리 보기** 에 나타납니다.

## <a name="overwrite-the-packaged-manifest-file"></a>패키지 된 매니페스트 파일 덮어쓰기
 패키지 디자이너를 사용 하지 않도록 설정 하 고 *manifest.xml* 파일을 수동으로 만들 수 있습니다. 이 절차를 처음 수행 하면 패키지 디자이너의 현재 설정이 패키지 템플릿 XML 파일에 저장 됩니다. 그런 다음 XML 코드를 수정 하거나 덮어쓸 수 있습니다.

> [!NOTE]
> 패키지 디자이너를 사용 하지 않도록 설정 하는 동안 XML 파일에서 SharePoint 프로젝트 항목과 기능을 추가 하거나 제거 하는 경우 이러한 프로젝트 항목과 기능은 패키지 되지 않습니다.

#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>디자이너를 사용 하지 않도록 설정 하 여 패키지 된 매니페스트 파일을 덮어쓰려면

1. **패키지 디자이너**에서 **매니페스트** 탭을 선택 합니다.

2. **편집 옵션** 노드를 확장 하 고 **xml 편집기에서 생성 된 xml 덮어쓰기 및 매니페스트 편집** 링크를 선택한 다음 **예** 단추를 선택 합니다.

     템플릿이 현재 패키지 된 매니페스트 파일로 업데이트 됩니다.

## <a name="enable-the-package-designer"></a>패키지 디자이너 사용
 패키지 디자이너를 다시 사용 하도록 설정 하 여 *manifest.xml* 파일을 사용자 지정할 수 있습니다.

#### <a name="to-re-enable-the-designer"></a>디자이너를 다시 사용 하도록 설정 하려면

1. **패키지 디자이너**에서 **매니페스트 편집 취소를 선택 하 고 디자이너를 다시 사용 하도록 설정한** 후 **예** 단추를 선택 합니다.

     원래 텍스트를 사용 하 여 템플릿을 새로 고치면 XML의 모든 변경 내용이 손실 됩니다.

## <a name="see-also"></a>추가 정보
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
