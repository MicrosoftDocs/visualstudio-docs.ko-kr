---
title: '연습: 레거시 언어 서비스 만들기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703696"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>연습: 레거시 언어 서비스 만들기
관리되는 패키지 프레임워크(MPF) 언어 클래스를 사용하여 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 언어 서비스를 구현하는 것은 간단합니다. 언어 서비스, 언어 서비스 자체 및 해당 언어에 대한 파서를 호스트하려면 VSPackage가 필요합니다.

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../../extensibility/visual-studio-sdk.md)를 참조하십시오.

## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio 패키지 프로젝트 템플릿의 위치
 Visual Studio 패키지 프로젝트 템플릿은 **새 프로젝트** 대화 상자의 세 가지 다른 템플릿 위치에서 찾을 수 있습니다.

1. Visual Basic 확장성에 위치한 템플릿 프로젝트의 기본 언어는 Visual Basic입니다.

2. C# 확장성에 위치한 템플릿 프로젝트의 기본 언어는 C#입니다.

3. 다른 프로젝트 형식 확장성에 위치한 템플릿 프로젝트의 기본 언어는 C++입니다.

### <a name="create-a-vspackage"></a>VS패키지 만들기

1. Visual Studio 패키지 프로젝트 템플릿을 사용하여 새 VSPackage를 만듭니다.

    기존 VSPackage에 언어 서비스를 추가하는 경우 다음 단계를 건너뛰고 "언어 서비스 클래스 만들기" 프로시저로 바로 이동합니다.

2. 프로젝트 이름을 위해 MyLanguagePackage를 입력하고 **확인을**클릭합니다.

    원하는 이름을 사용할 수 있습니다. 여기에 자세히 설명된 이러한 절차는 MyLanguagePackage를 이름으로 가정합니다.

3. 언어및새 키 파일을 생성하는 옵션으로 선택합니다. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] **다음**을 클릭합니다.

4. 적절한 회사 및 패키지 정보를 입력합니다. **다음**을 클릭합니다.

5. **메뉴 명령을 선택합니다.** **다음**을 클릭합니다.

    코드 조각을 지원하지 않으려면 완료를 클릭하고 다음 단계를 무시할 수 있습니다.

6. **명령 이름과 명령** `cmdidInsertSnippet` **ID에**대해 **삽입 스니펫을** 입력합니다. **Finish**를 클릭합니다.

    **명령 이름과** **명령 ID는** 원하는 대로 될 수 있습니다., 이들은 단지 예.

### <a name="create-the-language-service-class"></a>언어 서비스 클래스 만들기

1. **솔루션 탐색기에서**MyLanguagePackage 프로젝트를 마우스 오른쪽 단추로 클릭하고 **참조** **추가를**선택한 다음 **새 참조 추가** 단추를 선택합니다.

2. 참조 **추가** 대화 상자에서 **Microsoft.VisualStudio.Package.Language** **.NET** 탭에서 **확인을**클릭합니다.

     이 작업은 언어 패키지 프로젝트에 대해 한 번만 수행해야 합니다.

3. **솔루션 탐색기에서**VSPackage 프로젝트를 마우스 오른쪽 단추로 클릭하고 **클래스** **추가를**선택합니다.

4. 템플릿 목록에서 **클래스가** 선택되어 있는지 확인합니다.

5. 클래스 파일 의 이름에 대한 **MyLanguageService.cs** 입력하고 **추가를**클릭합니다.

     원하는 이름을 사용할 수 있습니다. 여기에 자세히 설명된 `MyLanguageService` 이러한 절차는 이름으로 가정합니다.

6. MyLanguageService.cs 파일에 다음 `using` 지시문을 추가합니다.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. 클래스에서 `MyLanguageService` 파생하도록 클래스를 수정합니다. <xref:Microsoft.VisualStudio.Package.LanguageService>

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. "LanguageService"와 **편집**, **IntelliSense** 메뉴에서 커서를 배치하고 **추상 클래스 구현을**선택합니다. 이렇게 하면 언어 서비스 클래스를 구현하는 데 필요한 최소 메서드가 추가됩니다.

9. 레거시 언어 서비스 구현에 설명된 대로 추상 [메서드를 구현합니다.](../../extensibility/internals/implementing-a-legacy-language-service2.md)

### <a name="register-the-language-service"></a>언어 서비스 등록

1. MyLanguagePackagePackage.cs 파일을 열고 다음 `using` 지시문을 추가합니다.

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. 레거시 언어 서비스 등록에 설명된 대로 언어 [서비스 클래스를 등록합니다.](../../extensibility/internals/registering-a-legacy-language-service1.md) 여기에는 ProvideXX 특성과 "언어 서비스 제공" 섹션이 포함됩니다. 이 항목에서 TestLanguageService를 사용하는 MyLanguageService를 사용합니다.

### <a name="the-parser-and-scanner"></a>파서 및 스캐너

1. [레거시 언어 서비스 파서](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)및 스캐너에 설명된 대로 해당 언어에 대한 파서 및 스캐너를 구현합니다.

     파서 와 스캐너를 구현하는 방법은 전적으로 사용자의 것이며이 항목의 범위를 벗어납니다.

## <a name="language-service-features"></a>언어 서비스 기능
 언어 서비스에서 각 기능을 구현하려면 일반적으로 적절한 MPF 언어 서비스 클래스에서 클래스를 파생하고 필요에 따라 추상 메서드를 구현하고 적절한 메서드를 재정의합니다. 어떤 클래스를 만들거나 파생하는지 지원하려는 기능에 따라 다릅니다. 이러한 기능은 레거시 언어 [서비스 기능에서](../../extensibility/internals/legacy-language-service-features1.md)자세히 설명합니다. 다음 절차는 MPF 클래스에서 클래스를 파생하는 일반적인 방법입니다.

#### <a name="deriving-from-an-mpf-class"></a>MPF 클래스에서 파생

1. **솔루션 탐색기에서**VSPackage 프로젝트를 마우스 오른쪽 단추로 클릭하고 **클래스** **추가를**선택합니다.

2. 템플릿 목록에서 **클래스가** 선택되어 있는지 확인합니다.

     클래스 파일에 적합한 이름을 입력하고 **추가 를**클릭합니다.

3. 새 클래스 파일에서 다음 `using` 지시문을 추가합니다.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. 원하는 MPF 클래스에서 파생하도록 클래스를 수정합니다.

5. 기본 클래스의 생성자와 동일한 매개 변수를 사용 하 고 생성자 매개 변수를 기본 클래스 생성자에 전달 하는 클래스 생성자 추가 합니다.

     예를 들어 <xref:Microsoft.VisualStudio.Package.Source> 클래스에서 파생된 클래스의 생성자는 다음과 같습니다.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. **편집**- **IntelliSense** 메뉴에서 기본 클래스에 구현해야 하는 추상 메서드가 있는 경우 **추상 클래스 구현을** 선택합니다.

7. 그렇지 않으면 클래스 내부에 카릿을 배치하고 재정의할 메서드를 입력합니다.

     예를 들어 `public override` 해당 클래스에서 재정의할 수 있는 모든 메서드의 목록을 보려면 입력합니다.

## <a name="see-also"></a>참조
- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)
