---
title: '방법: 소스 제어 플러그 인 설치 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 997e734f6d2ab6bcf70e3a4843ac66564683c79b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843269"
---
# <a name="how-to-install-a-source-control-plug-in"></a>방법: 소스 제어 플러그 인 설치
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스 제어 플러그 인을 만들려면 다음 세 단계를 수행 해야 합니다.  
  
1. 이 설명서의 소스 제어 플러그 인 API 참조 섹션에서 정의한 함수를 사용 하 여 DLL을 만듭니다.  
  
2. 소스 제어 플러그 인 API 정의 함수를 구현 합니다. 에서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 호출 하는 경우 플러그 인에서 인터페이스 및 대화 상자를 사용할 수 있도록 설정 합니다.  
  
3. 적절 한 레지스트리 항목을 만들어 DLL을 등록 합니다.  
  
## <a name="integration-with-visual-studio"></a>Visual Studio와의 통합  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 소스 제어 플러그 인 API를 준수 하는 소스 제어 플러그 인을 지원 합니다.  
  
### <a name="registering-the-source-control-plug-in"></a>소스 제어 플러그 인 등록  
 실행 중인 IDE (통합 개발 환경)에서 소스 제어 시스템으로 호출할 수 있으려면 먼저 API를 내보내는 소스 제어 플러그 인 DLL을 찾아야 합니다.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>소스 제어 플러그 인 DLL을 등록 하려면  
  
1. 회사 이름 하위 키를 지정 하 고 product name 하위 키를 지정 하는 소프트웨어 하위 키의 HKEY_LOCAL_MACHINE 키 아래에 두 항목을 추가 합니다. 패턴은 HKEY_LOCAL_MACHINE \software \\ *[회사 이름]* \\ *[product name]* \\ *[entry]* = value입니다. 두 항목은 항상 SCCServerName 및 SCCServerPath 라고 합니다. 각은 일반 문자열입니다.  
  
     예를 들어 회사 이름이 Microsoft이 고 원본 제어 제품 이름이 SourceSafe 인 경우이 레지스트리 경로는 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe. 됩니다. 이 하위 키에서 첫 번째 항목인 SCCServerName은 제품 이름을 지정 하는 사용자가 읽을 수 있는 문자열입니다. 두 번째 항목인 SCCServerPath는 IDE를 연결 해야 하는 소스 제어 플러그 인 DLL의 전체 경로입니다. 다음은 샘플 레지스트리 항목을 제공 합니다.  
  
    |샘플 레지스트리 항목|샘플 값|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\SCCServerName|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\SCCServerPath|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    > SCCServerPath는 SourceSafe 플러그 인의 전체 경로입니다. 소스 제어 플러그 인은 서로 다른 회사 및 제품 이름을 사용 하지만 동일한 레지스트리 항목 경로를 사용 합니다.  
  
