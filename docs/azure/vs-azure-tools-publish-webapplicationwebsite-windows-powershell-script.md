---
title: PowerShell 스크립트를 사용 하 여 웹 앱 게시
description: Azure 웹 사이트에 웹 프로젝트를 게시하는 방법에 대해 알아봅니다. 없는 경우 이 스크립트는 Azure 구독에 필요한 리소스를 만듭니다.
author: ghogen
manager: jillfra
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 3d8a6a73f50c331c516f1e433d7d9b1104731380
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89739889"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (Windows PowerShell 스크립트)
## <a name="syntax"></a>구문
Azure 웹 사이트에 웹 프로젝트를 게시합니다. 없는 경우 스크립트는 Azure 구독에 필요한 리소스를 만듭니다.

```
Publish-WebApplicationWebSite
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

## <a name="configuration"></a>구성
배포의 세부 정보를 설명하는 JSON 구성 파일에 대한 경로입니다.

| 매개 변수 | 기본값 |
| --- | --- |
| 별칭 |없음 |
| 필수 여부 |true |
| 위치 |명명됨 |
| 기본값 |없음 |
| 파이프라인 입력 허용 |false |
| 와일드카드 문자 허용 |false |

## <a name="subscriptionname"></a>SubscriptionName
웹사이트를 만들려는 Azure 구독의 이름입니다.

| 매개 변수 | 기본값 |
| --- | --- |
| 별칭 |없음 |
| 필수 여부 |false |
| 위치 |명명됨 |
| 기본값 |없음 |
| 파이프라인 입력 허용 |false |
| 와일드카드 문자 허용 |false |

## <a name="webdeploypackage"></a>WebDeployPackage
웹 사이트에 게시하는 웹 배포 패키지에 대한 경로입니다. Visual Studio에서 웹 게시 마법사를 사용하여 이 패키지를 만들 수 있습니다. 자세한 내용은 [Azure Cloud Services 및 ASP.NET으로 시작하기](vs-azure-tools-publish-webapplicationwebsite-windows-powershell-script.md)를 참조하세요.

| 매개 변수 | 기본값 |
| --- | --- |
| 별칭 |없음 |
| 필수 여부 |false |
| 위치 |명명됨 |
| 기본값 |없음 |
| 파이프라인 입력 허용 |false |
| 와일드카드 문자 허용 |false |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Azure에서 SQL 데이터베이스의 사용자 이름 및 암호입니다.

| 매개 변수 | 기본값 |
| --- | --- |
| 별칭 |없음 |
| 필수 여부 |false |
| 위치 |명명됨 |
| 기본값 |없음 |
| 파이프라인 입력 허용 |false |
| 와일드카드 문자 허용 |false |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
True이면 스크립트에서 출력 스트림으로 메시지를 프린트합니다.

| 매개 변수 | 기본값 |
| --- | --- |
| 별칭 |없음 |
| 필수 여부 |false |
| 위치 |명명됨 |
| 기본값 |false |
| 파이프라인 입력 허용 |false |
| 와일드카드 문자 허용 |false |

## <a name="remarks"></a>설명
스크립트를 사용하여 개발 및 테스트 환경을 만드는 방법에 대한 전체 설명은 [Windows PowerShell 스크립트를 사용하여 개발 및 테스트 환경에 게시](vs-azure-tools-publishing-using-powershell-scripts.md)를 참조하세요.

JSON 구성 파일은 배포될 내용의 세부 정보를 지정합니다. 해당 웹 사이트의 이름 및 사용자 이름과 같은 프로젝트를 만들 때 지정된 정보를 포함합니다. 있는 경우 프로비전할 새 데이터베이스도 포함합니다. 다음 코드에서는 JSON 구성 파일을 예로 보여줍니다.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication10554",
            "location": "West US"
        },
        "databases": [
            {
                "connectionStringName": "DefaultConnection",
                "databaseName": "WebApplication10554_db",
                "serverName": "iss00brc88",
                "user": "sqluser2",
                "password": "",
                "edition": "",
                "size": "",
                "collation": "",
                "location": "West US"
            }
        ]
    }
}
```

배포된 내용을 변경하도록 JSON 구성 파일을 편집할 수 있습니다. 웹 사이트 섹션은 필수이지만 데이터 섹션은 선택 사항입니다.

## <a name="next-steps"></a>다음 단계
자세한 내용은 [publish-webapplicationvm (Windows PowerShell script)](vs-azure-tools-publish-webapplicationvm.md)를 참조 하세요.
