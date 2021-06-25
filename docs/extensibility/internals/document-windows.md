---
title: Windows | 문서화 Microsoft Docs
description: 구현 방법 및 RDT(문서 테이블 실행)에서 상태를 추적하는 방법을 포함하여 Visual Studio 문서 창에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: df7a797c0b4587698197412f49eef6bfab183a7a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899916"
---
# <a name="document-windows"></a>문서 창
Visual Studio *문서 창은* MDI(다중 문서 인터페이스) 창과 연결된 프레임 자식 창입니다. 문서 창은 일반적으로 소스 코드 또는 텍스트의 표시 및 수정에 사용되지만 다른 기능 형식을 호스트할 수도 있습니다. 문서 창:

- 여러 파일을 동시에 볼 수 있도록 부모 MDI에서 별도의 가로 또는 세로 탭 그룹으로 구성할 수 있습니다.

- 부모 MDI에서 순서에 따라 도킹할 수 있습니다.

- 자유롭게 부동할 수 있습니다.

- 탭 순서로 다른 MDI 창에 연결됩니다.

  그룹화, 도킹 및 부동에 대한 명령은 문서 창 탭의 바로 가기 메뉴에서 찾을 수 있습니다.

  Visual Studio 창 동작에 대한 자세한 내용은 [창 레이아웃 사용자 지정을 참조하세요.](../../ide/customizing-window-layouts-in-visual-studio.md)

## <a name="document-window-implementation"></a>문서 창 구현
 문서 창은 편집기를 구현하여 만들어집니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>인터페이스는 편집기 인스턴스화의 일부로 문서 창을 만듭니다. 자세한 내용은 [편집기 의 레거시 인터페이스를 참조하세요.](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)

> [!NOTE]
> 창에서 뒤로 및 앞으로 탐색 지점을 제공하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> 인터페이스를 구현합니다. 텍스트 편집기는 텍스트 표식 을 사용하여 문서의 탐색 지점을 식별합니다.

## <a name="the-running-document-table"></a>실행 중인 문서 테이블
 IDE는 RDT(실행 중인 문서 테이블)를 사용하여 모든 문서 창의 상태를 추적합니다. RDT는 솔루션이 닫힌 경우 또는 파일을 편집한 경우와 같은 이벤트 알림을 문서 창에 제공하는 메커니즘입니다. 자세한 내용은 [문서 테이블 실행을 참조하세요.](../../extensibility/internals/running-document-table.md)

## <a name="see-also"></a>참조
- [지연된 문서 로드](../../extensibility/internals/delayed-document-loading.md)
