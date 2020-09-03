---
title: 사용자 설정 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704785"
---
# <a name="support-for-user-settings"></a>사용자 설정 지원
VSPackage는 사용자가 **도구** 메뉴에서 **가져오기/내보내기 설정** 명령을 선택할 때 유지 되는 상태 변수의 그룹인 하나 이상의 설정 범주를 정의할 수 있습니다. 이 지 속성을 사용 하려면의 설정 Api를 사용 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 합니다.

 사용자 지정 설정 지점 이라고 하는 레지스트리 항목 및 GUID는 VSPackage의 설정 범주를 정의 합니다. VSPackage는 각각 사용자 지정 설정 지점에서 정의 되는 여러 설정 범주를 지원할 수 있습니다.

- 인터페이스를 사용 하 여 interop 어셈블리를 기반으로 하는 설정의 구현은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 레지스트리를 편집 하거나 등록자 스크립트 (.rgs 파일)를 사용 하 여 사용자 지정 설정 지점을 만들어야 합니다. 자세한 내용은 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)을 참조하세요.

- MPF (관리 되는 패키지 프레임 워크)를 사용 하는 코드는를 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 각 사용자 지정 설정 지점에 대 한 VSPackage에 연결 하 여 사용자 지정 설정 지점을 만들어야 합니다.

     단일 VSPackage에서 여러 사용자 지정 설정 지점을 지 원하는 경우 각 사용자 지정 설정 지점은 별도의 클래스에 의해 구현 되며 각 지점은 클래스의 고유한 인스턴스에 의해 등록 됩니다 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . 따라서 클래스 구현 설정에서 둘 이상의 설정 범주를 지원할 수 있습니다.

## <a name="custom-settings-point-registry-entry-details"></a>사용자 지정 설정 지점 레지스트리 항목 세부 정보
 사용자 지정 설정 지점은 다음 위치의 레지스트리 항목에 생성 됩니다. HKLM\Software\Microsoft\VisualStudio \UserSettings. \\ *\<Version>* \\ `<CSPName>` 여기서 `<CSPName>` 는 VSPackage에서 지 원하는 사용자 지정 설정 지점의 이름이 고 *\<Version>* 버전 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (예: 8.0)입니다.

> [!NOTE]
> HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio의 루트 경로는 \\ *\<Version>* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (통합 개발 환경)가 초기화 될 때 대체 루트로 재정의할 수 있습니다. 자세한 내용은 [명령줄 스위치](../../extensibility/command-line-switches-visual-studio-sdk.md)를 참조 하세요.

 레지스트리 항목의 구조는 다음과 같습니다.

 HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \Usersettings\

 `<CSPName`>= s ' #12345 '

 Package = ' {XXXXXX XXXX xxxx XXXX XXXXXXXXX} '

 Category = ' {YYYYYY YYYY YYYY yyyy YYYYYYYYY} '

 ResourcePackage = ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ} '

 AlternateParent = 범주

| Name | 형식 | 데이터 | Description |
|-----------------|--------| - | - |
| (기본값) | REG_SZ | 사용자 지정 설정 지점의 이름입니다. | 키의 이름인>은 `<CSPName` 사용자 지정 설정 지점의 지역화 되지 않은 이름입니다.<br /><br /> MPF를 기반으로 하는 구현에서는 `categoryName` `objectName` 생성자의 및 인수를로 결합 하 여 키의 이름을 가져옵니다 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `categoryName_objectName` .<br /><br /> 키는 비어 있거나 위성 DLL의 지역화 된 문자열에 대 한 참조 ID를 포함할 수 있습니다. 이 값은 `objectNameResourceID` 생성자에 대 한 인수에서 가져옵니다 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . |
| 패키지 | REG_SZ | GUID | 사용자 지정 설정 지점을 구현 하는 VSPackage의 GUID입니다.<br /><br /> 클래스를 사용 하는 MPF를 기반으로 하는 구현 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 에서는 `objectType` VSPackage의 및 리플렉션을 포함 하는 생성자의 인수를 사용 <xref:System.Type> 하 여이 값을 가져옵니다. |
| 범주 | REG_SZ | GUID | 설정 범주를 식별 하는 GUID입니다.<br /><br /> Interop 어셈블리를 기반으로 하는 구현의 경우이 값은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에서 및 메서드에 전달 하는 임의로 선택 된 GUID 일 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> . 이러한 두 메서드의 모든 구현은 해당 GUID 인수를 확인 해야 합니다.<br /><br /> MPF 기반 구현에서이 GUID는 <xref:System.Type> 설정 메커니즘을 구현 하는 클래스의에서 가져옵니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . |
| ResourcePackage | REG_SZ | GUID | 선택 사항입니다.<br /><br /> 구현 하는 VSPackage에서 제공 하지 않는 경우 지역화 된 문자열이 포함 된 위성 DLL의 경로입니다.<br /><br /> MPF는 리플렉션을 사용 하 여 올바른 리소스 VSPackage를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> . 따라서 클래스는이 인수를 설정 하지 않습니다. |
| AlternateParent | REG_SZ | 이 사용자 지정 설정 지점을 포함 하는 도구 옵션 페이지 아래에 있는 폴더의 이름입니다. | 선택 사항입니다.<br /><br /> 상태를 저장 하기 위해 자동화 모델의 메커니즘이 아닌의 지 속성 메커니즘을 사용 하는 **도구 옵션** 페이지를 설정 구현에서 지 원하는 경우에만이 값을 설정 해야 합니다 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .<br /><br /> 이러한 경우 AlternateParent 키의 값은 `topic` `topic.sub-topic` 특정 **ToolsOptions** 페이지를 식별 하는 데 사용 되는 문자열의 섹션입니다. 예를 들어 **ToolsOptions** 페이지의 경우 `"TextEditor.Basic"` AlternateParent의 값은 `"TextEditor"` 입니다.<br /><br /> 에서 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 사용자 지정 설정 지점을 생성할 때 범주 이름과 동일 합니다. |
