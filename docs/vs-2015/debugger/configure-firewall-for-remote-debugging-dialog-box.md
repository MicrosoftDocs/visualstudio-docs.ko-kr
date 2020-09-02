---
title: 원격 디버깅을 위한 방화벽 구성 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e2b1300feb8d2a15e63089ee9bddde5f2d1ef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702291"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>원격 디버깅을 위한 방화벽 구성 대화 상자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 대화 상자는 Windows 방화벽에서 디버거가 네트워크를 통해 정보를 받는 것을 차단할 때 나타납니다. 원격 디버깅을 계속하려면 디버거가 정보를 받을 수 있도록 방화벽에서 한 지점을 열어야 합니다.  
  
> [!CAUTION]
> 방화벽에서 한 지점을 열면 방화벽을 통해 차단해야 하는 보안 위협에 컴퓨터가 노출될 수 있습니다. 원격 디버깅을 위해 빈 영역을 열면 Visual Studio 2015에서 4020 및 4021 포트가 차단 해제됩니다. 다른 버전의 Visual Studio에서는 다른 포트 번호가 사용됩니다. 자세한 내용은 [원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요. 또한 디버거가 포트를 추가로 열 수 있습니다. 자세한 내용은 [원격 디버깅을 위해 Windows 방화벽 구성](../debugger/configure-the-windows-firewall-for-remote-debugging.md)을 참조하세요.  
  
## <a name="uielement-list"></a>UI 요소 목록  
 **원격 디버깅 취소**  
 원격 디버깅 시도를 취소합니다. 컴퓨터의 보안 설정은 그대로 유지됩니다.  
  
 **로컬 네트워크(서브넷)의 컴퓨터에서 원격 디버깅 차단 해제**  
 로컬 서브넷에 있는 컴퓨터의 원격 디버깅을 활성화합니다. 이 옵션을 설정하면 로컬 서브넷에 있는 컴퓨터의 보안이 취약해질 수 있지만 방화벽은 계속해서 서브넷 외부에서 들어오는 정보를 차단합니다.  
  
 **모든 컴퓨터에서 원격 디버깅 차단 해제**  
 네트워크에 있는 모든 컴퓨터의 원격 디버깅을 활성화합니다. 이 설정은 보안이 가장 취약합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 보안](../debugger/debugger-security.md)   
 [장치에서 원격 도구 설정](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [사용자 인터페이스 참조 디버그](../debugger/debugging-user-interface-reference.md)
