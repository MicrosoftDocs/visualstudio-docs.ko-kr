---
title: VS패키지 개발을 위한 Devenv 커맨드 라인 스위치 | 마이크로 소프트 문서
ms.date: 12/10/2018
ms.topic: conceptual
helpviewer_keywords:
- /Setup command line switch
- /ResetSkipPkgs command line switch
- /RootSuffix command line switch
- /SafeMode command line switch
- /Splash command line switch
- command-line switches
- registry, Visual Studio SDK
- command line, switches
- Visual Studio SDK, command-line switches
ms.assetid: d65d2c04-dd84-42b0-b956-555b11f5a645
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad3a5125a730b9230959bbf9342b4c0a4823c4d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712189"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage 개발을 위한 Devenv 명령줄 스위치

Visual Studio를 사용하면 개발자가 Visual Studio IDE를 `devenv.exe`시작하는 파일인 실행 시 명령줄에서 작업을 자동화할 수 있습니다.

 작업에는 다음이 포함됩니다.

- IDE 외부에서 미리 설계된 구성으로 응용 프로그램을 배포합니다.

- 사전 설정된 빌드 설정 또는 디버그 구성을 사용하여 프로젝트를 자동으로 빌드합니다.

- IDE 외부에서 특정 구성에서 IDE를 로드합니다. 당신은 또한 시작시 IDE를 사용자 정의 할 수 있습니다.

## <a name="guidelines-for-switches"></a>스위치 에 대한 지침

Visual Studio 설명서는 사용자 `devenv` 수준 명령줄 스위치에 대해 설명합니다. 자세한 내용은 [Devenv 명령줄 스위치를](../ide/reference/devenv-command-line-switches.md)참조하십시오. 또한 `devenv` 이 도구는 VSPackage 개발, 배포 및 디버깅에 유용한 추가 명령줄 스위치를 지원합니다.

| 명령줄 스위치 | 설명 |
|---------------------| - |
| `/ResetSkipPkgs` | 문제가 있는 VSPackage를 로드하지 않으려는 사용자가 추가한 모든 건너뛰기 로드 옵션을 지운 다음 Visual Studio를 시작합니다. SkipLoading 태그가 있으면 VSPackage로 딩이 비활성화됩니다. 태그를 지우면 VSPackage를 다시 로드할 수 있습니다.<br /><br /> 이 스위치는 인수가 필요 없습니다. |
| `/RootSuffix` | 대체 위치를 사용하여 Visual Studio를 시작합니다. 다음 명령은 Visual Studio SDK 설치 관리자에서 만든 바로 가기에서 실행됩니다.<br /><br /> `devenv /RootSuffix exp`<br /><br /> 이 경우 `exp` 특정 접미사가 있는 위치(예: `10.0Exp` `10.0`대신)를 식별합니다. 실험 적 인스턴스를 사용하면 코드를 작성하는 데 사용하는 Visual Studio의 인스턴스와 별도로 VSPackage를 디버깅할 수 있습니다.<br /><br /> 이 스위치는 VSRegEx.exe를 사용하여 만든 위치를 식별하는 모든 문자열을 취할 수 있습니다. 자세한 내용은 [실험 인스턴스 를](../extensibility/the-experimental-instance.md)참조하십시오. |
| `/SafeMode` | 기본 IDE 및 서비스만 로드하는 안전 모드에서 Visual Studio를 시작합니다. 이 `/SafeMode` 스위치는 Visual Studio가 시작될 때 모든 타사 VSPackage가 로드되지 않도록 하여 안정적인 실행을 보장합니다.<br /><br /> 이 스위치는 인수가 필요 없습니다. |
| `/Setup` | Visual Studio를 강제로 사용 가능한 모든 VSPackage의 메뉴, 도구 모음 및 명령 그룹을 설명하는 리소스 메타데이터를 병합합니다. 이 명령은 관리자로만 실행할 수 있습니다. <br /><br /> 이 스위치는 인수가 필요 없습니다. `devenv /Setup` 명령은 일반적으로 설치 프로세스의 마지막 단계로 표시됩니다. 스위치를 `/Setup` 사용하면 IDE가 시작되지 않습니다.|
| `/Splash` | 평소와 같이 Visual Studio 시작 화면을 표시한 다음 기본 IDE를 표시하기 전에 메시지 상자를 표시합니다. 메시지 상자를 사용하면 시작 화면을 연구할 수 있습니다(예: VSPackage 제품 아이콘 확인).<br /><br /> 이 스위치는 인수가 필요 없습니다. |

## <a name="see-also"></a>참조

- [명령줄 스위치 추가](../extensibility/adding-command-line-switches.md)
- [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)
