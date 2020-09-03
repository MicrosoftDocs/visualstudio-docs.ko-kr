---
title: SharePoint 프로젝트 항목에 대 한 항목 템플릿/프로젝트 템플릿
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 65bbd58bf9b3e0b399603a083615daccc382a98f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72981170"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>SharePoint 프로젝트 항목에 대 한 항목 템플릿 및 프로젝트 템플릿 만들기

사용자 지정 SharePoint 프로젝트 항목 형식을 정의 하는 경우 항목 템플릿이나 프로젝트 템플릿에 연결할 수 있습니다. 이 연결을 통해 다른 개발자가 Visual Studio에서 프로젝트 항목을 사용할 수 있습니다. 템플릿에 대 한 마법사를 만들 수도 있습니다.

예를 들어, Visual Studio에는 SharePoint 사이트에 필드를 추가 하기 위한 프로젝트 템플릿 또는 항목 템플릿이 포함 되어 있지 않습니다. 필드를 나타내는 SharePoint 프로젝트 항목 형식을 정의한 다음 다른 개발자가 SharePoint 프로젝트에 필드 항목을 추가 하는 데 사용할 수 있는 항목 템플릿을 생성할 수 있습니다. 또는 개발자가 필드 항목이 있는 새 SharePoint 프로젝트를 만들 수 있도록 프로젝트 템플릿을 생성할 수 있습니다. 두 경우 모두 개발자가 템플릿을 사용할 때 표시 되는 마법사를 제공할 수도 있습니다. 이 마법사는 개발자가 새 항목 또는 프로젝트를 구성 하는 정보를 수집할 수 있습니다.

항목 템플릿과 프로젝트 템플릿은 Visual Studio에서 프로젝트 항목 또는 프로젝트를 만드는 데 사용 하는 파일이 포함 된 *.zip* 파일입니다. 항목 템플릿 및 프로젝트 템플릿의 기본 사항에 대 한 자세한 내용은 [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)를 참조 하세요.

## <a name="create-item-templates"></a>항목 템플릿 만들기
 SharePoint 프로젝트 항목에 대 한 항목 템플릿을 만들면 항상 필요한 몇 가지 파일과 특정 형식의 프로젝트 항목에서 사용할 수 있는 선택적 파일이 있습니다. SharePoint 프로젝트 항목 형식을 정의 하 고이에 대 한 항목 템플릿을 만드는 방법을 보여 주는 연습은 [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)를 참조 하세요.

 다음 표에서는 SharePoint 프로젝트 항목의 항목 템플릿을 만드는 데 필요한 파일을 보여 줍니다.

|필수 파일|설명|
|-------------------|-----------------|
|*.Spdata* 파일|이 XML 파일은 프로젝트 항목의 내용과 기본 동작을 지정 합니다. 이 파일은 항목 템플릿에 포함 되어야 합니다. *.Spdata* 파일의 내용에 대 한 자세한 내용은 [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)를 참조 하세요.|
|*.Vstemplate* 파일.|이 파일은 **새 항목 추가** 대화 상자에 템플릿을 표시 하 고 템플릿에서 프로젝트 항목을 만드는 데 필요한 정보를 Visual Studio에 제공 합니다. 이 파일은 항목 템플릿에 포함 되어야 합니다. 자세한 내용은 [Visual Studio 템플릿 메타 데이터 파일](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\))을 참조 하세요.|
|인터페이스를 구현 하는 Visual Studio 확장 어셈블리 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 입니다.|이 어셈블리는 프로젝트 항목의 런타임 동작을 정의 합니다. 이 어셈블리는 항목 템플릿을 사용 하 여 VSIX 패키지에 포함 되어야 합니다. 자세한 내용은 [사용자 지정 sharepoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md) 및 [Visual Studio에서 sharepoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.|

 다음 표에서는 항목 템플릿에 포함 될 수 있는 가장 일반적인 선택적 파일 중 일부를 나열 합니다. 일부 유형의 프로젝트 항목에는 여기에 나열 되지 않은 다른 파일이 필요할 수 있습니다.

| 선택적 파일 | 설명 |
|----------------------| - |
| *Elements.xml* | *기능 요소* 파일입니다. 이 파일은 프로젝트 항목에서 만든 사용자 지정의 UI 및 동작을 정의 합니다. 목록 인스턴스, 콘텐츠 형식 또는 사용자 지정 작업과 같은 각 유형의 사용자 지정에는이 파일의 콘텐츠를 정의 하는 다른 스키마가 있습니다. 자세한 내용은 [블록 구성: 기능](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) 및 [기능 스키마](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14))를 참조 하세요. |
| *Schema.xml* | 목록 정의에 대 한 스키마 파일입니다. 자세한 내용은 [구성 요소: 목록 및 문서 라이브러리](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) 및 [Schema.xml](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14))을 참조 하세요. |
| *webpart* | *웹 파트 정의* 파일입니다. 이 파일에는 웹 파트에 대 한 속성 설정이 포함 되어 있습니다. 자세한 내용은 [빌딩 블록: 웹 파트](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14))를 참조 하세요. |
| *.ascx* | ASP.NET UserControl 파일입니다. 이 파일은 비주얼 웹 파트의 UI를 정의 합니다. |
| *.aspx* | ASP.NET 페이지 파일입니다. 이 파일은 응용 프로그램 페이지를 정의 하는 XML 태그를 포함 합니다. |
| *.cs* 또는 *.vb* 파일 | 이러한 코드 파일은 Visual c # 또는 Visual Basic 코드 (예: 응용 프로그램 페이지, 웹 파트, 워크플로)에서 액세스할 수 있는 프로그래밍 모델을 포함 하는 SharePoint 사용자 지정 동작을 정의 합니다. |

