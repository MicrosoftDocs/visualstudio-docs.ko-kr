---
title: IntelliSense에 대한 C++ 프로젝트 구성
ms.date: 10/08/2018
ms.topic: conceptual
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 8c43c48a797619f86f81e219e31ccf2afab5ba87
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279317"
---
# <a name="configure-a-c-project-for-intellisense"></a>IntelliSense에 대한 C++ 프로젝트 구성

IntelliSense가 제대로 작동하도록 C++ 프로젝트를 수동으로 구성해야 하는 경우도 있습니다. MSBuild 프로젝트(.vcxproj 파일 기반)의 경우 프로젝트 속성에서 설정을 조정할 수 있습니다. 비 MSBuild 프로젝트의 경우 프로젝트의 루트 디렉터리에 있는 CppProperties.json 파일에서 설정을 조정합니다. IntelliSense가 매크로 정의를 이해할 수 있도록 힌트 파일을 만들어야 하는 경우도 있습니다. Visual Studio IDE는 IntelliSense 문제를 식별하고 수정하는 데 도움이 됩니다.

## <a name="single-file-intellisense"></a>단일 파일 IntelliSense

프로젝트에 포함되지 않은 파일을 여는 경우 Visual Studio에서 일부 IntelliSense 지원을 제공하지만, 기본적으로 오류 물결선은 표시되지 않습니다. **탐색 모음**에 ‘기타 파일’이 표시되면 잘못된 코드 아래에 오류 물결선이 표시되지 않는 이유 또는 전처리기 매크로가 정의되지 않은 이유를 설명하는 것일 수 있습니다. 

## <a name="check-the-error-list"></a>오류 목록 확인

파일이 단일 파일 모드로 열리지 않았으며 IntelliSense가 제대로 작동하지 않는 경우 먼저 오류 목록 창을 확인해야 합니다. 현재 소스 파일 및 포함된 모든 헤더 파일에 대한 IntelliSense 오류를 모두 보려면 드롭다운에서 **빌드 + IntelliSense**를 선택합니다.

![오류 목록의 VC++ IntelliSense](media/vcpp-intellisense-error-list.png)

IntelliSense에서는 최대 1000개의 오류를 생성합니다. 소스 파일에 포함된 헤더 파일에 1000개가 넘는 오류가 있는 경우 소스 파일의 시작 부분에만 오류 물결선 하나가 표시됩니다.

## <a name="ensure-include-paths-are-correct"></a>#include 경로가 올바른지 확인합니다.

### <a name="msbuild-projects"></a>MSBuild 프로젝트

Visual Studio IDE 외부에서 빌드를 실행하고, 빌드에 성공하지만 IntelliSense가 잘못된 경우 명령줄이 하나 이상의 구성에 대한 프로젝트 설정과 동기화되지 않을 수 있습니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 현재 구성 및 플랫폼에 대한 모든 **#include** 경로가 올바른지 확인합니다. 모든 구성 및 플랫폼에서 경로가 동일한 경우 **모든 구성** 및 **모든 플랫폼**을 선택한 다음, 경로가 올바른지 확인할 수 있습니다.

![VC++ 포함 디렉터리](media/vcpp-intellisense-include-paths.png)

**VC_IncludePath**와 같은 빌드 매크로의 현재 값을 보려면 포함 디렉터리 줄을 선택하고 오른쪽에 있는 드롭다운을 클릭합니다. **\<편집>** 을 선택하고 **매크로** 단추를 클릭합니다.

### <a name="makefile-projects"></a>메이크파일 프로젝트

NMake 프로젝트 템플릿을 기반으로 하는 메이크파일 프로젝트의 경우 왼쪽 창에서 **NMake**를 선택한 다음, **IntelliSense** 범주 아래의 **포함 검색 경로**를 선택합니다.

![메이크파일 프로젝트 포함 경로](media/vcpp-intellisense-makefile-include-paths.png)

### <a name="open-folder-projects"></a>폴더 열기 프로젝트

CMake 프로젝트의 경우, CMakeLists.txt에서 모든 구성에 대한 #include 경로가 올바르게 지정되었는지 확인합니다. 기타 프로젝트 형식에는 CppProperties.json 파일이 필요할 수 있습니다. 자세한 내용은 [CppProperties.json으로 IntelliSense 구성](/cpp/build/open-folder-projects-cpp#configure-code-navigation-with-cpppropertiesjson)을 참조하세요. 파일에 정의된 각 구성에 대한 경로가 올바른지 확인합니다.

CppProperties.json 파일에 구문 오류가 있는 경우 영향을 받는 파일의 IntelliSense가 잘못됩니다. Visual Studio에서 출력 창에 오류를 표시합니다.

## <a name="tag-parser-issues"></a>태그 구문 분석기 문제

태그 구문 분석기는 검색 및 탐색에 사용되는 “퍼지” C++ 구문 분석기입니다. 매우 빠르지만 모든 코드 구문을 완전히 이해하려고 하지는 않습니다.

예를 들어 전처리기 매크로를 평가하지 않으므로 전처리기 매크로를 많이 사용하는 코드를 잘못 구문 분석할 수 있습니다. 태그 구문 분석기는 익숙하지 않은 코드 구문을 발견할 경우 해당 코드 영역 전체를 건너뛸 수 있습니다.

