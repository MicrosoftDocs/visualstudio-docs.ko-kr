---
title: Visual Studio 찾기 | Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93a6f39a9240002cd8008c9368799e10ab63b78d
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012479"
---
# <a name="locate-visual-studio"></a>Visual Studio 찾기

Visual Studio 2017부터 동일한 버전 또는 심지어 버전의 여러 인스턴스를 설치할 수 있습니다. 이는 이전 설치를 유지 하면서 주 개발 컴퓨터에서 새 기능을 미리 보려는 경우에 유용 합니다. 이러한 변경으로 인해 인스턴스를 찾는 데 사용할 수 있는 단일 환경 변수 또는 레지스트리 값이 없습니다. 대신 [COM 쿼리 API](/dotnet/api/microsoft.visualstudio.setup.configuration) 를 사용 하 여 확장과 관련 된 조건에 따라 인스턴스를 찾을 수 있습니다.

이는 네이티브 코드 및 관리 코드에 사용할 수 있는 NuGet 패키지를 포함 하는 빠른 읽기 전용 API입니다.

| 코드 | 패키지 |
| ---- | --- |
| 네이티브 | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| 관리 대상 | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

경로 또는 현재 프로세스가 지정 된 단일 인스턴스를 찾거나 모든 인스턴스를 열거할 수 있습니다. Visual Studio를 찾는 방법의 전체 예제는 [샘플](https://github.com/Microsoft/vs-setup-samples) 을 참조 하세요.

## <a name="tools"></a>도구

빌드 환경, PowerShell 스크립트, 설치 관리자 및 기타 시나리오에서 Visual Studio 및 기타 도구를 찾기 위해 고유한 스크립트와 함께 직접 또는 재배포할 수 있는 여러 오픈 소스 도구가 있습니다.

| 프로젝트 | 설명 |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | 단일 파일 기본 실행 파일은 릴리스 또는 시험판, 설치 된 제품, 설치 되는 작업 등의 인스턴스를 검색 하는 기본 실행 파일입니다. Visual studio 2017 이상에 대 한 정보가 더 이상 반환 되지 않지만 visual Studio 2010 이상 찾기도 지원 됩니다. 예는 [wiki](https://github.com/Microsoft/vswhere/wiki) 를 참조 하세요. |
| [VSSetup cmdlet](https://github.com/Microsoft/vssetup.powershell) | PowerShell cmdlet은 다양 한 정보를 개체로 반환 하는 2.0 이상 버전을 지원 합니다 .이는 _vswhere_ 와 동일한 조건에 따라 인스턴스를 찾고 인스턴스에 대 한 훨씬 더 많은 속성을 검색 하는 데 사용할 수 있습니다. 예는 [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) 를 참조 하세요. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | 는 _VSIXInstaller_ 를 자동으로 찾고 **.vsix* 파일을 설치 하기 위해 명령줄을 전달 합니다. 이 기능은 쿼리 Api를 직접 지원 하지 않는 설치 관리자에서 유용할 수 있습니다. 예는 [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) 를 참조 하세요. |

## <a name="see-also"></a>참고 항목

* [Visual Studio 2017 설정 변경](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [DTE를 사용하여 Visual Studio 시작](launch-visual-studio-dte.md)