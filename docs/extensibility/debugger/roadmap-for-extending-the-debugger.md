---
title: 디버거 확장 로드맵 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713142"
---
# <a name="roadmap-for-extending-the-debugger"></a>디버거 확장 로드맵
이 설명서에서는로 디버거를 확장 하는 방법에 대 한 지침 및 참조 정보를 제공 [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅 설명서는 샘플, 포괄적인 참조 및 디버거를 사용자 지정 하는 일반적인 방법을 보여 주는 몇 가지 대표적인 시나리오를 포함 합니다.

 컴파일러와 해당 출력은 제품에서 디버깅을 설정 하는 데 필요한 항목을 결정 합니다. 컴파일러가 다음과 같은 경우:

- Windows 네이티브 운영 체제를 대상으로 지정 하 고를 작성 *합니다. PDB* 파일을 사용 하 여에 통합 된 네이티브 코드 디버그 엔진 (DE)으로 프로그램을 디버그할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . DE 또는 expression 계산기를 구현할 필요가 없습니다. 식 계산기는 c + + 프로그래밍 언어의 구문에 대해 작성 되었습니다.

- MSIL (Microsoft 중간 언어) 출력을 생성 하 고, 관리 코드 디버그 엔진 DE를 사용 하 여 프로그램을 디버그할 수 있습니다 .이는에도 통합 되어 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 따라서 식 계산기를 구현 하기만 하면 됩니다. 샘플 식 계산기가 제공 됩니다. 자세한 내용은 다음 항목을 참조하세요.

   [식 계산](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [식 계산](../../extensibility/debugger/evaluating-expressions.md)

   [식 계산 컨텍스트](../../extensibility/debugger/expression-evaluation-context.md)

   [중단 모드에서 식 계산](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [공용 언어 런타임 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- 는 독점 운영 체제 또는 다른 런타임 환경을 대상으로 하므로 사용자가 직접 작성 해야 합니다. ATL COM을 사용 하 여 간단한 DE를 만드는 자습서가 제공 됩니다. 자세한 내용은 다음 항목을 참조하세요.

   [사용자 지정 디버그 엔진 만들기](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [자습서: ATL COM을 사용 하 여 디버그 엔진 빌드](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [포트 공급자 구현](../../extensibility/debugger/implementing-a-port-supplier.md)

   [샘플](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>추가 정보
- [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
