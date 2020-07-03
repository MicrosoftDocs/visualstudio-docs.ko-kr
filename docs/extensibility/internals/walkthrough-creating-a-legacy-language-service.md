---
title: '연습: 레거시 언어 서비스 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbdad85dd1c0f62b22bb33b5ed6ab2c597e62164
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905987"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>연습: 레거시 언어 서비스 만들기
MPF (관리 패키지 프레임 워크) 언어 클래스를 사용 하 여에서 언어 서비스를 구현 하 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 는 것은 간단 합니다. 언어 서비스, 언어 서비스 자체 및 해당 언어의 파서를 호스트 하는 VSPackage 필요 합니다.

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio 패키지 프로젝트 템플릿의 위치
 Visual Studio 패키지 프로젝트 템플릿은 **새 프로젝트** 대화 상자의 세 가지 템플릿 위치에서 찾을 수 있습니다.

1. Visual Basic 확장성에 위치한 템플릿 프로젝트의 기본 언어는 Visual Basic입니다.

2. C# 확장성에 위치한 템플릿 프로젝트의 기본 언어는 C#입니다.

3. 다른 프로젝트 형식 확장성에 위치한 템플릿 프로젝트의 기본 언어는 C++입니다.

### <a name="create-a-vspackage"></a>VSPackage 만들기

1. Visual Studio 패키지 프로젝트 템플릿을 사용 하 여 새 VSPackage를 만듭니다.

    기존 VSPackage에 언어 서비스를 추가 하는 경우 다음 단계를 건너뛰고 "언어 서비스 클래스 만들기" 절차로 직접 이동 합니다.

2. 프로젝트 이름에 MyLanguagePackage를 입력 하 고 **확인**을 클릭 합니다.

    원하는 이름을 사용할 수 있습니다. 여기에 자세히 설명 된 절차에서는 MyLanguagePackage를 이름으로 가정 합니다.

3. 를 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 언어로 선택 하 고 옵션을 선택 하 여 새 키 파일을 생성 합니다. **다음**을 클릭합니다.

4. 적절 한 회사 및 패키지 정보를 입력 합니다. **다음**을 클릭합니다.

5. **메뉴 명령**을 선택 합니다. **다음**을 클릭합니다.

    코드 조각을 지원 하지 않으려는 경우 마침을 클릭 하면 다음 단계를 무시할 수 있습니다.

6. 명령 **이름** 및 명령 ID로 **Insert 코드 조각을** 입력 `cmdidInsertSnippet` **Command ID**합니다. **Finish**를 클릭합니다.

    **명령 이름** 및 **명령 ID** 는 원하는 대로 지정할 수 있으며,이는 단지 예일 뿐입니다.

### <a name="create-the-language-service-class"></a>언어 서비스 클래스 만들기

1. **솔루션 탐색기**에서 MyLanguagePackage 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가**, **참조**를 선택한 다음 **새 참조 추가** 단추를 선택 합니다.

2. **참조 추가** 대화 상자의 **.Net** 탭에서 **VisualStudio. LanguageService** 를 선택 하 고 **확인**을 클릭 합니다.

     이 작업은 언어 패키지 프로젝트에 대해 한 번만 수행 해야 합니다.

3. **솔루션 탐색기**에서 VSPackage 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가**, **클래스**를 차례로 선택 합니다.

4. 템플릿 목록에서 **클래스** 가 선택 되어 있는지 확인 합니다.

5. 클래스 파일의 이름에 **MyLanguageService.cs** 를 입력 하 고 **추가**를 클릭 합니다.

     원하는 이름을 사용할 수 있습니다. 여기에서 자세히 설명 `MyLanguageService` 하는 절차는 이름으로 가정 합니다.

6. MyLanguageService.cs 파일에서 다음 지시문을 추가 합니다 `using` .

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. 클래스를 수정 하 여 클래스 `MyLanguageService` 에서 파생 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService> .

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. "LanguageService"에 커서를 놓고 **편집**, **IntelliSense** 메뉴에서 **추상 클래스 구현**을 선택 합니다. 이렇게 하면 언어 서비스 클래스를 구현 하는 데 필요한 최소 메서드가 추가 됩니다.

9. [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service2.md)에 설명 된 대로 추상 메서드를 구현 합니다.

### <a name="register-the-language-service"></a>언어 서비스 등록

1. MyLanguagePackagePackage.cs 파일을 열고 다음 지시문을 추가 합니다 `using` .

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)에 설명 된 대로 언어 서비스 클래스를 등록 합니다. 여기에는 ProvideXX 특성과 "Proffering the Language Service" 섹션이 포함 됩니다. 이 항목에서 TestLanguageService를 사용 하는 MyLanguageService를 사용 합니다.

### <a name="the-parser-and-scanner"></a>파서 및 스캐너

1. [레거시 언어 서비스 파서 및 스캐너](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)에 설명 된 대로 언어에 대 한 파서 및 스캐너를 구현 합니다.

     파서 및 스캐너를 구현 하는 방법은 전적으로 사용자에 게 적용 되며이 항목에서는 다루지 않습니다.

## <a name="language-service-features"></a>언어 서비스 기능
 언어 서비스의 각 기능을 구현 하려면 일반적으로 적절 한 MPF 언어 서비스 클래스에서 클래스를 파생 시키고 필요에 따라 모든 추상 메서드를 구현 하 고 적절 한 메서드를 재정의 합니다. 사용자가 만들고 파생 시킨 클래스는 지원 하려는 기능에 따라 달라 집니다. 이러한 기능은 [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)에 자세히 설명 되어 있습니다. 다음 절차는 MPF 클래스에서 클래스를 파생 하는 일반적인 방법입니다.

#### <a name="deriving-from-an-mpf-class"></a>MPF 클래스에서 파생

1. **솔루션 탐색기**에서 VSPackage 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가**, **클래스**를 차례로 선택 합니다.

2. 템플릿 목록에서 **클래스** 가 선택 되어 있는지 확인 합니다.

     클래스 파일에 대 한 적절 한 이름을 입력 하 고 **추가**를 클릭 합니다.

3. 새 클래스 파일에서 다음 지시문을 추가 합니다 `using` .

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. 원하는 MPF 클래스에서 파생 되도록 클래스를 수정 합니다.

5. 기본 클래스의 생성자와 동일한 매개 변수를 사용 하 고 생성자 매개 변수를 기본 클래스 생성자에 전달 하는 클래스 생성자를 추가 합니다.

     예를 들어 클래스에서 파생 된 클래스에 대 한 생성자는 <xref:Microsoft.VisualStudio.Package.Source> 다음과 같을 수 있습니다.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. 기본 클래스에 구현 해야 하는 추상 메서드가 있는 경우 **편집**, **IntelliSense** 메뉴에서 **추상 클래스 구현** 을 선택 합니다.

7. 그렇지 않으면 캐럿을 클래스 내부에 배치 하 고 재정의할 메서드를 입력 합니다.

     예를 들어를 입력 `public override` 하 여 해당 클래스에서 재정의할 수 있는 모든 메서드 목록을 표시 합니다.

## <a name="see-also"></a>참조
- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)
