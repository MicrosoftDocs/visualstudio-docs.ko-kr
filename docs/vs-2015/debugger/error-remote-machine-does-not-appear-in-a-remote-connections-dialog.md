---
title: '오류: 원격 머신은 원격 연결 대화 상자에 표시되지 않음 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a97211c1fa86123a2a7a65f2ff86b0cecac957dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697322"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>오류: 원격 컴퓨터는 원격 연결 대화 상자에 표시되지 않습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

원격 컴퓨터가 원격 연결 대화 상자에 표시되지 않는 경우 다음과 같은 일반적인 원인을 확인합니다.  
  
 관리되는 호환성 모드를 사용하는 경우 Visual Studio 2010 설명서를 확인하세요. [원격 디버깅 문제 해결 - Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>이 오류의 일반적인 원인  
  
- 원격 컴퓨터가 다른 서브넷에 있는 컴퓨터에서 실행되고 있습니다. 이 문제를 해결하려면 수동으로 한정자 대화 상자에 컴퓨터 이름 또는 IP 주소를 입력합니다.  
  
- 원격 컴퓨터에서 원격 디버거가 실행되고 있지 않습니다. 이 문제를 해결하려면 원격 디버거를 시작합니다.  
  
- 방화벽이 Visual Studio와 원격 컴퓨터 간의 통신을 차단하고 있습니다. 이 문제를 해결하려면 Visual Studio와 원격 디버거(msvsmon) 간의 통신을 허용하도록 방화벽을 구성합니다.  
  
- 바이러스 백신 소프트웨어가 Visual Studio와 원격 컴퓨터 간의 통신을 차단하고 있습니다. 이 문제를 해결하려면 Visual Studio와 원격 디버거(msvsmon) 간의 통신을 허용하도록 바이러스 백신 소프트웨어를 구성합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디바이스에서 원격 도구 설정](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
