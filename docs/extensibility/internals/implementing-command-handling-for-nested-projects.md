---
title: 중첩 된 프로젝트에 대한 명령 처리 구현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing command handling
ms.assetid: 48a9d66e-d51c-4376-a95a-15796643a9f2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2092fc8033d5a5cc53b12bd63a945bd9865ca30e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707602"
---
# <a name="implementing-command-handling-for-nested-projects"></a>중첩된 프로젝트에 대한 명령 처리 구현
IDE는 중첩된 프로젝트에 전달되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 명령과 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 전달하거나 상위 프로젝트에서 명령을 필터링하거나 재정의할 수 있습니다.

> [!NOTE]
> 일반적으로 상위 프로젝트에서 처리하는 명령만 필터링할 수 있습니다. IDE에서 처리하는 **빌드** 및 **배포와** 같은 명령은 필터링할 수 없습니다.

 다음 단계에서는 명령 처리를 구현하는 프로세스를 설명합니다.

## <a name="procedures"></a>절차

#### <a name="to-implement-command-handling"></a>명령 처리를 구현하려면

1. 사용자가 중첩 된 프로젝트에서 중첩 된 프로젝트 또는 노드를 선택하는 경우 :

   1. IDE는 메서드를 호출합니다. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>

      — 또는 —

   2. 솔루션 탐색기의 바로 가기 메뉴 명령과 같은 계층 구조 창에서 명령이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 시작된 경우 IDE는 프로젝트의 부모에 대한 메서드를 호출합니다.

2. 상위 프로젝트는 에 전달할 매개 변수를 `QueryStatus`검사하여 `prgCmds` `pguidCmdGroup` 부모 프로젝트가 명령을 필터링해야 하는지 여부를 결정할 수 있습니다. 상위 프로젝트가 명령을 필터링하기 위해 구현되는 경우 다음을 설정해야 합니다.

   ```
   prgCmds[0].cmdf = OLECMDF_SUPPORTED;
   // make sure it is disabled
   prgCmds[0].cmdf &= ~MSOCMDF_ENABLED;
   ```

    그런 다음 상위 `S_OK`프로젝트가 반환됩니다.

    상위 프로젝트가 명령을 필터링하지 않으면 반환하기만 `S_OK`하면 됩니다. 이 경우 IDE는 자동으로 명령을 자식 프로젝트에 라우팅합니다.

    상위 프로젝트는 명령을 자식 프로젝트로 라우팅할 필요가 없습니다. IDE는 이 작업을 수행합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [명령, 메뉴 및 도구 모음](../../extensibility/internals/commands-menus-and-toolbars.md)
- [프로젝트 중첩](../../extensibility/internals/nesting-projects.md)
