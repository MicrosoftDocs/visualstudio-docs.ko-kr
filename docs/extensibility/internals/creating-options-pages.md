---
title: 옵션 페이지 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 368efaa78a56723d4a72c482bea9ee739385127e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709146"
---
# <a name="create-options-pages"></a>옵션 페이지 만들기
관리되는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 패키지 <xref:Microsoft.VisualStudio.Shell.DialogPage> 프레임워크에서 파생된 클래스는 **도구** 메뉴 아래에 **옵션** 페이지를 추가하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE를 확장합니다.

 지정된 **도구 옵션** 페이지를 구현하는 개체는 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 개체의 특정 VSPackage와 연결됩니다.

 환경은 IDE에서 특정 페이지가 표시될 때 특정 **도구 옵션** 페이지를 구현하는 개체를 인스턴스화하므로 다음과 같은 작업환경이 표시됩니다.

- **도구 옵션** 페이지는 VSPackage를 구현하는 개체가 아니라 자체 개체에서 구현되어야 합니다.

- 개체는 여러 **도구 옵션** 페이지를 구현할 수 없습니다.

## <a name="register-as-a-tools-options-page-provider"></a>도구 옵션 페이지 공급자로 등록
 **도구 옵션** 페이지를 통해 사용자 구성을 지원하는 VSPackage는 구현에 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 적용된 인스턴스를 <xref:Microsoft.VisualStudio.Shell.Package> 적용하여 이러한 **도구 옵션** 페이지를 제공하는 개체를 나타냅니다.

 **도구 옵션** 페이지를 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 구현하는 <xref:Microsoft.VisualStudio.Shell.DialogPage>모든 파생 형식에 대해 하나의 인스턴스가 있어야 합니다.

 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 각 인스턴스는 **도구 옵션** 페이지를 구현하는 형식, 도구 옵션 페이지를 식별하는 데 사용되는 범주 및 하위 범주를 포함하는 문자열 및 도구 **옵션** 페이지를 제공하는 것으로 형식을 등록하는 리소스 정보를 사용합니다. **Tools Options**

## <a name="persist-tools-options-page-state"></a>도구 유지 옵션 페이지 상태
 도구 **옵션** 페이지 구현이 자동화 지원을 사용하도록 사용하도록 설정된 상태로 등록된 경우 IDE는 다른 모든 **도구 옵션** 페이지와 함께 페이지의 상태를 유지합니다.

 VSPackage는 을 사용하여 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>자체 지속성을 관리할 수 있습니다. 하나 또는 다른 지속성 방법만 사용해야 합니다.

## <a name="implement-dialogpage-class"></a>대화 상자 페이지 클래스 구현
 VSPackage에서 -derived 형식의 <xref:Microsoft.VisualStudio.Shell.DialogPage>구현을 제공하는 개체는 다음과 같은 상속된 기능을 활용할 수 있습니다.

- 기본 사용자 인터페이스 창입니다.

- 클래스에 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 적용되거나 속성이 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> 클래스에 적용되는 `true` <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 것에 대해 설정된 경우 사용할 수 있는 기본 지속성 메커니즘입니다.

- 자동화 지원.

  **도구 옵션** 페이지를 사용하는 <xref:Microsoft.VisualStudio.Shell.DialogPage> 개체에 대한 최소 요구 사항은 공용 속성을 추가하는 것입니다.

  클래스가 **도구 옵션** 페이지 공급자로 올바르게 등록된 경우 해당 공용 속성은 속성 그리드 의 형태로 **도구** 메뉴의 **옵션** 섹션에서 사용할 수 있습니다.

  이러한 모든 기본 기능을 재정의할 수 있습니다. 예를 들어 보다 정교한 사용자 인터페이스를 만들려면 <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>의 기본 구현만 재정의하면 됩니다.

## <a name="example"></a>예제
 다음은 옵션 페이지의 간단한 "Hello world" 구현입니다. **메뉴 명령** 옵션을 선택한 Visual Studio 패키지 템플릿에서 만든 기본 프로젝트에 다음 코드를 추가하면 옵션 페이지 기능이 적절하게 보여집니다.

### <a name="description"></a>설명
 다음 클래스는 최소한의 "Hello world" 옵션 페이지를 정의합니다. 열면 사용자는 속성 그리드에서 `HelloWorld` 공용 속성을 설정할 수 있습니다.

### <a name="code"></a>코드
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]

### <a name="description"></a>설명
 패키지 클래스에 다음 특성을 적용하면 패키지가 로드될 때 옵션 페이지를 사용할 수 있습니다. 숫자는 범주 및 페이지에 대한 임의리소스 아이디이며 끝에 있는 부울 값은 페이지가 자동화를 지원하는지 여부를 지정합니다.

### <a name="code"></a>코드
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]

### <a name="description"></a>설명
 다음 이벤트 처리기는 옵션 페이지에 설정된 속성값에 따라 결과를 표시합니다. 사용자 지정 <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> 옵션 페이지 유형에 명시적으로 캐스팅된 결과와 함께 메서드를 사용하여 페이지에서 노출되는 속성에 액세스합니다.

 패키지 템플릿에서 생성된 프로젝트의 경우 `MenuItemCallback` 함수에서 이 함수를 호출하여 **Tools** 메뉴에 추가된 기본 명령에 연결합니다.

### <a name="code"></a>코드
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]

## <a name="see-also"></a>참조
- [사용자 설정 및 옵션 확장](../../extensibility/extending-user-settings-and-options.md)
- [옵션 페이지에 대한 자동화 지원](../../extensibility/internals/automation-support-for-options-pages.md)