## <a name="create-project-templates"></a>프로젝트 템플릿 만들기
 SharePoint 프로젝트 템플릿을 만들 때 항상 필요한 몇 가지 파일과 특정 형식의 프로젝트에서 사용할 수 있는 선택적 파일이 있습니다. 일반적으로 SharePoint 프로젝트는 하나 이상의 SharePoint 프로젝트 항목을 포함 합니다. 그러나 반드시 이렇게 해야 하는 것은 아닙니다. 예를 들어 다른 프로젝트에서 만든 SharePoint 솔루션을 배포 하는 데만 사용 하기 위한 SharePoint 프로젝트 템플릿을 정의할 수 있습니다.

 SharePoint 프로젝트 항목 형식을 정의 하 고이에 대 한 프로젝트 템플릿을 만드는 방법을 보여 주는 연습은 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)를 참조 하세요.

 다음 표에서는 SharePoint 프로젝트 템플릿에 포함 되어야 하는 파일을 나열 합니다.

|필수 파일|설명|
|-------------------|-----------------|
|*.Vstemplate* 파일|이 파일은 **새 프로젝트** 대화 상자에 템플릿을 표시 하 고 템플릿에서 프로젝트를 만드는 데 필요한 정보를 Visual Studio에 제공 합니다. 자세한 내용은 [Visual Studio 템플릿 메타 데이터 파일](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\))을 참조 하세요.|
|*.Csproj* 또는 *.vbproj* 파일|이 파일은 프로젝트 파일입니다. 프로젝트의 내용과 구성 설정을 정의 합니다.|
|*Package. 패키지*|이 파일은 프로젝트에 대 한 배포 패키지를 정의 합니다. 패키지 디자이너를 사용 하 여 프로젝트에 대 한 솔루션 패키지를 사용자 지정 하는 경우 Visual Studio는 솔루션 패키지에 대 한 데이터를이 파일에 저장 합니다.<br /><br /> 사용자 지정 SharePoint 프로젝트 템플릿을 만들 때 *패키지* 파일에 필요한 최소 콘텐츠만 포함 하 고, <xref:Microsoft.VisualStudio.SharePoint.Packages> 프로젝트 템플릿과 연결 된 확장에서 네임 스페이스의 api를 사용 하 여 솔루션 패키지를 구성 하는 것이 좋습니다. 이 작업을 수행 하는 경우 프로젝트 템플릿은 나중에 패키지 파일의 구조에 대 한 변경 내용 으로부터 보호 됩니다 *.* 필요한 최소한의 콘텐츠만 포함 하는 *패키지* 파일을 만드는 방법을 보여 주는 예제는 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부를](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)참조 하세요.<br /><br /> *패키지* 파일을 직접 수정 하려면 *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\PackageModelSchema.xsd*에서 스키마를 사용 하 여 내용을 확인할 수 있습니다.|
|*Package.Template.xml*|이 파일은 프로젝트에서 생성 되는 SharePoint 솔루션 패키지 (*.wsp*)의 솔루션 매니페스트 파일 (*manifest.xml*)에 대 한 기초를 제공 합니다. 프로젝트 형식의 사용자가 변경할 수 없는 동작을 지정 하려면이 파일에 콘텐츠를 추가할 수 있습니다. 자세한 내용은 [구성 요소: 솔루션](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) 및 [솔루션 스키마](/sharepoint/dev/schema/solution-schema)를 참조 하세요.<br /><br /> 프로젝트에서 솔루션 패키지를 빌드하면 Visual Studio *에서 패키지의* 내용과 *Package.Template.xml* 파일을 솔루션 매니페스트 파일에 병합 합니다. 솔루션 패키지 빌드에 대 한 자세한 내용은 [방법: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)를 참조 하세요.|

 다음 표에는 프로젝트 템플릿에 포함 될 수 있는 선택적 파일이 나열 되어 있습니다.

