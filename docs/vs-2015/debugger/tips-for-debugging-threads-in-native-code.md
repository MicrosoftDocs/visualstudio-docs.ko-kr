---
title: 네이티브 코드의 스레드 디버그 팁 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], threads
ms.assetid: 0374c8c6-57a3-4cfe-8047-2effef5ff5dc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7c299d3585d9089f8525c2ec7f470601797cc3a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684864"
---
# <a name="tips-for-debugging-threads-in-native-code"></a>네이티브 코드의 스레드 디버깅 팁
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음은 네이티브 코드에서 스레드를 디버깅할 때 사용할 수 있는 몇 가지 팁입니다.  
  
- **조사식** 창이나 **간략한 조사식** 대화 상자에 `@TIB`를 입력하면 스레드 정보 블록의 내용이 표시됩니다.  
  
- **조사식** 창이나 **간략한 조사식** 대화 상자에 `@Err`을 입력하면 현재 스레드의 마지막 오류 코드가 표시됩니다.  
  
- CRT(C Run-Time Libraries) 함수는 다중 스레드 애플리케이션을 디버깅하는 데 유용합니다. 자세한 내용은 [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [다중 스레드 응용 프로그램 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [네이티브 코드 디버그](../debugger/debugging-native-code.md)
