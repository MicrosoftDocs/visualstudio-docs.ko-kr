---
title: Visual Studio에서 템플릿 검색 문제 해결 | Microsoft Docs
description: 진단 로깅을 사용 하 여 Visual Studio SDK의 사용자 지정 프로젝트 및 템플릿 배포 문제를 해결 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 23e30ddb5f43a755fc2dc0206509e403e802c3e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893492"
---
# <a name="troubleshooting-template-installation"></a>템플릿 설치 문제 해결

프로젝트 또는 항목 템플릿을 배포할 때 문제가 발생 하는 경우 진단 로깅을 사용 하도록 설정할 수 있습니다.

::: moniker range="vs-2017"

1. 설치용 *Common7\IDE\CommonExtensions* 폴더에 .pkgdef 파일을 만듭니다. 예: *C:\Program files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. 설치용 *Common7\IDE\CommonExtensions* 폴더에 .pkgdef 파일을 만듭니다. 예: *C:\Program files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. .Pkgdef 파일에 다음을 추가 합니다.

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. 설치에 대 한 [개발자 명령 프롬프트](/dotnet/framework/tools/developer-command-prompt-for-vs) 를 열고를 실행 `devenv /updateConfiguration` 합니다.

::: moniker range="vs-2017"

4. Visual Studio를 열고 새 프로젝트 및 새 항목 대화 상자를 시작 하 여 두 템플릿 트리를 모두 초기화 합니다.

   이제 템플릿 로그가 **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_ [instanceid] \VsTemplateDiagnosticsList.csv** 에 표시 됩니다 (Instanceid는 Visual Studio 인스턴스의 설치 ID에 해당). 각 템플릿 트리 초기화는이 로그에 항목을 추가 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

4. Visual Studio를 열고 **새 프로젝트** 및 **새 항목** 만들기 대화 상자를 시작 하 여 두 템플릿 트리를 모두 초기화 합니다.

   이제 템플릿 로그가 **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_ [instanceid] \VsTemplateDiagnosticsList.csv** 에 표시 됩니다 (Instanceid는 Visual Studio 인스턴스의 설치 ID에 해당). 각 템플릿 트리 초기화는이 로그에 항목을 추가 합니다.

::: moniker-end

로그 파일에는 다음 열이 포함 되어 있습니다.

- **FullPathToTemplate** 에는 다음 값이 있습니다.

  - 매니페스트 기반 배포의 경우 1

  - 디스크 기반 배포의 경우 0

- **템플릿 파일 이름**

- 기타 템플릿 속성

> [!NOTE]
> 로깅을 사용 하지 않도록 설정 하려면 .pkgdef 파일을 제거 하거나의 값을 `EnableTemplateDiscoveryLog` 로 변경한 `dword:00000000` 다음를 다시 실행 `devenv /updateConfiguration` 합니다.

## <a name="see-also"></a>참고 항목

- [사용자 지정 프로젝트 및 항목 템플릿 만들기](creating-custom-project-and-item-templates.md)
- [Visual Studio 문제 해결](/troubleshoot/visualstudio/welcome-visual-studio/)
