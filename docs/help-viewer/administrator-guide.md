---
title: 도움말 뷰어 관리자 가이드
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 037ee411c156d21145160dc95b40078fd841493c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825120"
---
# <a name="help-viewer-administrator-guide"></a>도움말 뷰어 관리자 가이드

도움말 뷰어에서는 인터넷에 액세스하거나 액세스하지 않고 네트워크 환경에 대한 로컬 도움말 설치를 관리할 수 있습니다. 로컬 도움말 콘텐츠는 컴퓨터별로 구성됩니다. 기본적으로 사용자가 로컬 도움말 설치를 업데이트하려면 관리자 권한을 갖고 있어야 합니다.

네트워크 환경에서 클라이언트가 인터넷에 액세스할 수 있는 경우 **도움말 콘텐츠 관리자** 실행 파일을 사용 하 여 인터넷에서 로컬 도움말 콘텐츠를 배포할 수 있습니다. *HlpCtntMgr.exe* 명령줄 구문에 대 한 자세한 내용은 [도움말 콘텐츠 관리자에 대 한 명령줄 인수](../help-viewer/command-line-arguments.md)를 참조 하세요.

콘텐츠 만들기, 인트라넷 서비스 엔드포인트 만들기 및 이와 유사한 종류의 작업에 대한 자세한 내용은 [도움말 뷰어 SDK](../extensibility/internals/microsoft-help-viewer-sdk.md)를 참조하세요.

네트워크 환경에서 클라이언트가 인터넷에 액세스할 수 없는 경우에는 도움말 뷰어를 통해 인트라넷 또는 네트워크 공유에서 로컬 도움말 콘텐츠를 배포할 수 있습니다. 또한 다음과 같은 기능에 대해 [레지스트리 키 재정의](../help-viewer/behavior-overrides.md)를 사용하여 Visual Studio IDE 도움말 옵션을 사용하지 않도록 설정할 수도 있습니다.

- 온라인과 오프라인 도움말

- IDE의 처음 시작 시 콘텐츠 설치

- 인트라넷 콘텐츠 서비스 지정

- 콘텐츠 관리

## <a name="deploy-local-help-content-from-the-internet"></a>인터넷에서 로컬 도움말 콘텐츠 배포

**도움말 콘텐츠 관리자**(*HlpCtntMgr.exe*)를 사용하여 인터넷에서 클라이언트 컴퓨터로 로컬 도움말 콘텐츠를 배포할 수 있습니다. 다음 구문을 사용합니다.

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

*HlpCtntMgr.exe* 명령줄 구문에 대 한 자세한 내용은 [도움말 콘텐츠 관리자에 대 한 명령줄 인수](../help-viewer/command-line-arguments.md)를 참조 하세요.

요구 사항:

- 클라이언트 컴퓨터가 인터넷에 액세스할 수 있어야 합니다.

- 사용자가 로컬 도움말 콘텐츠가 설치된 후 해당 콘텐츠를 업데이트, 추가 또는 설치하려면 관리자 권한을 갖고 있어야 합니다.

주의 사항:

- 도움말에 대한 기본 원본은 여전히 온라인입니다.

### <a name="example"></a>예

다음 예제에서는 클라이언트 컴퓨터에 Visual Studio에 대한 영어 콘텐츠를 설치합니다.

#### <a name="to-install-english-content-from-the-internet"></a>인터넷에서 영어 콘텐츠를 설치하려면

1. **시작**, **실행**을 차례로 선택합니다.

2. 다음과 같이 입력합니다.

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3. **Enter** 키를 누릅니다.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>클라이언트 컴퓨터에 사전 설치된 로컬 도움말 콘텐츠 배포

콘텐츠 집합을 온라인에서 한 컴퓨터에 설치한 다음 설치된 해당 콘텐츠 집합을 다른 컴퓨터에 복사할 수 있습니다.

요구 사항:

- 콘텐츠 집합을 설치하는 컴퓨터에서 인터넷에 액세스할 수 있어야 합니다.

- 사용자가 로컬 도움말 콘텐츠가 설치된 후 해당 콘텐츠를 업데이트, 추가 또는 설치하려면 관리자 권한을 갖고 있어야 합니다.

    > [!TIP]
    > 사용자에게 관리자 권한이 없는 경우 도움말 뷰어에서 **콘텐츠 관리** 탭을 사용하지 않도록 설정하는 것이 좋습니다. 자세한 내용은 [도움말 콘텐츠 관리자 재정의](../help-viewer/behavior-overrides.md)를 참조 하세요.

주의 사항:

- 도움말에 대한 기본 원본은 여전히 온라인입니다.

### <a name="create-the-content-set"></a>콘텐츠 집합 만들기

기본 콘텐츠 집합을 만들기 전에 먼저 대상 컴퓨터에서 모든 로컬 Visual Studio 콘텐츠를 제거해야 합니다.

#### <a name="to-uninstall-local-help"></a>로컬 도움말을 제거하려면

1. 도움말 뷰어에서 **콘텐츠 관리** 탭을 선택합니다.

2. Visual Studio 문서 집합으로 이동합니다.

3. 각 하위 항목 옆의 **제거**를 선택합니다.

4. **업데이트**를 선택하여 제거합니다.

5. *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* 으로 이동 하 여 폴더에 파일 *catalogType.xml*만 포함 되어 있는지 확인 합니다.

   이전에 설치한 로컬 Visual Studio 도움말 콘텐츠를 모두 제거하면 기본 콘텐츠 집합을 다운로드할 준비가 됩니다.

#### <a name="to-download-the-content"></a>콘텐츠를 다운로드하려면

1. 도움말 뷰어에서 **콘텐츠 관리** 탭을 선택합니다.

2. **권장 설명서** 또는 **사용 가능한 설명서** 아래에서 다운로드하려는 설명서 집합으로 이동한 다음 **추가**를 선택합니다.

3. **업데이트**를 선택합니다.

이제 클라이언트 컴퓨터에 배포할 수 있도록 콘텐츠를 패키지해야 합니다.

#### <a name="to-package-the-content"></a>콘텐츠를 패키지하려면

1. 나중에 배포하기 위해 콘텐츠를 복사할 폴더를 만듭니다. 예: *\myserver\vshelp*.

2. 관리자 권한으로 *cmd.exe*를 엽니다.

3. 1단계에서 만든 폴더로 이동합니다.

4. 다음과 같이 입력합니다.

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o`

     예: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>콘텐츠 배포

1. 네트워크 공유를 만들고 해당 위치에 도움말 콘텐츠를 복사합니다.

     예를 들어 *\myserver\vshelp* 의 콘텐츠를 * \\ \myserver\VSHelp*로 복사 합니다.

2. 도움말 콘텐츠에 대한 배포 스크립트를 포함할 *.bat* 파일을 만듭니다. 클라이언트에서 푸시의 일부로 삭제될 파일에 대한 읽기 잠금이 있을 수 있으므로 업데이트를 푸시하기 전에 클라이언트를 종료해야 합니다. 예를 들면 다음과 같습니다.

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3. 도움말 콘텐츠를 설치 하려는 로컬 컴퓨터에서 *.bat* 파일을 실행 합니다.

## <a name="see-also"></a>추가 정보

- [도움말 콘텐츠 관리자에 대 한 명령줄 인수](../help-viewer/command-line-arguments.md)
- [도움말 콘텐츠 관리자 재정의](../help-viewer/behavior-overrides.md)
- [Microsoft 도움말 뷰어](../help-viewer/overview.md)
- [도움말 뷰어 SDK](../extensibility/internals/microsoft-help-viewer-sdk.md)