---
title: '방법: RPC 디버깅을 사용 하 여 COM 클라이언트 및 서버 디버깅 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- RPC (Remote Procedure Call), debugging COM clients and servers
- COM, debugging
- RPC (Remote Procedure Call)
- RPC (Remote Procedure Call), debugging
- COM clients, debugging
- COM servers, debugging
- out-of-process remote procedure call debugging
- remote debugging, RPC (Remote Procedure Call)
- in-process remote procedure call debugging
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fda2a10cd559f940ab87e5cc8c26f5b47dbec194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843359"
---
# <a name="how-to-debug-com-clients-and-servers-using-rpc-debugging"></a>방법: RPC 디버깅을 사용하여 COM 클라이언트 및 서버 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

RPC(원격 프로시저 호출) 디버깅을 사용하면 COM 클라이언트/서버 애플리케이션을 디버깅할 수 있습니다. RPC 디버깅을 사용하려면 다음과 같은 방법으로 활성화해야 합니다. RPC 디버깅을 활성화하고 클라이언트에서 서버 호출을 한 단계씩 실행하면 디버거에서 서버에 연결하여 코드를 디버깅할 수 있습니다. 디버거를 연결하면 클라이언트 및 서버 프로세스에서 모든 디버거 기능을 사용할 수 있습니다.  
  
### <a name="to-enable-rpc-debugging"></a>RPC 디버깅을 활성화하려면  
  
1. **도구** 메뉴에서 **옵션**을 클릭합니다.  
  
2. **옵션** 대화 상자에서 **Debugging** 폴더를 선택합니다.  
  
3. **네이티브** 페이지를 클릭합니다.  
  
4. **RPC 디버깅** 확인란을 선택합니다.  
  
    > [!NOTE]
    > RPC 호출을 디버깅하려면 관리자 또는 고급 사용자 권한이 있어야 합니다.  
  
    > [!NOTE]
    > Microsoft Windows Vista가 실행되는 원격 서버에서 RPC 단계별 실행을 사용하려면 원격 서버에 네이티브 디버거가 연결되어 있어야 합니다. 그렇지 않으면 RPC 호출이 실패하고 오류 메시지는 표시되지 않습니다. 또는 RPC 호출이 완료되더라도 RPC 호출에 대한 단계별 실행이 작동하지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [COM 서버 및 컨테이너 디버깅](../debugger/com-server-and-container-debugging.md)   
 [Visual Studio의 디버깅](../debugger/debugging-in-visual-studio.md)
