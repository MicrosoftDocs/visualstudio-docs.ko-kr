---
title: 프로젝트 디자이너, 서비스 페이지
ms.date: 01/18/2018
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d30d8e8ddcdc8c1fa4fe1935da1f1dedd1b18f4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593566"
---
# <a name="services-page-project-designer"></a>프로젝트 디자이너, 서비스 페이지

클라이언트 애플리케이션 서비스를 통해 Windows Forms 및 WPF(Windows Presentation Foundation) 애플리케이션에서 [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] 로그인, 역할 및 프로필 서비스에 간편하게 액세스할 수 있습니다. **프로젝트 디자이너**의 **서비스** 페이지를 사용하여 프로젝트에 대해 클라이언트 애플리케이션 서비스를 사용하도록 설정하고 구성할 수 있습니다.

클라이언트 애플리케이션 서비스를 통해 중앙 집중식 서버를 사용하여 사용자를 인증하고, 각 사용자의 할당된 역할을 결정하고, 네트워크에서 공유할 수 있는 사용자별 애플리케이션 설정을 저장할 수 있습니다. 자세한 내용은 [클라이언트 애플리케이션 서비스](/dotnet/framework/common-client-technologies/client-application-services)를 참조하세요.

**서비스** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택하고 **프로젝트** 메뉴에서 **속성**을 클릭합니다. **프로젝트 디자이너**가 나타나면 **서비스** 탭을 클릭합니다.

## <a name="task-list"></a>작업 목록

[방법: 클라이언트 애플리케이션 서비스 구성](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)

## <a name="uielement-list"></a>UIElement 목록

 **Configuration**

이 컨트롤은 이 페이지에서 편집할 수 없습니다. 이 컨트롤에 대한 자세한 내용은 [프로젝트 디자이너, 컴파일 페이지(Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) 또는 [프로젝트 디자이너, 빌드 페이지(C#)](../../ide/reference/build-page-project-designer-csharp.md)를 참조하세요.

 **플랫폼**

이 컨트롤은 이 페이지에서 편집할 수 없습니다. 이 컨트롤에 대한 자세한 내용은 [프로젝트 디자이너, 컴파일 페이지(Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) 또는 [프로젝트 디자이너, 빌드 페이지(C#)](../../ide/reference/build-page-project-designer-csharp.md)를 참조하세요.

 **클라이언트 애플리케이션 서비스 사용**

클라이언트 애플리케이션 서비스를 사용하려면 선택합니다. 클라이언트 애플리케이션 서비스를 사용하려면 **서비스** 페이지에서 서비스 위치를 지정해야 합니다.

 **Windows 인증 사용**

인증 공급자가 Windows 기반 인증(Windows 운영 체제에서 제공된 ID)을 사용할 것임을 나타냅니다.

 **폼 인증 사용**

인증 공급자가 폼 인증을 사용할 것임을 나타냅니다. 이는 애플리케이션에서 로그인용 사용자 인터페이스를 제공해야 함을 의미합니다. 자세한 내용은 [방법: 클라이언트 애플리케이션 서비스에서 사용자 로그인 구현](/dotnet/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services)을 참조하세요.

 **인증 서비스 위치**

폼 인증에서만 사용됩니다. 인증 서비스의 위치를 지정합니다.

 **선택 사항: 자격 증명 공급자**

폼 인증에서만 사용됩니다. 애플리케이션이 `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> 메서드를 호출하고 매개 변수에 대해 빈 문자열이나 `null`을 전달할 때 인증 서비스에서 로그인 대화 상자를 표시하는 데 사용할 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> 구현을 나타냅니다. 이 상자를 비워 두면 유효한 사용자 이름 및 암호를 <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> 메서드에 전달해야 합니다. 자격 증명 공급자를 정규화된 어셈블리 형식 이름을 지정해야 합니다. 자세한 내용은 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> 및 [어셈블리 이름](/dotnet/framework/app-domains/assembly-names)을 참조하세요. 가장 단순한 형식의 정규화된 어셈블리 형식 이름은 다음 예제와 같습니다. `MyNamespace.MyLoginClass, MyAssembly`

 **역할 서비스 위치**

역할 서비스의 위치를 지정합니다.

 **웹 설정 서비스 위치**

프로필(웹 설정) 서비스의 위치를 지정합니다.

 **고급**

기본 동작을 재정의하는 데 사용할 수 있는 [서비스의 고급 설정 대화 상자](../../ide/reference/advanced-settings-for-services-dialog-box.md)를 엽니다. 예를 들어 이 대화 상자를 사용하여 로컬 파일 시스템을 사용하는 대신 오프라인 스토리지용 데이터베이스를 지정할 수 있습니다. 자세한 내용은 [서비스의 고급 설정 대화 상자](../../ide/reference/advanced-settings-for-services-dialog-box.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [클라이언트 애플리케이션 서비스](/dotnet/framework/common-client-technologies/client-application-services)
- [서비스의 고급 설정 대화 상자](../../ide/reference/advanced-settings-for-services-dialog-box.md)
- [방법: 클라이언트 애플리케이션 서비스 구성](/dotnet/framework/common-client-technologies/how-to-configure-client-application-services)
- [프로젝트 디자이너, 컴파일 페이지(Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [프로젝트 디자이너, 빌드 페이지(C#)](../../ide/reference/build-page-project-designer-csharp.md)
