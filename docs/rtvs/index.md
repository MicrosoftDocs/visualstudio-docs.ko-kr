---
title: R Tools for Visual Studio
description: Visual Studio 2017용 R 도구(RTVS)는 IntelliSense, 디버깅 및 원격 작업 영역을 비롯한 여러 언어 기능을 제공하는 무료 오픈 소스 확장입니다.
ms.date: 11/13/2017
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 1132a7a0363e2d508d6eff1026192aad3407fca4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "73189247"
---
# <a name="work-with-r-in-visual-studio"></a>Visual Studio에서 R 작업

R은 통계 계산 및 그래픽을 위한 고도로 확장 가능한 언어 및 환경입니다. 이 프로그램은 GNU General Public License에 따라 무료로 배포되며, 강력한 커뮤니티 지원을 활용할 수 있고, 수학 기호 및 수식을 포함하는 게시 품질 도표를 생성하는 기능으로 잘 알려져 있습니다. [r project.org](https://www.r-project.org/about.html) 및 [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html)(R 소개)에서 R에 대해 자세히 알아볼 수 있습니다.

RTVS(R Tools for Visual Studio)는 MIT 라이선스에 따라 출시된 Visual Studio 2017 및 Visual Studio 2015 Update 3 이상을 위한 무료 [오픈 소스](https://github.com/microsoft/RTVS) 확장 프로그램입니다. ([RHost](https://github.com/microsoft/R-Host)라고 하며 R 인터프리터 이진 파일에 연결되는 또 다른 오픈 소스 구성 요소가 GNU 공용 라이선스 V2에 따라 출시되었습니다.)

> [!Note]
> RTVS는 현재 Windows 기반의 Visual Studio 2017에서만 지원되고 Mac용 Visual Studio에서는 지원되지 않습니다. Visual Studio 2019에는 사용할 수 없습니다.

Visual Studio에서 R을 사용해 보려면

- [R Tools를 설치](installing-r-tools-for-visual-studio.md)합니다.
- [시작](getting-started-with-r.md) 가이드와 [샘플](getting-started-samples.md) 및 [도움말 보기](getting-started-help.md) 문서를 수행합니다.

그런 후 아래 링크에 따라 R 관련 기능과 Visual Studio 자체의 일반 기능에 대해 알아보세요.

| 기능 | 설명 | 일반 Visual Studio 설명서 |
| --- | --- | --- |
| [Visual Studio 프로젝트 시스템](r-projects-in-visual-studio.md) | 관련 파일을 편리한 구조로 구성하고 관리하며, R 코드, R 설명서, R Markdown, SQL 쿼리 및 저장 프로시저와 같은 항목에 대한 유용한 템플릿을 사용할 수 있습니다. 또한 [패키지 관리자](r-package-manager-in-visual-studio.md) 및 [SQL Server Integration](integrating-sql-server-with-r.md) 기능도 사용해볼 수 있습니다.  | [Visual Studio의 솔루션 및 프로젝트](../ide/solutions-and-projects-in-visual-studio.md) |
| [작업 영역](r-workspaces-in-visual-studio.md) | RTVS는 로컬 및 원격 작업 영역에 바인딩되어 좀 더 작은 데이터 집합으로 로컬로 R 코드를 개발한 다음, 훨씬 더 큰 데이터 집합을 사용해서 더욱 강력한 클라우드 기반 컴퓨터에서 코드를 쉽게 실행할 수 있도록 합니다. | N/A |
| [R Tools 옵션](options-for-r-tools-in-visual-studio.md) | RTVS의 다양한 측면을 제어합니다. | [옵션 대화 상자](../ide/reference/options-dialog-box-visual-studio.md) |
| [다양한 편집 기능, IntelliSense 및 코드 조각](editing-r-code-in-visual-studio.md) | 구문 색 지정, 모든 코드 및 라이브러리에 대한 [IntelliSense](r-intellisense.md), 코드 서식 지정, 시그니처 도움말, 정의로 이동, 모든 참조 찾기, [코드 조각](code-snippets-for-r.md) 등을 포함합니다. | [코드 편집기의 기능](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | R Markdown 문서는 데이터 결과를 markdown 코드 블록 내에 통합된 R 코드와 공유하도록 도와줍니다. | N/A |
| [대화형 창](interactive-repl-for-r-in-visual-studio.md) | R에 대한 전체 REPL 환경에 대화형 창에서 소스 파일의 코드를 쉽게 실행할 수 있는 기능을 제공합니다. | N/A |
| [코드 시각화](visualizing-data-with-r-in-visual-studio.md) | 도표는 R 환경의 통합 부분이며, RTVS는 각각이 자체적인 기록과 창 간에 도표를 이동하는 기능을 갖춘 여러 개의 독립적인 도표 창을 지원합니다. 도표는 비트맵 및 PDF 파일에 저장되거나 비트맵 또는 메타파일로 클립보드에 복사될 수 있습니다.  | N/A |
| [변수 탐색기](variable-explorer.md) | 정렬 가능한 표를 보고 CSV로 내보내는 기능을 사용해 전역 또는 패키지별 범위에서 변수를 검사합니다. | N/A |
| [완전한 기능의 디버깅](debugging-r-in-visual-studio.md) | 대화형 창과의 통합을 포함합니다. | [Visual Studio의 디버깅](../debugger/debugger-feature-tour.md) |

[질문과 대답](faq.md)을 참조하세요.

|   |   |
|---|---|
| ![동영상에 대한 비디오 카메라 아이콘](../install/media/video-icon.png "비디오 시청") | Visual Studio용 R 도구(12m 36s)의 개요에 대한 [비디오 보기(youtube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ). 또한 [더 많은 R 도구 비디오](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio)를 참조합니다. |

## <a name="send-us-your-feedback"></a>피드백을 보내주세요.

1. **GitHub 문제**: RTVS 팀에 연락하는 가장 좋은 방법은 [GitHub에서 문제를 신고](https://github.com/Microsoft/RTVS/issues)하거나 **R Tools** > **피드백** 메뉴를 사용하는 것입니다.

1. **웃는 얼굴/찡그린 얼굴 보내기**: **R Tools** > **피드백** 메뉴에서는 문제점 진단에 도움이 될 수 있게 신속하게 피드백을 보내고 RTVS 로그 파일을 첨부할 수 있습니다. (로그를 따로 전송하려는 경우 해당 로그가 *%temp%/RTVSlogs.zip*에 기록됩니다.) **도움말** > **피드백** > **설정** 메뉴 명령을 사용하거나 설치 중에 Visual Studio 원격 분석에서 옵트아웃하면 로깅이 사용되지 않도록 설정됩니다.

1. **이메일**: *microsoft.com의 rtvsuserfeedback*에서 팀으로 직접 피드백을 보낼 수 있습니다.
