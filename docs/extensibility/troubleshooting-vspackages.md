---
title: Vspackage 문제 해결 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a231d8d02ce7432188053293684d09c7243dfd5e
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506403"
---
# <a name="troubleshooting-vspackages"></a>VSPackage 문제 해결
다음은 문제를 해결 하기 위한 VSPackage 및 팁과 함께 발생할 수 있는 일반적인 문제입니다.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Visual Studio가 시작 되지 않도록 하는 VSPackage 문제를 해결 하려면

- 안전 모드에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]를 시작 합니다.

   안전 모드에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]를 시작 하려면 명령 프롬프트에서 **devenv.exe/안전**모드를 입력 합니다.

   이 프로세스 동안 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 포함 된 Vspackage를 제외 하 고 Vspackage가 로드 되지 않습니다.

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>로드 되지 않는 VSPackage 문제를 해결 하려면

1. VSPackage가 실행 되도록 등록 된 레지스트리 루트 (일반적으로 실험적 레지스트리 루트)를 사용 하 고 있는지 확인 합니다.

    자세한 내용은 [실험적 인스턴스](../extensibility/the-experimental-instance.md)를 참조 하세요.

2. VSPackage이 실험적 레지스트리 루트에서 실행 되도록 지정 된 경우 실험 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]를 실행 하 고 있는지 확인 합니다.

    실험적 버전을 실행 하려면 명령 창에서 **devenv/rootsuffix exp**를 입력 합니다.

3. VSPackage 레지스트리 항목을 확인 합니다.

    자세한 내용은 [Vspackage 등록](registering-and-unregistering-vspackages.md) 및 [vspackage 관리](../extensibility/managing-vspackages.md)를 참조 하세요.

4. VSPackage를 로드 하지 못한 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 인스턴스의 **출력** 창을 엽니다. VSPackage를 로드 하지 못하는 이유에 대 한 정보는 해당 창에 표시 될 수 있습니다.

   > [!NOTE]
   > [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE (통합 개발 환경)에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 실험 버전을 시작 하는 경우 두 버전의 **출력** 창을 검사 합니다.

5. 활동 로그를 검사 합니다.

    자세한 내용은 [방법: 활동 로그 사용](../extensibility/how-to-use-the-activity-log.md)을 참조 하세요.

6. IDE에서 throw 되는 예외에 대 한 자세한 내용을 보려면 **디버그** 메뉴에서 **예외** 를 클릭 하 여 예외를 사용 하도록 설정 합니다. **예외** 대화 상자에서 자세한 정보를 보려는 예외 유형을 선택 합니다.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>등록 되지 않은 VSPackage 문제를 해결 하려면

1. VSPackage 어셈블리가 신뢰할 수 있는 위치에 있어야 합니다. RegPkg는 기본 .net 보안 구성의 네트워크 공유와 같은 신뢰할 수 없거나 부분적으로 신뢰할 수 있는 위치에 어셈블리를 등록할 수 없습니다. 사용자가 신뢰할 수 없는 위치에서 프로젝트를 만들 때마다 경고가 표시 되기는 하지만 "이 메시지를 다시 표시 안 함" 확인란을 선택 하면이 경고가 되풀이 되지 않을 수 있습니다.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>표시 되지 않거나 명령을 클릭할 때 오류를 생성 하는 명령 문제를 해결 하려면

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 명령 프롬프트에서 다음을 입력 하 여 새 또는 변경 된 메뉴 명령과 IDE에 이미 있는 메뉴 명령을 병합 합니다. **devenv/rootsuffix Exp/setup**.

2. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 VSPackage에 대 한 UI .dll을 찾을 수 있는지 확인 합니다.

   1. 레지스트리의 패키지 섹션에서 VSPackage의 CLSID를 찾습니다.

        HKLM\Software\Microsoft\Visual Studio\\ *\<버전 >* \packages

   2. SatelliteDll 하위 키에 지정 된 경로가 올바른지 확인 합니다.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>예기치 않게 동작 하는 VSPackage 문제를 해결 하려면

1. 코드에 중단점을 설정합니다.

     디버깅을 위한 좋은 출발점은 생성자 및 초기화 메서드입니다. 메뉴 명령과 같이 평가할 영역에 중단점을 설정할 수도 있습니다. 중단점을 사용 하도록 설정 하려면 디버거에서를 실행 해야 합니다.

    1. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

    2. **속성 페이지** 대화 상자에서 **디버그** 탭을 선택 합니다.

    3. **명령줄 인수** 상자에 VSPackage가 대상으로 하는 개발 환경의 루트 접미사를 입력 합니다. 예를 들어 실험적 빌드를 선택 하려면 **/Rootsuffix Exp**를 입력 합니다.

    4. **디버그** 메뉴에서 **디버깅 시작** 을 클릭 하거나 f5 키를 누릅니다.

        > [!NOTE]
        > 프로젝트를 디버깅 하는 경우 프로젝트의 기존 인스턴스를 지금 만들거나 로드 합니다.

2. 활동 로그를 사용 합니다.

     키 지점에서 활동 로그에 정보를 기록 하 여 VSPackage 동작을 추적 합니다. 이 기법은 특히 소매 환경에서 VSPackage를 실행 하는 경우에 유용 합니다. 자세한 내용은 [방법: 활동 로그 사용](../extensibility/how-to-use-the-activity-log.md)을 참조 하세요.

3. 공용 기호를 사용 합니다.

     디버깅 하는 동안 가독성을 높이려면 디버거에 기호를 연결 하면 됩니다.

    1. **도구/옵션** 메뉴에서 **디버깅/기호** 대화 상자로 이동 합니다.

    2. 이 **기호 파일 (.pdb) 위치**를 추가 합니다.

         `https://msdl.microsoft.com/download/symbols`

    3. 성능을 향상 시키려면 기호 캐시 폴더를 지정 합니다. 예를 들면 다음과 같습니다.

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>누락 된 VSPackage 또는 해당 종속성 중 하나에 대 한 문제를 해결 하려면

1. 관리 코드의 경우 참조 경로가 올바른지 확인 합니다.

   1. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

   2. **속성 페이지** 대화 상자에서 **참조** 탭을 선택 하 고 모든 경로가 올바른지 확인 합니다. 또는 **개체 브라우저** 를 사용 하 여 참조 된 개체를 찾을 수 있습니다.

        관리 코드의 경우 [fuslogvw.exe (어셈블리 바인딩 로그 뷰어)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) 를 사용 하 여 실패 한 어셈블리 로드에 대 한 세부 정보를 표시할 수 있습니다.

2. 비관리 코드의 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CLSID 레지스트리 노드에서 VSPackage의 CLSID를 찾습니다.

    HKLM\Software\Microsoft\Visual Studio\\ *\<버전 >* \clsid

   InprocServer32 항목에 VSPackage dll의 올바른 경로가 있는지 확인 합니다.

## <a name="see-also"></a>참고 항목
- [VSPackage](../extensibility/internals/vspackages.md)