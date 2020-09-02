---
title: 도움말 뷰어 관리자 가이드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 03cacd8de574de92002b44b237cd84c22e761eaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645570"
---
# <a name="help-viewer-administrator-guide"></a>도움말 뷰어 관리자 가이드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도움말 뷰어에서는 인터넷에 액세스하거나 액세스하지 않고 네트워크 환경에 대한 로컬 도움말 설치를 관리할 수 있습니다. 로컬 도움말 콘텐츠는 컴퓨터별로 구성됩니다. 기본적으로 사용자가 로컬 도움말 설치를 업데이트하려면 관리자 권한을 갖고 있어야 합니다.

 네트워크 환경에서 클라이언트가 인터넷에 액세스할 수 있는 경우 도움말 뷰어를 통해 명령줄 스크립트를 사용하여 인터넷에서 로컬 도움말 콘텐츠를 배포할 수 있습니다.

 네트워크 환경에서 클라이언트가 인터넷에 액세스할 수 없는 경우에는 도움말 뷰어를 통해 인트라넷 또는 네트워크 공유에서 로컬 도움말 콘텐츠를 배포할 수 있습니다. 또한 온라인/오프라인 도움말, 처음 IDE 시작 시 콘텐츠 설치, 인트라넷 콘텐츠 서비스 지정, 콘텐츠 관리, 레지스트리 키 재정의 사용 등의 Visual Studio IDE 도움말 옵션을 사용하지 않도록 설정할 수도 있습니다.

 기본 구문은 다음과 같습니다.

 \<*path to*>\HlpCtntmgr.exe/작업 \<*argument*> /catalogname \<*name*> \<*locale*> /sourceuri \<*.msha path or URL*>

 HlpCtntMgr.exe 명령줄 구문에 대한 자세한 내용은 [도움말 콘텐츠 관리자 명령줄 인수](../ide/command-line-arguments-for-the-help-content-manager.md)를 참조하세요.

 콘텐츠 만들기, 인트라넷 서비스 엔드포인트 만들기 및 이와 유사한 종류의 작업에 대한 자세한 내용은 도움말 뷰어 SDK를 참조하세요.

## <a name="deploying-local-help-content-from-the-internet"></a>인터넷에서 로컬 도움말 콘텐츠 배포
 MSDN 콘텐츠 패키지 서비스를 사용하여 인터넷에서 클라이언트 컴퓨터로 로컬 도움말 콘텐츠를 배포할 수 있습니다. 다음 구문을 사용합니다.

 \\<*path to* # C0\v2.2\HlpCtntmgr.exe/작업 \<*name*> /catalogname \<*catalog name*> /로캘의 경로\<*locale*>

 HlpCtntMgr.exe 명령줄 구문에 대한 자세한 내용은 [도움말 콘텐츠 관리자 명령줄 인수](../ide/command-line-arguments-for-the-help-content-manager.md)를 참조하세요.

 요구 사항:

- 클라이언트 컴퓨터가 인터넷에 액세스할 수 있어야 합니다.

- 사용자가 로컬 도움말 콘텐츠가 설치된 후 해당 콘텐츠를 업데이트, 추가 또는 설치하려면 관리자 권한을 갖고 있어야 합니다.

  주의 사항:

- 도움말에 대한 기본 원본은 여전히 온라인입니다.

  > [!TIP]
  > HKEY_LOCAL_MACHINE\SoftwareHKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp 레지스트리 키를 수정하여 도움말에 대한 기본 원본을 변경할 수 있습니다. 자세한 내용은 [도움말 콘텐츠 관리자 재정의](../ide/help-content-manager-overrides.md)를 참조하세요.

- 클라이언트에서 Visual Studio를 처음 시작할 때 기본 도움말 콘텐츠를 설치하라는 메시지가 계속 표시됩니다. HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection 레지스트리 키를 수정하여 이 메시지가 표시되지 않도록 설정할 수 있습니다.

### <a name="example"></a>예
 다음 예제에서는 클라이언트 컴퓨터에 Visual Studio에 대한 영어 콘텐츠를 설치합니다.

##### <a name="to-install-english-content-from-the-internet"></a>인터넷에서 영어 콘텐츠를 설치하려면

1. **시작**, **실행**을 차례로 선택합니다.

2. 다음과 같이 입력합니다.

     C:\Program Files (x86)\Microsoft Help Viewer\v2.2\hlpctntmgr.exe /operation install /catalogname VisualStudio14 /locale en-us

3. Enter 키를 누릅니다.

## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>클라이언트 컴퓨터에 사전 설치된 로컬 도움말 콘텐츠 배포
 콘텐츠 집합을 온라인에서 한 컴퓨터에 설치한 다음 설치된 해당 콘텐츠 집합을 다른 컴퓨터에 복사할 수 있습니다.

 요구 사항:

- 콘텐츠 집합을 설치하는 컴퓨터에서 인터넷에 액세스할 수 있어야 합니다.

