---
title: Visual Studio Container Tools 시작 설정
author: ghogen
description: 컨테이너 도구 빌드 프로세스 개요
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: de0e3cc4e563f7082b91b904a110996cdb85b3b4
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247985"
---
# <a name="container-tools-launch-settings"></a>컨테이너 도구 시작 설정

ASP.NET Core 프로젝트의 *Properties* 폴더에서, 개발 머신에서 웹앱이 시작되는 방식을 제어하는 설정이 포함된 launchSettings.json 파일을 찾을 수 있습니다. ASP.NET 개발에서 이 파일을 사용하는 방법에 대한 자세한 내용은 [ASP.NET Core에서 여러 환경 사용](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2)을 참조하세요. *launchSettings.json*의 **Docker** 섹션 설정은 Visual Studio에서 컨테이너화된 앱을 처리하는 방법과 관련이 있습니다.

::: moniker range="vs-2017"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"
    }
```

::: moniker-end
::: moniker range=">=vs-2019"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}",
      "environmentVariables": {
        "ASPNETCORE_URLS": "https://+:443;http://+:80",
        "ASPNETCORE_HTTPS_PORT": "44360"
      },
      "httpPort": 51803,
      "useSSL": true,
      "sslPort": 44360
    }
```

::: moniker-end

commandName 설정은 이 섹션이 컨테이너 도구에 적용됨을 확인합니다. 다음 표에서는 이 섹션에서 설정할 수 있는 속성을 보여 줍니다.

::: moniker range="vs-2017"

|설정 이름|버전|예제|Description|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|“launchBrowser”: true|프로젝트를 시작한 후에 브라우저를 시작할지 여부를 나타냅니다.|
|launchUrl|Visual Studio 2017|“launchUrl”: “{Scheme}://{ServiceHost}:{ServicePort}”|이 URL은 브라우저를 시작할 때 사용됩니다.  이 문자열에 대해 지원되는 대체 토큰은 다음과 같습니다.<br>   {Scheme} - SSL 사용 여부에 따라 “http” 또는 “https”로 바뀝니다.<br>   {ServiceHost} - 일반적으로 “localhost”로 바뀝니다. 하지만 Windows 10 RS3 또는 이전 버전의 Windows 컨테이너를 대상으로 하는 경우에는 컨테이너의 IP로 바뀝니다.<br>   {ServicePort} - 일반적으로 SSL 사용 여부에 따라 sslPort 또는 httpPort로 바뀝니다.  하지만 Windows 10 RS3 또는 이전 버전의 Windows 컨테이너를 대상으로 하는 경우에는 SSL 사용 여부에 따라 “443” 또는 “80”으로 바뀝니다.|

::: moniker-end

::: moniker range=">=vs-2019"

| 설정 이름         | 예제                                               | Description                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| commandLineArgs      | “commandLineArgs”: “--mysetting myvalue”              | 앱을 시작하기 위한 이 명령줄 인수는 컨테이너에서 프로젝트를 시작할 때 사용됩니다.                                     |
| environmentVariables | “environmentVariables”: {                             | 이 환경 변수 값은 컨테이너에서 시작되는 프로세스에 전달됩니다.                       |
|                      | “ASPNETCORE_URLS”: “https://+:443; http://+:80,       |                                                                                                                         |
|                      | “ASPNETCORE_HTTPS_PORT”: “44381”                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | “httpPort”: 24051                                     | 호스트의 이 포트는 컨테이너를 시작할 때 컨테이너의 포트 80에 매핑됩니다.                                |
|                      |                                                       | 값을 지정하지 않으면 iisSettings 값에서 가져옵니다.                                                          |
| launchBrowser        | “launchBrowser”: true                                 | 프로젝트를 시작한 후에 브라우저를 시작할지 여부를 나타냅니다.                                       |
| launchUrl            | “launchUrl”: “{Scheme}://{ServiceHost}:{ServicePort}” | 이 URL은 브라우저를 시작할 때 사용됩니다. 이 문자열에 대해 지원되는 대체 토큰은 다음과 같습니다.                          |
|                      |                                                       | - {Scheme} - SSL 사용 여부에 따라 “http” 또는 “https”로 바뀝니다.                                   |
|                      |                                                       | - {ServiceHost} - 일반적으로 “localhost”로 바뀝니다.                                                                    |
|                      |                                                       | 하지만 Windows 10 RS3 또는 이전 버전의 Windows 컨테이너를 대상으로 하는 경우에는 컨테이너의 IP로 바뀝니다.           |
|                      |                                                       | - {ServicePort} - 일반적으로 SSL 사용 여부에 따라 sslPort 또는 httpPort로 바뀝니다.                   |
|                      |                                                       | 하지만 Windows 10 RS3 또는 이전 버전의 Windows 컨테이너를 대상으로 하는 경우에는         |
|                      |                                                       | SSL 사용 여부에 따라 "443" 또는 "80"으로 바뀝니다.                                                                                       |
| sslPort              | “sslPort”: 44381                                      | 호스트의 이 포트는 컨테이너를 시작할 때 컨테이너의 포트 443에 매핑됩니다.                               |
|                      |                                                       | 값을 지정하지 않으면 iisSettings 값에서 가져옵니다.                                                          |
| useSSL               | “useSSL”: true                                        | 프로젝트를 시작할 때 SSL을 사용할지 여부를 나타냅니다. useSSL을 지정하지 않으면, sslPort가 0보다 클 때 SSL이 사용됩니다. |

::: moniker-end

## <a name="next-steps"></a>다음 단계

[컨테이너 도구 빌드 속성](container-msbuild-properties.md)을 설정하여 프로젝트를 구성합니다.

## <a name="see-also"></a>참고 항목

[Docker Compose 빌드 속성](docker-compose-properties.md)
