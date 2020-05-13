---
title: 문서 컨텍스트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48fe651e69e5e2c97756788cc30e54454c26e51e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738924"
---
# <a name="document-context"></a>문서 컨텍스트
디버깅에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *문서 컨텍스트*:

- 소스 파일의 위치를 나타냅니다. 원본 파일이 없는 언어의 경우 문서 컨텍스트는 일반적으로 런타임 환경에서 생성된 문서의 위치를 식별합니다. 예를 들어 스크립팅 엔진은 스크립트에서 문서를 생성할 수 있습니다. 자세한 내용은 [문서 위치를](../../extensibility/debugger/document-position.md)참조하십시오.

- 코드 컨텍스트에 해당하는 원본 문서의 위치를 설명합니다. 심볼 처리기는 컴파일러 또는 인터프리터에서 생성된 정보를 사용하여 코드 컨텍스트를 문서 컨텍스트에 매핑합니다.

- [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스에 의해 구현됩니다.

## <a name="see-also"></a>참조
- [코드 컨텍스트](../../extensibility/debugger/code-context.md)
- [기호 공급자](../../extensibility/debugger/symbol-provider.md)
- [기호 공급자 인터페이스](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
