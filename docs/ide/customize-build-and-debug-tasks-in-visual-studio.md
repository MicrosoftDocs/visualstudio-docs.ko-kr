---
title: tasks.vs.json launch.vs.json을 사용하여 빌드 디버그 작업 사용자 지정
ms.date: 02/21/2018
ms.topic: conceptual
helpviewer_keywords:
- NMAKE [Visual Studio]
- makefiles [Visual Studio]
- customize codebases [Visual Studio]
- tasks.vs.json file [Visual Studio]
- launch.vs.json file [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e912459f45086b1bf5f96a9458f006354e982ffd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76542687"
---
# <a name="customize-build-and-debug-tasks-for-open-folder-development"></a>“폴더 열기” 개발에 대한 빌드 및 디버그 작업 사용자 지정

Visual Studio는 여러 다른 언어 및 코드베이스를 실행하는 방법을 알고 있지만, 모든 것을 실행하는 방법은 알고 있지 않습니다. Visual Studio에서 [코드 폴더를 열었고](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Visual Studio에서 코드 실행 방법을 아는 경우에는 아무런 추가 구성 없이 바로 코드를 실행할 수 있습니다.

코드베이스가 Visual Studio에서 인식하지 못하는 사용자 지정 빌드 도구를 사용하는 경우 Visual Studio에서 코드를 실행하고 디버그하려면 몇 가지 구성 세부 정보를 제공해야 할 수 있습니다. *빌드 작업*을 정의하여 코드 빌드 방법을 Visual Studio에 알립니다. 코드를 빌드하고 실행할 수 있도록 언어에 필요한 모든 항목을 지정하는 하나 이상의 빌드 작업을 만들 수 있습니다. 또한 원하는 거의 모든 작업을 수행할 수 있는 임의의 작업을 만들 수도 있습니다. 예를 들어 폴더의 내용을 나열하거나 파일의 이름을 바꾸는 작업을 만들 수 있습니다.

다음 *.json* 파일을 사용하여 프로젝트 없는 코드베이스를 사용자 지정합니다.

|파일 이름|목적|
|-|-|
|*tasks.vs.json*|사용자 지정 빌드 명령 및 컴파일러 스위치와 임의(빌드와 관련되지 않은) 작업을 지정합니다.<br>**솔루션 탐색기**의 오른쪽 클릭 메뉴 항목 **작업 구성**을 통해 액세스합니다.|
|*launch.vs.json*|디버깅을 위한 명령줄 인수를 지정합니다.<br>**솔루션 탐색기**의 오른쪽 클릭 메뉴 항목 **디버그 및 시작 설정**을 통해 액세스합니다.|

이러한 *.json* 파일은 코드베이스의 루트 폴더에 있는 *.vs*라는 숨겨진 폴더에 있습니다. **솔루션 탐색기**에서 파일이나 폴더에 대한 **작업 구성** 또는 **디버그 및 시작 설정**을 선택하면 Visual Studio에서 *tasks.vs.json* 및 *launch.vs.json* 파일이 필요에 따라 만들어집니다. 사용자는 일반적으로 이러한 *.json* 파일을 소스 제어로 체크 인하지 않으므로 파일이 숨겨져 있습니다. 그러나 소스 제어로 체크 인할 수 있도록 파일을 코드베이스의 루트로 끌어서 놓으면 파일이 표시됩니다.

> [!TIP]
> Visual Studio에서 숨겨진 파일을 보려면 **솔루션 탐색기** 도구 모음에서 **모든 파일 표시** 단추를 선택합니다.

## <a name="define-tasks-with-tasksvsjson"></a>tasks.vs.json으로 작업 정의

현재 작업 영역에 있는 파일에 대한 빌드 스크립트 또는 기타 외부 작업을 IDE에서 직접 작업으로 실행하여 자동화할 수 있습니다. 파일 또는 폴더를 마우스 오른쪽 단추로 클릭하고 **작업 구성**을 선택하여 새 작업을 구성할 수 있습니다.

![작업 구성 메뉴](../ide/media/customize-configure-tasks-menu.png)

이 명령은 *.vs* 폴더에서 *tasks.vs.json* 파일을 만들거나 엽니다. 이 파일에서 빌드 작업 또는 임의 작업을 정의한 다음, **솔루션 탐색기**의 오른쪽 클릭 메뉴에서 지정한 이름을 사용하여 호출할 수 있습니다.

사용자 지정 작업을 개별 파일이나 특정 형식의 모든 파일에 추가할 수 있습니다. 예를 들어 “패키지 복원” 작업을 포함하도록 NuGet 패키지 파일을 구성하거나, 모든 *.js* 파일에 대해 linter와 같은 정적 분석 작업을 포함하도록 모든 소스 파일을 구성할 수 있습니다.

### <a name="define-custom-build-tasks"></a>사용자 지정 빌드 작업 정의

코드베이스가 Visual Studio에서 인식하지 못하는 사용자 지정 빌드 도구를 사용하는 경우 몇 가지 구성 단계를 완료할 때까지 Visual Studio에서 코드를 실행하고 디버그할 수 없습니다. Visual Studio는 코드를 빌드, 다시 빌드 및 정리하는 방법을 Visual Studio에 알릴 수 있는 *빌드 작업*을 제공합니다. *tasks.vs.json* 빌드 작업 파일은 Visual Studio 내부 개발 루프를 코드베이스에서 사용하는 사용자 지정 빌드 도구에 연결합니다.

*hello.cs*라는 단일 C# 파일로 구성된 코드베이스를 고려하세요. 이러한 코드베이스에 대한 *메이크파일*은 다음과 같이 표시됩니다.

<!-- markdownlint-disable MD010 -->
```makefile
build: directory hello.exe

hello.exe: hello.cs
    csc -debug hello.cs /out:bin\hello.exe

clean:
    del bin\hello.exe bin\hello.pdb

rebuild: clean build

directory: bin

bin:
    md bin
```
<!-- markdownlint-enable MD010 -->

빌드, 정리 및 다시 빌드 대상이 포함된 이러한 *메이크파일*의 경우 다음 *tasks.vs.json* 파일을 정의할 수 있습니다. NMAKE를 빌드 도구로 사용하여 코드베이스를 빌드, 다시 빌드 및 정리하기 위한 세 가지 빌드 작업을 포함합니다.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "makefile-build",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "build",
      "command": "nmake",
      "args": [ "build" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-clean",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "clean",
      "command": "nmake",
      "args": [ "clean" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    },
    {
      "taskName": "makefile-rebuild",
      "appliesTo": "makefile",
      "type": "launch",
      "contextType": "rebuild",
      "command": "nmake",
      "args": [ "rebuild" ],
      "envVars": {
        "VSCMD_START_DIR": "\"${workspaceRoot}\""
      }
    }
  ]
}
```

*tasks.vs.json*에서 빌드 작업을 정의한 후 **솔루션 탐색기**의 해당 파일에 추가적인 오른쪽 클릭 메뉴(상황에 맞는 메뉴) 항목이 추가됩니다. 이 예제의 경우 “빌드”, “다시 빌드” 및 “정리” 옵션이 *메이크파일* 파일의 상황에 맞는 메뉴에 추가됩니다.

![빌드, 다시 빌드 및 정리가 포함된 메이크파일 상황에 맞는 메뉴](media/customize-build-rebuild-clean.png)

> [!NOTE]
> 이 명령은 `contextType` 설정으로 인해 **작업 구성** 명령 아래의 상황에 맞는 메뉴에 표시됩니다. “build”, “rebuild” 및 “clean”은 빌드 명령이므로 상황에 맞는 메뉴의 중간에 있는 빌드 섹션에 표시됩니다.

이러한 옵션 중 하나를 선택하면 작업이 실행됩니다. **출력** 창에 출력이 표시되고 **오류 목록**에 빌드 오류가 표시됩니다.

### <a name="define-arbitrary-tasks"></a>임의 작업 정의

*tasks.vs.json* 파일에서 임의 작업을 정의하여 원하는 모든 작업을 수행할 수 있습니다. 예를 들어 **출력** 창에서 현재 선택된 파일의 이름을 표시하거나 지정된 디렉터리에 있는 파일을 나열하는 작업을 정의할 수 있습니다.

다음 예제는 단일 작업을 정의하는 *tasks.vs.json* 파일을 보여줍니다. 호출되면 작업은 현재 선택된 *.js* 파일의 파일 이름을 표시합니다.

```json
{
  "version": "0.2.1",
  "tasks": [
    {
      "taskName": "Echo filename",
      "appliesTo": "*.js",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "echo ${file}" ]
    }
  ]
}
```

- `taskName`은 오른쪽 클릭 메뉴에 표시되는 이름을 지정합니다.
- `appliesTo`는 명령이 수행될 수 있는 파일을 지정합니다.
- `command` 속성은 호출할 명령을 지정합니다. 이 예제에서는 `COMSPEC` 환경 변수를 사용하여 명령줄 인터프리터(일반적으로 *cmd.exe*)를 식별합니다.
- `args` 속성은 호출된 명령에 전달할 인수를 지정합니다.
- `${file}` 매크로는 **솔루션 탐색기**에서 선택한 파일을 검색합니다.

*tasks.vs.json*을 저장한 후 폴더에서 *.js* 파일을 마우스 오른쪽 단추로 클릭하고 **Echo 파일 이름**을 선택할 수 있습니다. 파일 이름이 **출력** 창에 표시됩니다.

> [!NOTE]
> 코드베이스에 *tasks.vs.json* 파일이 없는 경우 **솔루션 탐색기**에서 파일의 마우스 오른쪽 단추 메뉴나 상황에 맞는 메뉴에서 **작업 구성**을 선택하여 파일을 만들 수 있습니다.

다음 예제에서는 *bin* 디렉터리의 파일 및 하위 폴더를 나열하는 작업을 정의합니다.

```json
{
  "version": "0.2.1",
  "outDir": "\"${workspaceRoot}\\bin\"",
  "tasks": [
    {
      "taskName": "List Outputs",
      "appliesTo": "*",
      "type": "default",
      "command": "${env.COMSPEC}",
      "args": [ "dir ${outDir}" ]
    }
  ]
}
```

- `${outDir}`는 `tasks` 블록 이전에 처음 정의된 사용자 지정 매크로입니다. 이 매크로는 이후에 `args` 속성에서 호출됩니다.

이 작업은 모든 파일에 적용됩니다. **솔루션 탐색기**의 임의 파일에서 상황에 맞는 메뉴를 열면 작업의 이름 **출력 나열**이 메뉴 아래쪽에 나타납니다. **출력 나열**을 선택하면 *bin* 디렉터리의 내용이 Visual Studio의 **출력** 창에 나열됩니다.

![상황에 맞는 메뉴의 임의 작업](../ide/media/customize-arbitrary-task-menu.png)

### <a name="settings-scope"></a>설정 범위

코드베이스의 루트 및 하위 디렉터리에 여러 개의 *tasks.vs.json* 파일이 있을 수 있습니다. 이 디자인을 사용하면 코드베이스의 하위 디렉터리별로 서로 다른 동작을 수행할 수 있습니다. Visual Studio는 코드베이스 전체에서 설정을 집계하거나 재정의하여 다음 순서로 파일 우선 순위를 지정합니다.

- 루트 폴더의 *.vs* 디렉터리의 설정 파일.
- 설정을 계산 중인 디렉터리.
- 현재 디렉터리부터 루트 디렉터리까지의 모든 부모 디렉터리.
- 루트 디렉터리의 설정 파일.

이러한 집계 규칙은 *tasks.vs.json*에 적용됩니다. 다른 파일의 설정이 집계되는 방법에 대한 자세한 내용은 이 문서에서 해당 파일에 해당하는 섹션을 참조하세요.

### <a name="properties-for-tasksvsjson"></a>tasks.vs.json의 속성

이 섹션에서는 *tasks.vs.json*에서 지정할 수 있는 일부 속성에 대해 설명합니다.

#### <a name="appliesto"></a>appliesTo

`appliesTo` 필드에 이름을 지정하여 모든 파일 또는 폴더에 대한 작업을 만들 수 있습니다(예: `"appliesTo": "hello.js"`). 다음 파일 마스크를 값으로 사용할 수 있습니다.

|||
|-|-|
|`"*"`| 작업 영역의 모든 파일 및 폴더에서 작업을 사용할 수 있음|
|`"*/"`| 작업 영역의 모든 폴더에서 작업을 사용할 수 있음|
|`"*.js"`| 작업 영역의 확장명이 *.js*인 모든 파일에서 작업을 사용할 수 있음|
|`"/*.js"`| 작업 영역 루트의 확장명이 *.js*인 모든 파일에서 작업을 사용할 수 있음|
|`"src/*/"`| *src* 폴더의 모든 하위 폴더에서 작업을 사용할 수 있음|
|`"makefile"`| 작업 영역의 모든 *메이크파일* 파일에서 작업을 사용할 수 있음|
|`"/makefile"`| 작업 영역 루트의 *메이크파일*에만 작업을 사용할 수 있음|

#### <a name="macros-for-tasksvsjson"></a>tasks.vs.json의 매크로

|||
|-|-|
|`${env.<VARIABLE>}`| 개발자 명령 프롬프트에 대해 설정된 환경 변수(예: ${env.PATH}, ${env.COMSPEC} 등)를 지정합니다. 자세한 내용은 [Visual Studio용 개발자 명령 프롬프트](/dotnet/framework/tools/developer-command-prompt-for-vs)를 참조하세요.|
|`${workspaceRoot}`| 작업 영역 폴더의 전체 경로(예: *C:\sources\hello*)|
|`${file}`| 이 작업을 실행하도록 선택된 파일 또는 폴더의 전체 경로(예: *C:\sources\hello\src\hello.js*)|
|`${relativeFile}`| 파일 또는 폴더의 상대 경로(예: *src\hello.js*)|
|`${fileBasename}`| 경로 또는 확장명이 없는 파일 이름(예: *hello*)|
|`${fileDirname}`| 파일 이름을 제외한 파일의 전체 경로(예: *C:\sources\hello\src*)|
|`${fileExtname}`| 선택한 파일의 확장명(예: *.js*)|

## <a name="configure-debugging-with-launchvsjson"></a>launch.vs.json을 사용하여 디버깅 구성

디버깅을 위해 CMake 프로젝트를 구성하려면 [CMake 디버깅 세션 구성](/cpp/build/configure-cmake-debugging-sessions)을 참조하세요.

1. 디버깅을 위한 코드베이스를 구성하려면 **솔루션 탐색기**에서, 실행 파일의 마우스 오른쪽 단추 메뉴나 상황에 맞는 메뉴에서 **디버그 및 시작 설정** 메뉴 항목을 선택합니다.

   ![디버그 및 시작 설정 상황에 맞는 메뉴](media/customize-debug-launch-menu.png)

1. **디버거 선택** 대화 상자에서 옵션을 선택한 다음, **선택** 단추를 선택합니다.

   ![디버거 대화 상자 선택](media/customize-select-a-debugger.png)

   *launch.vs.json* 파일이 없는 경우 파일이 만들어집니다.

   ```json
   {
     "version": "0.2.1",
     "defaults": {},
     "configurations": [
       {
         "type": "default",
         "project": "bin\\hello.exe",
         "name": "hello.exe"
       }
     ]
   }
   ```

1. 그런 다음, **솔루션 탐색기**에서 실행 파일을 마우스 오른쪽 단추로 클릭하고 **시작 항목으로 설정**을 선택합니다.

   실행 파일은 코드베이스의 시작 항목으로 지정되고 디버깅 **시작** 단추의 제목이 실행 파일 이름을 반영하도록 변경됩니다.

   ![사용자 지정 시작 단추](media/customize-start-button.png)

   **F5** 키를 선택하면 디버거가 이미 설정한 중단점에서 시작 및 중지합니다. 모든 친숙한 디버거 창이 사용 가능하고 작동합니다.

   > [!IMPORTANT]
   > C++ 폴더 열기 프로젝트의 C++ 사용자 지정 빌드 및 디버그 작업에 대한 자세한 내용은 [Visual Studio에서 C++ 빌드 시스템에 대해 폴더 열기 지원](/cpp/build/open-folder-projects-cpp)을 참조하세요.

### <a name="specify-arguments-for-debugging"></a>디버깅을 위한 인수 지정

*launch.vs.json* 파일에서 디버깅을 위해 전달할 명령줄 인수를 지정할 수 있습니다. 다음 예제에 표시된 것처럼 `args` 배열에 인수를 추가합니다.

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe"
    },
    {
      "type": "default",
      "project": "bin\\hello.exe",
      "name": "hello.exe a1",
      "args": [ "a1" ]
    }
  ]
}
```

