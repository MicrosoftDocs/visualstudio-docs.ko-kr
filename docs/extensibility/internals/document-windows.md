---
title: 문서 창 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711033a4ad2e782ecbe509595266426d186bed8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708509"
---
# <a name="document-windows"></a>문서 창
Visual Studio에서 *문서 창은* MDI(다중 문서 인터페이스) 창과 연결된 프레임이 있는 자식 창입니다. 문서 창은 일반적으로 소스 코드 또는 텍스트의 표시 및 수정에 사용되지만 다른 기능 형식을 호스트할 수도 있습니다. 문서 창:

- 여러 파일을 동시에 볼 수 있도록 부모 MDI의 별도의 가로 또는 세로 탭 그룹으로 구성할 수 있습니다.

- 상위 MDI의 순서에 따라 도킹할 수 있습니다.

- 자유롭게 부동 할 수 있습니다.

- 탭 순서대로 다른 MDI 창에 연결됩니다.

  그룹화, 도킹 및 부동에 대한 명령은 문서 창 탭의 바로 가기 메뉴에서 찾을 수 있습니다.

  Visual Studio의 창 동작에 대한 자세한 내용은 [창 레이아웃 사용자 지정을](../../ide/customizing-window-layouts-in-visual-studio.md)참조하십시오.

## <a name="document-window-implementation"></a>문서 창 구현
 문서 창은 편집기 구현에 의해 만들어집니다. 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 편집기 인스턴스화의 일부로 문서 창을 만듭니다. 자세한 내용은 [편집기의 레거시 인터페이스를](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)참조하십시오.

> [!NOTE]
> 창에서 역방향 및 앞으로 탐색 지점을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> 제공하려면 인터페이스를 구현합니다. 텍스트 편집기는 텍스트 마커를 사용하여 문서의 탐색 지점을 식별합니다.

## <a name="the-running-document-table"></a>실행 중인 문서 테이블
 IDE는 실행 중인 문서 테이블(RDT)을 사용하여 모든 문서 창의 상태를 추적합니다. RDT는 솔루션이 닫혔거나 파일이 편집된 시기와 같은 이벤트에 대한 문서 창알림을 받는 메커니즘입니다. 자세한 내용은 [문서 실행 테이블을](../../extensibility/internals/running-document-table.md)참조하십시오.

## <a name="see-also"></a>참조
- [문서 로드 지연](../../extensibility/internals/delayed-document-loading.md)
