---
title: 모듈을 사용하여 솔루션에 파일 포함 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015813"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>모듈을 사용하여 솔루션에 파일 포함
  파일 형식(예: 새 마스터 페이지)과 관계없이 SharePoint Server에 파일을 배포해야 하는 경우도 있습니다. 이렇게 하려면 ‘모듈’([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 코드 모듈 아님)을 사용할 수 있습니다. 모듈은 SharePoint 솔루션 내 파일의 컨테이너입니다. 솔루션을 배포하면 모듈의 파일이 SharePoint Server의 지정한 폴더에 복사됩니다.

## <a name="module-items-and-elements"></a>모듈 항목 및 요소
 모듈을 만들려면 **새 항목 추가** 대화 상자에서 모듈을 선택하여 프로젝트에 추가합니다. 그런 다음, 배포할 파일 이름, 시스템에서 현재 파일 위치, SharePoint Server에서 파일을 복사할 위치가 포함되도록 *Elements.xml* 파일을 수정합니다.

 다음은 모듈의 *Elements.xml* 파일 예입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 새로 만든 모듈에는 다음과 같은 기본 파일이 포함되어 있습니다.

|파일 이름|설명|
|---------------|-----------------|
|*Elements.xml*|모듈의 정의 파일입니다.|
|*Sample.txt*|모듈의 파일 예로 사용되는 자리 표시자 파일입니다.|

 *Elements.xml* 파일에는 다음 요소가 포함되어 있습니다.

|요소 이름|설명|
|------------------|-----------------|
|요소|모듈에 정의된 모든 요소를 포함합니다.|
|모듈|Module 요소에는 `<Module Name="Module1">` 형식으로 모듈 이름을 지정하는 단일 특성 *Name*이 있습니다.<br /><br /> 모듈 이름(또는 해당 ‘폴더 이름’ 속성)을 변경하는 경우 Module 요소의 이름을 수동으로 업데이트해야 합니다.<br /><br /> Module 요소에 파일의 하위 디렉터리를 지정하면 WSS([!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)])에서 일치하는 디렉터리 구조를 자동으로 만듭니다.|
|파일|File 요소에는 두 가지 매개 변수(*Path* 및 *Url*)가 있습니다.<br /><br /> - Path: SharePoint 솔루션 파일의 이름 및 위치입니다. 형식은 `Path="Module1\Sample.txt"`입니다.<br /><br /> - Url: SharePoint Server에서 파일이 배포되는 위치입니다. 형식은 `Url="Module1/Sample.txt"`입니다.<br /><br /> - Type: 두 가지 설정(*GhostableInLibrary* 및 *Ghostable*)이 있는 선택적 특성입니다. 형식은 `Type="GhostableInLibrary"`입니다. *GhostableInLibrary*를 지정하면 라이브러리에 파일을 추가할 때 파일에 수반되는 목록 항목과 함께 파일이 SharePoint의 문서 라이브러리에 추가됩니다. *Ghostable*을 지정하면 파일이 SharePoint의 문서 라이브러리 외부에 추가됩니다.|

 배포하려는 각 파일에 해당하는 `<File>` 요소 항목이 *Elements.xml*에 있어야 합니다.

## <a name="see-also"></a>추가 정보
- [방법: 모듈을 사용하여 파일 포함](../sharepoint/how-to-include-files-by-using-a-module.md)
- [방법: 파일 프로비저닝](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)
- [SharePoint 솔루션 패키지 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
