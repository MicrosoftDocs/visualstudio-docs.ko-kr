---
title: 설정 범주에 대 한 지원 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- settings, supporting with Visual Studio SDK
- Visual Studio SDK, supporting settings
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
manager: jillfra
ms.openlocfilehash: 15a3896f8a2010a063393d3a11c1ed3453a008d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689090"
---
# <a name="support-for-settings-categories"></a>설정 범주에 대한 지원
설정 범주는 IDE(통합 개발 환경)를 사용자 지정하는 옵션 그룹으로 구성됩니다. 예를 들어 설정은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 창의 레이아웃과 메뉴의 내용을 제어할 수 있습니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 클릭하여 **설정 가져오기 및 내보내기 마법사**를 시작합니다. 마법사는 설정 내보내기, 가져오기 또는 다시 설정의 세 가지 옵션을 제공합니다. 예를 들어 내보내기를 선택하면 마법사의 **내보낼 설정 선택** 페이지가 열립니다.  
  
 이 페이지의 탐색 창에 있는 트리 컨트롤에 범주가 나열됩니다. 범주는 관련된 설정의 그룹으로서, "사용자 지정 설정 지점", 즉 확인란으로 나타납니다. 이러한 확인란을 사용하여 .vsettings 파일에 유지할 범주를 선택할 수 있습니다. 마법사를 사용하면 .vsettings 파일 이름을 지정하고 해당 경로 지정할 수 있습니다.  
  
> [!NOTE]
> 설정이 저장되거나 범주로서 복원되고, 개별 설정 이름은 마법사에 표시되지 않습니다.  
  
 MPF(Managed Package Framework)는 최소한의 추가 코드로 설정 범주를 만들도록 지원합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Package> 클래스의 서브클래스를 지정하여 범주에 대한 컨테이너를 제공하려면 VSPackage를 만듭니다.  
  
- <xref:Microsoft.VisualStudio.Shell.DialogPage> 클래스에서 파생시켜 범주 자체를 만듭니다.  
  
- <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>로 둘을 연결합니다.  
  
## <a name="support-for-settings-categories"></a>설정 범주에 대한 지원  
 <xref:Microsoft.VisualStudio.Shell.Package> 클래스는 범주 만들기 지원을 제공합니다. <xref:Microsoft.VisualStudio.Shell.DialogPage> 클래스는 범주를 구현합니다. <xref:Microsoft.VisualStudio.Shell.DialogPage>의 기본 구현은 public 속성을 범주로서 사용자에게 제공합니다. 자세한 내용은 [Creating a Settings Category](../extensibility/creating-a-settings-category.md)을 참조하세요.  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> 클래스는 옵션 페이지와 사용자 설정에 대해 지속성을 제공하는 <xref:Microsoft.VisualStudio.Shell.IProfileManager>를 구현합니다. <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> 및 <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> 메서드는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 각각 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>로서 제공하는 vssettings 파일에 설정을 유지합니다. <xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> 메서드는 설정을 기본값으로 다시 설정합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> 클래스는 xml 피드에서 이름-값 쌍을 읽는 <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> 메서드의 구현을 제공하고, 리플렉션을 사용하여 <xref:Microsoft.VisualStudio.Shell.DialogPage> 파생 클래스에서 public 속성을 검색합니다. 이름-값 쌍과 일치하는 이름을 가진 속성에 해당 값이 제공됩니다.  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A>의 기본 구현은 리플렉션을 사용하여 <xref:Microsoft.VisualStudio.Shell.DialogPage> 파생 클래스에서 public 속성을 검색하고, 속성 이름과 값을 이름-값 쌍으로 XML 피드에 기록합니다.  
  
### <a name="settings-category-registry-path"></a>설정 범주 레지스트리 경로  
 설정 범주의 레지스트리 경로는 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, 단어, UserSettings, 설정 범주, 사용자 지정 설정 지점의 이름을 결합하여 결정됩니다. 설정 범주 및 사용자 지정 설정 지점의 이름은 밑줄로 결합되고 분리되어 레지스트리에 나타나는, 지역화되지 않은 정식 이름을 구성합니다. 예를 들어 설정 범주가 "My Category", 사용자 지정 설정 지점 이름 "My Settings", ApplicationRegistryRoot HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp이면, 설정 범주의 레지스트리 키는 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\UserSettings\My Category_My Settings입니다.  
  
> [!NOTE]
> 정식 이름은 UI(사용자 인터페이스)에 나타나지 않습니다. 정식 이름은 읽을 수 있는 이름을 ProgID(프로그래밍 ID) 같은 설정 범주와 연결하는 데 사용됩니다.  
  
### <a name="settings-category-attribute"></a>설정 범주 특성  
 는 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 범주를 제공 하는 VSPackage와 범주를 연결 하 여 **설정 가져오기 및 내보내기 마법사** 에서 사용자 지정 설정 지점과 범주의 매핑을 결정 합니다. 다음과 같은 코드 조각을 생각해 봅시다.  
  
 [!code-csharp[VSSDKSupportForSettingsCategories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforsettingscategories/cs/vssdksupportforsettingscategoriespackage.cs#1)]
 [!code-vb[VSSDKSupportForSettingsCategories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforsettingscategories/vb/vssdksupportforsettingscategoriespackage.vb#1)]  
  
 리소스 ID 106은 "My Category", 107은 "My Settings", 108은 "Various Options"에 매핑됩니다. 이는 `MyPackage` 가 범주 Category_My Settings를 제공함을 선언합니다. 범주는 <xref:Microsoft.VisualStudio.Shell.IProfileManager>를 구현해야 하는 `OptionsPageGeneral` 클래스에 의해 제공됩니다. 해당 범주의 설정은 `OptionsPageGeneral` 클래스의 public 속성입니다.  
  
 **설정 가져오기 및 내보내기 마법사**에서 설정 지점의 이름은 My Settings입니다. 설정 지점을 선택하면 **Various Options**설명이 나타납니다. 설정 지점 이름 및 설명은 지역화된 문자열 리소스에서 가져옵니다.  
  
## <a name="see-also"></a>관련 항목  
 [옵션 페이지 만들기](../extensibility/creating-an-options-page.md)   
 [가 나 진한 샘플](../misc/vssdk-samples.md)   
 [VSPackage 상태](../misc/vspackage-state.md)   
 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)