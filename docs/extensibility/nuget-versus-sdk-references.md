---
title: NuGet을 사용한 참조 추가와 확장명 SDK를 사용한 참조 추가
description: Visual Studio 프로젝트에서 참조 하는 경우 소프트웨어를 NuGet 패키지로 패키지 하는 경우와 소프트웨어 개발 키트의 차이점에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab2a99c2230c9fc150fe06c305741eedf14ded37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874037"
---
# <a name="nuget-versus-sdk-as-a-project-reference"></a>프로젝트 참조로 서의 NuGet 및 SDK

이 문서는 개발자가 소프트웨어를 NuGet 패키지로 패키지할 지, 아니면 SDK (소프트웨어 개발 키트)로 패키지할 지를 돕기 위해 작성 되었습니다. 특히 Visual Studio 프로젝트에서 참조 되는 경우 두 가지 간의 차이점을 설명 합니다.

- [NuGet](/nuget) 은 프로젝트에 라이브러리를 통합 하는 프로세스를 간소화 하는 오픈 소스 패키지 관리 시스템입니다. .Net (.NET Core 포함)의 경우 NuGet은 코드를 공유 하는 Microsoft 지원 메커니즘입니다. NuGet은 .NET 용 패키지를 만들고 호스트 하 고 사용 하는 방법을 정의 하 고 각 역할에 대 한 도구를 제공 합니다. Visual Studio에서 [패키지 관리자](/nuget/consume-packages/install-use-packages-visual-studio) 사용자 인터페이스를 사용 하 여 NuGet 패키지를 프로젝트에 추가 합니다.

- [SDK](../extensibility/creating-a-software-development-kit.md) 는 Visual Studio에서 단일 참조 항목으로 처리 하는 파일의 컬렉션입니다. Visual Studio의 참조 관리자 대화 상자에는 **참조 추가** 를 선택 하는 경우 현재 프로젝트와 관련 된 모든 sdk가 나열 됩니다. 프로젝트에 SDK를 추가 하는 경우 IntelliSense, 도구 상자 창, 디자이너, 개체 브라우저, MSBuild, 배포, 디버깅 및 패키징을 통해 해당 SDK의 모든 콘텐츠에 액세스할 수 있습니다.

## <a name="which-mechanism-should-i-use"></a>어떤 메커니즘을 사용해야 하나요?

다음 표에서는 SDK의 참조 기능과 NuGet의 참조 기능을 비교합니다.

