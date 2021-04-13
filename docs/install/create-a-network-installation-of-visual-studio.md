---
title: 네트워크 기반 설치 만들기
description: 기업 내에서 Visual Studio를 배포하기 위한 네트워크 설치 지점을 만드는 방법을 알아봅니다.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 748f0da7810918d8b41247059277fb73158f1bc9
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547429"
---
# <a name="create-a-network-installation-of-visual-studio"></a>Visual Studio의 네트워크 설치 만들기

때로 엔터프라이즈 관리자는 클라이언트 워크스테이션에 배포할 수 있는 Visual Studio 파일이 포함된 네트워크 설치 지점을 만들고 싶어 합니다. 이는 클라이언트 컴퓨터의 권한이나 인터넷 액세스가 제한되어 있는 상황, 또는 조직이 특정 버전의 개발자 도구 집합을 표준화하기 전에 내부 팀이 호환성 테스트를 수행하려는 경우 용이하게 하기 위한 것입니다. Microsoft는 관리자가 초기 설치와 향후 모든 제품 업데이트를 위한 모든 Visual Studio 파일을 포함하는 내부 정적 네트워크 공유에 있는 파일 캐시를 기본적으로 만드는 _네트워크 레이아웃을 만들_ 수 있도록 Visual Studio를 설계했습니다.

 > [!NOTE]
 >  - 엔터프라이즈 내에서 여러 버전의 Visual Studio를 사용 중인 경우(예: Visual Studio 2019 Professional과 Visual Studio 2019 Enterprise 모두 사용) 각 버전에 대한 별도의 네트워크 설치 공유를 만들어야 합니다.
 >  - 초기 클라이언트 설치를 수행하기 _전에_ 클라이언트에서 제품 업데이트를 받도록 할 방법을 결정하는 것이 좋습니다.  그렇게 하면 구성 옵션이 올바로 설정되었는지 쉽게 확인할 수 있습니다. 선택 사항에 따라 클라이언트에서 네트워크 레이아웃 위치나 인터넷의 업데이트를 가져올 수 있습니다. 
 >  - 복구 및 제거 기능이 제대로 작동하도록 하려면 원래 Visual Studio 설치 레이아웃과 모든 후속 제품 업데이트를 동일한 네트워크 디렉터리에 배치해야 합니다. 

## <a name="download-the-visual-studio-bootstrapper"></a>Visual Studio 부트스트래퍼 다운로드

원하는 Visual Studio 버전에 해당하는 부트스트래퍼 파일을 다운로드합니다. **저장** 을 선택한 다음 **폴더 열기** 를 선택합니다.

::: moniker range="vs-2017"

Visual Studio 2017 버전 15.9용 최신 부트스트래퍼를 가져오려면 [Visual Studio 이전 버전](https://visualstudio.microsoft.com/vs/older-downloads/) 페이지로 이동하여 다음 부트스트래퍼 파일 중 하나를 다운로드합니다.

| 버전 | 파일 이름 |
|-------------|-----------------------|
|Visual Studio 2017 Enterprise 버전 15.9 | vs_enterprise.exe |
|Visual Studio 2017 Professional 버전 15.9 | vs_professional.exe |
|Visual Studio 2017 Build Tools 버전 15.9  | vs_buildtools.exe |

이 밖에 지원되는 부트스트래퍼에는 vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe, vs_testprofessional.exe가 있습니다.

::: moniker-end

::: moniker range="vs-2019"

[Visual Studio 다운로드 페이지](https://visualstudio.microsoft.com/downloads)나 선택한 Visual Studio 에디션 및 버전의 [Visual Studio 2019 릴리스](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) 페이지에서 Visual Studio 2019 부트스트래퍼를 다운로드하여 시작합니다.  설치 실행 파일&mdash;(또는 더 구체적으로 말해 부트스트래퍼 파일)&mdash;은 다음 중 하나와 일치하거나 유사합니다.

|버전 | 다운로드|
|-------------|-----------------------|
|Visual Studio Enterprise | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
|Visual Studio Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2019) |
| Visual Studio Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=offline+install&utm_content=download+vs2019) |

