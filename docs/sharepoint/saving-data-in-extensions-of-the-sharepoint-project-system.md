---
title: SharePoint 프로젝트 시스템의 확장에 데이터 저장 | Microsoft Docs
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 30142b9aaec3df7ce0d43845e369eb538533de62
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583868"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>SharePoint 프로젝트 시스템의 확장에 데이터 저장
  SharePoint 프로젝트 시스템을 확장 하는 경우 SharePoint 프로젝트를 닫은 후에도 유지 되는 문자열 데이터를 저장할 수 있습니다. 일반적으로 데이터는 특정 프로젝트 항목 또는 프로젝트 자체와 연결 됩니다.

 유지할 필요가 없는 데이터가 있는 경우 해당 인터페이스를 구현 하는 SharePoint tools 개체 모델의 모든 개체에 데이터를 추가할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> . 자세한 내용은 [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)을 참조 하세요.

## <a name="save-data-that-is-associated-with-a-project-item"></a>프로젝트 항목과 연결 된 데이터 저장
 특정 SharePoint 프로젝트 항목과 연결 된 데이터 (예: 프로젝트 항목에 추가 하는 속성의 값)가 있는 경우 프로젝트 항목의 *.spdata* 파일에 데이터를 저장할 수 있습니다. 이렇게 하려면 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 개체의 속성을 사용 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> 합니다. 이 속성에 추가 하는 데이터는 프로젝트 항목에 대 한 *.spdata* 파일의 **extensiondata** 요소에 저장 됩니다. 자세한 내용은 [Extensiondata 요소](../sharepoint/extensiondata-element.md)를 참조 하세요.

 다음 코드 예제에서는 속성을 사용 하 여 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 사용자 지정 SharePoint 프로젝트 항목 형식에 정의 된 문자열 속성의 값을 저장 하는 방법을 보여 줍니다. 큰 예제의 컨텍스트에서이 예제를 보려면 [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)를 참조 하세요.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>프로젝트에 연결 된 데이터 저장
 SharePoint 프로젝트에 추가 하는 속성의 값과 같은 프로젝트 수준 데이터가 있는 경우 프로젝트 파일 ( *.csproj* 파일 또는 *.vbproj* 파일) 또는 프로젝트 사용자 옵션 파일 ( *.csproj. user* 파일 또는 *.vbproj* 파일)에 데이터를 저장할 수 있습니다. 데이터를 저장 하도록 선택 하는 파일은 데이터를 사용 하는 방법에 따라 달라 집니다.

- SharePoint 프로젝트를 여는 모든 개발자가 데이터를 사용할 수 있게 하려면 데이터를 프로젝트 파일에 저장 합니다. 이 파일은 항상 소스 제어 데이터베이스에 체크 인 되므로 프로젝트를 체크 아웃 하는 다른 개발자가이 파일의 데이터를 사용할 수 있습니다.

- Visual Studio에서 SharePoint 프로젝트를 연 현재 개발자만 데이터를 사용할 수 있도록 하려면 프로젝트 사용자 옵션 파일에 데이터를 저장 합니다. 이 파일은 일반적으로 소스 제어 데이터베이스에 체크 인 되지 않으므로 프로젝트를 체크 아웃 하는 다른 개발자가이 파일의 데이터를 사용할 수 없습니다.

### <a name="save-data-to-the-project-file"></a>프로젝트 파일에 데이터 저장
 프로젝트 파일에 데이터를 저장 하려면 개체를 개체로 변환 하 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 고 메서드를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 합니다. 다음 코드 예제에서는이 메서드를 사용 하 여 프로젝트 속성의 값을 프로젝트 파일에 저장 하는 방법을 보여 줍니다. 큰 샘플의 컨텍스트에서이 예제를 보려면 [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)를 참조 하세요.

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>Visual Studio 자동화 개체 모델 또는 통합 개체 모델에서 개체를 다른 형식으로 변환 하는 방법에 대 한 자세한 내용은 [SharePoint 프로젝트 시스템 형식과 기타 Visual studio 프로젝트 형식 간의 변환](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)을 참조 하세요.

### <a name="save-data-to-the-project-user-option-file"></a>프로젝트 사용자 옵션 파일에 데이터 저장
 프로젝트 사용자 옵션 파일에 데이터를 저장 하려면 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> 개체의 속성을 사용 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 합니다. 다음 코드 예제에서는이 속성을 사용 하 여 프로젝트 속성의 값을 프로젝트 사용자 옵션 파일에 저장 하는 방법을 보여 줍니다. 큰 샘플의 컨텍스트에서이 예제를 보려면 [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)를 참조 하세요.

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>참고 항목
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
- [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 변환](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
