---
title: Python 프로젝트에 대한 사용자 지정 메뉴 명령 정의
description: 프로젝트 및 대상 파일을 편집하여 Visual Studio의 Python 프로젝트 컨텍스트 메뉴에 사용자 지정 명령을 추가하여 실행 가능 프로그램, 스크립트, 모듈, 인라인 코드 조각 및 pip를 호출할 수 있습니다.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: ec53a67980866ed6422fae5764bbf6a9313ef91e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957710"
---
# <a name="define-custom-commands-for-python-projects"></a>Python 프로젝트에 대한 사용자 지정 명령 정의

Python 프로젝트로 작업하는 과정에서 명령 창으로 전환하여 특정 스크립트 또는 모듈을 실행하거나, pip 명령을 실행하거나, 다른 임의의 도구를 사용하게 될 수 있습니다. 워크플로를 개선하려면 Python 프로젝트 상황에 맞는 메뉴의 **Python** 하위 메뉴에 사용자 지정 명령을 추가할 수 있습니다. 이러한 명령은 콘솔 창 또는 Visual Studio **출력** 창에서 실행할 수 있습니다. 또한 정규식을 사용하여 Visual Studio에 대해 명령의 출력에서 오류 및 경고를 구문 분석하는 방법을 지시할 수 있습니다.

기본적으로 이러한 메뉴에는 다음과 같은 단일 **PyLint 실행** 명령이 포함됩니다.

![프로젝트의 상황에 맞는 메뉴에서 Python 하위 메뉴의 기본 모양](media/custom-commands-default-menu.png)

사용자 지정 명령은 이와 같은 상황에 맞는 메뉴에 나타납니다. 사용자 지정 명령은 프로젝트 파일에 직접 추가되며, 이 파일이 해당 개별 프로젝트에 적용됩니다. 또한 *.targets* 파일에서 여러 프로젝트 파일로 쉽게 가져올 수 있는 사용자 지정 명령을 정의할 수도 있습니다.

Visual Studio의 특정 Python 프로젝트 템플릿은 해당 *.targets* 파일을 사용하여 고유한 사용자 지정 명령을 추가합니다. 예를 들어 Bottle 웹 프로젝트 및 Flask 웹 프로젝트 템플릿은 모두 **서버 시작** 및 **디버그 서버 시작** 두 명령을 추가합니다. Django 웹 프로젝트 템플릿은 이와 같은 명령과 몇몇 명령을 더 추가합니다.

![Django 프로젝트의 상황에 맞는 메뉴에서 Python 하위 메뉴의 모양](media/custom-commands-django-menu.png)

각 사용자 지정 명령은 Python 파일, Python 모듈, 인라인 Python 코드 및 임의의 실행 파일 또는 pip 명령을 참조할 수 있습니다. 명령이 실행되는 방법과 위치를 지정할 수도 있습니다.

> [!Tip]
> 텍스트 편집기에서 프로젝트 파일을 변경할 때마다 Visual Studio에서 프로젝트를 다시 로드하여 해당 변경 내용을 적용해야 합니다. 예를 들어 프로젝트의 상황에 맞는 메뉴에 표시할 명령에 대해 사용자 지정 명령 정의를 추가한 후 프로젝트를 다시 로드해야 합니다.
>
> 아시다시피 Visual Studio는 프로젝트 파일을 직접 편집하는 수단을 제공합니다. 먼저 프로젝트 파일을 마우스 오른쪽 단추로 클릭하고 **프로젝트 언로드**를 선택한 다음, 다시 마우스 오른쪽 단추로 클릭하고 **편집\<프로젝트 이름>** 을 선택하여 Visual Studio 편집기에서 프로젝트를 엽니다. 그런 다음, 편집을 하고 편집 내용을 저장하고 프로젝트를 한 번 더 마우스 오른쪽 단추로 클릭하고 **프로젝트 다시 로드**를 선택하며, 이때 편집기의 프로젝트 파일을 닫았는지 확인하라는 메시지도 나타납니다.
>
> 그러나 사용자 지정 명령을 개발할 때 이러한 모든 클릭은 지루할 수 있습니다. 더 효율적인 워크플로를 위해 Visual Studio에서 프로젝트를 로드하고 별도의 편집기에서 *.pyproj* 파일을 함께 엽니다(Visual Studio의 다른 인스턴스, Visual Studio Code, 메모장 등). 편집기에서 변경 내용을 저장하고 Visual Studio로 전환하면 Visual Studio가 변경 내용을 검색하고 프로젝트를 다시 로드할지 묻습니다.(**프로젝트\<이름>가 환경 외부에서 수정되었습니다.** ) **다시 로드**를 선택하면 변경 내용이 한 단계 만에 즉시 적용됩니다.

