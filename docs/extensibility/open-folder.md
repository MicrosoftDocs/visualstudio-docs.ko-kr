---
title: Visual Studio 폴더 열기 확장성 개요 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d213a7add358c46f7088f504d8c54352cda44a1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905968"
---
# <a name="open-folder-extensibility"></a>폴더 열기 확장성

[폴더 열기](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 기능을 사용하면 사용자가 프로젝트 또는 솔루션 파일 없이 Visual Studio에서 코드 베이스를 열 수 있습니다. 폴더 열기는 다음과 같이 Visual Studio에서 사용자에게 필요한 기능을 제공합니다.

* 솔루션 탐색기 통합 및 검색
* 편집기 색 지정
* 탐색으로 이동
* 파일에서 찾기 검색

.NET 및 C++ 개발 등과 같은 워크로드에 사용하는 경우에는 이러한 기능도 제공합니다.

* 풍부한 IntelliSense
* 언어별 기능

폴더 열기를 사용하여 확장 작성자는 모든 언어에 대한 풍부한 기능을 만들 수 있습니다. 사용자의 코드베이스에 있는 모든 파일에 대한 빌드, 디버깅 및 기호 검색을 지원하는 API가 있습니다. 현재 Extender는 프로젝트 또는 솔루션을 백업하지 않고 코드를 이해할 수 있도록 기존 Visual Studio 기능을 업데이트할 수 있습니다.

## <a name="an-api-without-project-systems"></a>프로젝트 시스템이 없는 API

지금까지는 Visual Studio에서 프로젝트 시스템을 사용하여 솔루션 및 해당 프로젝트에 있는 파일을 인식했습니다. 프로젝트 시스템은 로드된 프로젝트의 기능 및 사용자 상호 작용을 담당합니다. 프로젝트에 포함된 파일, 프로젝트 콘텐츠의 시각적 표시, 다른 프로젝트에 대한 종속성 및 기본 프로젝트 파일의 수정 내용을 이해합니다. 다른 구성 요소가 사용자를 대신하여 수행하는 계층 구조 및 기능을 통해 이루어집니다. 일부 코드베이스가 프로젝트 및 솔루션 구조에 잘 표시되지 않습니다. Linux용 C++로 작성된 스크립팅 언어 및 오픈 소스 코드가 좋은 예입니다. 폴더 열기를 사용하면 Visual Studio에서 사용자에게 소스 코드와 상호 작용할 수 있는 새로운 방법을 제공합니다.

폴더 열기 API는 `Microsoft.VisualStudio.Workspace.*` 네임스페이스에 있으며 Extender가 폴더 열기 내의 데이터 또는 파일 관련 작업을 생성하고 사용할 수 있습니다. 확장은 해당 API를 사용하여 다음을 포함한 여러 영역에 대한 기능을 제공할 수 있습니다.

- [작업 영역](workspaces.md) - 폴더 열기 확장성의 시작점은 작업 영역과 해당 API입니다.
- [파일 컨텍스트 및 작업](workspace-file-contexts.md) - 파일 컨텍스트를 통해 제공되는 파일별 코드 인텔리전스입니다.
- [인덱싱](workspace-indexing.md) - 폴더 열기 작업 영역에 대한 데이터를 수집하고 유지합니다.
- [언어 서비스](workspace-language-services.md) - 폴더 열기 작업 영역에 언어 서비스를 통합합니다.
- [빌드](workspace-build.md) - 폴더 열기 작업 영역에 대한 지원을 빌드합니다.

다음 형식을 사용하는 기능은 폴더 열기를 지원하기 위해 새 API를 채택해야 합니다.

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>피드백, 의견, 문제

폴더 열기와 `Microsoft.VisualStudio.Workspace.*` API는 현재 개발 중입니다. 예기치 않은 동작을 보게 되는 경우 해당 릴리스에 대한 알려진 문제를 확인하세요. [Developer Community](https://developercommunity.visualstudio.com)는 투표와 문제 제기에 있어 권장되는 장소입니다. 모든 피드백에 관해서는 구체적으로 문제를 설명하는 것이 좋습니다. 개발 대상인 Visual Studio 버전, 사용 중인 API(구현한 API 및 상호 작용하는 API), 예상 결과 및 실제 결과를 포함합니다. 가급적 devenv.exe 프로세스의 덤프를 포함합니다. 이 문서 및 관련 문서에 대한 피드백 제공은 GitHub의 문제 추적을 사용하세요.

## <a name="next-steps"></a>다음 단계

* [작업 영역](workspaces.md) - 폴더 열기 작업 영역 API에 대해 알아봅니다.