| 기능 | SDK 지원 | SDK 참고 사항 | NuGet 지원 | NuGet 참고 사항 |
| - | - | - |---------------| - |
| 메커니즘에서 하나의 엔터티를 참조하면 모든 파일과 기능을 사용할 수 있습니다. | Y | **참조 관리자** 대화 상자를 사용하여 SDK를 추가하면 개발 워크플로 중에 모든 파일과 기능을 사용할 수 있습니다. | Y | |
| MSBuild에서 어셈블리와 Windows 메타데이터(*.winmd*) 파일을 자동으로 사용합니다. | Y | SDK의 참조가 컴파일러에 자동으로 전달됩니다. | Y | |
| MSBuild에서 .h 또는 .lib 파일을 자동으로 사용합니다. | Y | *.h* 또는 *.lib* 파일을 자동으로 사용하기 위한 Visual C++ 디렉터리 설정 방법 등이 *SDKName.props* 파일을 통해 Visual Studio에서 지정됩니다. | N | |
| MSBuild에서 *.js* 또는 *.css* 파일을 자동으로 사용합니다. | Y | **솔루션 탐색기** 에서 JavaScript SDK 참조 노드를 확장하여 개별 *.js* 또는 *.css* 파일을 표시한 다음, 해당 파일을 소스 파일로 끌어 `<source include/>` 태그를 생성할 수 있습니다. SDK에서 F5 키와 자동 패키지 설치를 지원합니다. | Y | |
| MSBuild에서 **도구 상자** 에 컨트롤을 자동으로 추가합니다. | Y | **도구 상자** 에서 SDK를 사용하고 지정된 탭에 컨트롤을 표시할 수 있습니다. | N | |
| 메커니즘에서 VSIX(확장용 Visual Studio 설치 관리자)를 지원합니다. | Y | VSIX에 SDK 패키지를 만들기 위한 특수 매니페스트 및 논리가 있습니다. | Y | 다른 설치 프로그램에 VSIX를 포함할 수 있습니다. |
| **개체 브라우저** 에 참조가 열거됩니다. | Y | **개체 브라우저** 에서 자동으로 SDK의 참조 목록을 가져와서 열거합니다. | N | |
| 파일 및 링크가 **참조 관리자** 대화 상자에 자동으로 추가됩니다(도움말 링크 등의 자동 채우기). | Y | **참조 관리자** 대화 상자에 SDK가 도움말 링크 및 SDK 종속성 목록과 함께 자동으로 열거됩니다. | N | NuGet은 고유한 **NuGet 패키지 관리** 대화 상자를 제공합니다. |
| 메커니즘에서 여러 아키텍처를 지원합니다. | Y | SDK는 여러 구성을 제공할 수 있습니다. MSBuild에서 각 프로젝트 구성에 적합한 파일을 사용합니다. | N | |
| 메커니즘에서 여러 구성을 지원합니다. | Y | SDK는 여러 구성을 제공할 수 있습니다. 프로젝트 아키텍처에 따라 MSBuild에서 각 프로젝트 아키텍처에 적합한 파일을 사용합니다. | N | |
| 메커니즘에서 “복사하지 않을 항목”을 지정할 수 있습니다. | Y | *\redist* 또는 *\designtime* 폴더에 파일을 넣는지에 따라 소비 애플리케이션 패키지에 복사할 파일을 제어할 수 있습니다. | N | 패키지 매니페스트에서 복사할 파일을 선언합니다. |
| 콘텐츠가 지역화된 파일에 표시됩니다. | Y | 디자인 타임 환경 개선을 위해 SDK의 지역화된 XML 문서가 자동으로 포함됩니다. | N | |
| MSBuild에서 동시에 여러 버전의 SDK를 사용할 수 있도록 지원합니다. | Y | SDK에서 동시에 여러 버전을 사용할 수 있도록 지원합니다. | N | 참조가 아닙니다. 프로젝트에 여러 버전의 NuGet 파일을 동시에 사용할 수 없습니다. |
| 메커니즘에서 해당하는 대상 프레임워크, Visual Studio 버전 및 프로젝트 형식을 지정할 수 있도록 지원합니다. | Y | 사용자가 적절한 SDK를 쉽게 선택할 수 있도록 프로젝트에 적용되는 SDK만 **참조 관리자** 대화 상자와 **도구 상자** 에 표시됩니다. | Y(부분) | 피벗이 대상 프레임워크입니다. 사용자 인터페이스에 필터링이 없습니다. 설치 시 오류가 반환될 수도 있습니다. |
| 메커니즘에서 네이티브 WinMD에 대한 등록 정보를 지정할 수 있도록 지원합니다. | Y | *SDKManifest.xml* 에서 .winmd 파일과 .dll 파일 간의 상관 관계를 지정할 수 있습니다. | N | |
| 메커니즘에서 다른 SDK에 대한 종속성을 지정할 수 있도록 지원합니다. | Y | SDK는 사용자에게 알림만 제공하며, 사용자가 설치하고 수동으로 참조해야 합니다. | Y | NuGet이 자동으로 끌어오며 사용자에게 알리지 않습니다. |
| 메커니즘이 앱 매니페스트 및 프레임워크 ID와 같은 [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] 개념과 통합됩니다. | Y | 패키징 및 F5 키가 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]를 통해 제공되는 SDK에서 제대로 작동하도록 SDK가 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 관련 개념을 전달해야 합니다. | N | |
| 메커니즘이 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 앱에 대한 앱 디버깅 파이프라인과 통합됩니다. | Y | 패키징 및 F5 키가 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]를 통해 제공되는 SDK에서 제대로 작동하도록 SDK가 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 관련 개념을 전달해야 합니다. | Y | NuGet 콘텐츠는 프로젝트의 일부가 됩니다. F5 키를 특별히 고려하지 않아도 됩니다. |
| 메커니즘이 앱 매니페스트와 통합됩니다. | Y | 패키징 및 F5 키가 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]를 통해 제공되는 SDK에서 제대로 작동하도록 SDK가 [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] 관련 개념을 전달해야 합니다. | Y | NuGet 콘텐츠는 프로젝트의 일부가 됩니다. F5 키를 특별히 고려하지 않아도 됩니다. |
| 메커니즘에서 비참조 파일을 배포합니다(예: [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 앱 테스트를 실행할 테스트 프레임워크 배포). | Y | *\redist* 폴더에 파일을 넣는 경우 파일이 자동으로 배포됩니다. | Y | |
| 메커니즘에서 플랫폼 SDK를 Visual Studio IDE에 자동으로 추가합니다. | Y | [!INCLUDE[win8](../debugger/includes/win8_md.md)] SDK 또는 Windows Phone SDK를 특정 위치에 특정 레이아웃으로 넣는 경우 SDK가 모든 Visual Studio 기능과 자동으로 통합됩니다. | N | |
| 메커니즘에서 클린 개발자 컴퓨터를 지원합니다. 즉, 설치할 필요가 없으며 소스 코드 제어에서 간단하게 검색할 수 있습니다. | N | SDK를 참조하기 때문에 솔루션과 SDK를 별도로 체크 인해야 합니다. MSBuild가 SDK를 반복하는, 레지스트리가 아닌 두 개의 기본 위치에서 SDK를 체크 인할 수 있습니다(자세한 내용은 [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md) 참조). 또는 사용자 지정 위치가 SDK로 구성된 경우 프로젝트 파일에서 다음 코드를 지정할 수 있습니다.<br /><br />`<PropertyGroup>`<br />&nbsp;&nbsp;`<SDKReferenceDirectoryRoot>`<br />&nbsp;&nbsp;`C:\MySDKs`<br />&nbsp;&nbsp;`</SDKReferenceDirectoryRoot>`<br />`</PropertyGroup>`<br /><br /> 그런 다음 해당 위치에 SDK를 체크 인합니다. | Y | 솔루션을 체크 아웃하면 Visual Studio에서 즉시 파일을 인식하고 작업을 수행합니다. |
| 기존의 대규모 패키지 작성자 커뮤니티에 연결할 수 있습니다. | 해당 없음 | 커뮤니티는 새로운 기능입니다. | Y | |
| 기존의 대규모 패키지 소비자 커뮤니티에 연결할 수 있습니다. | 해당 없음 | 커뮤니티는 새로운 기능입니다. | Y | |
| 파트너 에코시스템(사용자 지정 갤러리, 리포지토리 등)에 연결할 수 있습니다. | 해당 없음 | 사용 가능한 리포지토리로는 Visual Studio Marketplace, Microsoft 다운로드 센터, [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] 등이 있습니다. | Y | |
| 패키지 생성 및 사용 둘 다를 위해 메커니즘이 연속 통합 빌드 서버와 통합됩니다. | Y | SDK에서 명령줄을 통해 체크 인된 위치(SDKReferenceDirectoryRoot 속성)를 MSBuild에 전달해야 합니다. | Y | |
| 메커니즘에서 안정적인 패키지 버전과 시험판 패키지 버전을 둘 다 지원합니다. | Y | SDK에서 여러 버전에 대한 참조 추가를 지원합니다. | Y | |
| 메커니즘에서 설치된 패키지에 대한 자동 업데이트를 지원합니다. | Y | VSIX 또는 Visual Studio 자동 업데이트의 일부로 제공된 경우 SDK에서 자동 알림을 제공합니다. | Y | |
| 메커니즘에 패키지 생성 및 사용을 위한 독립 실행형 *.exe* 파일이 포함됩니다. | Y | SDK에는 *MSBuild.exe* 가 포함됩니다. | Y | |
| 패키지를 버전 제어에 체크 인할 수 있습니다. | Y | 문서 노드 외부에서 아무것도 체크 인할 수 없으므로 확장 SDK를 체크 인하지 못할 수도 있습니다. 확장 SDK의 크기가 클 수 있습니다. | Y | |
| PowerShell 인터페이스를 사용하여 패키지를 만들고 사용할 수 있습니다. | Y(사용), N(만들기) | SDK를 만들기 위한 도구가 없습니다. 사용하려면 명령줄에서 MSBuild를 실행합니다. | Y | |
| 디버깅 지원을 위해 기호 패키지를 사용할 수 있습니다. | Y | SDK에 *.pdb* 파일을 넣으면 파일이 자동으로 선택됩니다. | Y | |
| 메커니즘에서 패키지 관리자 자동 업데이트를 지원합니다. | 해당 없음 | SDK가 MSBuild로 수정됩니다. | Y | |
| 메커니즘에서 경량 매니페스트 형식을 지원합니다. | Y | *SDKManifest.xml* 에서 많은 특성을 지원하지만 일반적으로 작은 하위 집합만 있으면 됩니다. | Y | |
| 모든 Visual Studio 버전에 메커니즘을 사용할 수 있습니다. | Y | SDK가 모든 Visual Studio 버전을 지원합니다. | Y | NuGet이 모든 Visual Studio 버전을 지원합니다. |

## <a name="see-also"></a>참조

- [프로젝트에서 참조 관리](../ide/managing-references-in-a-project.md)
- [프로젝트에서 참조 관리(Mac용 Visual Studio)](/visualstudio/mac/managing-references-in-a-project)
