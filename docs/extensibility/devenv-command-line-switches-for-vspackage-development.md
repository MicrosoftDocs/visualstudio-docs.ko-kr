---
title: VSPackage 개발용 Devenv 명령줄 스위치 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712189"
---
# <a name="devenv-command-line-switches-for-vspackage-development"></a>VSPackage 개발을 위한 Devenv 명령줄 스위치

개발자는 visual Studio를 사용 하 여 `devenv.exe` Visual STUDIO IDE를 시작 하는 파일을 실행 하는 경우 명령줄에서 작업을 자동화할 수 있습니다.

 작업은 다음과 같습니다.

- 미리 디자인 된 구성의 응용 프로그램을 IDE 외부에서 배포 합니다.

- 미리 설정 된 빌드 설정이 나 디버그 구성을 사용 하 여 프로젝트를 자동으로 빌드합니다.

- Ide 외부에서 특정 구성으로 IDE를 로드 합니다. 또한 시작 시 IDE를 사용자 지정할 수 있습니다.

## <a name="guidelines-for-switches"></a>스위치에 대 한 지침

Visual Studio 설명서에서는 사용자 수준 명령줄 스위치에 대해 설명 합니다 `devenv` . 자세한 내용은 [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)를 참조 하세요. `devenv`또한이 도구는 VSPackage 개발, 배포 및 디버깅에 유용한 추가 명령줄 스위치를 지원 합니다.

| 명령줄 스위치 | 설명 |
|---------------------| - |
| `/ResetSkipPkgs` | 문제가 있는 Vspackage 로드를 방지 하려는 사용자가 추가한 모든 건너뛰기 로드 옵션을 지운 다음 Visual Studio를 시작 합니다. SkipLoading 태그가 있으면 VSPackage 로드를 사용할 수 없습니다. 태그를 지우면 VSPackage을 다시 로드할 수 있습니다.<br /><br /> 이 스위치는 인수가 필요 없습니다. |
| `/RootSuffix` | 대체 위치를 사용 하 여 Visual Studio를 시작 합니다. 다음 명령은 Visual Studio SDK 설치 관리자에서 만든 바로 가기로 실행 됩니다.<br /><br /> `devenv /RootSuffix exp`<br /><br /> 이 경우는 `exp` 특정 접미사를 사용 하는 위치를 식별 합니다 (예: `10.0Exp` 대신 `10.0` ). 실험적 인스턴스를 사용 하면 코드를 작성 하는 데 사용 하 고 있는 Visual Studio의 인스턴스와 별도로 VSPackage을 디버그할 수 있습니다.<br /><br /> 이 스위치는 VSRegEx.exe을 사용 하 여 만든 위치를 식별 하는 모든 문자열을 사용할 수 있습니다. 자세한 내용은 [실험적 인스턴스](../extensibility/the-experimental-instance.md)를 참조 하세요. |
| `/SafeMode` | 안전 모드에서 Visual Studio를 시작 하 고 기본 IDE 및 서비스만 로드 합니다. `/SafeMode`스위치는 Visual Studio가 시작 될 때 모든 타사 vspackage 로드를 방지 하 여 안정적인 실행을 보장 합니다.<br /><br /> 이 스위치는 인수가 필요 없습니다. |
| `/Setup` | Visual Studio가 사용 가능한 모든 Vspackage에서 메뉴, 도구 모음 및 명령 그룹을 설명 하는 리소스 메타 데이터를 병합 하도록 합니다. 관리자 권한으로이 명령만 실행할 수 있습니다. <br /><br /> 이 스위치는 인수가 필요 없습니다. `devenv /Setup` 명령은 일반적으로 설치 프로세스의 마지막 단계로 표시됩니다. 스위치를 사용 `/Setup` 하면 IDE가 시작 되지 않습니다.|
| `/Splash` | 일반적인 방법으로 Visual Studio 시작 화면을 표시 한 다음 주 IDE를 표시 하기 전에 메시지 상자를 표시 합니다. 메시지 상자를 사용 하 여 시작 화면을 학습할 수 있습니다. 예를 들어 VSPackage 제품 아이콘을 확인할 수 있습니다.<br /><br /> 이 스위치는 인수가 필요 없습니다. |

## <a name="see-also"></a>추가 정보

- [명령줄 스위치 추가](../extensibility/adding-command-line-switches.md)
- [Devenv 명령줄 스위치](../ide/reference/devenv-command-line-switches.md)
