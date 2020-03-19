---
title: Devenv 명령줄 스위치
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3ed82bd8ba3845541d7dce628f99fb78b62ab9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595711"
---
# <a name="devenv-command-line-switches"></a>Devenv 명령줄 스위치

Devenv를 사용하면 명령줄에서 IDE에 대한 다양한 옵션을 설정하고 프로젝트를 빌드, 디버그 및 배포할 수 있습니다. 이러한 스위치를 사용하여 스크립트 또는 .bat 파일(예: 야간 빌드 스크립트)에서 IDE를 실행하거나 특정 구성으로 IDE를 시작할 수 있습니다.

> [!NOTE]
> 빌드 관련 작업의 경우 devenv 대신 MSBuild를 사용하는 것이 좋습니다. 자세한 내용은 [MSBuild 명령줄 참조](../../msbuild/msbuild-command-line-reference.md)를 참조하세요.

VSPackage 개발과 관련된 스위치에 대한 자세한 내용은 [VSPackage 개발을 위한 Devenv 명령줄 스위치](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)를 참조하세요.

## <a name="devenv-switch-syntax"></a>Devenv 스위치 구문

`devenv`로 시작하는 명령은 `stdout` 및 `stderr`와 같은 표준 시스템 스트림을 통해 출력을 제공하는 `devenv.com` 유틸리티에서 처리됩니다. 유틸리티는 출력을 캡처할 때 적절한 I/O 리디렉션을 결정합니다(예: .txt 파일).

또는 `devenv.exe`로 시작하는 명령은 동일한 스위치를 사용할 수 있지만 `devenv.com` 유틸리티는 무시됩니다. `devenv.exe`를 직접 사용하면 콘솔에 출력이 표시되지 않도록 방지합니다.

`devenv` 스위치의 구문 규칙은 다른 DOS 명령줄 유틸리티의 규칙과 비슷합니다. 다음 구문 규칙은 모든 `devenv` 스위치 및 해당 인수에 적용됩니다.

- 명령이 `devenv`로 시작합니다.

- 스위치는 대/소문자를 구분하지 않습니다.

- 하이픈(“-”) 또는 슬래시(“/”)를 사용하여 스위치를 지정할 수 있습니다.

- 솔루션 또는 프로젝트를 지정하는 경우 첫 번째 인수는 파일 경로를 포함하여 솔루션 파일 또는 프로젝트 파일의 이름입니다.

- 첫 번째 인수가 솔루션 또는 프로젝트가 아닌 파일인 경우 해당 파일이 새 IDE 인스턴스의 적절한 편집기에서 열립니다.

- 솔루션 파일 이름 대신 프로젝트 파일 이름을 제공하는 경우 `devenv` 명령은 프로젝트 파일의 부모 폴더에서 이름이 같은 솔루션 파일을 검색합니다. 예를 들어 `devenv myproject1.vbproj /build` 명령은 부모 폴더에서 이름이 `myproject1.sln`인 솔루션 파일을 검색합니다.

  > [!NOTE]
  > 이 프로젝트를 참조하는 솔루션 파일 하나만 해당 부모 폴더에 있어야 합니다. 부모 폴더에 이 프로젝트를 참조하는 솔루션 파일이 없거나 두 개 이상 있는 경우 임시 솔루션 파일이 생성됩니다.

- 파일 경로 및 파일 이름에 공백이 포함된 경우 큰따옴표("")로 묶어야 합니다. 예: `"c:\project a\"`.

- 동일한 줄에 있는 스위치와 인수 사이에 공백 문자를 하나 삽입합니다. 예를 들어 `devenv /log output.txt` 명령은 IDE를 열고 해당 세션에 대한 모든 로그 정보를 output.txt에 출력합니다.

- `devenv` 명령에서는 패턴 일치 구문을 사용할 수 없습니다.

## <a name="devenv-switches"></a>Devenv 스위치

다음 명령줄 스위치는 IDE를 표시하고 설명된 작업을 수행합니다.