## <a name="walkthrough-add-a-command-to-a-project-file"></a>연습: 프로젝트 파일에 명령 추가

사용자 지정 명령을 익히기 위해 이 섹션에서는 *python.exe*를 사용하여 프로젝트의 시작 파일을 실행하는 간단한 에제를 연습합니다. (그러한 명령은 **디버그** > **디버깅하지 않고 시작**을 사용하는 것과 같은 효과입니다.)

1. **Python 애플리케이션** 템플릿을 사용하여 "Python-CustomCommands"라는 새 프로젝트를 만듭니다. (프로세스를 아직 익히지 못한 경우 지침은 [빠른 시작: 템플릿에서 Python 프로젝트 만들기](quickstart-02-python-in-visual-studio-project-from-template.md)를 참조하세요.)

1. *Python_CustomCommands.py*에서 `print("Hello custom commands")` 코드를 추가합니다.

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 버튼으로 클릭하고 **Python**을 선택하고 하위 메뉴에 표시되는 유일한 명령이 **PyLint 실행**인지 확인합니다. 사용자 지정 명령은 이와 같은 하위 메뉴에 표시됩니다.

1. 소개에서 제안한 대로 별도의 텍스트 편집기에서 *Python-CustomCommands.pyproj*를 엽니다. 그런 다음, 닫는 `</Project>`의 바로 안에 있는 파일의 끝에 다음 줄을 추가하고 파일을 저장합니다.

    ```xml
    <PropertyGroup>
      <PythonCommands>
        $(PythonCommands);
      </PythonCommands>
    </PropertyGroup>
    ```

1. Visual Studio로 다시 전환하고 파일 변경에 관한 메시지가 표시될 때 **다시 로드**를 선택합니다. 그런 다음, 앞에서 추가한 줄은 PyLint 명령이 포함된 기본 **속성 그룹을 복제할 뿐이므로**Python**메뉴를 다시 확인하여**PyLint 실행`<PythonCommands>`이 여전히 거기에 표시된 유일한 항목인지 확인합니다.

1. 프로젝트 파일을 포함한 편집기로 전환하고 `<Target>` 뒤에 다음 `<PropertyGroup>` 정의를 추가합니다. 이 아티클의 뒷부분에서 설명하듯이, 이 `Target` 요소는 콘솔 창에서 *python.exe*를 사용하여 시작 파일("StartupFile" 속성에 의해 식별됨)을 실행하는 사용자 지정 명령을 정의합니다. 특성 `ExecuteIn="consolepause"`는 닫기 전에 키를 누르기를 기다리는 콘솔을 사용합니다.

    ```xml
    <Target Name="Example_RunStartupFile" Label="Run startup file" Returns="@(Commands)">
      <CreatePythonCommandItem
        TargetType="script"
        Target="$(StartupFile)"
        Arguments=""
        WorkingDirectory="$(MSBuildProjectDirectory)"
        ExecuteIn="consolepause">
        <Output TaskParameter="Command" ItemName="Commands" />
      </CreatePythonCommandItem>
    </Target>
    ```

1. 대상의 `Name` 특성의 값을 앞서 추가한 `<PythonCommands>` 속성에 추가하여 요소가 아래 코드와 같아 보이도록 합니다. 대상의 이름을 이 목록에 추가하면 **Python** 메뉴에 추가하는 것입니다.

    ```xml
      <PythonCommands>
        $(PythonCommands);
        Example_RunStartupFile
      </PythonCommands>
    ```

    명령이 `$(PythonCommands)`에 정의된 명령보다 앞에 표시되도록 하려면 해당 토큰 앞에 배치합니다.

