---
title: 디버거 확장성 시작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152707"
---
# <a name="getting-started-with-debugger-extensibility"></a>디버거 확장성 시작
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

는 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 환경 내에서 프로그램을 디버깅 하는 데 사용 되는 디버거 구성 요소를 만들고 사용자 지정 하는 데 필요한 정보를 제공 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버깅은 이전 디버거에서 수행한 광범위 한 유용성 테스트에서 파생 된 향상 된 기능을 추가 했습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]디버깅을 사용 하 여 다중 언어 응용 프로그램을 단계별로 실행 하거나, 응용 프로그램 및 다국어 솔루션을 디버깅 하는 동안 변수를 즉시 편집할 수 있습니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버깅은 디버깅 중인 프로그램에서 out-of-process로 실행 되므로 응용 프로그램의 프로세스 공간에서 사용이 중단 되지 않습니다. 따라서 디버깅 프로그램에 영향을 주지 않고 디버거와 상호 작용 하는 구성 요소를 작성 하는 것이 더 쉽습니다.  
  
 을 사용 하려면 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 다음에 대해 잘 알고 있어야 합니다.  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE (통합 개발 환경)  
  
- C + + 프로그래밍 언어  
  
- ATL COM  
  
## <a name="in-this-section"></a>섹션 내용  
 [디버거 확장 로드맵](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 컴파일러 및 해당 출력에 따라 제품에서 디버깅을 구현 하는 프로세스를 간략하게 설명 합니다.  
  
 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]디버그 엔진 (DE), 식 계산기 (EE) 및 기호 처리기 (SH)를 포함 하는 디버깅 구성 요소에 대 한 개요를 제공 합니다.  
  
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)  
 주요 디버깅 아키텍처 개념을 설명 합니다.  
  
 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)  
 디버그 엔진 (DE)이 코드, 설명서 및 식 계산 컨텍스트 내에서 동시에 작동 하는 방법을 설명 합니다. 각각의 세 가지 컨텍스트, 위치, 위치 또는 평가에 대해 설명 합니다.  
  
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)  
 프로그램 시작 및 식 계산과 같은 다양 한 디버깅 태스크에 대 한 링크를 포함 합니다.
