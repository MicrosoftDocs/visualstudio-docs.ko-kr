---
title: 공용 언어 런타임 식 계산기 작성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 961a4d646a61fedda381f9451902b3bcdcc956d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842006"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>공용 언어 런타임 식 계산기 작성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 식 계산기 (EE)는 디버깅 중인 코드를 생성 한 프로그래밍 언어의 구문 및 의미 체계를 처리 하는 디버그 엔진 (DE)의 일부입니다. 식은 프로그래밍 언어의 컨텍스트 내에서 계산 되어야 합니다. 예를 들어 일부 언어에서 "A + B" 식은 "A와 B의 합계"를 의미 합니다. 다른 언어에서는 동일한 식이 "A 또는 B"를 의미할 수 있습니다. 따라서 Visual Studio IDE에서 디버그할 개체 코드를 생성 하는 각 프로그래밍 언어에 대해 별도의 EE를 작성 해야 합니다.  
  
 Visual Studio 디버그 패키지의 일부 측면은 프로그래밍 언어의 컨텍스트에서 코드를 해석 해야 합니다. 예를 들어 실행이 중단점에서 중단 되 면 사용자가 **조사식** 창에 입력 한 모든 식을 평가 하 여 표시 해야 합니다. 또한 사용자는 **조사식** 창 또는 **직접 실행** 창에 식을 입력 하 여 지역 변수 값을 변경할 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [공용 언어 런타임 및 식 계산](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 전용 프로그래밍 언어를 Visual Studio IDE에 통합 하는 경우 소유 언어의 컨텍스트 내에서 식을 평가할 수 있는 EE를 작성 하면 디버그 엔진을 작성 하지 않고도 MSIL (Microsoft 중간 언어)로 컴파일할 수 있음을 설명 합니다.  
  
 [식 계산기 아키텍처](../../extensibility/debugger/expression-evaluator-architecture.md)  
 필요한 EE 인터페이스를 구현 하 고 공용 언어 런타임 기호 공급자 (SP) 및 바인더 인터페이스를 호출 하는 방법을 설명 합니다.  
  
 [식 계산기 등록](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 EE는 공용 언어 런타임 및 Visual Studio 런타임 환경을 모두 사용 하 여 클래스 팩터리로 자신을 등록 해야 합니다.  
  
 [식 계산기 구현](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 식 계산 프로세스에 디버그 엔진 (DE), 기호 공급자 (SP), 바인더 개체 및 식 계산기 (EE)를 포함 하는 방법을 설명 합니다.  
  
 [로컬 항목 표시](../../extensibility/debugger/displaying-locals.md)  
 실행이 일시 중지 되 면 디버그 패키지에서 DE를 호출 하 여 지역 변수 및 인수 목록을 가져오는 방법에 대해 설명 합니다.  
  
 [조사식 창 식 계산](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Visual Studio 디버그 패키지에서 DE를 호출 하 여 조사식 목록에서 각 식의 현재 값을 확인 하는 방법을 보여 줍니다.  
  
 [로컬 항목 값 변경](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 로컬의 값을 변경 하는 경우 지역 창의 각 줄에는 로컬의 이름, 형식 및 현재 값을 제공 하는 관련 개체가 있습니다.  
  
 [형식 시각화 도우미 및 사용자 지정 뷰어 구현](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 형식 시각화 도우미 및 사용자 지정 뷰어를 지 원하는 구성 요소에서 구현 해야 하는 인터페이스에 대해 설명 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