1. 프로젝트 파일을 저장하고 Visual Studio로 전환하고 메시지가 표시될 때 프로젝트를 다시 로드합니다. 그런 다음, **Python-CustomCommands** 프로젝트를 마우스 오른쪽 단추로 클릭하고 **Python**을 선택합니다. 메뉴에 **시작 파일 실행** 항목이 표시되어야 합니다. 이 메뉴 항목이 보이지 않으면 `<PythonCommands>` 요소에 해당 항목의 이름을 추가했는지 확인합니다. 또한 이 문서의 뒷부분에 나오는 [문제 해결](#troubleshooting)을 참조하세요.

    ![Python 상황에 맞는 서브 메뉴에 나타나는 사용자 지정 명령](media/custom-commands-walkthrough-menu-item.png)

1. **시작 파일 실행** 명령을 선택하면 **Hello 사용자 지정 명령**에 이어서 **계속하려면 아무 키나 누르세요**라는 텍스트가 포함된 명령 창이 표시됩니다.  아무 키나 눌러 창을 닫습니다.

    ![콘솔 창의 사용자 지정 명령 출력](media/custom-commands-walkthrough-console.png)

1. 프로젝트 파일을 포함한 편집기로 돌아가서 `ExecuteIn` 특성의 값을 `output`으로 변경합니다. 파일을 저장하고 Visual Studio로 전환하고 프로젝트를 다시 로드하고 명령을 다시 호출합니다. 이번에는 Visual Studio의 **출력** 창에 프로그램의 출력이 표시되는지 확인합니다.

    ![출력 창의 사용자 지정 명령 출력](media/custom-commands-walkthrough-output-window.png)

1. 명령을 더 추가하려면 각 명령에 적합한 `<Target>` 요소를 정의하고 `<PythonCommands>` 속성 그룹에 대상의 이름을 추가하고 Visual Studio에서 프로젝트를 다시 로드합니다.

>[!Tip]
> `($StartupFile)`과 같은 프로젝트 속성을 사용하는 명령을 호출하는데 토큰이 정의되지 않아서 명령이 실패하는 경우 프로젝트를 다시 로드할 때까지 Visual Studio가 명령을 비활성화합니다. 그러나 프로젝트에 대해 속성을 정의하는 변경을 하면 이 명령의 상태가 새로 고쳐지지 않으므로 그러한 경우 여전히 프로젝트를 다시 로드해야 합니다.

## <a name="command-target-structure"></a>명령 대상 구조

`<Target>` 요소의 일반 형식은 다음과 같은 의사 코드에 표시됩니다.

```xml
<Target Name="Name1" Label="Display Name" Returns="@(Commands)">
    <CreatePythonCommandItem Target="filename, module name, or code"
        TargetType="executable/script/module/code/pip"
        Arguments="..."
        ExecuteIn="console/consolepause/output/repl[:Display name]/none"
        WorkingDirectory="..."
        ErrorRegex="..."
        WarningRegex="..."
        RequiredPackages="...;..."
        Environment="...">

      <!-- Output always appears in this form, with these exact attributes -->
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

특성 값의 프로젝트 속성 또는 환경 변수를 참조하려면 `$()` 토큰 내에 `$(StartupFile)` 및 `$(MSBuildProjectDirectory)` 같은 이름을 사용합니다. 자세한 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

### <a name="target-attributes"></a>대상 특성

| attribute | 필수 | Description |
| --- | --- | --- |
| 속성 | yes | Visual Studio 프로젝트 내에서 명령에 대한 식별자입니다. 명렁을 Python 하위 메뉴에 표시하려면 이 이름을 명령에 대한 `<PythonCommands>` 속성 그룹에 추가해야 합니다. |
| 레이블 | yes | Python 하위 메뉴에 나타나는 UI 표시 이름입니다. |
| 반환 | yes | 대상을 명령으로 식별하는 `@(Commands)`를 포함해야 합니다. |

### <a name="createpythoncommanditem-attributes"></a>CreatePythonCommandItem 특성

모든 특성 값은 대/소문자를 구분하지 않습니다.

| attribute | 필수 | Description |
| --- | --- | --- |
| TargetType | yes | 포함된 대상 특성 및 해당 특성이 Arguments 특성과 함께 사용되는 방법을 지정합니다.<ul><li>**executable**: 대상에 이름 지정된 실행 파일을 실행하여 Arguments의 값을 마치 명령줄에서 직접 입력한 것처럼 추가합니다. 값은 인수 없이 프로그램 이름만 포함해야 합니다.</li><li>**script**: 대상에서 파일 이름이 포함된 *python.exe*를 실행하면 인수의 값이 이어집니다.</li><li>**module**: `python -m` 뒤에 Target의 모듈 이름 및 그 뒤에 Arguments의 값을 실행합니다.</li><li>**code**: Target에 포함된 인라인 코드를 실행합니다. Arguments 값은 무시됩니다.</li><li>**pip**: Target의 명령 및 그 뒤에 Arguments를 사용하여 `pip`를 실행합니다. ExecuteIn은 "output"으로 설정되지만 pip는 `install` 명령을 가정하고 Target을 패키지 이름으로 사용합니다.</li></ul> |
| 대상 | yes | TargetType에 따라 사용할 파일 이름, 모듈 이름, 코드 또는 pip 명령입니다. |
| 인수 | 옵션 | 대상에 부여할 인수(있는 경우)의 문자열을 지정합니다. TargetType이 `script`이면 *python.exe*가 아닌 Python 프로그램에 인수가 지정됩니다. `code` TargetType에 대해서는 무시됩니다. |
| ExecuteIn | yes | 명령을 실행할 환경을 지정합니다.<ul><li>**console**: (기본값) Target 및 인수를 마치 명령줄에서 직접 입력한 것처럼 실행합니다. Target이 실행되는 동안 명령 창이 표시되었다가 자동으로 닫힙니다.</li><li>**consolepause**: 콘솔과 같지만 창을 닫기 전에 키를 누르기를 기다립니다.</li><li>**output**: 대상을 실행하고 그 결과를 Visual Studio의 **출력** 창에 표시합니다. TargetType이 "pip"인 경우 Visual Studio는 Target을 패키지 이름으로 사용하고 Arguments를 추가합니다.</li><li>**repl**: [Python 대화형](python-interactive-repl-in-visual-studio.md) 창에서 대상을 실행합니다. 창의 제목에 선택적 표시 이름이 사용됩니다.</li><li>**none**: console과 같이 동작합니다.</li></ul>|
| WorkingDirectory | 옵션 | 명령을 실행할 폴더입니다. |
| ErrorRegex<br>WarningRegEx | 옵션 | ExecuteIn이 `output`인 경우에만 사용됩니다. 두 값 모두 Visual Studio가 명령 출력을 구문 분석하여 해당 **오류 목록** 창에 오류 및 경고를 표시하는 정규식을 지정합니다. 지정되지 않은 경우 이 명령은 **오류 목록** 창에 영향을 미치지 않습니다. Visual Studio에서 예상되는 내용에 대한 자세한 내용은 [명명된 캡처 그룹](#named-capture-groups-for-regular-expressions)을 참조하세요. |
| RequiredPackages | 옵션 | [*requirements.txt*](https://pip.readthedocs.io/en/1.1/requirements.html)와 같은 형식을 사용하는 명령에 대한 패키지 요구 사항의 목록입니다(pip.readthedocs.io). 예를 들어 **PyLint 실행** 명령은 `pylint>=1.0.0`을 지정합니다. 명령을 실행하기 전에 Visual Studio은 목록의 모든 패키지가 설치되었는지 확인합니다. Visual Studio는 pip를 사용하여 누락된 패키지를 설치합니다. |
| Environment | 옵션 | 명령을 실행하기 전에 정의하는 환경 변수의 문자열입니다. 각 변수는 여러 변수를 세미콜론으로 구분하고 \<NAME>=\<VALUE> 양식을 사용합니다. 여러 값을 가진 변수는 'NAME=VALUE1;VALUE2'와 같이 홑따옴표 또는 따옴표로 둘러싸야 합니다. |

#### <a name="named-capture-groups-for-regular-expressions"></a>정규식에 대해 이름 지정된 캡처 그룹

명령의 출력에서 오류 및 경고를 구문 분석할 때 Visual Studio는 `ErrorRegex` 및 `WarningRegex` 값의 정규식이 다음과 같은 이름 지정된 그룹을 사용할 것을 예상합니다.

- `(?<message>...)`: 오류의 텍스트
- `(?<code>...)`: 오류 코드
- `(?<filename>...)`: 오류가 보고되는 파일의 이름
- `(?<line>...)`: 오류가 보고되는 파일에서 위치의 줄 번호입니다.
- `(?<column>...)`: 오류가 보고되는 파일에서 위치의 열 번호입니다.

예를 들어 PyLint는 다음 형식의 경고를 생성합니다.

```output
************* Module hello
C:  1, 0: Missing module docstring (missing-docstring)
```

Visual Studio가 해당 경고에서 올바른 정보를 추출하고 이를 **오류 목록** 창에 표시하려면 `WarningRegex`Pylint 실행**명령에 대한** 값은 다음과 같습니다.

```regex
^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]
```

(값의 `msg_id`는 실제로 `code`이어야 합니다. [문제 3680](https://github.com/Microsoft/PTVS/issues/3680) 참조.)

## <a name="create-a-targets-file-with-custom-commands"></a>사용자 지정 명령을 사용하여 .targets 파일 만들기

프로젝트 파일에 사용자 지정 명령을 정의하면 해당 프로젝트 파일에서만 사용할 수 있습니다. 명령을 여러 프로젝트 파일에 사용하려면 그 대신에 `<PythonCommands>` 속성 그룹 및 모든 `<Target>` 요소를 *.targets* 파일에 정의합니다. 그런 다음, 해당 파일을 개별 프로젝트 파일에 가져옵니다.

*.targets* 파일의 형식은 다음과 같습니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PythonCommands>
      $(PythonCommands);
      <!-- Additional command names -->
    </PythonCommands>
  </PropertyGroup>

  <Target Name="..." Label="..." Returns="@(Commands)">
    <!-- CreatePythonCommandItem and Output elements... -->
  </Target>

  <!-- Any number of additional Target elements-->
</Project>
```

