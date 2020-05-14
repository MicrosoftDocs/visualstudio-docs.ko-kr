---
title: 문제 해결 VS패키지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698924"
---
# <a name="troubleshooting-vspackages"></a>VSPackage 문제 해결
다음은 VSPackage와 함께 발생할 수 있는 일반적인 문제와 문제를 해결하기 위한 팁입니다.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Visual Studio를 시작하지 못하게 하는 VS패키지 문제 해결

- 안전 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 모드에서 시작합니다.

   안전 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 모드에서 시작하려면 명령 프롬프트에서 **devenv.exe /safemode를**입력합니다.

   이 프로세스 중에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 포함된 VSPackage를 제외한 VS패키지가 로드되지 않습니다.

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>로드되지 않는 VS패키지 문제 해결

1. VSPackage가 실행되도록 등록된 레지스트리 루트(일반적으로 실험적 레지스트리 루트)를 사용하고 있는지 확인합니다.

    자세한 내용은 [실험 인스턴스 를](../extensibility/the-experimental-instance.md)참조하십시오.

2. VSPackage가 실험 레지스트리 루트에서 실행되도록 타겟팅된 경우 실험 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]을 실행하고 있는지 확인합니다.

    실험 버전을 실행하려면 명령 창에 다음을 **devenv /rootsuffix exp**입력합니다.

3. VSPackage 레지스트리 항목을 확인합니다.

    자세한 내용은 [VS패키지 등록](registering-and-unregistering-vspackages.md) 및 [VSPackage 관리를](../extensibility/managing-vspackages.md)참조하십시오.

4. VSPackage를 로드하지 못하는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 인스턴스의 **출력** 창을 엽니다. VSPackage를 로드하지 못하는 이유에 대한 정보가 해당 창에 표시될 수 있습니다.

   > [!NOTE]
   > 통합 개발 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 환경(IDE)에서 실험 버전을 시작하는 경우 두 버전의 출력 창을 검사합니다. **Output** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

5. 활동 로그를 검사합니다.

    자세한 내용은 [사용 방법: 활동 로그를 사용](../extensibility/how-to-use-the-activity-log.md)하 여 참조 하십시오.

6. IDE에서 throw된 예외에 대한 자세한 내용을 보려면 **디버그** 메뉴에서 **예외를** 클릭하여 예외를 활성화합니다. **예외** 대화 상자에서 자세한 정보를 원하는 예외 유형을 선택합니다.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>등록하지 않은 VSPackage 문제를 해결하려면

1. VSPackage 어셈블리가 신뢰할 수 있는 위치에 있는지 확인합니다. RegPkg은 기본 .net 보안 구성의 네트워크 공유와 같이 신뢰할 수 없거나 부분적으로 신뢰할 수 있는 위치에 어셈블리를 등록할 수 없습니다. 사용자가 신뢰할 수 없는 위치에 프로젝트를 만들 때마다 경고가 나타나지만 "이 메시지를 다시 표시하지 않음" 확인란을 사용하면 이 경고가 다시 발생하지 않을 수 있습니다.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>보이지 않거나 명령을 클릭할 때 오류를 생성하는 명령을 트러블슈팅하려면

1. 명령 프롬프트에서 다음을 입력하여 새 메뉴 명령이나 변경된 메뉴 명령 및 IDE에 이미 있는 명령어를 병합합니다. **devenv /rootsuffix Exp /setup** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

2. VSPackage에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 대한 UI.dll을 찾을 수 있는지 확인합니다.

   1. 레지스트리의 패키지 섹션에서 VS패키지의 CLSID를 찾습니다.

        HKLM\소프트웨어\마이크로소프트\비주얼\\스튜디오*\<버전>* \패키지

   2. SatelliteDll 하위 키에서 제공한 경로가 올바른지 확인합니다.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>예기치 않게 비할 데 없는 VSPackage 문제를 해결하려면

1. 코드에 중단점을 설정합니다.

     디버깅을 위한 좋은 출발점은 생성자와 초기화 방법입니다. 메뉴 명령과 같이 평가하려는 영역에 중단점을 설정할 수도 있습니다. 중단점을 사용하려면 디버거에서 실행해야 합니다.

    1. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

    2. 속성 **페이지** 대화 상자에서 **디버그** 탭을 선택합니다.

    3. **명령줄 인수** 상자에서 VSPackage가 대상으로 하는 개발 환경의 루트 접미사를 입력합니다. 예를 들어 실험 빌드를 선택하려면 **입력합니다.**

    4. **디버그** 메뉴에서 **디버깅 시작을** 클릭하거나 F5를 누릅니다.

        > [!NOTE]
        > 프로젝트를 디버깅하는 경우 지금 프로젝트의 기존 인스턴스를 만들거나 로드합니다.

2. 활동 로그를 사용합니다.

     VSPackage 동작을 추적하여 키 포인트의 활동 로그에 정보를 작성합니다. 이 기술은 소매 환경에서 VSPackage를 실행할 때 특히 유용합니다. 자세한 내용은 [사용 방법: 활동 로그를 사용](../extensibility/how-to-use-the-activity-log.md)하 여 참조 하십시오.

3. 공용 기호를 사용합니다.

     디버깅 하는 동안 가독성을 향상 시키기 위해 디버거에 기호를 연결할 수 있습니다.

    1. **도구/옵션** 메뉴에서 **디버깅/기호** 대화 상자로 이동합니다.

    2. 이 **기호 파일 (.pdb) 위치**추가 :

         `https://msdl.microsoft.com/download/symbols`

    3. 성능을 향상시키기 위해 다음과 같은 기호 캐시 폴더를 지정합니다.

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>누락된 VSPackage 또는 해당 종속성 중 하나를 해결하려면

1. 관리 코드의 경우 참조 경로가 올바른지 확인합니다.

   1. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

   2. **속성 페이지** 대화 상자에서 **참조** 탭을 선택하고 모든 경로가 올바른지 확인합니다. 또는 **개체 브라우저를** 사용하여 참조된 개체를 찾아볼 수 있습니다.

        관리 코드의 경우 [Fuslogvw.exe(어셈블리 바인딩 로그 뷰어)를](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) 사용하여 실패한 어셈블리 로드의 세부 정보를 표시할 수 있습니다.

2. 관리되지 않는 코드의 경우 CLSID 레지스트리 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 노드에서 VSPackage의 CLSID를 찾습니다.

    HKLM\소프트웨어\마이크로소프트\비주얼\\스튜디오*\<버전>* \CLSID

   InprocServer32 항목에 VSPackage dll의 올바른 경로가 있는지 확인합니다.

## <a name="see-also"></a>참조
- [VSPackage](../extensibility/internals/vspackages.md)
