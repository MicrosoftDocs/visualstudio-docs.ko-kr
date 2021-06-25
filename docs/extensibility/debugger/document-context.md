---
title: 문서 컨텍스트 | Microsoft Docs
description: 소스 파일의 위치 또는 코드 컨텍스트에 대한 소스 문서의 위치를 나타내는 Visual Studio 디버깅의 문서 컨텍스트에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4b7554e274977f23474f6cf3e8e1af30d9e73b3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898190"
---
# <a name="document-context"></a>문서 컨텍스트
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버깅에서 문서 *컨텍스트:*

- 소스 파일의 위치를 나타냅니다. 소스 파일이 없을 수 있는 언어의 경우 문서 컨텍스트는 일반적으로 런타임 환경에서 생성되는 문서의 위치를 식별합니다. 예를 들어 스크립팅 엔진은 스크립트에서 문서를 생성할 수 있습니다. 자세한 내용은 문서 위치 를 [참조하세요.](../../extensibility/debugger/document-position.md)

- 코드 컨텍스트에 해당하는 소스 문서의 위치를 설명합니다. 기호 처리기는 컴파일러 또는 인터프리터에서 생성된 정보를 사용하여 코드 컨텍스트를 문서 컨텍스트에 매핑합니다.

- [IDebugDocumentContext2 인터페이스에](../../extensibility/debugger/reference/idebugdocumentcontext2.md) 의해 구현됩니다.

## <a name="see-also"></a>참조
- [코드 컨텍스트](../../extensibility/debugger/code-context.md)
- [기호 공급자](../../extensibility/debugger/symbol-provider.md)
- [기호 공급자 인터페이스](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
