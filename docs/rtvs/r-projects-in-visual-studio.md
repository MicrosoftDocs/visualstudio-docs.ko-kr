---
title: R 프로젝트
description: 속성, 프로젝트 명령 및 템플릿을 포함하여 Visual Studio에서 관리자 R 프로젝트를 만드는 방법입니다.
ms.date: 06/29/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: bcdef95935c0522c8b93a972d7f44fbd7632c53b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312693"
---
# <a name="create-r-projects-in-visual-studio"></a>Visual Studio에서 R 프로젝트 만들기

R 프로젝트( *.rxproj* 파일)는 프로젝트와 관련된 모든 소스 및 콘텐츠 파일을 식별합니다. 또한 각 파일에 대한 빌드 정보를 포함하고 소스 제어 시스템과 통합할 정보를 유지 관리하며 애플리케이션을 논리 구성 요소로 구성하는 데 도움을 줍니다. 그러나 설치된 패키지 목록과 같은 작업 영역 관련 정보는 작업 영역 자체에서 별도로 유지 관리됩니다.

프로젝트는 항상 Visual Studio *솔루션* 내에서 관리되므로 서로를 참조할 수 있는 프로젝트를 여러 개 포함할 수 있습니다. [Visual Studio에서 여러 프로젝트 형식 사용](#use-multiple-project-types-in-visual-studio)을 참조하세요.

## <a name="creating-a-new-r-project"></a>새 R 프로젝트 만들기

1. Visual Studio를 엽니다.
1. **파일 > 새로 만들기 > 프로젝트** 선택(**Ctrl**+**Shift**+**N**)
1. **템플릿** > **R** 아래에서 “R 프로젝트”를 선택하고, 프로젝트의 이름과 위치를 입력한 후 **확인**을 선택합니다.

    ![Visual Studio의 R(VS2017의 RTVS)에 대한 새 프로젝트 대화 상자](media/getting-started-01-new-project.png)

이 명령은 프로젝트를 만들고 편집기에서 빈 *script.R* 파일을 엽니다. **솔루션 탐색기**에서는 프로젝트의 두 가지 기타 파일을 확인할 수 있습니다.

![템플릿에서 생성된 R 프로젝트의 콘텐츠](media/projects-template-results.png)

[R 대화형](interactive-repl-for-r-in-visual-studio.md) 창에 입력한 명령에 관계없이 *.Rhistory* 레코드. **R 도구** > **Windows** > **기록** 명령을 사용하여 전용 기록 창을 열 수 있습니다. 해당 창에는 기록 내용을 지우는 도구 모음 단추 및 상황에 맞는 메뉴 항목이 있습니다.

*rproject.rproj* 파일에서는 Visual Studio에서 관리되지 않는 R 관련 프로젝트 설정이 유지 관리됩니다.

| 속성 | 기본값 | 설명 |
| --- | --- | --- |
| 버전 | 1.0 | 프로젝트를 만드는 데 사용되는 Visual Studio용 R 도구 버전. |
| RestoreWorkspace | 기본값 | `.RData` 파일에서 이전 작업 영역 변수를 프로젝트 디렉터리에 자동으로 로드합니다. |
| SaveWorkspace | 기본값 | 프로젝트를 닫을 때 현재 작업 영역 변수를 직접 프로젝트 디렉터리의 `.RData` 파일에 저장합니다. |
| AlwaysSaveHistory | 기본값 | 프로젝트를 닫을 때 현재 대화형 창 기록을 직접 프로젝트 디렉터리의 `.RHistory` 파일에 저장합니다. |
| EnableCodeIndexing | 예 | 코드 검색 속도를 높이기 위해 백그라운드 인덱싱 작업을 실행할지 결정합니다. |
| UseSpacesForTab | 예 | 편집기에서 **Tab** 키를 누를 때 공백(Yes) 또는 Tab 문자(No)를 삽입할지 결정합니다. |
| NumSpacesForTab | 2 | UseSpacesForTab이 Yes인 경우 삽입할 공백 수. |
| 인코딩 | UTF-8 | `.R` 파일의 기본 인코딩. |
| RnwWeave | Sweave | Rnw 파일을 평직 처리할 때 사용할 패키지. |
| LaTeX | pdfLaTeX | RMarkdwon을 PDF로 변환할 때 사용할 라이브러리. |

### <a name="converting-a-folder-of-files-to-an-r-project"></a>파일 폴더를 R 프로젝트로 변환

프로젝트에서 관리할 *.R* 파일의 기존 폴더가 있는 경우 다음 단계를 수행합니다.

1. 이전 섹션처럼 Visual Studio에서 새 프로젝트를 만듭니다.
1. 파일을 프로젝트 폴더로 복사합니다.
1. Visual Studio 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **기존 항목**을 선택하고 추가할 파일로 이동합니다. **확인**을 선택하면 이러한 파일이 프로젝트 트리에 표시됩니다.
1. 코드를 하위 폴더로 구성하려면 프로젝트를 마우스 오른쪽 단추로 클릭하고 먼저 **추가** > **새 폴더**를 선택한 다음, 파일을 해당 폴더로 복사하고 3단계의 기존 항목을 추가합니다.

## <a name="project-properties"></a>프로젝트 속성

프로젝트 속성 페이지를 열려면 **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택하거나, **프로젝트 > (프로젝트 이름) 속성** 메뉴 항목을 선택합니다. 창이 열리면 프로젝트 속성이 표시됩니다.

| 탭 | 속성 | 설명 |
| --- | --- | --- |
| Run | 시작 파일 | **소스 시작 파일** 명령, **F5**, **디버그** > **디버깅 시작** 또는 **디버그** > **디버깅하지 않고 시작**을 통해 실행된 파일의 이름입니다. 프로젝트에서 파일을 마우스 오른쪽 단추로 클릭하고 **시작 R 스크립트로 설정**을 선택해도 시작 파일로 설정됩니다. |
| | 실행 시 R 대화형 다시 설정 | 프로젝트를 실행할 때 대화형 창의 작업 영역에서 모든 변수를 지웁니다. 이 작업을 실행하면 이전 실행의 남은 작업 영역 콘텐츠가 없게 됩니다. |
| | 원격 프로젝트 경로 | 원격 작업 영역의 경로입니다. |
| | 실행 시 파일 전송 | **전송할 파일**에서 필터를 적용할 프로젝트 파일을 실행할 때마다 원격 작업 영역으로 복사할지 여부를 나타냅니다. |
| | 전송할 파일 | **실행 시 파일 전송**이 선택된 경우 원격 작업 영역으로 복사할 특정 파일을 나타내는 파일 이름 및 와일드카드입니다. |
| 설정 | (Settings.R 파일) | R 프로젝트 설정은 프로젝트 내부에 있는 *Settings.R* 또는 * *.Settings.R* 파일에서 가져옵니다. 설정 파일이 없는 경우 변수를 추가하고 페이지를 저장할 수 있으며, 기본 *Settings.R* 파일이 자동으로 생성됩니다. **파일** > **새 항목 추가** 메뉴 명령을 통해 프로젝트에 설정 파일을 추가할 수도 있습니다. <br/> 설정은 R 코드로 저장되며, 다른 모듈을 실행하기 전에 파일을 원본 제공하여 환경을 미리 정의된 설정으로 미리 채울 수 있습니다. |

## <a name="r-specific-project-commands"></a>R 관련 프로젝트 명령

Visual Studio 프로젝트는 마우스 오른쪽 클릭 메뉴 및 **프로젝트** 메뉴를 통해 다양한 일반적인 명령을 지원합니다. 이러한 일반적인 기능에 대한 자세한 내용은 [Visual Studio의 솔루션 및 프로젝트](../ide/solutions-and-projects-in-visual-studio.md)를 참조하세요. 하지만 RTVS(Visual Studio용 R 도구)에서는 다양한 자체 명령을 R 프로젝트 및 프로젝트 내 파일과 폴더에 대한 마우스 오른쪽 클릭 메뉴에 추가한다는 것에 주의하세요.

| 명령 | 설명 |
| --- | --- |
| 여기에 작업 디렉터리 설정 | R 대화형 창의 작업 디렉터리를 프로젝트 내의 모든 하위 폴더에서도 사용할 수 있는 프로젝트 폴더로 설정합니다. |
| 상위 폴더 열기 | 선택한 파일의 위치에서 Windows 탐색기를 엽니다. |
| R 스크립트 추가 | 기본 이름으로 새 *.R* 파일을 만들고 엽니다. **추가** > **새 항목** 명령을 사용하여 *.R* 파일 및 다양한 기타 파일 형식을 만들 수도 있습니다. [R 관련 항목 템플릿](#r-specific-item-templates)을 참조하세요. |
| R Markdown 추가 | 기본 이름으로 새 *.rmd* 문서를 만들고 엽니다. **추가** > **새 항목** 명령을 사용하여 *.rmd* 파일 및 다양한 기타 파일 형식을 만들 수도 있습니다. [R 관련 항목 템플릿](#r-specific-item-templates)을 참조하세요.  |
| 저장 프로시저 게시 | R 스크립트에 포함된 저장 프로시저를 게시하기 위한 프로세스를 시작합니다. [SQL Server 저장 프로시저 작업](integrating-sql-server-with-r.md#work-with-sql-server-stored-procedures)을 참조하세요. |

## <a name="r-specific-item-templates"></a>R 관련 항목 템플릿

RTVS에는 특정 파일 형식에 대한 다양한 템플릿이 포함되어 있습니다. R 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택하거나, **프로젝트** > **새 항목 추가**를 선택하거나, **파일** > **새로 만들기** > **파일**을 사용하고 **R** 탭을 선택하여 템플릿에 액세스합니다. 템플릿을 탐색하는 가장 좋은 방법은 새 프로젝트를 만들고 각 형식의 파일을 삽입하는 것입니다.

> [!Note]
> **추가** > **새 항목** 명령은 표에 나열되지 않은 일반적인 파일 형식도 표시합니다. **파일** > **새로 만들기** > **파일**을 사용하면 해당 형식이 **일반** 탭에 포함됩니다.

| 파일 형식 | 설명 |
| --- | --- |
| R 스크립트 | R 명령줄에서 입력할 수 있는 동일한 명령이 포함된 텍스트 파일입니다. |
| R Markdown | [R Markdown](rmarkdown-with-r-in-visual-studio.md) 문서가 포함된 파일입니다. |
| R 설정 | R 애플리케이션 설정을 포함하는 파일입니다. |
| R 설명서 | 이름, 별칭 및 제목 필드만 포함된 일반 R 설명서 파일입니다. |
| R 설명서(함수) | 함수를 설명하기 위한 많은 필드가 주석과 함께 포함된 R 설명서 파일입니다. |
| R 설명서(데이터 세트) | 데이터 세트를 설명하기 위한 많은 필드가 주석과 함께 포함된 R 설명서 파일입니다. |
| SQL 쿼리 | 빈 *.sql* 파일입니다. [SQL Server 및 R 사용](integrating-sql-server-with-r.md)을 참조하세요. |
| 저장 프로시저(R 사용) | 자식 SQL 쿼리 및 자식 저장 프로시저 템플릿 파일이 있는 R 파일입니다. [SQL Server 및 R 사용](integrating-sql-server-with-r.md)을 참조하세요. |

## <a name="use-multiple-project-types-in-visual-studio"></a>Visual Studio에서 여러 프로젝트 형식 사용

Visual Studio 솔루션은 관련 프로젝트를 하나의 논리적 위치에서 수집 및 관리할 수 있는 편리한 위치를 제공합니다. 솔루션을 사용하여 코드를 정리된 상태로 유지하고 팀 내에서 쉽게 협업을 진행할 수 있습니다.

아래 예제에서 솔루션에는 R과 Azure Machine Learning을 사용하여 빌드된 모델이 포함된 R 프로젝트, Python/scikit-learn 프로젝트, 계산 집약적인 작업에 대한 모듈이 포함된 C++ 프로젝트, 데이터 관리에 대한 SQL 프로젝트 및 결과를 게시하는 웹 사이트에 대한 Python/Bottle 프로젝트가 포함됩니다.

![솔루션의 여러 관련 프로젝트를 보여 주는 Visual Studio 솔루션 탐색기](media/projects-polyglot.png)

굵게 강조 표시된 프로젝트는 솔루션에 대한 “시작” 프로젝트입니다. 변경하려면 다른 프로젝트를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.

> [!Note]
> 현재 명시적인 R과 C#/C++의 언어 통합이 제공되지 않습니다. 제공되는 Python 언어 통합에 대해서는 [Python용 C++ 확장 만들기](../python/working-with-c-cpp-python-in-visual-studio.md)를 참조하세요.  하지만 R에 대한 C# 및 C++ 브리지를 제공하는 라이브러리를 사용할 수 있습니다.

일반적인 프로젝트 및 솔루션 관리에 대한 자세한 내용은 [Visual Studio의 솔루션 및 프로젝트](../ide/solutions-and-projects-in-visual-studio.md)를 참조하세요.