2. 다음 선택적 레지스트리 항목을 사용 하 여 소스 제어 플러그 인의 동작을 수정할 수 있습니다. 이러한 항목은 SccServerName 및 SccServerPath와 동일한 하위 키로 이동 합니다.  
  
    - HideInVisualStudioregistry 항목은의 플러그 인 선택 목록에 소스 제어-플러그 인을 표시 하지 않으려는 경우에 사용할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 이 항목은 원본 제어 플러그 인에 대 한 자동 전환에도 영향을 줍니다. 이 항목은 소스 제어 플러그 인을 대체 하는 소스 제어 패키지를 제공 하지만 사용자가 소스 제어 플러그 인을 사용 하 여 소스 제어 패키지에 쉽게 마이그레이션할 수 있게 하려는 경우에 한 가지 방법으로 사용할 수 있습니다. 원본 제어 패키지가 설치 되 면 플러그 인을 숨기는이 레지스트리 항목을 설정 합니다.  
  
         HideInVisualStudio는 DWORD 값 이며 플러그 인을 숨기 거 나 0으로 설정 하 여 플러그 인을 표시 합니다. 레지스트리 항목이 표시 되지 않으면 기본 동작은 플러그 인을 표시 하는 것입니다.  
  
    - DisableSccManager 레지스트리 항목은 일반적으로 **파일** ** \<Source Control Server> **  ->  **원본 제어** 하위 메뉴 아래에 표시 되는 시작 메뉴 옵션을 사용 하지 않도록 설정 하거나 숨기는 데 사용할 수 있습니다. 이 메뉴 옵션을 선택 하면 [SccRunScc](../../extensibility/sccrunscc-function.md) 함수가 호출 됩니다. 소스 제어 플러그 인은 외부 프로그램을 지원 하지 않으므로 **시작** 메뉴 옵션을 사용 하지 않도록 설정 하거나 숨길 수 있습니다.  
  
         DisableSccManager은 DWORD 값을 0으로 설정 하 여 **시작 \<Source Control Server> ** 메뉴 옵션을 사용 하도록 설정 하 고,를 1로 설정 하 여 메뉴 옵션을 사용 하지 않도록 설정 하 고,를 2로 설정 하 여 메뉴 옵션을 숨깁니다. 이 레지스트리 항목이 표시 되지 않는 경우 기본 동작은 메뉴 옵션을 표시 하는 것입니다.  
  
    |샘플 레지스트리 항목|샘플 값|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\HideInVisualStudio|1|  
    |HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\SourceSafe\DisableSccManager|1|  
  
3. 소프트웨어 하위 키의 HKEY_LOCAL_MACHINE 키 아래에 하위 키 인 SourceCodeControlProvider를 추가 합니다.  
  
     이 하위 키 아래에서 레지스트리 항목 ProviderRegKey는 1 단계에서 레지스트리에 배치한 하위 키를 나타내는 문자열로 설정 됩니다. 패턴은 HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider\providerregkey = SOFTWARE \\ *[회사 이름]* \\ *[product name]* 입니다.  
  
     다음은이 하위 키에 대 한 샘플 콘텐츠입니다.  
  
    |레지스트리 항목|샘플 값|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE \SOFTWARE\SourceCodeControlProvider\ProviderRegKey|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    > 소스 제어 플러그 인은 동일한 하위 키와 항목 이름을 사용 하지만 값은 다릅니다.  
  
4. SourceCodeControlProvider 하위 키 아래에 InstalledSCCProviders 라는 하위 키를 만들고 해당 하위 키 아래에 한 항목을 놓습니다.  
  
     이 항목의 이름은 사용자가 읽을 수 있는 공급자 이름 (SCCServerName 항목에 대해 지정 된 값과 동일)이 고 값은 1 단계에서 만든 하위 키입니다. 패턴은 HKEY_LOCAL_MACHINE \software\sourcecodecontrolprovider\installedsccproviders \\ *[표시 이름]* = 소프트웨어 \\ *[회사 이름]* \\ *[제품 이름]* 입니다.  
  
     예를 들면 다음과 같습니다.  
  
    |샘플 레지스트리 항목|샘플 값|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE \SOFTWARE\SourceCodeControlProvider\InstalledSCCProviders\Microsoft Visual SourceSafe|SOFTWARE\Microsoft\SourceSafe|  
  
    > [!NOTE]
    > 이러한 방식으로 여러 소스 제어 플러그 인을 등록할 수 있습니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에서 설치 된 모든 원본 제어 플러그 인 API 기반 플러그 인을 찾는 방법입니다.  
  
## <a name="how-an-ide-locates-the-dll"></a>IDE에서 DLL을 찾는 방법  
 IDE에는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 소스 제어 플러그 인 DLL을 검색 하는 두 가지 방법이 있습니다.  
  
- 기본 소스 제어 플러그 인을 찾아서 자동으로 연결 합니다.  
  