*.targets* 파일을 프로젝트로 로드하려면 `<Import Project="(path)">` 요소를 `<Project>` 요소 내에 배치합니다. 예를 들어 프로젝트의 *targets* 하위 폴더에 *CustomCommands.targets*라는 파일이 있는 경우 다음 코드를 사용합니다.

```xml
<Import Project="targets/CustomCommands.targets"/>
```

> [!Note]
> *.targets* 파일을 변경할 때마다 프로젝트 자체가 아닌 프로젝트를 포함한 *솔루션*을 다시 로드해야 합니다.

## <a name="example-commands"></a>예제 명령

### <a name="run-pylint-module-target"></a>PyLint 실행(모듈 대상)

다음 코드는 *Microsoft.PythonTools.targets* 파일에 표시됩니다.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);PythonRunPyLintCommand</PythonCommands>
  <PyLintWarningRegex>
    <![CDATA[^(?<filename>.+?)\((?<line>\d+),(?<column>\d+)\): warning (?<msg_id>.+?): (?<message>.+?)$]]>
  </PyLintWarningRegex>
</PropertyGroup>

<Target Name="PythonRunPyLintCommand"
        Label="resource:Microsoft.PythonTools.Common;Microsoft.PythonTools.Common.Strings;RunPyLintLabel"
        Returns="@(Commands)">
  <CreatePythonCommandItem Target="pylint.lint"
                           TargetType="module"
                           Arguments="&quot;--msg-template={abspath}({line},{column}): warning {msg_id}: {msg} [{C}:{symbol}]&quot; -r n @(Compile, ' ')"
                           WorkingDirectory="$(MSBuildProjectDirectory)"
                           ExecuteIn="output"
                           RequiredPackages="pylint&gt;=1.0.0"
                           WarningRegex="$(PyLintWarningRegex)">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-pip-install-with-a-specific-package-pip-target"></a>특정 패키지(pip 대상)를 사용하여 pip 설치 실행

