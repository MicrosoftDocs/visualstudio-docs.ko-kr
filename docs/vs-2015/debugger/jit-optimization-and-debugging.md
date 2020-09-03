---
title: JIT 최적화 및 디버깅 | Microsoft Docs
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
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690535"
---
# <a name="jit-optimization-and-debugging"></a>JIT 최적화 및 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

관리 되는 응용 프로그램을 디버깅할 때에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 기본적으로 JIT (just-in-time) 코드 최적화를 적용 하지 않습니다. JIT 최적화를 사용하지 않으면 최적화되지 않은 코드를 디버깅하게 됩니다. 코드가 최적화되지 않으므로 코드 실행 속도는 약간 느려지지만 디버깅은 더 철저하게 수행할 수 있습니다. 최적화된 코드는 디버깅하기가 더 어려우므로 최적화된 코드에서는 발생하지만 최적화되지 않은 버전의 코드에서는 재현되지 않는 버그를 발견한 경우에만 이를 수행하는 것이 좋습니다.  
  
 JIT 최적화는 모듈을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **로드할 때 jit 최적화** 해제 옵션을 통해 제어 됩니다. 이 옵션은 **옵션** 대화 상자의 **디버깅** 노드 아래에 있는 **일반** 페이지에서 찾을 수 있습니다.  
  
 **모듈을 로드할 때 JIT 최적화 기능 표시 안 함** 옵션을 선택 취소 하면 최적화 된 JIT 코드를 디버깅할 수 있지만 최적화 된 코드는 소스 코드와 일치 하지 않기 때문에 디버깅 기능이 제한 될 수 있습니다. 따라서 **지역** 및 **자동** 창과 같은 디버거 창에는 최적화 되지 않은 코드를 디버깅 하는 경우와 같은 정보가 표시 되지 않을 수 있습니다.  
  
 또 하나의 중요한 차이점은 내 코드만을 사용한 디버깅과 관련된 것입니다. 내 코드만을 사용하여 디버깅하는 경우 디버거는 최적화된 코드를 사용자가 작성하지 않은 코드로 간주합니다. 이러한 코드는 디버깅하는 동안 표시되지 않습니다. 따라서 JIT 최적화된 코드를 디버깅하는 경우 내 코드만 옵션을 해제해야 할 수도 있습니다. 자세한 내용은  [내 코드만 단계별 실행 제한](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code)을 참조 하세요.  
  
 **모듈 로드 시 JIT 최적화 무시** 옵션은 모듈이 로드 될 때 코드 최적화를 억제 합니다. 이미 실행 중인 프로세스에 연결하는 경우 이 프로세스에는 이미 로드되어 JIT 컴파일 및 최적화된 코드가 포함되어 있을 수 있습니다. **모듈을 로드할 때 JIT 최적화 기능 적용 안 함** 옵션은 연결 후 로드 된 모듈에 영향을 주지만 이러한 코드에는 영향을 주지 않습니다. 또한 **모듈을 로드할 때 JIT 최적화 사용 안 함** 옵션은 NGEN을 사용 하 여 만든 WinForms.dll와 같은 모듈에 영향을 주지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [관리 코드 디버깅](../debugger/debugging-managed-code.md)   
 [디버거로 코드 탐색](../debugger/navigating-through-code-with-the-debugger.md)   
 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [관리되는 실행 프로세스](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
