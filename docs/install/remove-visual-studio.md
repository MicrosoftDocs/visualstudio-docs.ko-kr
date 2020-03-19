---
title: Visual Studio 제거
titleSuffix: ''
description: 컴퓨터에서 Visual Studio를 완전히 제거하는 방법을 단계별로 알아봅니다.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b0e8c8fe10451e9e5906eabf7f4f65086d147904
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113716"
---
# <a name="remove-visual-studio"></a>Visual Studio 제거

치명적인 오류가 발생하여 Visual Studio를 복구 또는 제거할 수 없는 경우 `InstallCleanup.exe` 도구를 실행하여 설치된 모든 Visual Studio 2017 또는 Visual Studio 2019 인스턴스에 대한 설치 파일 및 제품 정보를 제거할 수 있습니다.

> [!WARNING]
> 복구 또는 제거에 실패하는 경우 **최후의 수단으로** InstallCleanup 도구를 사용합니다. 이 도구는 다른 Visual Studio 설치 또는 다른 제품에서 기능을 제거할 수 있으며 해당 기능을 복구 또는 다시 설치할 수도 있습니다.

## <a name="run-installcleanupexe"></a>InstallCleanup.exe 실행

`InstallCleanup.exe` 도구에서 다음 명령줄 스위치 중 하나를 사용할 수 있습니다.

| 스위치 | 동작 |
| ------ | -------- |
| `-i`   | 이 스위치는 다른 스위치가 전달되지 않은 경우의 기본값입니다. 주 설치 디렉터리 및 제품 정보만 제거합니다. `InstallCleanup.exe` 도구를 실행한 후 동일한 버전의 Visual Studio를 다시 설치하려는 경우이 스위치를 사용합니다. |
| `-f`   | 이 스위치는 기본 설치 디렉터리, 제품 정보는 물론, 다른 Visual Studio 설치 또는 다른 제품과 공유할 수도 있는 설치 디렉터리 외부에 설치된 다른 기능 대부분을 제거합니다. 이 스위치는 나중에 다시 설치하지 않고 Visual Studio를 제거하려는 경우에 사용합니다. |

`InstallCleanup.exe` 도구를 실행하는 방법은 다음과 같습니다.

1. Visual Studio 설치 관리자를 닫습니다.
1. 관리자 명령 프롬프트를 엽니다. 관리자 명령 프롬프트를 열려면 다음 단계를 따릅니다.
   * "검색하려면 여기에 입력" 상자에 **cmd**를 입력합니다.
   * **명령 프롬프트**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 선택합니다.
1. `InstallCleanup.exe` 도구의 전체 경로를 입력하고 원하는 명령줄 스위치를 추가합니다. 기본적으로 이 도구의 경로는 다음과 같습니다.

   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

   > [!NOTE]
   > 항상 `InstallCleanup.exe`에 위치하는 Visual Studio 설치 관리자 디렉터리 아래에서 `%ProgramFiles(x86)%\Microsoft Visual Studio`를 찾을 수 없는 경우 다음 단계를 수행합니다. 지침에 따라 [Visual Studio를 설치](install-visual-studio.md)합니다. 그런 다음 워크로드 선택 화면이 표시되면 창을 닫고 이 페이지의 단계를 다시 수행합니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 설치](install-visual-studio.md)
* [Visual Studio 업데이트](update-visual-studio.md)
* [Visual Studio 수정](modify-visual-studio.md)
* [Visual Studio 제거](uninstall-visual-studio.md)
