---
title: 포트 공급자 구현 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738561"
---
# <a name="implement-a-port-supplier"></a>포트 공급자 구현
포트 공급자는 요청 시 포트를 SDM (세션 디버그 관리자)에 제공 합니다. 비 DCOM 컴퓨터를 디버깅할 때 또는 새 장치에 지원이 필요한 경우 포트 공급자를 구현 해야 합니다. 예를 들어 휴대폰에 대 한 디버깅을 제공 하려면 포트를 제공 하는 포트 공급자를 설정할 수 있습니다 .이 포트는 IR 또는 셀 연결을 통해 휴대폰에 연결 하 고 휴대폰에서 실행 되는 프로세스와 프로그램을 열거 합니다.

 Windows 기반 컴퓨터 (원격 디버깅 포함)에서 프로그램을 디버깅 하는 경우 Visual Studio는 네이티브 및 CLR (공용 언어 런타임) 프로세스를 위한 포트 공급자를 제공 하므로 이러한 경우에 자체 포트 공급자를 설정할 필요가 없습니다.

## <a name="in-this-section"></a>섹션 내용
 [포트 공급자 구현 및 등록](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md) SDM이 포트 공급자 및 해당 포트와 상호 작용 하는 방법에 대해 설명 합니다.

 [필요한 포트 공급자 인터페이스](../../extensibility/debugger/required-port-supplier-interfaces.md) 포트 공급자를 가져오기 위해 구현 해야 하는 인터페이스를 문서화 합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md) 주요 디버깅 아키텍처 개념을 설명 합니다.

## <a name="see-also"></a>추가 정보
 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
