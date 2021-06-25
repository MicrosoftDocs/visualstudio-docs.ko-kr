---
title: 모듈 | Microsoft Docs
description: 이 문서에서는 Visual Studio의 디버거 아키텍처에서 모듈의 정의 및 역할에 대해 설명 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 03a3ad588b0a2e0f3aa6f04ddeb742ab66064bc9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902607"
---
# <a name="modules"></a>모듈
디버거 아키텍처 측면에서 *모듈* 은 다음과 같습니다.

- 는 실행 파일 또는 DLL과 같은 코드의 물리적 컨테이너입니다.

- 기호를 다시 로드 하 고 자체를 설명할 수 있습니다. 모듈 설명은 IDE의 모듈 창에 표시 됩니다.

- 는 디버그 엔진에서 모듈을 설명 하기 위해 만든 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) 인터페이스로 표시 됩니다.

## <a name="see-also"></a>참조
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
