---
title: 비주얼 스튜디오에서 템플릿 검색 문제 해결 | 마이크로 소프트 문서
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698928"
---
# <a name="troubleshooting-template-installation"></a>템플릿 설치 문제 해결

프로젝트 또는 항목 템플릿을 배포하는 데 문제가 발생하면 진단 로깅을 사용하도록 설정할 수 있습니다.

::: moniker range="vs-2017"

1. 설치를 위해 *Common7\IDE\CommonExtensions* 폴더에 pkgdef 파일을 만듭니다. 예를 들어, *C:\프로그램 파일 (x86)\마이크로소프트 비주얼 스튜디오\2017\엔터프라이즈\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. 설치를 위해 *Common7\IDE\CommonExtensions* 폴더에 pkgdef 파일을 만듭니다. 예를 들어, *C:\프로그램 파일 (x86)\마이크로소프트 비주얼 스튜디오\2019\엔터프라이즈\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. pkgdef 파일에 다음을 추가합니다.

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. 설치를 위한 [개발자 명령 프롬프트를](/dotnet/framework/tools/developer-command-prompt-for-vs) 열고 실행합니다. `devenv /updateConfiguration`

::: moniker range="vs-2017"

4. Visual Studio를 열고 새 프로젝트 및 새 항목 대화 상자를 시작하여 두 템플릿 트리를 초기화합니다.

   템플릿 로그는 이제 **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv(인스턴스** ID는 Visual Studio 인스턴스의 설치 ID에 해당)에 나타납니다. 각 템플릿 트리 초기화는 이 로그에 항목을 더합니다.

::: moniker-end

::: moniker range=">=vs-2019"

4. Visual Studio를 열고 새 프로젝트 및 **새 항목** 대화 상자 **만들기를** 시작하여 두 템플릿 트리를 초기화합니다.

   템플릿 로그는 이제 **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv(인스턴스** ID는 Visual Studio 인스턴스의 설치 ID에 해당)에 나타납니다. 각 템플릿 트리 초기화는 이 로그에 항목을 더합니다.

::: moniker-end

로그 파일에는 다음 열이 포함됩니다.

- 다음과 같은 값을 가지는 **FullPathToTemplate:**

  - 매니페스트 기반 배포의 경우 1

  - 디스크 기반 배포의 경우 0

- **템플릿파일이름**

- 기타 템플릿 속성

> [!NOTE]
> 로깅을 사용하지 않으려면 pkgdef 파일을 제거하거나 `EnableTemplateDiscoveryLog` `dword:00000000`의 값을 `devenv /updateConfiguration` 로 변경한 다음 다시 실행합니다.

## <a name="see-also"></a>참조

- [사용자 지정 프로젝트 및 항목 템플릿 만들기](creating-custom-project-and-item-templates.md)