|선택적 파일|설명|
|-------------------|-----------------|
|SharePoint 프로젝트 항목|SharePoint 프로젝트 항목 형식을 정의 하는 하나 이상의 .spdata 파일을 포함할 수 있습니다. 각 *.spdata* 파일 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> 에는 프로젝트 템플릿을 사용 하 여 VSIX 패키지에 포함 된 확장 어셈블리에 일치 하는 구현이 있어야 합니다. 자세한 내용은 [항목 템플릿 만들기](#create-item-templates)를 참조 하세요.<br /><br /> 일반적으로 SharePoint 프로젝트는 하나 이상의 SharePoint 프로젝트 항목을 포함 합니다. 그러나 반드시 이렇게 해야 하는 것은 아닙니다.|
|*\<featureName>. 기능*|이 파일은 배포를 위해 여러 프로젝트 항목을 그룹화 하는 데 사용 되는 SharePoint 기능을 정의 합니다. 기능 디자이너를 사용 하 여 프로젝트의 기능을 사용자 지정 하는 경우 Visual Studio는 해당 기능에 대 한 데이터를이 파일에 저장 합니다. 프로젝트 항목을 다른 기능으로 그룹화 하려는 경우 여러 개의 *기능* 파일을 포함할 수 있습니다.<br /><br /> 사용자 지정 SharePoint 프로젝트 템플릿을 만들 때 각 *. 기능* 파일에 필요한 최소 콘텐츠만 포함 하 고, <xref:Microsoft.VisualStudio.SharePoint.Features> 프로젝트 템플릿과 연결 된 확장에서 네임 스페이스의 api를 사용 하 여 기능을 구성 하는 것이 좋습니다. 이 작업을 수행 하는 경우 프로젝트 템플릿은 나중에 *기능* 파일의 구조를 변경 하지 못하도록 보호 됩니다. 필요한 최소한의 콘텐츠만 포함 하는 *기능* 파일을 만드는 방법을 보여 주는 예제는 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부를](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)참조 하세요.<br /><br /> *기능* 파일을 직접 수정 하려면 *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\FeatureModelSchema.xsd*에서 스키마를 사용 하 여 내용을 확인할 수 있습니다.|
|*\<featureName>.Template.xml*|이 파일은 프로젝트에서 생성 되는 각 기능에 대 한 기능 매니페스트 파일 (*Feature.xml*)의 기반을 제공 합니다. 프로젝트 형식의 사용자가 변경할 수 없는 동작을 지정 하려면이 파일에 콘텐츠를 추가할 수 있습니다. 자세한 내용은 [블록 구성: 기능](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) 및 [Feature.xml](/sharepoint/dev/schema/feature-xml-files) 파일을 참조 하세요.<br /><br /> 프로젝트에서 솔루션 패키지를 빌드하면 Visual Studio에서 각 * \<featureName> 기능* 파일 쌍의 내용과 * \<featureName>.Template.xml* 파일을 기능 매니페스트 파일에 병합 합니다. 솔루션 패키지 빌드에 대 한 자세한 내용은 [방법: MSBuild 작업을 사용 하 여 SharePoint 솔루션 패키지 만들기](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)를 참조 하세요.|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>항목 템플릿 및 프로젝트 템플릿에 대 한 마법사 만들기
 SharePoint 프로젝트 항목 형식을 정의 하 고 항목 또는 프로젝트 템플릿에 연결한 후 마법사를 만들 수도 있습니다. 개발자가 항목 템플릿을 사용 하 여 SharePoint 프로젝트 항목을 프로젝트에 추가 하거나 개발자가 프로젝트 템플릿을 사용 하 여 SharePoint 프로젝트 항목을 포함 하는 새 프로젝트를 만드는 경우 마법사가 표시 됩니다. 이 마법사를 사용 하 여 개발자의 정보를 수집 하 고 새 SharePoint 프로젝트 항목을 초기화할 수 있습니다.

 항목 템플릿 및 프로젝트 템플릿에 대 한 마법사를 만드는 방법을 보여 주는 연습은 [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) 및 [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부를](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)참조 하세요.

## <a name="see-also"></a>추가 정보

- [사용자 지정 SharePoint 프로젝트 항목 형식 정의](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [연습: 항목 템플릿을 사용 하 여 사용자 지정 작업 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 1 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [연습: 프로젝트 템플릿을 사용 하 여 사이트 열 프로젝트 항목 만들기, 2 부](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