이 밖에 지원되는 부트스트래퍼에는 [vs_teamexplorer.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/4026077127d25d33789f3882998266946608d8ada378b6ed7c8fff8c07f3dde2/vs_TeamExplorer.exe), [vs_testagent.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/1383bf8bcda3d0e986a2e42c14114aaea8a7b085d31aa0623c9f70b2bad130e4/vs_TestAgent.exe), [vs_testcontroller.exe](https://download.visualstudio.microsoft.com/download/pr/f6473c9f-a5f6-4249-af28-c2fd14b6a0fb/54dcf24b76e7cd9fb8be0ac518a9dfba6daf18fe9b2aa1543411b1cda8820918/vs_TestController.exe)가 있습니다.

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>이전에 다운로드한 부트스트래퍼 파일의 버전을 확인하려는 경우에는 다음 방법을 참조하세요. Windows에서 파일 탐색기를 열고 부트스트래퍼 파일을 마우스 오른쪽 단추로 클릭한 다음, **속성** 을 선택하고 **세부 정보** 탭을 선택한 다음, **제품 버전** 번호를 확인합니다. 이 번호가 Visual Studio 릴리스와 일치하는지 확인하려면 [Visual Studio 빌드 번호 및 릴리스 날짜](visual-studio-build-numbers-and-release-dates.md)를 참조하세요.

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>이전에 다운로드한 부트스트래퍼 파일의 버전을 확인하려는 경우에는 다음 방법을 참조하세요. Windows에서 파일 탐색기를 열고 부트스트래퍼 파일을 마우스 오른쪽 단추로 클릭한 다음, **속성** 을 선택하고 **세부 정보** 탭을 선택한 다음, **제품 버전** 번호를 확인합니다. 이 번호가 Visual Studio 릴리스와 일치하는지 확인하려면 [Visual Studio 2019 릴리스](https://docs.microsoft.com/visualstudio/releases/2019/history)를 참조하세요.

::: moniker-end

## <a name="create-an-offline-installation-folder"></a>오프라인 설치 관리자 폴더 만들기

이 단계를 완료하려면 인터넷에 연결되어 있는 상태여야 합니다. 

명령 프롬프트를 열고, 부트스트래퍼를 다운로드한 디렉터리로 이동하고, [명령줄 매개 변수를 사용하여 Visual Studio를 설치](../install/use-command-line-parameters-to-install-visual-studio.md) 페이지에서 정의한 대로 부트스트래퍼의 매개 변수를 사용하여 네트워크 설치 캐시를 만들고 유지 관리합니다. 초기 레이아웃을 만드는 일반적인 예는 아래와 [Visual Studio 설치에 대한 명령줄 매개 변수 예](../install/command-line-parameter-examples.md)에 나와 있습니다.  

   > [!IMPORTANT]
   > 단일 언어 로캘의 전체 초기 레이아웃에 필요한 디스크 공간은 Visual Studio Community의 경우 약 35GB, Visual Studio Enterprise의 경우 42GB입니다. 추가 [언어 로캘](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)마다 약 0.5GB가 각각 필요합니다. 자세한 내용은 [네트워크 레이아웃 사용자 지정](#customize-the-network-layout) 섹션을 참조하세요. 이후의 레이아웃 업데이트도 동일한 네트워크 위치에 저장해야 하므로 네트워크 레이아웃 위치의 디렉터리 콘텐츠가 시간이 지남에 따라 상당히 커질 수 있습니다.  
   
- 모든 언어 및 모든 기능을 사용하여 Visual Studio Enterprise 초기 레이아웃을 만들려면 다음을 실행합니다.

  ```vs_enterprise.exe --layout c:\VSLayout```

- 모든 언어 및 모든 기능을 사용하여 Visual Studio Professional 초기 레이아웃을 만들려면 다음을 실행합니다.

  ```vs_professional.exe --layout c:\VSLayout```

## <a name="modify-the-responsejson-file"></a>response.json 파일 수정

`response.json` 파일을 수정하여 설치 프로그램이 실행될 때 사용되는 기본값을 설정할 수 있습니다.  예를 들어 자동으로 선택되어야 하는 특정 워크로드 집합을 선택하도록 `response.json` 파일을 구성할 수 있습니다. 또한 클라이언트가 네트워크 레이아웃 위치에서 업데이트된 파일만 수신할지 여부를 지정하도록 `response.json`을 구성할 수도 있습니다. 자세한 내용은 [지시 파일을 사용하여 Visual Studio 설치 자동화](../install/automated-installation-with-response-file.md)를 참조하세요. 

`response.json` 파일과 함께 사용할 때 Visual Studio 부트스트래퍼에서 오류가 throw하는 문제가 발생할 경우 자세한 내용은 [Visual Studio 설치 또는 사용 시의 네트워크 관련 오류 문제 해결](../install/troubleshooting-network-related-errors-in-visual-studio.md#error-failed-to-parse-id-from-parent-process) 페이지를 참조하세요.

## <a name="copy-the-layout-to-a-network-share"></a>레이아웃을 네트워크 공유로 복사

다른 클라이언트 컴퓨터에서 실행될 수 있도록 레이아웃을 네트워크 공유에 호스트합니다.

다음 예제에서는 [xcopy](/windows-server/administration/windows-commands/xcopy/)를 사용합니다. 원하는 경우 [robocopy](/windows-server/administration/windows-commands/robocopy/)를 사용할 수도 있습니다.

::: moniker range="vs-2017"

예:

```cmd
xcopy /e c:\VSLayout \\server\products\VS2017
```

::: moniker-end

::: moniker range="vs-2019"

```cmd
xcopy /e c:\VSLayout \\server\products\VS2019
```

::: moniker-end

> [!IMPORTANT]
> 오류를 방지하려면 전체 레이아웃 경로가 80자 미만인지 확인합니다.

## <a name="customize-the-network-layout"></a>네트워크 레이아웃 사용자 지정

네트워크 레이아웃을 사용자 지정하는 데 사용할 수 있는 여러 가지 옵션이 있습니다. [언어 로캘](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [워크로드, 구성 요소, 권장 또는 선택적 종속성](workload-and-component-ids.md)의 특정 집합만 포함된 부분 레이아웃을 만들 수 있습니다. 워크로드의 하위 집합만 클라이언트 워크스테이션에 배포하려는 경우 이 방법이 유용할 수 있습니다. 레이아웃을 사용자 지정하기 위한 일반적인 명령줄 매개 변수는 다음과 같습니다.

* `--add` - [워크로드 또는 구성 요소 ID](workload-and-component-ids.md)를 지정합니다. <br>`--add`가 사용되면 `--add`로 지정된 워크로드 및 구성 요소만 다운로드됩니다.  `--add`를 사용하지 않으면 모든 워크로드 및 구성 요소가 다운로드됩니다.
* `--includeRecommended` - 지정된 워크로드 ID에 대한 모든 권장 구성 요소를 포함합니다.
* `--includeOptional` - 지정된 워크로드 ID에 대한 모든 권장 및 선택적 구성 요소를 포함합니다.
* `--lang` - [언어 로캘](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)을 지정합니다.

다음은 사용자 지정 부분 레이아웃을 만드는 방법에 대한 몇 가지 예제입니다.

* 한 언어의 작업과 구성 요소를 모두 다운로드하려면 다음을 실행합니다.

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US
    ```

* 여러 언어의 작업과 구성 요소를 모두 다운로드하려면 다음을 실행합니다.

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --lang en-US de-DE ja-JP
    ```

* 모든 언어의 작업 하나만 다운로드하려면 다음을 실행합니다.

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* 세 가지 언어의 작업 두 개와 선택적 구성 요소 하나를 다운로드하려면 다음을 실행합니다.

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* 두 가지 워크로드 및 모든 권장 구성 요소를 다운로드하려면:

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended
    ```

* 두 가지 워크로드 및 모든 권장/선택적 구성 요소를 다운로드하려면 다음을 실행합니다.

    ```cmd
    vs_enterprise.exe --layout C:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional
    ```

### <a name="save-your-layout-options"></a>레이아웃 옵션 저장

레이아웃 명령을 실행할 때 지정하는 옵션(예: 워크로드 및 언어)은 저장됩니다. 후속 레이아웃 명령에는 이전 옵션이 모두 포함됩니다.  다음은 영어용 워크로드 하나만 포함된 레이아웃의 예입니다.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

해당 레이아웃을 최신 버전으로 업데이트하려면 추가 명령줄 매개 변수를 지정할 필요가 없습니다. 이전 설정이 저장되어 이 레이아웃 폴더의 모든 후속 레이아웃 명령에 사용됩니다.  다음 명령은 기존 부분 레이아웃을 업데이트합니다.

```cmd
vs_enterprise.exe --layout c:\VSLayout
```

워크로드를 추가하려는 경우 방법은 다음 예제와 같습니다. 여기서는 Azure 워크로드와 지역화된 언어를 추가합니다.  이제 관리되는 데스크톱과 Azure가 이 레이아웃에 포함됩니다.  이러한 모든 워크로드에 대해 영어 및 독일어용 언어 리소스가 포함됩니다. 레이아웃이 사용 가능한 최신 버전으로 업데이트됩니다.

```cmd
vs_enterprise.exe --layout c:\VSLayout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

기존 레이아웃을 전체 레이아웃으로 업데이트하려면 다음 예제와 같이 --all 옵션을 사용합니다.

```cmd
vs_enterprise.exe --layout c:\VSLayout --all
```

## <a name="deploy-from-a-network-installation"></a>네트워크 설치에서 배포

관리자는 설치 스크립트의 일부로 Visual Studio를 클라이언트 워크스테이션에 배포할 수 있습니다. 또는 관리자 권한을 가진 사용자는 공유에서 직접 설치 프로그램을 실행하여 Visual Studio를 머신에 설치할 수 있습니다.

* 사용자는 다음 명령을 실행하여 설치할 수 있습니다. <br>

    ```cmd
    \\server\products\VS\vs_enterprise.exe
    ```

* 관리자는 다음 명령을 실행하여 무인 모드로 설치할 수 있습니다.

    ```cmd
    \\server\products\VS\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> 오류를 방지하려면 전체 레이아웃 경로가 80자 미만인지 확인합니다.

> [!TIP]
> `--wait` 옵션을 배치 파일의 일부로 실행하면 `vs_enterprise.exe` 프로세스는 설치가 완료될 때까지 기다린 후에 종료 코드를 반환합니다.
>
> 엔터프라이즈 관리자가 완료된 설치에 대한 추가 작업을 수행하려는 경우(예: [성공적인 설치에 제품 키 적용](automatically-apply-product-keys-when-deploying-visual-studio.md)) 이 방법이 유용하지만, 해당 설치에서 반환 코드를 처리하려면 설치가 완료될 때까지 기다려야 합니다.
>
> `--wait`를 사용하지 않으면 설치가 완료되기 전에 `vs_enterprise.exe` 프로세스가 종료되고 설치 작업 상태를 나타내지 않는 부정확한 종료 코드가 반환됩니다.
>

::: moniker range="vs-2019"
> [!IMPORTANT]
> 오프라인 설치의 경우 "다음 매개 변수와 일치하는 제품을 찾을 수 없습니다"라는 오류 메시지가 표시되면 버전 16.3.5 이상에서 `--noweb` 스위치를 사용하고 있는지 확인합니다.
>
::: moniker-end

레이아웃에서 설치하는 경우 설치되는 콘텐츠는 레이아웃에서 가져옵니다. 그러나 레이아웃에 없는 구성 요소를 선택하면 인터넷에서 해당 구성 요소를 가져옵니다.  Visual Studio 설치 프로그램이 레이아웃에 없는 콘텐츠를 다운로드하지 못하도록 하려면 `--noWeb` 옵션을 사용합니다. `--noWeb`을 사용하고 설치하도록 선택한 콘텐츠가 레이아웃에 없으면 설치가 실패합니다.

> [!TIP]
> 인터넷에 연결되지 않은 컴퓨터에서 오프라인 소스를 설치하려면 `--noWeb` 및 `--noUpdateInstaller` 옵션을 모두 지정합니다. 앞의 옵션은 업데이트된 워크로드, 구성 요소 등을 다운로드하지 못하게 하고, 뒤의 옵션은 설치 프로그램이 웹에서 자체 업데이트되지 못하게 합니다.

> [!IMPORTANT]
> `--noWeb` 옵션은 인터넷에 연결된 컴퓨터의 Visual Studio 설정에서 업데이트를 확인하도록 허용합니다. 자세한 내용은 [네트워크 기반 Visual Studio 배포에 대한 업데이트 제어](controlling-updates-to-visual-studio-deployments.md) 페이지를 참조하세요.

### <a name="error-codes"></a>오류 코드

`--wait` 매개 변수를 사용한 경우 작업 결과에 따라 `%ERRORLEVEL%` 환경 변수는 다음 값 중 하나로 설정됩니다.

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

## <a name="update-a-network-install-layout"></a>네트워크 설치 레이아웃 업데이트

사용 가능한 제품 업데이트가 있을 경우 [네트워크 설치 레이아웃을 업데이트](update-a-network-installation-of-visual-studio.md)하여 업데이트된 패키지를 통합해야 할 수 있습니다.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-release"></a>이전 Visual Studio 릴리스에 대한 레이아웃을 만드는 방법

먼저 Visual Studio 부트스트래퍼의 유형에는 "최신", "현재의", "에버그린", "팁"이라는 단어로 특징지을 수 있는 유형과 기본적으로 "고정 버전"을 의미하는 유형, 이렇게 두 가지가 있다는 것을 이해해야 합니다. 두 유형의 부트스트래퍼 파일은 모두 정확히 동일한 이름을 가지며 유형을 구분하는 가장 좋은 방법은 이 파일을 가져온 곳에 주의를 기울이는 것입니다. [Visual studio 다운로드 페이지](https://visualstudio.microsoft.com/downloads)에서 사용할 수 있는 Visual Studio 부트스트래퍼는 에버그린 Visual Studio 부트스트래퍼로 간주 되며, 항상 부트스트래퍼가 실행될 때 채널에서 사용할 수 있는 최신 릴리스를 설치(또는 업데이트)합니다. [Visual Studio 2019 릴리스](https://docs.microsoft.com/visualstudio/releases/2019/history) 페이지에서 사용할 수 있거나 Microsoft 업데이트 카탈로그의 관리자 업데이트 내부에 포함된 Visual Studio 부트스트래퍼는 특정 고정 버전의 제품을 설치합니다. 

따라서 오늘 에버그린 Visual Studio 부트스트래퍼를 다운로드하여 지금부터 6개월 동안 실행하면 이 부트스트래퍼가 실행되는 시점에서 최신인 Visual Studio 릴리스가 설치됩니다. 부트스트래퍼는 항상 최신 비트를 설치하고 최신을 유지하도록 설계되었습니다.

고정 링크 부트스트래퍼를 다운로드하거나 Microsoft 카탈로그에서 다운로드한 관리자 업데이트를 실행하는 경우 실행 시점에 관계없이 항상 특정 버전의 제품이 설치됩니다.

마지막으로, 부트스트래퍼 중 하나를 사용하여 네트워크 레이아웃을 만들 수 있으며, 레이아웃에 만들어지는 버전은 사용 중인 부트스트래퍼(예를 들어 고정 버전인지 아니면 최신 버전인지)에 따라 달라집니다. 그런 다음 이후의 부트스트래퍼를 사용하여 네트워크 레이아웃을 업데이트하거나 Microsoft 업데이트 카탈로그에서 관리자 업데이트 패키지를 사용할 수도 있습니다. 레이아웃을 업데이트하는 방법에 관계없이 업데이트된 결과 레이아웃은 특정 버전의 제품을 포함하는 패키지 캐시가 될 것이므로 고정 링크 부트스트래퍼처럼 동작합니다. 따라서 클라이언트가 레이아웃에서 설치될 때마다 클라이언트는 레이아웃에 있는 특정 버전의 Visual Studio를 설치합니다(최신 버전이 온라인으로 존재할 수 있더라도). 

### <a name="how-to-get-support-for-your-offline-installer"></a>오프라인 설치 관리자에 대한 지원을 받는 방법

오프라인 설치에 문제가 발생하는 경우와 관련하여 자세히 알려고 합니다. [문제 보고](../ide/how-to-report-a-problem-with-visual-studio.md)를 사용하여 알리는 것이 가장 좋습니다. 이 도구를 사용하면 문제를 진단하고 해결하는 데 필요한 원격 분석과 로그를 보낼 수 있습니다.

설치 관련 문제를 위한 [**설치 채팅**](https://visualstudio.microsoft.com/vs/support/#talktous)(영어만 가능) 지원 옵션도 제공됩니다.

사용 가능한 다른 지원 옵션도 있습니다. 목록은 [피드백](../ide/feedback-options.md) 페이지를 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
- [Visual Studio의 네트워크 기반 설치 업데이트](update-a-network-installation-of-visual-studio.md)
- [Visual Studio 설치 또는 사용 시의 네트워크 관련 오류 문제 해결](troubleshooting-network-related-errors-in-visual-studio.md)
- [네트워크 기반 Visual Studio 배포에 대한 업데이트 제어](controlling-updates-to-visual-studio-deployments.md)
- [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/releases/2019/servicing/)
- [서비스 기준선에서 Visual Studio 업데이트](update-servicing-baseline.md)
- [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
- [Visual Studio 작업 및 구성 요소 ID](workload-and-component-ids.md)
- [Visual Studio 오프라인 설치에 필요한 인증서 설치](install-certificates-for-visual-studio-offline.md)
