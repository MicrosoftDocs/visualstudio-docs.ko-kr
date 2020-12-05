---
title: 모듈 | Microsoft Docs
description: 이 문서에서는 Visual Studio의 디버거 아키텍처에서 모듈의 정의 및 역할에 대해 설명 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57202231c1bbfc7712d322b8cc7a30e3f64c87af
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606647"
---
# <a name="modules"></a>모듈
디버거 아키텍처 측면에서 *모듈* 은 다음과 같습니다.

- 는 실행 파일 또는 DLL과 같은 코드의 물리적 컨테이너입니다.

- 기호를 다시 로드 하 고 자체를 설명할 수 있습니다. 모듈 설명은 IDE의 모듈 창에 표시 됩니다.

- 는 디버그 엔진에서 모듈을 설명 하기 위해 만든 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) 인터페이스로 표시 됩니다.

## <a name="see-also"></a>참고 항목
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
