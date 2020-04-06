---
title: 디버거 확장성 시작하기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738600"
---
# <a name="get-started-with-debugger-extensibility"></a>디버거 확장성 시작
환경 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 내에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로그램을 디버깅하는 데 사용되는 디버거 구성 요소를 만들고 사용자 지정하는 데 필요한 정보를 제공합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버깅은 이전 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거에서 수행된 광범위한 유용성 테스트에서 파생된 향상된 기능을 추가했습니다. 디버깅을 사용하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다국어 응용 프로그램을 단계별로 실행하거나 응용 프로그램 및 다국어 솔루션을 디버깅하는 동안 변수의 즉석 편집을 구현할 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버깅은 프로그램이 디버깅되는 프로세스에서 실행되므로 응용 프로그램의 프로세스 공간에 덜 방해가 됩니다. 따라서 디버깅 프로그램에 영향을 주지 않고 디버거와 상호 작용하는 구성 요소를 작성하는 것이 더 쉽습니다.

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]을 가장 잘 사용하려면 다음 항목을 잘 알고 있어야 합니다.

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합 개발 환경(IDE)

- C++ 프로그래밍 언어

- ATL COM

## <a name="in-this-section"></a>섹션 내용
 [디버거 확장을 위한 로드맵](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) 컴파일러 및 출력에 따라 제품에서 디버깅을 구현하는 프로세스를 간략하게 설명합니다.

 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md) 디버그 엔진(DE), 식 계산기(EE) 및 기호 처리기(SH)를 포함하는 디버깅 구성 요소에 대한 개요를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제공합니다.

 [디버거 개념](../../extensibility/debugger/debugger-concepts.md) 주요 디버깅 아키텍처 개념에 대해 설명합니다.

 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md) DE버그 엔진(DE)이 코드, 설명서 및 식 평가 컨텍스트 내에서 동시에 작동하는 방법을 설명합니다. 세 가지 컨텍스트 각각에 대해 해당 컨텍스트와 관련된 위치, 위치 또는 평가에 대해 설명합니다.

 [작업 디버깅](../../extensibility/debugger/debugging-tasks.md) 프로그램 실행 및 식 평가와 같은 다양한 디버깅 작업에 대한 링크가 포함되어 있습니다.