이 파일을 저장하면 새 구성의 이름이 디버그 대상 드롭다운 목록에 표시되고 이름을 선택하여 디버거를 시작할 수 있습니다. 원하는 만큼 많은 디버그 구성을 만들 수 있습니다.

![디버그 구성 드롭다운 목록](media/customize-debug-configurations.png)

> [!NOTE]
> *launch.vs.json*의 `configurations` 배열 속성은 두 개의 파일 위치인&mdash;코드베이스의 루트 디렉터리 및 *.vs* 디렉터리에서 읽습니다. 충돌이 있으면 *.vs\launch.vs.json*의 값에 우선 순위가 제공됩니다.

## <a name="additional-settings-files"></a>추가 설정 파일

이 항목에서 설명하는 세 개의 *.json* 파일 외에도 Visual Studio는 코드베이스에 있는 일부 추가 파일의 설정을 읽습니다.

### <a name="vscodesettingsjson"></a>.vscode\settings.json

Visual Studio는 *.vscode*라는 디렉터리에 있는 *settings.json* 파일에서 제한된 설정을 읽습니다. 이 기능은 이전에 Visual Studio Code에서 개발된 코드베이스용으로 제공됩니다. 현재 *.vscode\settings.json*에서 읽은 유일한 설정은 솔루션 탐색기 및 일부 검색 도구에서 파일을 시각적으로 필터링하는 `files.exclude`입니다.

