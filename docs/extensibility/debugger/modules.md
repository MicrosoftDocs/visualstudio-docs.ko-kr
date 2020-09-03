---
title: 모듈 | Microsoft Docs
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
ms.openlocfilehash: abdf76c7f5f031d2ef7f3bcac2bae8a2c508b783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738353"
---
# <a name="modules"></a>모듈
디버거 아키텍처 측면에서 *모듈*은 다음과 같습니다.

- 는 실행 파일 또는 DLL과 같은 코드의 물리적 컨테이너입니다.

- 기호를 다시 로드 하 고 자체를 설명할 수 있습니다. 모듈 설명은 IDE의 모듈 창에 표시 됩니다.

- 는 디버그 엔진에서 모듈을 설명 하기 위해 만든 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) 인터페이스로 표시 됩니다.

## <a name="see-also"></a>추가 정보
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
