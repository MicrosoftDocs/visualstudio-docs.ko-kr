---
title: 공용 언어 런타임 및 식 계산 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b75cb1b0604f3611c0e51c6f458939433d2a5470
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842151"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>공용 언어 런타임 및 식 계산
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 CLR (공용 언어 런타임)을 대상으로 하는 Visual Basic 및 c #과 같은 컴파일러는 나중에 네이티브 코드로 컴파일되는 MSIL (Microsoft 중간 언어)을 생성 합니다. CLR은 결과 코드를 디버그 하기 위한 DE (디버그 엔진)를 제공 합니다. 소유 프로그래밍 언어를 Visual Studio IDE에 통합 하려는 경우 MSIL로 컴파일하도록 선택할 수 있으므로 사용자가 직접 작성 하지 않아도 됩니다. 그러나 프로그래밍 언어의 컨텍스트 내에서 식을 평가할 수 있는 EE (식 계산기)를 작성 해야 합니다.  
  
## <a name="discussion"></a>토론(Discussion)  
 일반적으로 컴퓨터 언어 식은 데이터 개체 집합 및 해당 개체를 조작 하는 데 사용 되는 연산자 집합을 생성 하기 위해 구문 분석 됩니다. 예를 들어 "A + B" 식을 구문 분석 하 여 데이터 개체 "A"와 "B"에 더하기 연산자 (+)를 적용 하면 다른 데이터 개체가 생성 될 수 있습니다. 데이터 개체, 연산자 및 연결의 총 집합은 일반적으로 프로그램에서 트리로 표시 되며 트리의 노드에는 연산자와 분기의 데이터 개체를 포함 합니다. 트리 형식으로 분할 된 식을 종종 구문 분석 된 트리 라고 합니다.  
  
 식을 구문 분석 한 후에는 각 데이터 개체를 평가 하기 위해 기호 공급자 (SP)가 호출 됩니다. 예를 들어 "A"가 둘 이상의 메서드에 정의 된 경우 "the A?" 라는 질문은 의 값을 이것이 winmd 하려면 먼저 응답 해야 합니다. SP에서 반환 하는 대답은 "5 번째 스택 프레임의 세 번째 항목" 또는 "이 메서드에 할당 된 정적 메모리의 시작 부분을 벗어난 50 바이트입니다."와 같습니다.  
  
 프로그램 자체에 대 한 MSIL을 생성 하는 것 외에도 CLR 컴파일러는 프로그램 데이터베이스 (.pdb) 파일에 기록 되는 매우 설명적인 디버깅 정보를 생성할 수 있습니다. 소유 언어 컴파일러가 CLR 컴파일러와 동일한 형식으로 디버그 정보를 생성 하는 한 CLR의 SP는 해당 언어의 명명 된 데이터 개체를 식별할 수 있습니다. 명명 된 데이터 개체가 식별 되 면 EE는 바인더 개체를 사용 하 여 데이터 개체를 해당 개체의 값을 보유 하는 메모리 영역에 연결 (또는 바인딩) 합니다. 그러면 DE는 데이터 개체의 새 값을 가져오거나 설정할 수 있습니다.  
  
 소유 컴파일러는 `ISymbolWriter` 네임 스페이스의 .NET Framework에 정의 된 인터페이스를 호출 하 여 CLR 디버깅 정보를 제공할 수 있습니다 `System.Diagnostics.SymbolStore` . MSIL로 컴파일하고 이러한 인터페이스를 통해 디버그 정보를 작성 하면 전용 컴파일러가 CLR DE 및 SP를 사용할 수 있습니다. 이렇게 하면 전용 언어를 Visual Studio IDE에 통합 하는 작업이 매우 간단해 집니다.  
  
 CLR DE가 독점 EE를 호출 하 여 식을 계산할 때 DE는 EE와 바인더 개체에 대 한 인터페이스를 제공 합니다. 따라서 CLR 기반 디버그 엔진을 작성 하는 것은 적절 한 식 계산기 인터페이스를 구현 하는 데만 필요 합니다. CLR은 바인딩과 기호 처리를 처리 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
