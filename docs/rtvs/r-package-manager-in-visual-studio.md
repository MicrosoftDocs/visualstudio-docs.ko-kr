---
title: R에 대한 패키지 관리자
description: Visual Studio의 R 패키지 관리자를 사용하여 R 패키지를 설치 및 관리하는 방법입니다.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: d35bfd45e862912ff78ae600eed01ce8dc002493
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62998867"
---
# <a name="package-manager"></a>패키지 관리자

RTVS(Visual Studio용 R 도구) 패키지 관리자는 R 패키지를 관리하기 위한 UI입니다. 패키지 관리자를 열려면 **R 도구** > **Windows** > **패키지**를 선택하거나 **Ctrl**+**7**을 누릅니다.

패키지 관리자에는 세 개의 탭이 있습니다. 각 탭에서 왼쪽에는 관련 패키지 목록이 표시되고 오른쪽에는 선택된 패키지의 패키지 버전, 설명, 라이선스, 설치 위치 및 기타 관련 정보 링크를 포함한 세부 정보가 표시됩니다. 오른쪽 위의 검색 상자에서 목록을 필터링할 수 있습니다.

> [!Tip]
> 탭을 전환해도 검색 상자의 용어는 적용된 상태로 유지됩니다.

- **사용 가능**에서는 설치할 패키지를 찾아볼 수 있습니다. 패키지가 설치되어 있으면 오른쪽의 **설치** 단추가 **제거**로 변경됩니다.

    ![Visual Studio용 R 도구 패키지 관리자의 사용 가능한 패키지 탭](media/package-manager-available.png)

- **설치됨**에는 설치되고 로드된 모든 패키지가 표시됩니다. 패키지 옆에 있는 녹색 점은 패키지가 R 세션으로 로드됨을 나타냅니다. 왼쪽 목록의 빨간색 X 아이콘 또는 오른쪽의 **제거** 단추를 사용하여 패키지를 제거할 수 있습니다. 설치된 패키지의 최신 버전을 사용할 수 있는 경우 패키지 오른쪽의 파란색 위쪽 화살표가 업데이트를 수행합니다.

    ![Visual Studio용 R 도구 패키지 관리자의 설치된 패키지 탭](media/package-manager-installed.png)

- **로드됨**에는 R 세션으로 로드된 패키지만 표시되며 모두 녹색 점이 표시됩니다. 여기서 패키지를 제거하고 업데이트할 수도 있습니다.

    ![Visual Studio용 R 도구 패키지 관리자의 로드된 패키지 탭](media/package-manager-loaded.png)

## <a name="package-locations"></a>패키지 위치

패키지는 다음 위치에 설치됩니다.

- RTVS와 함께 제공되는 코어 패키지는 *C:\Program Files\Microsoft\R Client\R_SERVER\library*에 설치됩니다.
- 추가 패키지는 *%userprofile%\Documents\R\win-library\3.3*에 설치됩니다.
