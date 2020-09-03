---
title: 포인터가 메모리 주소를 손상시키는지 어떻게 알 수 있습니까? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1d4f23b885b2e72e53d288946df18e038d9d956d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476775"
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>포인터가 메모리 주소를 손상시키는지 어떻게 알 수 있습니까?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

문제 설명  
 포인터 하나가 0x00408000 주소의 메모리를 손상시키고 있는 것 같습니다. 어떻게 알아 낼 수 있습니까?  
  
## <a name="solution"></a>솔루션  
  
#### <a name="check-for-heap-corruption"></a>힙 손상 확인  
  
- 대부분의 메모리 손상은 실제로 힙 손상으로 인해 발생합니다. 전역 플래그 유틸리티(gflags.exe) 또는 pageheap.exe를 사용해 보십시오. [GFlags 및 PageHeap](/windows-hardware/drivers/debugger/gflags-and-pageheap) 및 [PageHeap 유틸리티를 사용 하 여 Microsoft Visual C++ 프로젝트에서 메모리 오류를 검색 하는 방법](https://support.microsoft.com/help/264471/how-to-use-the-pageheap-utility-to-detect-memory-errors-in-a-microsoft)을 참조 하세요.
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>메모리 주소가 수정된 위치를 찾으려면  
  
1. 0x00408000에 데이터 중단점을 설정합니다. [데이터 변경 중단점 설정(네이티브 C++만 해당)](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only)을 참조하세요.  
  
2. 중단점이 적중되면 **메모리** 창을 사용하여 0x00408000에서 시작하는 메모리 내용을 검토합니다. 자세한 내용은 [메모리 창](../debugger/memory-windows.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [네이티브 코드 디버그 Faq](../debugger/debugging-native-code-faqs.md)   
 [네이티브 코드 디버그](../debugger/debugging-native-code.md)
