---
title: Visual Studio 폴더 확장 확장 개요 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d213a7add358c46f7088f504d8c54352cda44a1c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905968"
---
# <a name="open-folder-extensibility"></a>폴더 확장 열기

[폴더 열기](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 기능을 사용 하면 사용자가 프로젝트 또는 솔루션 파일이 없어도 Visual Studio에서 코드 베이스를 열 수 있습니다. 폴더 열기는 다음과 같은 Visual Studio에서 사용자가 필요로 하는 기능을 제공 합니다.

* 솔루션 탐색기 통합 및 검색
* 편집기 색 지정
* 탐색으로 이동
* 파일에서 찾기 검색

.NET 및 c + + 개발과 같은 워크 로드와 함께 사용 하는 경우 사용자는 다음을 얻을 수 있습니다.

* 풍부한 Intellisense
* 언어별 기능

열려 있는 폴더를 사용 하 여 확장 작성자는 모든 언어에 대 한 풍부한 기능을 만들 수 있습니다. 사용자의 코드 베이스에 있는 모든 파일에 대 한 빌드, 디버깅 및 기호 검색을 지 원하는 Api가 있습니다. 현재 extender는 프로젝트 또는 솔루션을 백업 하지 않고 코드를 이해 하도록 기존 Visual Studio 기능을 업데이트할 수 있습니다.

## <a name="an-api-without-project-systems"></a>프로젝트 시스템이 없는 API

지금까지 Visual Studio는 프로젝트 시스템을 사용 하 여 솔루션 및 해당 프로젝트에서 파일을 인식 했습니다. 프로젝트 시스템은 로드 된 프로젝트의 기능 및 사용자 상호 작용을 담당 합니다. 프로젝트에 포함 된 파일, 프로젝트 내용의 시각적 표시, 다른 프로젝트에 대 한 종속성 및 기본 프로젝트 파일의 수정 내용을 이해 합니다. 다른 구성 요소가 사용자를 대신 하 여 작업을 수행 하는 이러한 계층 구조 및 기능을 통해 수행 됩니다. 모든 코드 베이스가 프로젝트 및 솔루션 구조에 잘 표시 되는 것은 아닙니다. Linux 용 c + +로 작성 된 스크립트 언어 및 오픈 소스 코드는 좋은 예입니다. 열려 있는 폴더를 사용 하 여 Visual Studio에서는 사용자에 게 소스 코드와 상호 작용할 수 있는 새로운 방법을 제공 합니다.

Open Folder Api는 네임 스페이스 아래에 있으며 `Microsoft.VisualStudio.Workspace.*` extender가 Open 폴더 내의 파일에 대 한 데이터 또는 작업을 생성 하 고 사용 하는 데 사용할 수 있습니다. 확장은 다음을 비롯 한 여러 영역에 대 한 기능을 제공 하기 위해 이러한 Api를 사용할 수 있습니다.

- [작업 영역](workspaces.md) -열린 폴더 확장성의 시작점은 작업 영역 및 해당 api입니다.
- 파일 [컨텍스트 및 작업](workspace-file-contexts.md) -파일 컨텍스트를 통해 제공 되는 파일 관련 코드 인텔리전스.
- [인덱싱](workspace-indexing.md) -열린 폴더 작업 영역에 대 한 데이터를 수집 하 고 유지 합니다.
- [언어 서비스](workspace-language-services.md) -공개 폴더 작업 영역에 언어 서비스를 통합 합니다.
- [빌드](workspace-build.md) -폴더 열기 작업 영역에 대 한 빌드 지원.

다음 형식을 사용 하는 기능은 Open 폴더를 지원 하기 위해 새 Api를 채택 해야 합니다.

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>피드백, 설명, 문제

폴더를 열고 `Microsoft.VisualStudio.Workspace.*` api가 활성 개발 중입니다. 예기치 않은 동작이 표시 되는 경우 관심 릴리스에 대 한 알려진 문제를 참조 하세요. [개발자 커뮤니티](https://developercommunity.visualstudio.com) 는 투표 하 고 문제를 생성 하는 데 권장 되는 장소입니다. 각 피드백에 대해 문제에 대 한 자세한 설명을 적극 권장 합니다. 개발 중인 Visual Studio 버전, 사용 중인 Api (구현한 항목 및 상호 작용 하는 항목), 예상 결과 및 실제 결과를 포함 합니다. 가능 하면 devenv.exe 프로세스의 덤프를 포함 합니다. 이 문서 및 관련 설명서에 대 한 피드백을 제공 하기 위해 GitHub의 문제 추적을 사용 합니다.

## <a name="next-steps"></a>다음 단계

* [작업 영역](workspaces.md) -폴더 열기 작업 영역 API에 대해 알아봅니다.