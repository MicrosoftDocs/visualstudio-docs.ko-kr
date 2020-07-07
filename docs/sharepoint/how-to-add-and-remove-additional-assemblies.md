---
title: '방법: 추가 어셈블리 추가 및 제거 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
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
ms.openlocfilehash: 07b9016a4e246d3ed5a2697d924f556517a8226f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014832"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>방법: 추가 어셈블리 추가 및 제거
  SharePoint 패키지가 기능 또는 데이터의 다른 어셈블리에 종속 된 경우 솔루션 패키지 (.wsp)에 어셈블리를 추가할 수 있습니다. 이러한 방식으로 SharePoint 서버는 사용자 지정 어셈블리가 패키지와 함께 설치 되도록 합니다.

 어셈블리와 연결 된 안전 컨트롤 및 클래스 리소스 파일을 추가 하 고 변경할 수도 있습니다.

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>추가 어셈블리, 안전 컨트롤 및 클래스 리소스 추가
 SharePoint 솔루션 패키지에 어셈블리를 더 추가할 수 있습니다. 샌드박스가 적용 된 솔루션의 추가 어셈블리는 전역 어셈블리 캐시에 배포 하지만 샌드박스 솔루션의 SharePoint 프로젝트 항목은 콘텐츠 데이터베이스에 추가 됩니다. 이러한 추가 어셈블리에 안전 컨트롤 및 클래스 리소스를 추가할 수도 있습니다. 안전 컨트롤에 대 한 자세한 내용은 [SharePoint Foundation에서 웹 파트 배포](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))에서 [프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 또는 "SafeControl 항목 만들기"를 참조 하세요.

#### <a name="to-add-an-existing-assembly"></a>기존 어셈블리를 추가 하려면

1. **패키지 디자이너**를 엽니다. 자세한 내용은 [방법: SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)을 참조 하세요.

2. **고급** 탭을 선택 합니다.

3. **추가** 단추를 선택한 다음 목록에서 **기존 어셈블리 추가** 를 선택 합니다.

     **기존 어셈블리 추가** 대화 상자가 나타납니다.

4. 줄임표 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표"))를 선택한 다음 추가 하려는 어셈블리를 선택 합니다. 이식성을 위해 선택한 어셈블리에 대 한 상대 경로를 사용 하는 것이 좋습니다.

5. **배포 대상**의 경우 **globalassemblycache** 옵션 단추를 선택 하 여 어셈블리를 전역 어셈블리 캐시에 배포 하거나 **webapplication** 옵션 단추를 선택 하 여 SharePoint를 실행 하는 서버의 webapplication 폴더에 어셈블리를 배포 합니다.

#### <a name="to-add-an-assembly-from-project-output"></a>프로젝트 출력에서 어셈블리를 추가 하려면

1. **패키지 디자이너**를 엽니다.

     자세한 내용은 [방법: SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)을 참조 하세요.

2. **고급** 탭을 선택 합니다.

3. **추가** 단추를 선택한 다음 목록에서 **프로젝트 출력의 어셈블리 추가** 를 선택 합니다.

     **프로젝트 출력에서 어셈블리 추가** 대화 상자가 나타납니다.

4. **원본 프로젝트** 목록에서 추가 하려는 원본 프로젝트를 선택 합니다.

5. **배포 대상**의 경우 **globalassemblycache** 옵션 단추를 선택 하 여 어셈블리를 전역 어셈블리 캐시에 배포 하거나 **webapplication** 옵션 단추를 선택 하 여 SharePoint를 실행 하는 서버의 webapplication 폴더에 어셈블리를 배포 합니다.

#### <a name="to-add-a-safe-control"></a>안전 컨트롤을 추가 하려면

1. **기존 어셈블리 편집** 대화 상자를 엽니다. 이렇게 하려면 패키지 디자이너를 열고 **고급** 탭을 선택한 다음 어셈블리를 선택 하 고 **편집** 단추를 선택 합니다.

2. **안전 컨트롤** 창에서 **새 항목을 추가 하려면 여기를 클릭** 하십시오. 단추를 선택 합니다.

3. **어셈블리 이름** 열에 어셈블리의 이름을 입력 합니다.

4. **네임 스페이스** 열에 안전 컨트롤에 대 한 네임 스페이스의 이름을 입력 합니다.

5. **유형 이름** 열에 유형의 이름을 입력 합니다.

#### <a name="to-add-a-class-resource"></a>클래스 리소스를 추가 하려면

1. **기존 어셈블리 편집** 대화 상자를 엽니다. 이렇게 하려면 패키지 디자이너를 열고 **고급** 탭을 선택한 다음 어셈블리를 선택 하 고 **편집** 단추를 선택 합니다.

2. **클래스 리소스** 창에서 **새 항목을 추가 하려면 여기를 클릭** 하십시오. 단추를 선택 합니다.

3. **파일 이름** 열에서 줄임표 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표"))를 선택 하 고 추가 하려는 클래스 리소스를 선택 합니다.

## <a name="delete-custom-assemblies"></a>사용자 지정 어셈블리 삭제
 SharePoint 패키지에서 어셈블리를 삭제 하거나 기존 어셈블리에서 안전 컨트롤 및 클래스 리소스를 삭제할 수 있습니다.

#### <a name="to-delete-an-existing-assembly"></a>기존 어셈블리를 삭제 하려면

1. **패키지 디자이너**를 엽니다. 자세한 내용은 [방법: SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)을 참조 하세요.

2. **고급** 탭을 선택 합니다.

3. **추가 어셈블리** 창에서 삭제 하려는 사용자 지정 어셈블리를 선택 합니다.

4. **삭제** 단추를 선택합니다.

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>어셈블리에 대 한 안전 컨트롤을 삭제 하려면

1. **기존 어셈블리 편집** 대화 상자를 엽니다. 이렇게 하려면 패키지 디자이너를 열고 **고급** 탭을 선택한 다음 어셈블리를 선택 하 고 **편집** 단추를 선택 합니다.

2. 삭제 하려는 안전 컨트롤을 선택 합니다.

3. Delete 키를 선택 합니다.

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>어셈블리에 대 한 클래스 리소스를 삭제 하려면

1. **기존 어셈블리 편집** 대화 상자를 엽니다. 이렇게 하려면 패키지 디자이너를 열고 **고급** 탭을 선택한 다음 어셈블리를 선택 하 고 **편집** 단추를 선택 합니다.

2. 삭제할 클래스 리소스를 선택 합니다.

3. Delete 키를 선택 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 기능 만들기](../sharepoint/creating-sharepoint-features.md)
- [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [방법: SharePoint 기능에 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
