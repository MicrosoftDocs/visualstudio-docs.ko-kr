---
title: 비주얼 스튜디오 디버거 확장성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712510"
---
# <a name="visual-studio-debugger-extensibility"></a>비주얼 스튜디오 디버거 확장성
Visual Studio에는 완전 대화형 소스 코드 디버거가 포함되어 있어 프로그램의 버그를 추적할 수 있는 강력하고 사용하기 쉬운 도구를 제공합니다. 디버거는 비주얼 베이직, C#, C/C++및 자바스크립트를 완벽하게 지원합니다. 그러나 Microsoft [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [다운로드 센터에서](https://www.microsoft.com/download/details.aspx?id=21835)사용할 수 있는 을 사용하면 동일한 풍부한 기능을 가진 디버거에서 다른 프로그래밍 언어를 지원할 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거는 디버깅 중인 언어와 관련된 디버깅 구성 요소에 대한 일반적인 프런트 엔드(즉, 사용자 인터페이스)입니다. 새 언어의 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거가 지원하는 데 필요한 것은 DE(디버그 엔진)와 같은 필요한 백 엔드 구성 요소를 만드는 것입니다. 이 점은 들어오는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 곳입니다.

 여기에는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 새 DE를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 만드는 데 필요한 모든 요소에 대한 완전한 참조가 포함됩니다. 또한 시작하는 데 도움이되는 샘플과 자습서가 있습니다.

 디버깅 지원이 있는 언어 프로젝트 시스템의 전체 샘플은 [IronPython 샘플을](https://www.microsoft.com/download/details.aspx?id=55984)참조하십시오.

 다음 섹션에서는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]을 사용하여 디버거를 확장하는 방법을 설명합니다.

## <a name="in-this-section"></a>섹션 내용
 [시작하기](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) 디버깅이 제공하는 내용과 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] SDK 를 설치하는 방법에 대해 설명합니다.

 [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md) DE에 대한 프로그램 준비에서 DE 분리에 이르기까지 사용자 지정 DE 프로세스를 문서화합니다.

 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) 식 계산기 작성 여부를 설명합니다.

 [디버그 엔진 구현 전략 선택](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) DE를 구현하는 방법에 대해 설명합니다.

 [참고 자료](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) 디버깅 API를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 문서화합니다.

 [샘플](../../extensibility/debugger/visual-studio-debugging-samples.md) 공통 언어 런타임 식 계산기 샘플 및 디버그 엔진 샘플에 대한 링크가 포함되어 있습니다.
