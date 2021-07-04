---
title: 앱에서 단계별로 실행하는 경우 포커스 유지 | Microsoft Docs
description: 창 활성화 문제를 디버그할 때 프로그램에서 포커스가 손실되지 않도록 하려면 원격 디버깅을 사용합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.stepping
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], stepping
- focus, keeping
- stepping, focus
- windows, troubleshooting activation
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 561e5d4dc009642ee7773cd60d004ef8a64261d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386932"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-app"></a>앱에서 단계별로 실행하는 경우 어떻게 포커스를 유지할 수 있습니까?
## <a name="description"></a>설명
 프로그램에 창 활성화에 대한 문제가 생겼습니다. 프로그램에서 단계별로 디버거를 실행하면 프로그램이 계속해서 포커스를 잃어 버리기 때문에 문제 재현 기능이 방해를 받습니다. 어떻게 해결할 수 있습니까?

## <a name="solution"></a>솔루션
 다른 컴퓨터가 있을 경우 원격 디버깅을 사용합니다. 호스트에서 디버거를 실행하는 동안 원격 컴퓨터에서 프로그램을 작동시킬 수 있습니다. 자세한 내용은 [방법: 원격 컴퓨터 선택](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100))을 참조하세요.

## <a name="see-also"></a>참조
- [네이티브 코드 디버그 FAQ](../debugger/debugging-native-code-faqs.md)
- [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
