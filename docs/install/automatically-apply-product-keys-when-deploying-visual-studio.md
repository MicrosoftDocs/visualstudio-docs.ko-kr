---
title: 제품 키를 자동으로 적용
description: Visual Studio를 배포할 때 제품 키를 프로그래밍 방식으로 적용하는 방법을 알아봅니다.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e7f331536de264186bc2977cc4acaaab02147e13
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115225"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Visual Studio를 배포할 때 제품 키를 자동으로 적용

Visual Studio의 배포를 자동화하는 데 사용되는 스크립트의 일부로 제품 키를 프로그래밍 방식으로 적용할 수 있습니다. Visual Studio의 설치 중이나 설치가 완료된 후에 디바이스에서 프로그래밍 방식으로 제품 키를 설정할 수 있습니다.

## <a name="apply-the-license-after-installation"></a>설치 후 라이선스 적용

::: moniker range="vs-2017"

대상 컴퓨터에서 자동 모드로 `StorePID.exe` 유틸리티를 사용하여 설치된 Visual Studio 버전을 제품 키로 활성화할 수 있습니다. `StorePID.exe`는 다음 기본 위치에 Visual Studio 2017과 함께 설치되는 유틸리티 프로그램입니다. <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

대상 컴퓨터에서 자동 모드로 `StorePID.exe` 유틸리티를 사용하여 설치된 Visual Studio 버전을 제품 키로 활성화할 수 있습니다. `StorePID.exe`는 다음 기본 위치에 Visual Studio 2019와 함께 설치되는 유틸리티 프로그램입니다. <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 System Center 에이전트나 관리자 권한 명령 프로그램을 사용하여 높은 권한으로 `StorePID.exe`를 실행합니다. 이어서 제품 키와 MPC(Microsoft 제품 코드)를 입력합니다.

>[!IMPORTANT]
> 제품 키에 대시를 포함해야 합니다.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

다음 예제에서는 기본 위치에 설치한다고 가정하고 MPC가 08860이고 제품 키가 `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`인 Visual Studio 2017 Enterprise에 대한 라이선스를 적용하는 명령줄을 보여 줍니다.

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

다음 예제에서는 기본 위치에 설치한다고 가정하고 MPC가 09260이고 제품 키가 `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`인 Visual Studio 2019 Enterprise에 대한 라이선스를 적용하는 명령줄을 보여 줍니다.

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 다음 표에는 Visual Studio의 각 버전에 대한 MPC 코드가 나와 있습니다.

| Visual Studio 버전                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Visual Studio 버전                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

`StorePID.exe`는 제품 키를 성공적으로 적용한 경우 0의 `%ERRORLEVEL%`을 반환합니다. 오류가 발생하는 경우 오류 조건에 따라 다음 코드 중 하나를 반환합니다.

| Error                     | 코드 |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Visual Studio의 가상 인스턴스를 실행하는 경우, 로컬 AppData 폴더와 레지스트리도 가상화해야 합니다. 가상 인스턴스 문제를 해결하려면 `C:\Program Files (x86)\Microsoft Visual Studio\<version>\Common7\IDE\DDConfigCA.exe`를 실행합니다.  

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 설치](../install/install-visual-studio.md)
* [Visual Studio의 오프라인 설치 만들기](../install/create-an-offline-installation-of-visual-studio.md)
