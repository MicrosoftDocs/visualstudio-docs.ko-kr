---
title: 디버거 확장을 위한 로드맵 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713142"
---
# <a name="roadmap-for-extending-the-debugger"></a>디버거 확장을 위한 로드맵
이 설명서에서는 [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] 디버거를 로 확장하기 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]위한 가이드 및 참조 정보를 제공합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버깅 설명서에는 샘플, 포괄적인 참조 및 디버거를 사용자 지정하는 일반적인 방법을 보여 주는 몇 가지 대표 시나리오가 포함됩니다.

 컴파일러와 그 출력은 제품에서 디버깅을 설정하는 데 필요한 사항을 결정합니다. 컴파일러가 다음과 같은 경우:

- Windows 네이티브 운영 체제를 대상으로 하고 *을 작성합니다. PDB* 파일, 당신은 에 통합 된 기본 코드 디버그 엔진 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](DE)와 프로그램을 디버깅 할 수 있습니다. DE 또는 식 계산기를 구현할 필요가 없습니다. 식 계산기는 C++ 프로그래밍 언어의 구문에 대해 작성됩니다.

- 마이크로 소프트 중간 언어 (MSIL) 출력을 생성, 당신은 또한에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]통합 된 관리 코드 디버그 엔진 DE로 프로그램을 디버깅 할 수 있습니다. 따라서 식 계산기만 구현하면 됩니다. 샘플 식 계산기는 제공됩니다. 자세한 내용은 아래 항목을 참조하세요.

   [표현식 평가](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [식 계산](../../extensibility/debugger/evaluating-expressions.md)

   [식 평가 컨텍스트](../../extensibility/debugger/expression-evaluation-context.md)

   [중단 모드에서 표현식 평가](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [공통 언어 런타임 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- 독점 운영 체제 또는 다른 런타임 환경을 대상으로 하려면 고유한 DE를 작성해야 합니다. ATL COM을 사용하여 간단한 DE를 만드는 자습서가 제공됩니다. 자세한 내용은 아래 항목을 참조하세요.

   [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [자습서: ATL COM을 사용 하 여 디버그 엔진 빌드](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [포트 공급업체 구현](../../extensibility/debugger/implementing-a-port-supplier.md)

   [샘플](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>참조
- [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
