---
title: 'SharePoint 솔루션: 사용자 지정 기능 및 패키지 유효성 검사 규칙 만들기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
- SharePoint development in Visual Studio, validation rules
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f731b6af2ada8caddb84be5561d7f6dc304e7bbd
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016913"
---
# <a name="how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions"></a>방법: SharePoint 솔루션에 대 한 사용자 지정 기능 및 패키지 유효성 검사 규칙 만들기
  Visual Studio에서 생성 된 솔루션 패키지를 확인 하는 사용자 지정 유효성 검사 규칙을 만들 수 있습니다. **PackagingExplorer**의 패키지 또는 기능에 대 한 상황에 맞는 메뉴에서 **유효성** 검사를 선택 하 여 전체 기능 또는 패키지에 대 한 전체 유효성 검사를 수행할 수 있습니다. 프로젝트에 새 SharePoint 프로젝트 항목 또는 기능을 추가 하 여 패키지나 기능이 유효한 상태 인지 확인 하는 경우 부분 유효성 검사가 수행 됩니다.

### <a name="to-create-a-custom-package-validation-rule"></a>사용자 지정 패키지 유효성 검사 규칙을 만들려면

1. 클래스 라이브러리 프로젝트를 만듭니다.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    - VisualStudio

    - System.ComponentModel.Composition

3. 다음 인터페이스 중 하나를 구현 하는 클래스를 만듭니다.

    - 패키지 유효성 검사 규칙을 만들려면 인터페이스를 구현 <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule> 합니다.

    - 기능 유효성 검사 규칙을 만들려면 인터페이스를 구현 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 합니다.

4. 를 <xref:System.ComponentModel.Composition.ExportAttribute> 클래스에 추가 합니다. 이 특성을 사용 하면 Visual Studio에서 유효성 검사 규칙을 검색 하 고 로드할 수 있습니다. <xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>또는 <xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule> 형식을 특성 생성자에 전달 합니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 사용자 지정 기능 유효성 검사 규칙을 만드는 방법을 보여 줍니다.

 [!code-vb[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/VisualBasic/featurevalidation/extension/customvalidationrule.vb#1)]
 [!code-csharp[SPExtensibility.FeatureValidation#1](../sharepoint/codesnippet/CSharp/featurevalidation/extension/customfeaturevalidationrule.cs#1)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요 합니다.

- VisualStudio.

- System.componentmodel.

## <a name="deploy-the-extension"></a>확장 배포
 확장을 배포 하려면 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 모든 파일에 대 한 확장 (VSIX) 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