Visual Studio에서 이 문제는 다음 두 가지 방식으로 나타납니다.

1. 탐색 모음에서 가장 안쪽 매크로를 표시하는 경우 현재 함수 정의를 건너뛴 것입니다.

   ![태그 구문 분석기가 함수 정의를 건너뜀](media/vcpp-intellisense-tag-parser-macro.png)

1. IDE에서 이미 정의된 함수에 대한 함수 정의를 만들도록 제안합니다.

   ![태그 구문 분석기가 기존 함수를 정의하도록 제안함](media/vcpp-intellisense-tag-parser-function.png)

이러한 종류의 문제를 해결하려면 **cpp.hint**라는 파일을 솔루션 디렉터리의 루트에 추가합니다. 자세한 내용은 [힌트 파일](/cpp/build/reference/hint-files)을 참조하세요.

태그 구문 분석기 오류가 **오류 목록** 창에 표시됩니다.

## <a name="validate-project-settings-with-diagnostic-logging"></a>진단 로깅을 사용하여 프로젝트 설정의 유효성 검사

IntelliSense 컴파일러가 포함 경로 및 전처리기 매크로를 포함하여 올바른 컴파일러 옵션을 사용하는지 확인하려면 **도구 > 옵션 > 텍스트 편집기 > C/C++ > 고급 > 진단 로깅**에서 IntelliSense 명령줄의 진단 로깅을 켭니다. **로깅 사용**을 True로 설정하고 **로깅 수준**을 5(가장 자세한 정보 로깅), **로깅 필터**를 8(IntelliSense 로깅)로 설정합니다.

출력 창에는 이제 IntelliSense 컴파일러에 전달되는 명령줄이 표시됩니다. 샘플 출력은 다음과 같습니다.

```output
[IntelliSense] Configuration Name: Debug|Win32
[IntelliSense] Toolset IntelliSense Identifier:
[IntelliSense] command line options:
/c
/I.
/IC:\Repo\Includes
/DWIN32
/DDEBUG
/D_DEBUG
/Zc:wchar_t-
/Zc:forScope
/Yustdafx.h
```

이 정보는 IntelliSense에서 부정확한 정보를 제공하는 이유를 이해하는 데 도움이 될 수 있습니다. 예를 들어 프로젝트의 포함 디렉터리에 **$(MyVariable)\Include**가 들어 있고 진단 로그에 **/I\Include**가 포함 경로로 표시되는 경우 **$(MyVariable)** 이 평가되지 않았으며 최종 포함 경로에서 제거되었음을 의미합니다.

## <a name="about-the-intellisense-build"></a>IntelliSense 빌드 정보

Visual Studio에서는 전용 C++ 컴파일러를 사용하여 모든 IntelliSense 기능을 지원하는 데이터베이스를 만들고 유지 관리합니다. IntelliSense 데이터베이스를 코드와 동기화된 상태로 유지하기 위해 Visual Studio는 프로젝트 설정 또는 소스 파일의 특정 변경 내용에 대한 응답으로 IntelliSense 전용 빌드를 백그라운드 작업으로 자동 시작합니다.

그러나 Visual Studio에서 적절한 시기에 IntelliSense 데이터베이스를 업데이트하지 못하는 경우도 있습니다. 예를 들어 **git pull** 또는 **git checkout** 명령을 실행하는 경우 Visual Studio에서 파일의 변경 내용을 검색하는 데 최대 1시간이 걸릴 수 있습니다. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **솔루션 다시 검색**을 선택하여 솔루션의 모든 파일을 강제로 다시 검색할 수 있습니다.

## <a name="troubleshooting-intellisense-build-failures"></a>IntelliSense 빌드 문제 해결

IntelliSense 빌드에서는 이진 파일을 생성하지 않지만 여전히 실패할 수 있습니다. 한 가지 가능한 실패 원인은 사용자 지정 .props 또는 .targets 파일입니다. Visual Studio 2017 버전 15.6 이상에서는 IntelliSense 전용 빌드 오류가 출력 창에 기록됩니다. 오류를 보려면 **출력 보기 선택**을 **솔루션**으로 설정합니다.

![솔루션 오류 출력 창](media/vcpp-intellisense-output-window.png)

오류 메시지에서 디자인 타임 추적을 사용하도록 지시할 수 있습니다.

```output
error: Designtime build failed for project 'E:\src\MyProject\MyProject.vcxproj',
configuration 'Debug|x64'. IntelliSense might be unavailable.
Set environment variable TRACEDESIGNTIME=true and restart
Visual Studio to investigate.
```

환경 변수 TRACEDESIGNTIME을 true로 설정하고 Visual Studio를 다시 시작하면 빌드 실패 진단에 도움이 되는 로그 파일이 %TEMP% 디렉터리에 표시됩니다.

TRACEDESIGNTIME 환경 변수에 대한 자세한 내용은 [Roslyn](https://github.com/dotnet/roslyn/wiki/Diagnosing-Project-System-Build-Errors) 및 [공통 프로젝트 시스템](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md)을 참조하세요. 이러한 문서의 정보는 C++ 프로젝트와 관련이 있습니다.

## <a name="see-also"></a>참고 항목

- [Visual C++ IntelliSense](visual-cpp-intellisense.md)
