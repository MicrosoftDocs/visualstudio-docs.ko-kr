---
title: F1 도움말 키 변경
description: F1 키 매핑을 다시 매핑하거나 제거하는 방법을 설명합니다.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperfq1
robots: noindex,nofollow
manager: jillfra
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: debf469248a8ec1906f3692c37835d9f96476f54
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88802306"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Visual Studio에서 F1 도움말 키 변경

F1 키를 F1 도움말 서비스가 아닌 다른 기능으로 지정하거나 F1으로 도움말 기능을 사용하지 않으려면 키 매핑을 제거하거나 수정하면 됩니다.

> [!IMPORTANT]
> 성능 문제로 인해 F1 도움말을 사용하지 않으려고 한다면 Visual Studio 업데이트 시 F1 도움말 서비스의 개선 사항을 테스트할 수 있도록 키 매핑을 일시적으로 수정하는 것이 좋습니다. 대부분의 시나리오에서 F1은 언어 키워드 참조 페이지와 코드 편집기의 API를 열거나 IDE의 창 또는 UI 구성 요소와 연결된 도움말 페이지를 열 수 있는 간편한 방법입니다. 비활성화하는 경우 Visual Studio 내의 모든 용도에서 사용하지 않도록 설정됩니다.

**F1 도움말을 사용하지 않도록 설정하려면**

1. Visual Studio에서 **도구** > **옵션**을 선택한 다음 **환경**에서 **키보드**를 선택합니다.

1. **다음을 포함하는 명령 표시** 텍스트 상자에 **Help.f1**을 입력하여 명령 보기를 필터링합니다.

   ![F1 도움말 사용 안 함](../not-in-toc/media/disable-f1-help-key.png)

1. 키 매핑을 제거하려면 **제거**를 선택합니다.

1. **바로 가기 키 누르기** 텍스트 상자를 선택합니다.

1. 키보드에서 새로운 키 또는 **Alt + F1**과 같은 F1 도움말 키 조합을 누르고 **할당**과 **확인**을 차례로 선택합니다.

키보드 바로 가기 키에 대한 자세한 내용은 [키보드 바로 가기 키 식별 및 사용자 지정](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)을 참조하세요.