다음 명령은 `pip install my-package`출력**창에서**를 실행합니다. 패키지를 개발하고 설치를 테스트할 때 이런 명령을 사용할 수 있습니다. Target이 `install` 명령(`ExecuteIn="output"`을 사용할 때 가정됨) 대신 패키지 이름을 포함한다는 데 주목하십시오.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);InstallMyPackage</PythonCommands>
</PropertyGroup>

<Target Name="InstallMyPackage" Label="pip install my-package" Returns="@(Commands)">
  <CreatePythonCommandItem Target="my-package" TargetType="pip" Arguments=""
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="show-outdated-pip-packages-pip-target"></a>오래된 pip 패키지(pip 대상) 표시

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowOutdatedPackages</PythonCommands>
</PropertyGroup>

<Target Name="ShowOutdatedPackages" Label="Show outdated pip packages" Returns="@(Commands)">
  <CreatePythonCommandItem Target="list" TargetType="pip" Arguments="-o --format columns"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="consolepause">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-an-executable-with-consolepause"></a>consolepause를 사용하여 실행 파일 실행

다음 명령은 단순히 `where`를 실행하여 프로젝트 폴더에서 시작하는 Python 파일을 표시합니다.

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);ShowAllPythonFilesInProject</PythonCommands>
</PropertyGroup>

