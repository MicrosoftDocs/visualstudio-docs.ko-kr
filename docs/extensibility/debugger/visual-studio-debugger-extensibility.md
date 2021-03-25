---
title: Visual Studio 디버거 확장성 | Microsoft Docs
description: 이 문서에서는 visual studio 디버거 확장성을 설명 하 고 Visual Studio 디버깅 관련 문서에 대 한 링크를 제공 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbc44da3f98555774dd62c2b061bbf3a0799926e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057730"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio 디버거 확장성
Visual Studio에는 프로그램에서 버그를 추적 하는 데 사용할 수 있는 강력 하 고 사용 하기 쉬운 도구를 제공 하는 완전 한 대화형 소스 코드 디버거가 포함 되어 있습니다. 디버거는 Visual Basic, c #, c/c + + 및 JavaScript에 대 한 완전 한 지원을 제공 합니다. 그러나 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=21835)에서 제공 되는을 사용 하 여 다른 프로그래밍 언어는 동일한 풍부한 기능을 가진 디버거에서 지원 될 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버거는 디버깅 중인 언어와 관련 하 여 디버깅 구성 요소에 대 한 일반적인 프런트 엔드 (사용자 인터페이스)입니다. 새 언어의 경우 디버거를 지 원하는 데 필요한 모든 기능은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE (디버그 엔진)와 같은 필요한 백 엔드 구성 요소를 만드는 것입니다. 이 시점 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 에서가 제공 됩니다.

 에는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 새 DE를 만드는 데 필요한 모든 요소에 대 한 전체 참조가 포함 되어 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 또한 시작 하는 데 도움이 되는 샘플과 자습서가 있습니다.

 디버깅을 지 원하는 언어 프로젝트 시스템의 전체 샘플은 [IronPython 샘플](https://www.microsoft.com/download/details.aspx?id=55984)을 참조 하세요.

 다음 섹션에서는를 사용 하 여 디버거를 확장 하는 방법을 설명 합니다 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

## <a name="in-this-section"></a>단원 내용
 [시작 하기](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅에서 제공 하는 내용과 SDK를 설치 하는 방법을 설명 합니다.

 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md) De를 분리 하기 위해 프로그램 준비에서 사용자 지정 DE 프로세스를 문서화 합니다.

 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) 식 계산기를 작성 해야 하는지 여부를 설명 합니다.

 [디버그 엔진 구현 전략 선택](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) DE를 구현 하는 방법을 설명 합니다.

 [참조](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅 API를 문서화 합니다.

 [샘플](../../extensibility/debugger/visual-studio-debugging-samples.md) 공용 언어 런타임 식 계산기 샘플과 디버그 엔진 샘플에 대 한 링크를 포함 합니다.
