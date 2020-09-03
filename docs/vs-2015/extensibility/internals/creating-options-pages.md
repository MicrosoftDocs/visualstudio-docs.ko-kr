---
title: 옵션 페이지 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c2b993a6c6947adfa3b01f2947b992b23236b8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196937"
---
# <a name="creating-options-pages"></a>옵션 페이지 만들기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]관리 되는 패키지 프레임 워크에서에서 파생 된 클래스는 <xref:Microsoft.VisualStudio.Shell.DialogPage> [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **도구** 메뉴의 **옵션** 페이지를 추가 하 여 IDE를 확장 합니다.  
  
 지정 된 **도구 옵션** 페이지를 구현 하는 개체는 개체에 의해 특정 vspackage 연결 됩니다 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .  
  
 환경에서는 특정 페이지가 IDE에서 표시 될 때 특정 **도구 옵션** 페이지를 구현 하는 개체를 인스턴스화합니다.  
  
- **도구 옵션** 페이지는 VSPackage를 구현 하는 개체가 아니라 자체 개체에서 구현 되어야 합니다.  
  
- 개체는 여러 **도구 옵션** 페이지를 구현할 수 없습니다.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>도구 옵션 페이지 공급자로 등록  
 **도구 옵션** 페이지를 통한 VSPackage 지원 사용자 구성에서는 구현에 적용 된의 인스턴스를 적용 하 여 이러한 **도구 옵션** 페이지를 제공 하는 개체를 나타냅니다 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> <xref:Microsoft.VisualStudio.Shell.Package> .  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> <xref:Microsoft.VisualStudio.Shell.DialogPage> **도구 옵션** 페이지를 구현 하는 모든 파생 형식에 대해 인스턴스가 하나 있어야 합니다.  
  
 의 각 인스턴스는 도구 옵션 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 페이지를 구현 **Tools Options** 하는 형식, **도구 옵션** 페이지를 식별 하는 데 사용 되는 범주 및 하위 범주를 포함 하는 문자열, **도구 옵션** 페이지를 제공 하는 형식으로 등록 하기 위한 리소스 정보를 사용 합니다.  
  
## <a name="persisting-tools-options-page-state"></a>도구 옵션 페이지 상태 유지  
 자동화 지원을 사용 하도록 설정 하 여 **도구 옵션** 페이지 구현을 등록 하면 IDE는 다른 모든 **도구 옵션** 페이지와 함께 페이지의 상태를 유지 합니다.  
  
 VSPackage는을 사용 하 여 자체 지 속성을 관리할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . 하나 또는 다른 지 속성 메서드를 사용 해야 합니다.  
  
## <a name="implementing-dialogpage-class"></a>DialogPage 클래스 구현  
 VSPackage의 파생 형식 구현을 제공 하는 개체는 <xref:Microsoft.VisualStudio.Shell.DialogPage> 다음과 같은 상속 된 기능을 활용할 수 있습니다.  
  
- 기본 사용자 인터페이스 창  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>클래스에가 적용 된 경우 또는 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> `true` <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 클래스에 적용 되는에 대해 속성이로 설정 된 경우에 사용할 수 있는 기본 지 속성 메커니즘입니다.  
  
- 자동화 지원.  
  
  를 사용 하 여 **도구 옵션** 페이지를 구현 하는 개체의 최소 요구 사항은 <xref:Microsoft.VisualStudio.Shell.DialogPage> 공용 속성을 추가 하는 것입니다.  
  
  클래스가 **도구 옵션** 페이지 공급자로 올바르게 등록 된 경우 해당 공용 속성은 속성 표 형식으로 **도구** 메뉴의 **옵션** 섹션에서 사용할 수 있습니다.  
  
  이러한 모든 기본 기능을 재정의할 수 있습니다. 예를 들어 보다 정교한 사용자 인터페이스를 만들려면의 기본 구현만 재정의 하면 <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A> 됩니다.  
  
## <a name="example"></a>예  
 다음은 옵션 페이지의 간단한 "hello 세계" 구현입니다. **메뉴 명령** 옵션을 선택 하 여 Visual Studio 패키지 템플릿에서 만든 기본 프로젝트에 다음 코드를 추가 하면 옵션 페이지 기능을 적절 하 게 보여 줍니다.  
  
### <a name="description"></a>설명  
 다음 클래스는 최소 "hello 세계" 옵션 페이지를 정의 합니다. 사용자가 열면 속성 표에서 public 속성을 설정할 수 있습니다 `HelloWorld` .  
  
### <a name="code"></a>코드  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/class1.cs#11)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/class1.vb#11)]  
  
### <a name="description"></a>Description  
 Package 클래스에 다음 특성을 적용 하면 패키지가 로드 될 때 옵션 페이지를 사용할 수 있습니다. 숫자는 범주와 페이지에 대 한 임의의 리소스 Id이 고, 끝의 부울 값은 페이지에서 자동화를 지원 하는지 여부를 지정 합니다.  
  
### <a name="code"></a>코드  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#07)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#07)]  
  
### <a name="description"></a>Description  
 다음 이벤트 처리기는 옵션 페이지에 설정 된 속성의 값에 따라 결과를 표시 합니다. 이 메서드는 <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> 사용자 지정 옵션 페이지 형식으로 명시적으로 캐스팅 된 결과와 함께 메서드를 사용 하 여 페이지에 의해 노출 되는 속성에 액세스 합니다.  
  
 패키지 템플릿에 의해 생성 된 프로젝트의 경우 함수에서이 함수를 호출 `MenuItemCallback` 하 여 **도구** 메뉴에 추가 된 기본 명령에 연결 합니다.  
  
### <a name="code"></a>코드  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../snippets/csharp/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/cs/uiusersettingstoolsoptionspagespackage.cs#08)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../snippets/visualbasic/VS_Snippets_VSSDK/ui_usersettings_toolsoptionpages/vb/uiusersettingstoolsoptionspagespackage.vb#08)]  
  
## <a name="see-also"></a>참고 항목  
 [사용자 설정 및 옵션 확장](../../extensibility/extending-user-settings-and-options.md)   
 [옵션 페이지의 자동화 지원](../../extensibility/internals/automation-support-for-options-pages.md)