<Target Name="ShowAllPythonFilesInProject" Label="Show Python files in project" Returns="@(Commands)">
  <CreatePythonCommandItem Target="where" TargetType="executable" Arguments="/r . *.py"
    WorkingDirectory="$(MSBuildProjectDirectory)" ExecuteIn="output">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

### <a name="run-server-and-run-debug-server-commands"></a>서버 실행 및 디버그 서버 명령 실행

웹 프로젝트에 대한 **Start server** 및 **Start debug server** 명령이 정의되는 방법을 알아보려면 [Microsoft.PythonTools.Web.targets](https://github.com/Microsoft/PTVS/blob/master/Python/Product/BuildTasks/Microsoft.PythonTools.Web.targets)(GitHub)를 참조하세요.

### <a name="install-package-for-development"></a>개발용 패키지 설치

```xml
<PropertyGroup>
  <PythonCommands>PipInstallDevCommand;$(PythonCommands);</PythonCommands>
</PropertyGroup>

<Target Name="PipInstallDevCommand" Label="Install package for development" Returns="@(Commands)">
    <CreatePythonCommandItem Target="pip" TargetType="module" Arguments="install --editable $(ProjectDir)"
        WorkingDirectory="$(WorkingDirectory)" ExecuteIn="Repl:Install package for development">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa)(GitHub)에서 사용 권한과 함께 사용*

### <a name="generate-windows-installer"></a>Windows Installer 생성

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWinInstCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWinInstCommand" Label="Generate Windows Installer" Returns="@(Commands)">
    <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
        Arguments="bdist_wininst --user-access-control=force --title &quot;$(InstallerTitle)&quot; --dist-dir=&quot;$(DistributionOutputDir)&quot;"
        WorkingDirectory="$(WorkingDirectory)" RequiredPackages="setuptools"
        ExecuteIn="Repl:Generate Windows Installer">
      <Output TaskParameter="Command" ItemName="Commands" />
    </CreatePythonCommandItem>
  </Target>
```

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa)(GitHub)에서 사용 권한과 함께 사용*

### <a name="generate-wheel-package"></a>휠 패키지 생성

```xml
<PropertyGroup>
  <PythonCommands>$(PythonCommands);BdistWheelCommand;</PythonCommands>
</PropertyGroup>

<Target Name="BdistWheelCommand" Label="Generate Wheel Package" Returns="@(Commands)">

  <CreatePythonCommandItem Target="$(ProjectDir)setup.py" TargetType="script"
      Arguments="bdist_wheel --dist-dir=&quot;$(DistributionOutputDir)&quot;"
      WorkingDirectory="$(WorkingDirectory)" RequiredPackages="wheel;setuptools"
      ExecuteIn="Repl:Generate Wheel Package">
    <Output TaskParameter="Command" ItemName="Commands" />
  </CreatePythonCommandItem>
</Target>
```