- 사용자가 로컬 도움말 콘텐츠가 설치된 후 해당 콘텐츠를 업데이트, 추가 또는 설치하려면 관리자 권한을 갖고 있어야 합니다.

  > [!TIP]
  > 사용자에게 관리자 권한이 없는 경우 도움말 뷰어에서 콘텐츠 관리 탭을 사용하지 않도록 설정하는 것이 좋습니다. 자세한 내용은 [도움말 콘텐츠 관리자 재정의](../ide/help-content-manager-overrides.md)를 참조하세요.

  주의 사항:

- 사용자에게 관리자 권한이 없는 경우 도움말 뷰어에서 콘텐츠 관리 탭을 사용하지 않도록 설정하는 것이 좋습니다. 자세한 내용은 [도움말 콘텐츠 관리자 재정의](../ide/help-content-manager-overrides.md)를 참조하세요.

- 도움말에 대한 기본 원본은 여전히 온라인입니다.

- 클라이언트에서 Visual Studio를 처음 시작할 때 기본 도움말 콘텐츠를 설치하라는 메시지가 계속 표시됩니다. 자세한 내용은 [도움말 콘텐츠 관리자 재정의](../ide/help-content-manager-overrides.md)를 참조하세요.

### <a name="create-the-content-set"></a>콘텐츠 집합 만들기
 기본 콘텐츠 집합을 만들기 전에 먼저 대상 컴퓨터에서 모든 로컬 Visual Studio 콘텐츠를 제거해야 합니다.

##### <a name="to-uninstall-local-help"></a>로컬 도움말을 제거하려면

1. 도움말 뷰어에서 **콘텐츠 관리** 탭을 선택합니다.

2. **사용 가능한 설명서** 아래에서 Visual Studio 문서 집합으로 이동합니다.

3. 각 하위 항목 옆의 **제거**를 선택합니다.

4. **시작**을 선택하여 제거합니다.

5. *n*:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12로 이동하고 이 폴더에 catalogType.xml 파일만 포함되어 있는지 확인합니다.

   이전에 설치한 로컬 Visual Studio 도움말 콘텐츠를 모두 제거하면 기본 콘텐츠 집합을 다운로드할 준비가 됩니다.

##### <a name="to-download-the-content"></a>콘텐츠를 다운로드하려면

1. 도움말 뷰어에서 **콘텐츠 관리** 탭을 선택합니다.

2. **사용 가능한 설명서** 아래에서 다운로드하려는 설명서 집합으로 이동한 다음, **추가**를 선택합니다.

3. **시작**을 선택합니다.

   이제 클라이언트 컴퓨터에 배포할 수 있도록 콘텐츠를 패키지해야 합니다.

##### <a name="to-package-the-content"></a>콘텐츠를 패키지하려면

1. 나중에 배포하기 위해 콘텐츠를 복사할 폴더를 만듭니다.

     예를 들어 c:\VS12Help 폴더를 만들 수 있습니다.

2. 관리자 권한으로 cmd.exe를 엽니다.

3. 1단계에서 만든 폴더로 이동합니다.

4. 다음과 같이 입력합니다.

     Xcopy%SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \<*foldername*> \/y/e/k/o

     예: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`

### <a name="deploying-the-content"></a>콘텐츠 배포

##### <a name="to-deploy-the-content"></a>콘텐츠를 배포하려면

1. 네트워크 공유를 만들고 해당 위치에 도움말 콘텐츠를 복사합니다.

     예를 들어 c:\VS12Help의 콘텐츠를 \\\myserver\VS12Help에 복사합니다.

2. 도움말 콘텐츠에 대한 배포 스크립트를 포함할 .bat 파일을 만듭니다. 클라이언트에서 푸시의 일부로 삭제될 파일에 대한 읽기 잠금이 있을 수 있으므로 업데이트를 푸시하기 전에 클라이언트를 종료해야 합니다.

     예를 들면 다음과 같습니다.

    ```
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)

    REM - get processor type and create/run registry update file
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64

    @echo Architecture type is x86

    ECHO Windows Registry Editor Version 5.00 > x86.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg
    ECHO "FirstTimeRun"="False"  >> x86.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg

    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg

    regedit.exe /s x86.reg
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)

    GOTO CONTINUE

    :AMD64
    @echo Architecture type is AMD64

    ECHO Windows Registry Editor Version 5.00 > x64.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg
    ECHO "FirstTimeRun"="False"  >> x64.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg

    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg

    regedit.exe /s x64.reg
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)

    :CONTINUE
    ```

3. 도움말 콘텐츠가 설치될 로컬 컴퓨터에서 bat 파일을 실행합니다.

## <a name="see-also"></a>관련 항목
 [도움말 콘텐츠 관리자](../ide/command-line-arguments-for-the-help-content-manager.md) [도움말 내용 관리자에서 재정의할](../ide/help-content-manager-overrides.md) 수 있는 명령줄 인수
