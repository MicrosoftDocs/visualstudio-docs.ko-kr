---
title: Visual Studio 외부에서 앱을 실행하는 경우 액세스 위반 디버그
titleSuffix: ''
description: Just-In-Time 디버거를 사용하여 Visual Studio 환경 외부에서 발생하는 액세스 위반을 디버그합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dd4709807b176806d8a7ca56de4adda8cdfe13ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904319"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>디버거 외부에서 프로그램을 실행하는 경우 액세스 위반을 어떻게 디버깅할 수 있습니까?

## <a name="problem-description"></a>문제 설명
 프로그램이 Visual Studio 환경에서 올바르게 실행됩니다. 그러나 Windows 운영 체제에서 독립 실행형으로 실행하면 액세스 위반이 발생합니다. 이 문제를 어떻게 디버깅할 수 있습니까?

## <a name="solution"></a>솔루션
 [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md) 옵션을 설정하고 액세스 위반이 발생할 때까지 프로그램을 독립 실행형으로 실행합니다. 그런 다음, **액세스 위반** 대화 상자에서 **취소** 를 클릭하여 디버거를 시작할 수 있습니다.

## <a name="see-also"></a>참조
- [네이티브 코드 디버그 FAQ](../debugger/debugging-native-code-faqs.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)