*[fxthomas/Example.pyproj.xml](https://gist.github.com/fxthomas/5c601e3e0c1a091bcf56aed0f2960cfa)(GitHub)에서 사용 권한과 함께 사용*

## <a name="troubleshooting"></a>문제 해결

### <a name="message-the-project-file-could-not-be-loaded"></a>메시지: "프로젝트 파일을 로드할 수 없습니다"

프로젝트 파일에 구문 오류가 있음을 나타냅니다. 메시지는 줄 번호 및 문자 위치와 함께 구체적 오류를 포함합니다.

### <a name="console-window-closes-immediately-after-command-is-run"></a>명령이 실행된 직후에 콘솔 창이 닫힘

`ExecuteIn="consolepause"` 대신 `ExecuteIn="console"`를 사용합니다.

### <a name="command-does-not-appear-on-the-menu"></a>메뉴에 명령이 표시되지 않음

명령이 `<PythonCommands>` 속성 그룹에 포함되어 있는지, 명령 목록의 이름이 `<Target>` 요소에 지정된 이름과 일치하는지 확인합니다.

예를 들어 다음 요소에서 속성 그룹의 "Example" 이름은 대상의 이름 "ExampleCommand"와 일치하지 않습니다. Visual Studio는 "Example"이라는 명령을 찾지 못하므로 아무 명령도 표시되지 않습니다. 명령 목록에 "ExampleCommand"를 사용하거나 대상의 이름을 "Example"로만 변경합니다.

```xml
  <PropertyGroup>
    <PythonCommands>$(PythonCommands);Example</PythonCommands>
  </PropertyGroup>
  <Target Name="ExampleCommand" Label="Example Command" Returns="@(Commands)">
    <!-- ... -->
  </Target>
```

### <a name="message-an-error-occurred-while-running-command-name-failed-to-get-command-target-name-from-project"></a>메시지: \<명령 이름>을 실행하는 동안 오류가 발생했습니다. 프로젝트에서 \<대상 이름> 명령을 가져오지 못했습니다.

`<Target>` 또는 `<CreatePythonCommandItem>` 요소의 내용이 잘못되었음을 나타냅니다. 가능한 이유:

- 필수 `Target` 특성이 비어 있습니다.
- 필수 `TargetType` 특성이 비어 있거나 인식되지 않는 값을 포함합니다.
- 필수 `ExecuteIn` 특성이 비어 있거나 인식되지 않는 값을 포함합니다.
- `ErrorRegex` 또는 `WarningRegex`는 설정 `ExecuteIn="output"` 없이 지정됩니다.
- 요소에 인식되지 않는 특성이 존재합니다. `Argumnets` 대신 `Arguments`(철자 틀림)를 사용했을 수 있습니다.

정의되지 않은 특성을 참조하면 특성 값이 비어 있을 수 있습니다. 예를 들어 토큰 `$(StartupFile)`을 사용하지만 프로젝트에 시작 파일이 정의되어 있지 않으면 토큰이 빈 문자열로 확인됩니다. 그러한 경우 기본값을 정의하는 것이 좋습니다. 예를 들어 Bottle, Flask 및 Django 프로젝트 템플릿에 정의된 **Run server** 및 **Run debug server** 명령은 프로젝트 속성에 서버 시작 파일을 다른 방법으로 지정하지 않은 한 기본적으로 *manage.py*로 지정됩니다.

### <a name="visual-studio-hangs-and-crashes-when-running-the-command"></a>명령을 실행할 때 Visual Studio가 중지하고 작동 중단

`ExecuteIn="output"`을 사용하여 콘솔 명령의 실행을 시도했을 가능성이 있습니다. 이 경우 Visual Studio가 작동 중단되고 출력의 구문 분석을 시도할 수 있습니다. 대신 `ExecuteIn="console"`를 사용하세요. ([문제 3682](https://github.com/Microsoft/PTVS/issues/3681) 참조.)

### <a name="executable-command-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>실행 파일이 "내부 또는 외부 명령, 작동 가능 프로그램 또는 일괄 처리 파일으로 인식되지 않습니다."

`TargetType="executable"`을 사용할 때 `Target`의 값이 인수 없이 프로그램 이름*뿐*이어야 합니다(예: *python* 또는 *python.exe*만). 인수를 모두 `Arguments` 특성으로 이동합니다.
