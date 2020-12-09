---
title: 문서 위치 | Microsoft Docs
description: Visual Studio 디버깅의 문서 위치에서 IDE에 알려진 소스 파일의 위치에 대 한 추상화를 제공 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fef3debcbce3a178c4321114d69c87c627611a07
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915325"
---
# <a name="document-position"></a>문서 위치
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버그할 때 *문서 위치* 는 다음과 같습니다.

- IDE에 알려진 소스 파일의 위치에 대 한 추상화를 제공 합니다. 현재 대부분의 언어에서는 문서 위치를 소스 파일의 위치로 간주할 수 있습니다.

- 소스 문서에서 디버그 엔진에 대 한 위치를 설명 합니다.

- 는 [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) 인터페이스에 의해 구현 됩니다.

## <a name="see-also"></a>참고 항목
- [코드 컨텍스트](../../extensibility/debugger/code-context.md)
- [문서 컨텍스트](../../extensibility/debugger/document-context.md)
- [기호 공급자](../../extensibility/debugger/symbol-provider.md)
- [기호 공급자 인터페이스](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
