---
title: 옵션 및 옵션 페이지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d21bf6d5ab7e23047a02e1188fff9a47d0cbd58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706835"
---
# <a name="options-and-options-pages"></a>옵션 및 옵션 페이지
**도구** 메뉴에서 **옵션을** 클릭하면 **옵션** 대화 상자가 열립니다. 이 대화 상자의 옵션은 총칭하여 옵션 페이지라고 합니다. 탐색 창의 트리 컨트롤에는 옵션 범주가 포함되며 모든 범주에는 옵션 페이지가 있습니다. 페이지를 선택하면 해당 옵션이 오른쪽 창에 나타납니다. 이러한 페이지를 사용하면 VSPackage의 상태를 결정하는 옵션의 값을 변경할 수 있습니다.

## <a name="support-for-options-pages"></a>옵션 페이지 지원
 클래스는 <xref:Microsoft.VisualStudio.Shell.Package> 옵션 페이지 및 옵션 범주를 만드는 데 대한 지원을 제공합니다. 클래스는 <xref:Microsoft.VisualStudio.Shell.DialogPage> 옵션 페이지를 구현합니다.

 기본 구현은 <xref:Microsoft.VisualStudio.Shell.DialogPage> 속성의 일반 그리드에 있는 사용자에게 공용 속성을 제공합니다. 페이지의 다양한 메서드를 재정의하여 고유한 사용자 인터페이스(UI)가 있는 사용자 지정 옵션 페이지를 만들어 이 동작을 사용자 지정할 수 있습니다. 자세한 내용은 [옵션 페이지 만들기를](../../extensibility/creating-an-options-page.md)참조하십시오.

 클래스는 <xref:Microsoft.VisualStudio.Shell.DialogPage> <xref:Microsoft.VisualStudio.Shell.IProfileManager>옵션 페이지와 사용자 설정에 대한 지속성을 제공하는 을 구현합니다. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> 및 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 메서드의 기본 구현은 속성을 문자열로 변환할 수 있는 경우 속성 변경 내용을 레지스트리의 사용자 섹션으로 유지합니다.

## <a name="options-page-registry-path"></a>옵션 페이지 레지스트리 경로
 기본적으로 옵션 페이지에서 관리하는 속성의 레지스트리 경로는 [DialogPage]라는 단어와 옵션 페이지 클래스의 형식 이름을 결합하여 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>결정됩니다. 예를 들어 옵션 페이지 클래스는 다음과 같이 정의될 수 있습니다.

 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]

 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp인 경우 속성 이름과 값 쌍은 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\Company.OptionsPage.OptionsPage일반의 하위 키입니다.

 옵션 페이지 자체의 레지스트리 경로는 단어, <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>ToolsOptionsPages 및 옵션 페이지 범주 및 이름을 결합하여 결정됩니다. 예를 들어 사용자 지정 옵션 페이지에 범주가 있는 경우 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> 내 옵션 페이지가 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp인 경우 옵션 페이지에 레지스트리 키, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolsPages\내 옵션 페이지\사용자 지정입니다.

## <a name="toolsoptions-page-attributes-and-layout"></a>도구/옵션 페이지 속성 및 레이아웃
 특성은 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 옵션 대화 상자의 탐색 트리에서 사용자 지정 옵션 페이지를 범주로 그룹화하는 **것을** 결정합니다. 특성은 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 옵션 페이지를 인터페이스를 제공하는 VSPackage와 연결합니다. 다음과 같은 코드 조각을 생각해 봅시다.

 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]

 이렇게 하면 MyPackage에서 옵션 페이지일반 및 옵션페이지사용자라는 두 가지 옵션 페이지를 제공합니다. **옵션** 대화 상자에서 두 옵션 페이지가 **내 옵션 페이지** 범주에 일반 및 **맞춤**으로 각각 표시됩니다. **General**

## <a name="option-attributes-and-layout"></a>옵션 속성 및 레이아웃
 페이지에서 제공하는 사용자 인터페이스(UI)는 사용자 지정 옵션 페이지에서 옵션의 모양을 결정합니다. 일반 옵션 페이지의 레이아웃, 레이블 지정 및 옵션 설명은 다음 특성에 따라 결정됩니다.

- <xref:System.ComponentModel.CategoryAttribute>옵션의 범주를 결정합니다.

- <xref:System.ComponentModel.DisplayNameAttribute>옵션을 표시하는 이름이 결정됩니다.

- <xref:System.ComponentModel.DescriptionAttribute>옵션에 대한 설명을 결정합니다.

  > [!NOTE]
  > 동등한 특성, SRCategory, LocDisplayName 및 SRDescription는 지역화를 위해 문자열 리소스를 사용하고 [관리되는 프로젝트 샘플에](/azure/devops/integrate/index)정의됩니다.

  다음과 같은 코드 조각을 생각해 봅시다.

  [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]

  옵션인테이거 옵션은 옵션 페이지에 **내 옵션** 범주의 **정수 옵션으로** 표시됩니다. 옵션을 선택하면 설명, 내 **정수 옵션이**설명 상자에 나타납니다.

## <a name="accessing-options-pages-from-another-vspackage"></a>다른 VSPackage에서 옵션 페이지에 액세스
 옵션 페이지를 호스팅하고 관리하는 VSPackage는 자동화 모델을 사용하여 다른 VSPackage에서 프로그래밍 방식으로 액세스할 수 있습니다. 예를 들어 다음 코드에서 VSPackage는 옵션 페이지를 호스팅하는 것으로 등록됩니다.

 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]

 다음 코드 조각은 MyOptionPage에서 OptionInteger의 값을 가져옵니다.

 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]

 특성이 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 옵션 페이지를 등록하면 속성의 `SupportsAutomation` 인수가 `true`있는 경우 페이지가 AutomationProperties 키 아래에 등록됩니다. 자동화는 이 레지스트리 항목을 검사하여 연결된 VSPackage를 찾은 다음 호스팅된 옵션 페이지(이 경우 내 그리드 페이지)를 통해 속성에 액세스합니다.

 자동화 속성의 레지스트리 경로는 단어, <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>AutomationProperties 및 옵션 페이지 범주 및 이름을 결합하여 결정됩니다. 예를 들어 옵션 페이지에 내 범주 범주, 내 그리드 페이지 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>이름 및 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp가 있는 경우 자동화 속성에는 레지스트리 키, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My 범주\내 그리드 페이지입니다.

> [!NOTE]
> 표준 이름인 내 Category.My 그리드 페이지는 이 키의 이름 하위 키의 값입니다.
