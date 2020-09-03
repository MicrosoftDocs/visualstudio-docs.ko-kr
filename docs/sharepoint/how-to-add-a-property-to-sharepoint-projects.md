---
title: '방법: SharePoint 프로젝트에 속성 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb72b0546b504e2df1a7e93ea9d4def350143d1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015917"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>방법: SharePoint 프로젝트에 속성 추가
  프로젝트 확장을 사용 하 여 SharePoint 프로젝트에 속성을 추가할 수 있습니다. 속성은 **솔루션 탐색기**에서 프로젝트를 선택 하면 **속성** 창에 표시 됩니다.

 다음 단계에서는 프로젝트 확장을 이미 만들었다고 가정 합니다. 자세한 내용은 [방법: SharePoint 프로젝트 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)를 참조 하세요.

### <a name="to-add-a-property-to-a-sharepoint-project"></a>SharePoint 프로젝트에 속성을 추가 하려면

1. SharePoint 프로젝트에 추가 하는 속성을 나타내는 공용 속성을 사용 하 여 클래스를 정의 합니다. 여러 속성을 추가 하려면 동일한 클래스 또는 다른 클래스의 모든 속성을 정의 하면 됩니다.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 구현 메서드에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> *projectservice* 매개 변수의 이벤트를 처리 합니다.

3. 이벤트에 대 한 이벤트 처리기에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 속성 클래스의 인스턴스를 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> 이벤트 인수 매개 변수의 컬렉션에 추가 합니다.

## <a name="example"></a>예
 다음 코드 예제에서는 두 개의 속성을 SharePoint 프로젝트에 추가 하는 방법을 보여 줍니다. 한 속성은 프로젝트 사용자 옵션 파일 ( *.csproj. user* 파일 또는 *.vbproj* 파일)에서 해당 데이터를 유지 합니다. 다른 속성은 프로젝트 파일 (*.csproj* 파일 또는 *.vbproj* 파일)에 데이터를 유지 합니다.

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>코드 이해
 이벤트가 발생할 때마다 클래스의 동일한 인스턴스를 사용 하도록 하기 위해 `CustomProjectProperties` <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> 코드 예제에서는 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 이 이벤트가 처음 발생할 때 프로젝트의 속성에 속성 개체를 추가 합니다. 이 이벤트가 다시 발생 하면 코드에서이 개체를 검색 합니다. 속성을 사용 하 여 데이터를 프로젝트와 연결 하는 방법에 대 한 자세한 내용은 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)을 참조 하세요.

 속성 값에 대 한 변경 내용을 유지 하기 위해 속성의 **set** 접근자에는 다음 api가 사용 됩니다.

- `CustomUserFileProperty` 속성을 사용 하 여 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> 프로젝트 사용자 옵션 파일에 해당 값을 저장 합니다.

- `CustomProjectFileProperty` 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 해당 값을 프로젝트 파일에 저장 합니다.

  이러한 파일에 데이터를 유지 하는 방법에 대 한 자세한 내용은 [SharePoint 프로젝트 시스템의 확장에 데이터 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)을 참조 하세요.

### <a name="specify-the-behavior-of-custom-properties"></a>사용자 지정 속성의 동작 지정
 네임 스페이스의 특성 **Properties** <xref:System.ComponentModel> 을 속성 정의에 적용 하 여 사용자 지정 속성이 표시 되 고 속성 창에서 동작 하는 방식을 정의할 수 있습니다. 다음 특성은 많은 시나리오에서 유용 합니다.

- <xref:System.ComponentModel.DisplayNameAttribute>: **속성** 창에 표시 되는 속성의 이름을 지정 합니다.

- <xref:System.ComponentModel.DescriptionAttribute>: 속성을 선택 하는 경우 **속성** 창의 맨 아래에 표시 되는 설명 문자열을 지정 합니다.

- <xref:System.ComponentModel.DefaultValueAttribute>: 속성의 기본값을 지정 합니다.

- <xref:System.ComponentModel.TypeConverterAttribute>: **속성** 창에 표시 되는 문자열과 문자열이 아닌 속성 값 사이에 사용자 지정 변환을 지정 합니다.

- <xref:System.ComponentModel.EditorAttribute>: 속성을 수정 하는 데 사용할 사용자 지정 편집기를 지정 합니다.

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요 합니다.

- VisualStudio

- VisualStudio

- VisualStudio.

- VisualStudio입니다.

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 확장을 배포 하려면 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [SharePoint 프로젝트 확장](../sharepoint/extending-sharepoint-projects.md)
- [방법: SharePoint 프로젝트 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [방법: SharePoint 프로젝트에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
