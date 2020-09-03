---
title: 디버그 엔진 구현 전략 선택 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183464"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>디버그 엔진 구현 전략 선택
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

런타임 아키텍처를 사용 하 여 DE (디버그 엔진) 구현 전략을 결정 합니다. 디버그 엔진은 프로그램에서 in-process로 디버그 하거나, Visual Studio 세션 디버그 관리자 (SDM)에 대 한 프로세스 내에서 또는 둘 모두에 대해 out-of-process로 만들 수 있습니다. 다음 지침은 이러한 세 가지 전략 중 하나를 선택 하는 데 도움이 됩니다.  
  
## <a name="guidelines"></a>지침  
 제거 하는 것이 SDM 및 프로그램 모두에 대 한 out-of-process가 될 수 있지만 일반적으로 이러한 작업을 수행할 필요가 없습니다. 프로세스 경계를 넘어 호출 하는 것은 상대적으로 느립니다.  
  
 디버그 엔진은 Win32 네이티브 런타임 환경 및 공용 언어 런타임 환경에 대해 이미 제공 됩니다. 이러한 환경 중 하나에 대 한 DE를 교체 해야 하는 경우에는 SDM을 사용 하 여 DE-DE를 만들어야 합니다.  
  
 그렇지 않은 경우에는 SDM 또는 in-process로의 in-process를 만드는 중에서 디버그할 프로그램에 대해 선택할 수 있습니다. DE의 식 계산기가 프로그램 기호 저장소에 자주 액세스 해야 하는지 여부 및 빠른 액세스를 위해 기호 저장소를 메모리에 로드할 수 있는지 여부를 고려 하는 것이 중요 합니다. 또한 다음 사항도 고려합니다.  
  
- 식 계산기와 기호 저장소 사이에 많은 호출이 없거나 기호 저장소를 SDM 메모리 공간으로 읽을 수 있는 경우 SDM에 대해 in-process를 만듭니다. 프로그램에 연결 되 면 디버그 엔진의 CLSID를 SDM에 반환 해야 합니다. SDM은이 CLSID를 사용 하 여 DE-DE의 in-process 인스턴스를 만듭니다.  
  
- DE가 프로그램을 호출 하 여 기호 저장소에 액세스 해야 하는 경우 프로그램을 사용 하 여 DE-DE를 만듭니다. 이 경우 프로그램은 DE의 인스턴스를 만듭니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
