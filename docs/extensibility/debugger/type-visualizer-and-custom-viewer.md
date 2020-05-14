---
title: 유형 시각화 도우미 및 사용자 지정 뷰어 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712461"
---
# <a name="type-visualizer-and-custom-viewer"></a>시각화 도우미 및 사용자 지정 뷰어 유형
형식 시각화 도우미는 특정 형식으로 데이터를 표시하는 구성 요소입니다. 형식은 최종 사용자 또는 시각화 도우미의 타사 공급자등 시각화 도우미를 구현하는 사람에 전적으로 달려 있습니다.

 사용자 지정 뷰어는 특정 형식으로 데이터를 표시하는 사용자 지정 식 계산기의 일부입니다. 이 형식은 전적으로 사용자 지정 뷰어의 구현자에게 달려 있으며, 이는 형식이 식 계산기(EE)의 구현자에게 달려 있음을 의미합니다.

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>식 계산기에서 형식 시각화 도우미 지원
 EE는 [시각화](../../extensibility/debugger/reference/ieevisualizerservice.md) 도우미에 액세스할 수 있는 인터페이스 집합을 지원 하여 형식 시각화 도우미를 지원 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)합니다. 그러나 EE는 형식 시각화 도우미 자체를 구현할 책임이 없습니다. 이러한 시각화 도우미는 EE와 함께 제공 되어 다른 타사 공급 업체 또는 최종 사용자에 의해 제공 하는 Visual Studio의 적절 한 위치에 설치 될 수 있습니다.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>식 평가기에서 사용자 지정 뷰어 지원
 EE는 EE 자체가 데이터 형식을 보기 위한 코드를 제공하는 사용자 지정 뷰어를 지원할 수도 있습니다. 사용자 지정 뷰어는 원하는 형식으로 데이터를 표시하는 모든 임무를 처리하는 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) 인터페이스를 구현합니다. 뷰어는 디스플레이를 완전히 제어할 수 있으며 데이터를 수정할 수도 있습니다. EE에서 제공하는 모든 사용자 지정 뷰어는 제품이 배송될 때 EE와 함께 제공됩니다.

## <a name="see-also"></a>참조
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
- [식 계산기](../../extensibility/debugger/expression-evaluator.md)
- [디버그 엔진](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
