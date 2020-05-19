---
title: 진행 중인 디버깅 중지 대화 상자 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3beefe16f8883eb64d7d0a2641cabf9eb1f702fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729665"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>진행 중인 디버깅 중지 대화 상자
이 대화 상자는 디버거가 디버깅 세션을 중지하려고 할 때 세션 중지에 시간이 오래 걸릴 경우에 나타납니다. 일반적으로 디버깅 세션 중지는 매우 빠르게 이루어지므로 이 대화 상자가 나타나지 않습니다. 그러나 경우에 따라 디버깅 중인 모든 프로세스에서 분리하는 데 시간이 추가로 소요됩니다. 세션을 중지하는 데 몇 초 이상 걸리거나 분리 오류가 발생하는 경우 이 대화 상자가 나타납니다. 이러한 현상이 자주 발생하는 경우 내부 문제가 그 원인일 수 있으며 필요하면 기술 지원 서비스에 문의할 수 있습니다.

 프로세스가 분리되고 이 대화 상자가 사라질 때까지 기다리거나 **지금 중지** 단추를 사용하여 즉시 종료할 수 있습니다.

 **지금 중지** 디버깅 세션을 즉시 종료하려면 이 단추를 클릭합니다. **지금 중지**를 사용하면 디버그 중인 프로세스가 분리되는 것이 아니라 종료됩니다. 시스템 프로세스를 디버깅하는 경우 **지금 중지**를 사용하여 프로세스를 종료하면 예기치 않은 결과가 발생할 수 있습니다.

## <a name="see-also"></a>참조
- [디버거 보안](../debugger/debugger-security.md)
- [프로그램 분리](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))