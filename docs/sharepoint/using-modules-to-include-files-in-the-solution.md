---
title: 모듈을 사용 하 여 솔루션에 파일 포함 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 778bbc9cff2d7853628edbb5be6466acc55d9ab8
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015813"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>모듈을 사용 하 여 솔루션에 파일 포함
  파일 형식 (예: 새 마스터 페이지)에 관계 없이 파일을 SharePoint 서버에 배포 해야 하는 경우가 있을 수 있습니다. 이렇게 하려면 *모듈* 을 사용할 수 있습니다 (코드 모듈과 혼동 하지 않음 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ). 모듈은 SharePoint 솔루션의 파일에 대 한 컨테이너입니다. 솔루션이 배포 되 면 모듈의 파일이 SharePoint 서버의 지정 된 폴더에 복사 됩니다.

## <a name="module-items-and-elements"></a>모듈 항목 및 요소
 모듈을 만들려면 **새 항목 추가** 대화 상자에서 모듈을 선택 하 여 프로젝트에 추가 합니다. 그런 다음 배포 하려는 파일의 이름을 포함 하도록 *Elements.xml* 파일을 수정 합니다 .이 파일은 시스템에 위치 하 고 SharePoint 서버에서 복사 해야 하는 위치를 포함 합니다.

 모듈에 대 한 *Elements.xml* 파일의 예는 다음과 같습니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 새로 만든 모듈에는 다음과 같은 기본 파일이 포함 되어 있습니다.

|파일 이름|Description|
|---------------|-----------------|
|*Elements.xml*|모듈에 대 한 정의 파일입니다.|
|*Sample.txt*|모듈에서 파일의 예로 사용 되는 자리 표시자 파일입니다.|

 *Elements.xml* 파일에는 다음 요소가 포함 되어 있습니다.

|요소 이름|Description|
|------------------|-----------------|
|요소|모듈에 정의 된 모든 요소를 포함 합니다.|
|모듈|Module 요소에는 형식의 모듈 이름을 지정 하는 단일 특성인 *name*이 있습니다 `<Module Name="Module1">` .<br /><br /> 모듈의 이름 (또는 해당 *폴더 이름* 속성)을 변경 하는 경우 module 요소에서 이름을 수동으로 업데이트 해야 합니다.<br /><br /> Module 요소에 파일에 대 한 하위 디렉터리를 지정 하는 경우 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] WSS ()에서 일치 하는 디렉터리 구조를 자동으로 만듭니다.|
|파일|File 요소에는 *경로* 와 *Url*의 두 매개 변수가 있습니다.<br /><br /> -Path: SharePoint 솔루션에 있는 파일의 이름 및 위치입니다. 형식은, `Path="Module1\Sample.txt"` 입니다.<br /><br /> -Url: SharePoint 서버에서 파일이 배포 되는 위치입니다. 형식은, `Url="Module1/Sample.txt"` 입니다.<br /><br /> -Type: 두 가지 설정 ( *GhostableInLibrary* 및 *ghostable*수도 있음)을 포함 하는 선택적 특성입니다. 형식은, `Type="GhostableInLibrary"` 입니다. *GhostableInLibrary* 를 지정 하면 파일이 라이브러리에 추가 될 때 파일을 첨부할 목록 항목과 함께 SharePoint의 문서 라이브러리에 파일이 추가 됩니다. *Ghostable* 을 지정 하면 파일이 문서 라이브러리 외부의 SharePoint에 추가 됩니다.|

 배포 하려는 각 파일에는Elements.xml별도의 `<File>` 요소 항목이 필요 합니다 * *.

## <a name="see-also"></a>참고 항목
- [방법: 모듈을 사용 하 여 파일 포함](../sharepoint/how-to-include-files-by-using-a-module.md)
- [방법: 파일 프로 비전](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
