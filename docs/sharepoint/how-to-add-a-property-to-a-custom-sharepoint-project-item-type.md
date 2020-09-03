---
title: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 54765b9b6b82214a7deccaee4f9ee671a72dd40d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015996"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 속성 추가
  사용자 지정 SharePoint 프로젝트 항목 형식을 정의 하는 경우 프로젝트 항목에 속성을 추가할 수 있습니다. 속성은 **솔루션 탐색기**에서 프로젝트 항목을 선택 하면 **속성** 창에 표시 됩니다.

 다음 단계에서는 사용자가 SharePoint 프로젝트 항목 형식을 이미 정의 했다고 가정 합니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)를 참조 하세요.

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>프로젝트 항목 형식의 정의에 속성을 추가 하려면

1. 사용자 지정 프로젝트 항목 형식에 추가 하는 속성을 나타내는 공용 속성을 사용 하 여 클래스를 정의 합니다. 사용자 지정 프로젝트 항목 형식에 여러 속성을 추가 하려면 동일한 클래스 또는 다른 클래스의 모든 속성을 정의 하면 됩니다.

2. <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 구현 메서드에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> *projectItemTypeDefinition* 매개 변수의 이벤트를 처리 합니다.

3. 이벤트에 대 한 이벤트 처리기에서 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 사용자 지정 속성 클래스의 인스턴스를 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> 이벤트 인수 매개 변수의 컬렉션에 추가 합니다.

## <a name="example"></a>예
 다음 코드 예제에서는 **예제 속성** 이라는 속성을 사용자 지정 프로젝트 항목 형식에 추가 하는 방법을 보여 줍니다.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]

### <a name="understand-the-code"></a>코드 이해
 이벤트가 발생할 때마다 클래스의 동일한 인스턴스를 사용 하도록 하기 위해 `CustomProperties` <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> 코드 예제에서는 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> 이 이벤트가 처음 발생할 때 프로젝트 항목의 속성에 속성 개체를 저장 합니다. 이 이벤트가 다시 발생 하면 코드에서이 개체를 검색 합니다. 속성을 사용 하 여 프로젝트 항목과 함께 데이터를 저장 하는 방법에 대 한 자세한 내용은 <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)을 참조 하세요.

 속성 값에 대 한 변경 내용을 유지 하기 위해의 **set** 접근자는 `ExampleProperty` <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> 속성이 연결 된 개체의 속성에 새 값을 저장 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> . 속성을 사용 하 여 프로젝트 항목의 데이터를 유지 하는 방법에 대 한 자세한 내용은 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> [SharePoint 프로젝트 시스템의 확장에 데이터 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)을 참조 하세요.

### <a name="specify-the-behavior-of-custom-properties"></a>사용자 지정 속성의 동작 지정
 네임 스페이스의 특성 **Properties** <xref:System.ComponentModel> 을 속성 정의에 적용 하 여 사용자 지정 속성이 표시 되 고 속성 창에서 동작 하는 방식을 정의할 수 있습니다. 다음 특성은 많은 시나리오에서 유용 합니다.

- <xref:System.ComponentModel.DisplayNameAttribute>: **속성** 창에 표시 되는 속성의 이름을 지정 합니다.

- <xref:System.ComponentModel.DescriptionAttribute>: 속성을 선택 하는 경우 **속성** 창의 맨 아래에 표시 되는 설명 문자열을 지정 합니다.

- <xref:System.ComponentModel.DefaultValueAttribute>: 속성의 기본값을 지정 합니다.

- <xref:System.ComponentModel.TypeConverterAttribute>: **속성** 창에 표시 되는 문자열과 문자열이 아닌 속성 값 사이에 사용자 지정 변환을 지정 합니다.

- <xref:System.ComponentModel.EditorAttribute>: 속성을 수정 하는 데 사용할 사용자 지정 편집기를 지정 합니다.

## <a name="compile-the-code"></a>코드 컴파일
 이러한 코드 예제에는 다음 어셈블리에 대 한 참조가 포함 된 클래스 라이브러리 프로젝트가 필요 합니다.

- VisualStudio

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>프로젝트 항목 배포
 다른 개발자가 프로젝트 항목을 사용할 수 있도록 하려면 프로젝트 템플릿 또는 프로젝트 항목 템플릿을 만듭니다. 자세한 내용은 [SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)를 참조 하세요.

 프로젝트 항목을 배포 하려면 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리, 템플릿 및 프로젝트 항목과 함께 배포할 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [방법: 사용자 지정 SharePoint 프로젝트 항목 형식에 바로 가기 메뉴 항목 추가](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