|명령줄 스위치|설명|
| - |-----------------|
|[/Command](command-devenv-exe.md)|IDE를 시작하고 지정한 명령을 실행합니다.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|디버거의 제어로 C++ 실행 파일을 로드합니다. 이 스위치는 Visual Basic 또는 C# 실행 파일에 제공되지 않습니다. 자세한 내용은 [디버거에서 자동으로 프로세스 시작](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger)을 참조하세요.<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|두 파일을 비교합니다. 네 개의 매개 변수를 사용합니다. *SourceFile*, *TargetFile*, *SourceDisplayName*(선택 사항) 및 *TargetDisplayName*(선택 사항).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|프로젝트를 로드하지 않고 지정된 솔루션을 엽니다.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|이 애플리케이션의 실행 중인 인스턴스에서 지정한 파일을 엽니다. 실행 중인 인스턴스가 없으면 간단한 창 레이아웃을 사용하여 새 인스턴스를 시작합니다.<br /><br /> `devenv /edit File1 File2`|
|[/LCID 또는 /L](lcid-devenv-exe.md)|IDE의 기본 언어를 설정합니다. 지정한 언어가 Visual Studio 설치에 포함되어 있지 않은 경우 이 설정은 무시됩니다.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Visual Studio를 시작하고 모든 작업을 로그 파일에 기록합니다.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|시작 화면을 표시하지 않고 IDE를 엽니다.<br /><br /> `devenv /nosplash File1 File2`|
|[/Run 또는 /R](run-devenv-exe.md)|지정한 솔루션을 컴파일하고 실행합니다.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|지정한 솔루션을 컴파일 및 실행하고, 솔루션 실행 시 IDE를 최소화하고, 솔루션 실행이 완료되면 IDE를 닫습니다.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Visual Studio를 안전 모드로 시작합니다. 이 스위치는 기본 환경, 기본 서비스 및 타사 패키지의 배송된 버전만 로드합니다.<br /><br /> 이 스위치는 인수가 필요 없습니다.|
|[/UseEnv](useenv-devenv-exe.md)|IDE가 C++ 컴파일을 위한 PATH, INCLUDE, LIBPATH 및 LIB 환경 변수를 사용하게 합니다. **C++ 워크로드로 데스크톱 개발**을 사용하여 이 스위치를 설치합니다. 자세한 내용은 [명령줄 빌드에서 경로 및 환경 변수 설정](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds)을 참조하세요.|

다음 명령줄 스위치는 IDE를 표시하지 않습니다.

|명령줄 스위치|설명|
| - |-----------------|
|[/?](q-devenv-exe.md)|**명령 프롬프트 창**에 `devenv` 스위치의 도움말을 표시합니다.<br /><br /> 이 스위치는 인수가 필요 없습니다.|
|[/Build](build-devenv-exe.md)|지정한 솔루션의 구성에 따라 지정한 솔루션 또는 프로젝트를 빌드합니다.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|소스 파일에 영향을 주지 않고 빌드 명령에 의해 생성된 파일을 삭제합니다.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|솔루션 구성에 따라 배포에 필요한 파일과 함께 솔루션을 빌드합니다.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|빌드 시 오류를 받을 파일을 지정할 수 있습니다.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|빌드, 정리 또는 배포할 프로젝트입니다. `/Build`, `/Rebuild`, `/Clean` 또는 `/Deploy` 스위치도 제공한 경우에만 이 스위치를 사용할 수 있습니다.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|빌드 또는 배포할 프로젝트 구성을 지정합니다. `/Project` 스위치도 제공한 경우에만 이 스위치를 사용할 수 있습니다.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|지정한 솔루션의 구성에 따라 지정한 솔루션 또는 프로젝트를 정리한 후 빌드합니다.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Visual Studio 기본 설정을 복원합니다. 필요에 따라 설정을 지정한 `.vssettings` 파일로 초기화합니다.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Upgrade](upgrade-devenv-exe.md)|지정한 솔루션 파일 및 모든 프로젝트 파일이나 지정한 프로젝트 파일을 이러한 파일의 현재 Visual Studio 형식으로 업그레이드합니다.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>참조

- [옵션 대화 상자, 환경, 일반](general-environment-options-dialog-box.md)
- [VSPackage 개발을 위한 Devenv 명령줄 스위치](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
