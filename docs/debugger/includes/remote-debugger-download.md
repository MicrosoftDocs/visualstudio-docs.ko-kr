---
title: 원격 디버거 다운로드
description: 원격 디버거의 다운로드 링크
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 1e90a1d9e03892cf81bd2257d3dcc6e25ab36246
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149194"
---
디버그하려는 원격 디바이스 또는 서버에서(Visual Studio 머신 아님) 다음 표에 나온 링크를 통해 올바른 버전의 원격 도구를 다운로드하여 설치하세요.

- 사용 중인 버전의 Visual Studio용 최신 원격 도구를 다운로드합니다. 최신 원격 도구 버전은 이전 Visual Studio 버전과 호환되지만, 이전 원격 도구 버전은 이후 Visual Studio 버전과 호환되지 않습니다. 예를 들어 Visual Studio 2017을 사용하는 경우 Visual Studio 2017용 원격 도구의 최신 업데이트를 다운로드합니다. 이 시나리오에서는 Visual Studio 2019용 원격 도구를 다운로드하지 않습니다.
- 설치할 머신과 동일한 아키텍처를 가진 원격 도구를 다운로드합니다. 예를 들어 64비트 운영 체제를 실행하는 원격 컴퓨터에서 32비트 앱을 디버그하려는 경우 64비트 원격 도구를 설치합니다.

::: moniker range=">=vs-2019"

|버전|링크|참고|
|-|-|-|
|Visual Studio 2019|[원격 도구](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|모든 Visual Studio 2019 버전과 호환됩니다. 디바이스 운영 체제(x86, x64 또는 ARM64)와 일치하는 버전을 다운로드합니다. Windows Server에서 원격 도구 다운로드에 대한 도움말은 [Unblock the file download](../../debugger/remote-debugging-unblock-file-download.md)(파일 다운로드 차단 해제)를 참조하세요.|
|Visual Studio 2017|[원격 도구](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|모든 Visual Studio 2017 버전과 호환됩니다. 디바이스 운영 체제(x86, x64 또는 ARM64)와 일치하는 버전을 다운로드합니다. Windows Server에서 원격 도구 다운로드에 대한 도움말은 [Unblock the file download](../../debugger/remote-debugging-unblock-file-download.md)(파일 다운로드 차단 해제)를 참조하세요.|
|Visual Studio 2015|[원격 도구](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015용 원격 도구는 My.VisualStudio.com에서 사용할 수 있습니다. 메시지가 표시되면 무료 [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) 프로그램에 가입하거나 Visual Studio 구독 ID로 로그인하세요. Windows Server에서 원격 도구 다운로드에 대한 도움말은 [Unblock the file download](../../debugger/remote-debugging-unblock-file-download.md)(파일 다운로드 차단 해제)를 참조하세요.|
|Visual Studio 2013|[원격 도구](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 설명서의 다운로드 페이지|
|Visual Studio 2012|[원격 도구](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 설명서의 다운로드 페이지|

::: moniker-end

::: moniker range="vs-2017"

|버전|링크|참고|
|-|-|-|
|Visual Studio 2017|[원격 도구](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|모든 Visual Studio 2017 버전과 호환됩니다. 디바이스 운영 체제(x86, x64 또는 ARM64)와 일치하는 버전을 다운로드합니다. Windows Server에서 원격 도구 다운로드에 대한 도움말은 [Unblock the file download](../../debugger/remote-debugging-unblock-file-download.md)(파일 다운로드 차단 해제)를 참조하세요. 최신 버전의 원격 도구의 경우 [Visual Studio 2019 문서](../../debugger/remote-debugging.md?view=vs-2019)를 엽니다.|
|Visual Studio 2015|[원격 도구](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Visual Studio 2015용 원격 도구는 My.VisualStudio.com에서 사용할 수 있습니다. 메시지가 표시되면 무료 [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) 프로그램에 가입하거나 Visual Studio 구독 ID로 로그인하세요. Windows Server에서 원격 도구 다운로드에 대한 도움말은 [Unblock the file download](../../debugger/remote-debugging-unblock-file-download.md)(파일 다운로드 차단 해제)를 참조하세요.|
|Visual Studio 2013|[원격 도구](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Visual Studio 2013 설명서의 다운로드 페이지|
|Visual Studio 2012|[원격 도구](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Visual Studio 2012 설명서의 다운로드 페이지|

::: moniker-end

원격 도구를 설치하는 대신 *msvsmon.exe*를 원격 컴퓨터에 복사하여 원격 디버거를 실행할 수 있습니다. 그러나 원격 디버거 구성 마법사(*rdbgwiz.exe*)는 원격 도구를 설치하는 경우에만 사용할 수 있습니다. 원격 디버거를 서비스로 실행하려면 구성을 위해 마법사를 사용해야 할 수도 있습니다. 자세한 내용은 [(선택 사항) 원격 디버거를 서비스로 구성](../../debugger/remote-debugging.md#bkmk_configureService)을 참조하세요.

>[!NOTE]
>- ARM 디바이스에서 Windows 10 앱을 디버그하려면 최신 버전의 원격 도구에서 사용할 수 있는 ARM64를 사용합니다.
>- Windows RT 디바이스에서 Windows 10 앱을 디버그하려면 Visual Studio 2015 원격 도구 다운로드에서만 사용할 수 있는 ARM을 사용합니다.
