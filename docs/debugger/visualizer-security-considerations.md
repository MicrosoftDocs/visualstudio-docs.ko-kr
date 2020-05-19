---
title: 시각화 도우미 보안 고려 사항 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, security
- security [Visual Studio], visualizers
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1c18ec84a6a62da6cd564c69ef4b83ea76bcfd6
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187153"
---
# <a name="visualizer-security-considerations"></a>시각화 도우미 보안 고려 사항
시각화 도우미를 작성할 때는 보안 문제를 고려해야 합니다. 당장은 이러한 잠재적 위협에 대한 취약점이 발견되지 않더라도 개발자는 이러한 문제의 가능성을 인식하고 여기서 설명하는 적절한 보안 예방책에 따라 향후 발생할 수 있는 위험에 대비해야 합니다.

 디버거 시각화 도우미에는 부분 신뢰 애플리케이션에 허용되는 것보다 많은 권한이 필요합니다. 부분 신뢰 코드에서 중지하면 시각화 도우미가 로드되지 않습니다. 시각화 도우미를 사용하여 디버깅하려면 완전 신뢰 코드를 실행해야 합니다.

## <a name="possible-malicious-debuggee-component"></a>악의적으로 사용될 수 있는 디버기(debuggee) 구성 요소
 시각화 도우미는 디버거 쪽과 디버기 쪽에 하나씩 적어도 두 개 이상의 클래스로 구성됩니다. 시각화 도우미는 대개 특별한 디렉터리에 배치된 별도의 어셈블리로 배포되지만 디버기에서 로드할 수도 있습니다. 이 경우 디버거는 디버기에서 코드를 가져와 디버거 내에서 완전 신뢰 수준으로 이를 실행합니다.

 디버기 쪽 코드를 완전 신뢰 수준으로 실행하면 디버기를 완전히 신뢰할 수 없는 경우 문제가 발생할 수 있습니다. 시각화 도우미가 디버기에서 디버거로 부분 신뢰 어셈블리를 로드하려고 하면 Visual Studio가 시각화 도우미를 종료합니다.

 그러나 소소한 취약점은 여전히 존재합니다. 디버기가 아닌 다른 소스에서 로드된 디버거 쪽 코드에 디버기 쪽 코드가 연결될 수 있습니다. 그런 다음 디버기 쪽에서 디버기 대신 작업을 수행하도록 신뢰되는 디버거 쪽에 지시할 수 있습니다. 예를 들어, 신뢰되는 디버거 쪽 클래스가 "이 파일 삭제" 메커니즘을 노출하면 사용자가 해당 시각화 도우미를 호출할 때 부분 신뢰 디버기가 이 메커니즘을 호출할 수 있습니다.

 이러한 취약점을 줄이려면 시각화 도우미에서 노출되는 인터페이스에 주의를 기울여야 합니다.

## <a name="see-also"></a>참조
- [시각화 도우미 아키텍처](../debugger/visualizer-architecture.md)
- [방법: 시각화 도우미 작성](create-custom-visualizers-of-data.md)
- [Create Custom Visualizers of Data](../debugger/create-custom-visualizers-of-data.md)(데이터의 사용자 지정 시각화 도우미 만들기)
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)