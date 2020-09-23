---
title: Spy++ 시작 | Microsoft Docs
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7743d36671e1c651b9bcfa89b315399c0696e26d
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851907"
---
# <a name="how-to-start-spy"></a>방법: Spy++ 시작

Visual Studio 또는 명령 프롬프트에서 Spy++를 시작할 수 있습니다.

 Spy++를 시작할 때 컴퓨터를 변경할 수 있는 권한을 요청하는 메시지가 표시되면 **예**를 선택합니다.

> [!NOTE]
> Spy++ 인스턴스는 하나만 실행할 수 있습니다. 두 번째 인스턴스를 시작하려고 하면 단지 현재 실행 중인 인스턴스가 포커스를 가져옵니다.

## <a name="prerequisites"></a>사전 요구 사항

Spy++를 사용하려면 다음과 같은 구성 요소가 있어야 합니다. **개별 구성 요소** 탭을 선택한 후 다음 구성 요소를 선택하여 Visual Studio 설치 관리자에서 이러한 구성 요소를 선택할 수 있습니다.

* 디버깅 및 테스트에서 **C++ 프로파일링 도구**를 선택합니다.
* 개발 작업에서 **C++ 핵심 기능**을 선택합니다.

변경한 경우에는 프롬프트에 따라 이러한 구성 요소를 설치합니다.

## <a name="start-spy-from-visual-studio"></a>Visual Studio에서 Spy++ 시작

**도구** 메뉴에서 **Spy++** 를 선택합니다.

Spy++는 독립적으로 실행되므로 시작한 후 Visual Studio를 닫을 수 있습니다.

> [!NOTE]
> Spy++를 사용하여 메시지를 기록하는 경우 운영 체제가 느려질 수 있습니다.

## <a name="start-spy-at-a-command-prompt"></a>명령 프롬프트에서 Spy++ 시작

1. 명령 프롬프트 창에서 spyxx.exe가 있는 폴더로 디렉터리를 변경합니다. 일반적으로 이 폴더의 경로는 ..\\Visual Studio 설치 폴더\Common7\Tools\\입니다.

2. **spyxx.exe**를 입력합니다.

## <a name="see-also"></a>참조
- [Spy++ 사용](../debugger/using-spy-increment.md)
- [Spy++ 뷰](../debugger/spy-increment-views.md)
- [Spy++ 참조](../debugger/spy-increment-reference.md)
