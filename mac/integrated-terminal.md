---
title: Mac용 Visual Studio - 통합 터미널
description: Mac용 Visual Studio에서는 iOS, Android, Mac, Xamarin.Forms용 Xamarin 프로젝트와 ASP.NET Core 웹 사이트를 비롯하여 macOS에서 .NET 애플리케이션을 빌드하기 위한 통합 개발 환경을 제공합니다.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: d362938e8f0075591ea5d4ed8461d11395680b5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84185676"
---
# <a name="integrated-terminal"></a>통합 터미널
Mac용 Visual Studio에서 처음에는 솔루션의 루트에서 시작하여 통합 터미널 창을 열 수 있습니다. 터미널은 프런트 엔드 작업 실행(예: npm, ng, vue), 컨테이너 관리, 고급 Git 명령 실행, Entity Framework 명령 실행, dotnet CLI 출력 보기, NuGet 패키지 추가 등의 여러 상황에 유용할 수 있습니다. 

터미널을 열려면 다음을 수행합니다.
- **Ctrl+`** 바로 가기 키를 사용하여 터미널 창을 표시하거나 숨깁니다.
- **보기** \> **패드** \> **터미널** 메뉴를 사용합니다.
- 검색 표시줄에서 **terminal** 명령을 사용합니다.

![*실행된 직후의 Mac용 Visual Studio 통합 터미널*](media/integrated-terminal-intro.png)

기본적으로 터미널이 시작되면 다음을 수행합니다.
- 작업 디렉터리를 현재 솔루션의 경로로 설정합니다.
- 기본 시스템 셸을 로드합니다.

## <a name="search"></a>검색
**검색 > 찾기...** 메뉴를 사용하여 터미널 창의 콘텐츠를 검색할 수 있습니다.

![*Mac용 Visual Studio 통합 터미널의 검색 환경*](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>터미널 바로 가기 키
|명령|바로 가기 키|
|-|-|
|터미널 창 표시/숨기기|**Ctrl+`**|
|새 터미널 인스턴스 만들기|**Ctrl+'**|
|페이지 위로 스크롤|**PageUp**|
|페이지 아래로 스크롤|**PageDown**|
|이전에 사용한 명령 순환|**↑**, **↓**|
|글꼴 크기 크게|**⌘+**|
|글꼴 크기 작게|**⌘-**|

## <a name="multiple-instances"></a>여러 인스턴스
언제든 터미널의 여러 인스턴스를 실행할 수 있습니다. **Ctrl+'** 바로 가기 키를 사용하여 새 인스턴스를 만들 수 있습니다. 각 인스턴스에 대해 탭을 클릭하거나 **Ctrl+Tab** 바로 가기 키를 통해 창 선택기 대화 상자를 사용하여 인스턴스 간을 전환할 수 있습니다.

![*Mac용 Visual Studio의 여러 터미널 인스턴스*](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>터미널 창 사용자 지정
### <a name="configuring-the-terminal-font"></a>터미널 글꼴 구성
기본 설정 > 환경 > 글꼴 창에서 터미널 콘텐츠에 사용되는 글꼴 및 크기를 변경할 수 있습니다. 기본적으로 글꼴은 출력 패드 콘텐츠와 같이 Menlo Regular, 크기 11을 사용합니다. 편집기 글꼴과 관계없이 원하는 글꼴로 설정할 수 있습니다.

![*통합 터미널의 글꼴 설정 사용자 지정*](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>시스템 터미널 사용자 지정 다시 사용
통합 터미널은 macOS 시스템 터미널과 동일한 기본값과 구성을 사용합니다. 즉, 터미널 사용자 지정(zsh, oh-my-zsh 등)도 통합 터미널에서 사용할 수 있습니다.
