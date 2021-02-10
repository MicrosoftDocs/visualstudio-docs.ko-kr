---
title: 네이티브 코드의 스레드 디버그 팁 | Microsoft Docs
description: Visual Studio에서 다중 스레드 앱을 디버그하는 경우 네이티브 코드에서 스레드를 디버그하는 작업의 팁 목록을 읽어 봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 85bdd804e25dfa91b649e95daacef4bfb322df64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940568"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>네이티브 코드의 스레드 디버깅 팁
다음은 네이티브 코드에서 스레드를 디버깅할 때 사용할 수 있는 몇 가지 팁입니다.

- **조사식** 창이나 **간략한 조사식** 대화 상자에 `@TIB`를 입력하면 스레드 정보 블록의 내용이 표시됩니다.

- **조사식** 창이나 **간략한 조사식** 대화 상자에 `@Err`을 입력하면 현재 스레드의 마지막 오류 코드가 표시됩니다.

- CRT(C Run-Time Libraries) 함수는 다중 스레드 애플리케이션을 디버깅하는 데 유용합니다. 자세한 내용은 [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg)를 참조하세요.

## <a name="see-also"></a>참조
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)