코드베이스에는 많은 수의 *.vscode\settings.json* 파일이 있을 수 있습니다. 이 파일에서 읽은 설정은 *.vscode*의 부모 디렉터리 및 모든 하위 디렉터리에 적용됩니다.

### <a name="gitignore"></a>.gitignore

*.gitignore* 파일은 무시할 파일(체크 인하지 않을 파일 및 디렉터리)을 Git에 알리는 데 사용됩니다. *.gitignore* 파일은 대개 코드베이스의 모든 개발자와 설정을 공유할 수 있도록 코드베이스의 일부로 포함됩니다. Visual Studio는 *.gitignore* 파일에서 패턴을 읽어 시각적으로 또는 일부 검색 도구에서 항목을 필터링합니다.

*.gitignore* 파일에서 읽은 설정은 부모 디렉터리 및 모든 하위 디렉터리에 적용됩니다.

## <a name="see-also"></a>참고 항목

- [프로젝트 또는 솔루션 없이 코드 개발](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)
- [C++의 폴더 열기 프로젝트](/cpp/build/open-folder-projects-cpp)
- [C++의 CMake 프로젝트](/cpp/build/cmake-projects-in-visual-studio)
- [NMAKE 참조](/cpp/build/reference/nmake-reference)
- [코드 편집기의 기능](../ide/writing-code-in-the-code-and-text-editor.md)
