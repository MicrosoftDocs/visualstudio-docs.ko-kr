---
title: 항구 공급업체 구현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8218e372ad3aece922811bc20cfd7650f33296f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738561"
---
# <a name="implement-a-port-supplier"></a>포트 공급업체 구현
포트 공급자는 요청시 포트를 세션 디버그 관리자(SDM)에 공급합니다. 포트 공급자는 DCOM이 아닌 컴퓨터로 디버깅하거나 새 장치에 지원이 필요한 경우 구현해야 합니다. 예를 들어 휴대폰에 디버깅을 제공하려면 휴대폰에 연결하는 포트를 제공하는 포트 공급자를 설정하고(IR 또는 셀 연결을 통해) 휴대폰에서 실행되는 프로세스와 프로그램을 열어 줄 수 있습니다.

 Windows 기반 컴퓨터(원격 디버깅 포함)에서 프로그램을 디버깅하는 경우 Visual Studio는 기본 및 공통 언어 런타임(CLR) 프로세스에 대한 포트 공급자를 제공하므로 이러한 경우 고유한 포트 공급자를 설정할 필요가 없습니다.

## <a name="in-this-section"></a>섹션 내용
 [포트 공급업체 구현 및 등록](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) SDM이 포트 공급자 및 해당 포트와 상호 작용하는 방법에 대해 설명합니다.

 [필수 포트 공급업체 인터페이스](../../extensibility/debugger/required-port-supplier-interfaces.md) 포트 공급자를 얻으려면 구현해야 하는 인터페이스를 문서화합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md) 주요 디버깅 아키텍처 개념에 대해 설명합니다.

## <a name="see-also"></a>참조
 [비주얼 스튜디오 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
