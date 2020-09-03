---
title: 디버거 외부에서 프로그램을 실행하는 경우 액세스 위반을 어떻게 디버깅할 수 있습니까? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce5b21f92eecf2e8929c142bc1ee32e20d386335
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299257"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>디버거 외부에서 프로그램을 실행하는 경우 액세스 위반을 어떻게 디버깅할 수 있습니까?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

문제 설명  
 프로그램이 Visual Studio 환경에서 올바르게 실행됩니다. 그러나 Windows 운영 체제에서 독립 실행형으로 실행하면 액세스 위반이 발생합니다. 이 문제를 어떻게 디버깅할 수 있습니까?  
  
## <a name="solution"></a>솔루션  
 [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md) 옵션을 설정하고 액세스 위반이 발생할 때까지 프로그램을 독립 실행형으로 실행합니다. 그런 다음, **액세스 위반** 대화 상자에서 **취소**를 클릭하여 디버거를 시작할 수 있습니다.  
  
 또는 기술 자료 문서 Q133174 "How to Locate Where a General Protection (GP) Fault Occurs."를 참조하십시오. 기술 자료 문서는 MSDN Library CD 또는를 검색 하 여 찾을 수 있습니다 [http://support.microsoft.com/](https://support.microsoft.com/) .  
  
## <a name="see-also"></a>관련 항목  
 [네이티브 코드 디버그 Faq](../debugger/debugging-native-code-faqs.md)   
 [네이티브 코드 디버그](../debugger/debugging-native-code.md)