- 사용자가 하나를 선택 하는 등록 된 모든 원본 제어 플러그 인을 찾습니다.  
  
  첫 번째 방법으로 DLL을 찾기 위해 IDE는 ProviderRegKey 항목에 대 한 HKEY_LOCAL_MACHINE \Software\SourceCodeControlProvider 하위 키를 찾습니다. 이 항목의 값은 다른 하위 키를 가리킵니다. 그런 다음 IDE는 HKEY_LOCAL_MACHINE의 두 번째 하위 키에서 SccServerPath 라는 항목을 찾습니다. 이 항목의 값은 IDE를 DLL로 가리킵니다.  
  
> [!NOTE]
> IDE는 상대 경로에서 Dll을 로드 하지 않습니다 (예: .\NewProvider.DLL). DLL에 대 한 전체 경로를 지정 해야 합니다 (예: c:\Providers\NewProvider.DLL). 이렇게 하면 무단 또는 가장 된 플러그 인 Dll을 로드 하지 못하게 하 여 IDE의 보안을 강화할 수 있습니다.  
  
 두 번째 방법으로 DLL을 찾기 위해 IDE는 HKEY_LOCAL_MACHINE \Software\SourceCodeControlProvider\InstalledSCCProviders 하위 키 아래에서 모든 항목을 찾습니다<em>.</em> 각 항목에는 이름과 값이 있습니다. IDE는 사용자에 게 이러한 이름 목록을 표시 합니다<em>.</em> 사용자가 이름을 선택 하면 IDE에서 하위 키를 가리키는 선택 된 이름에 대 한 값을 찾습니다. IDE는 HKEY_LOCAL_MACHINE의 해당 하위 키에서 SccServerPath 라는 항목을 찾습니다. 해당 항목의 값은 IDE를 올바른 DLL로 가리킵니다.  
  
 소스 제어 플러그 인은 두 가지 방법을 모두 지원 해야 하며, 그에 따라 ProviderRegKey를 설정 하 여 이전 설정을 덮어씁니다. 무엇 보다도, 사용자가 사용할 소스 제어 플러그 인을 선택할 수 있도록 InstalledSccProviders 목록에 자신을 추가 해야 합니다.  
  
> [!NOTE]
> HKEY_LOCAL_MACHINE 키를 사용 하기 때문에 지정 된 컴퓨터에서 소스 제어 플러그 인 중 하나만 기본 소스 제어 플러그 인으로 등록할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 그러나 사용자는 특정 솔루션에 실제로 사용 하려는 소스 제어 플러그 인을 확인할 수 있습니다. 설치 과정에서 원본 제어 플러그 인이 이미 설정 되어 있는지 확인 합니다. 그렇다면 새 원본 제어 플러그 인을 기본값으로 설정할지 여부를 사용자에 게 요청 합니다. 설치를 취소 하는 동안 HKEY_LOCAL_MACHINE \SOFTWARE\SourceCodeControlProvider의 모든 원본 제어 플러그 인에 공통적인 다른 레지스트리 하위 키를 제거 하지 마십시오. 특정 SCC 하위 키만 제거 합니다.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>IDE에서 버전 1.2/1.3 지원을 검색 하는 방법  
 에서 플러그 인이 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 소스 제어 플러그 인 API 버전 1.2 및 1.3 기능을 지원 하는지 여부를 검색 하는 방법 고급 기능을 선언 하려면 소스 제어 플러그 인에서 해당 함수를 구현 해야 합니다.  
  
 먼저 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [Sccgetversion](../../extensibility/sccgetversion-function.md)를 호출 하 여 반환 된 값을 확인 합니다. 1.2 보다 크거나 같아야 합니다.  
  
 그런 다음 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] `lpSccCaps` [sccinitialize](../../extensibility/sccinitialize-function.md)에서 인수를 검사 하 여 특정 새 기능이 지원 되는지 여부를 결정 합니다.  
  
 이러한 두 조건이 모두 충족 되 면 버전 1.2 및 1.3에서 지원 되는 새 함수를 호출할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [시작](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
