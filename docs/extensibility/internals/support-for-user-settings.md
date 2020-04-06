---
title: 사용자 설정 지원 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704785"
---
# <a name="support-for-user-settings"></a>사용자 설정 지원
VSPackage는 사용자가 **도구** 메뉴에서 **가져오기/내보내기 설정** 명령을 선택할 때 지속되는 상태 변수 그룹인 하나 이상의 설정 범주를 정의할 수 있습니다. 이 지속성을 사용하려면 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]에서 설정 API를 사용합니다.

 사용자 지정 설정 지점 및 GUID라고 하는 레지스트리 항목은 VSPackage의 설정 범주를 정의합니다. VSPackage는 사용자 지정 설정 지점에 의해 정의된 여러 설정 범주를 지원할 수 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> 인터페이스를 사용하여 interop 어셈블리를 기반으로 하는 설정을 구현하려면 레지스트리를 편집하거나 등록자 스크립트(.rgs file)를 사용하여 사용자 지정 설정 지점을 만들어야 합니다. 자세한 내용은 [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts)을 참조하세요.

- MPF(관리되는 패키지 프레임워크)를 사용하는 코드는 각 사용자 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 지정 설정 지점에 대해 VSPackage에 를 연결하여 사용자 지정 설정 지점을 만들어야 합니다.

     단일 VSPackage가 여러 사용자 지정 설정 포인트를 지원하는 경우 각 사용자 지정 설정 지점은 별도의 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 클래스에 의해 구현되고 각 설정지점은 클래스의 고유한 인스턴스에 의해 등록됩니다. 따라서 클래스를 구현하는 설정은 두 개 이상의 설정 범주를 지원할 수 있습니다.

## <a name="custom-settings-point-registry-entry-details"></a>사용자 지정 설정 포인트 레지스트리 항목 세부 정보
 사용자 지정 설정 지점은 다음 위치의 레지스트리 항목에 만들어집니다: HKLM\Software\Microsoft\VisualStudio\\*\< * `<CSPName>` 버전>\UserSettings, 사용자 설정\\`<CSPName>` * \<* 지점의 이름은 VSPackage가 지원하는 이름이며 버전>[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]버전은 예를 들어 8.0입니다.

> [!NOTE]
> HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<버전>* 루트 경로를 IDE(통합 개발 환경)가 초기화될 때 대체 루트로 재정의할 수 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 자세한 내용은 [명령줄 스위치 를](../../extensibility/command-line-switches-visual-studio-sdk.md)참조하십시오.

 레지스트리 항목의 구조는 다음과 같습니다.

 HKLM\소프트웨어\마이크로소프트\비주얼\\스튜디오*\<버전>* \UserSettings\

 `<CSPName`>= '#12345'

 패키지 = '{XXXXXX 트리플엑스 트리플엑스XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX}'

 카테고리 = '{YYYYY YYYYYYYYYYYYYYYYYYYYYYYYYYYYYy}'

 리소스 패키지 = '{ZZZZ ZZZZ ZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZZ

 대체 부모 = 범주 이름

| 이름 | 형식 | 데이터 | 설명 |
|-----------------|--------| - | - |
| (기본값) | REG_SZ | 사용자 지정 설정 점의 이름 | 키의 이름인 `<CSPName`> 사용자 지정 설정 점의 지역화되지 않은 이름입니다.<br /><br /> MPF를 기반으로 하는 구현의 `categoryName` 경우 `objectName` <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 키 이름은 생성자의 인수와 를 에 `categoryName_objectName`결합하여 가져옵니다.<br /><br /> 키가 비어 있거나 위성 DLL의 지역화된 문자열에 대한 참조 ID를 포함할 수 있습니다. 이 값은 `objectNameResourceID` 인수에서 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 생성자로 가져옵니다. |
| 패키지 | REG_SZ | GUID | 사용자 지정 설정 지점을 구현하는 VSPackage의 GUID입니다.<br /><br /> 클래스를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> MPF를 기반으로 구현, `objectType` <xref:System.Type> VSPackage와 리플렉션을 포함 하는 생성자의 인수를 사용 하 여이 값을 가져옵니다. |
| Category | REG_SZ | GUID | 설정 범주를 식별하는 GUID입니다.<br /><br /> interop 어셈블리를 기반으로 하는 구현의 경우 이 값은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> IDE가 메서드에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> 전달하는 임의로 선택된 GUID일 수 있습니다. 이 두 메서드의 모든 구현은 GUID 인수를 확인해야 합니다.<br /><br /> MPF를 기반으로 하는 구현의 경우 이 <xref:System.Type> GUID는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 설정 메커니즘을 구현하는 클래스의 에서 가져옵니다. |
| 리소스 패키지 | REG_SZ | GUID | (선택 사항)<br /><br /> 구현 VSPackage가 문자열을 제공하지 않는 경우 지역화된 문자열을 포함하는 위성 DLL로의 경로입니다.<br /><br /> MPF는 리플렉션을 사용하여 올바른 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 리소스 VSPackage를 가져오므로 클래스에서 이 인수를 설정하지 않습니다. |
| 대체 부모 | REG_SZ | 이 사용자 지정 설정 점이 포함된 도구 옵션 페이지 아래의 폴더 이름입니다. | (선택 사항)<br /><br /> 설정 구현에서 상태를 저장하기 위해 **Tools Options** 자동화 모델의 메커니즘이 아닌 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 에서 지속성 메커니즘을 사용하는 도구 옵션 페이지를 지원하는 경우에만 이 값을 설정해야 합니다.<br /><br /> 이러한 경우 AlternateParent 키의 값은 `topic` 특정 `topic.sub-topic` **ToolsOptions** 페이지를 식별하는 데 사용되는 문자열의 섹션입니다. 예를 들어 **도구옵션** 페이지의 `"TextEditor.Basic"` 경우 대체 부모의 `"TextEditor"`값은 .가 됩니다.<br /><br /> 사용자 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 지정 설정 점을 생성하면 범주 이름과 동일합니다. |
