---
title: 문서 창 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708509"
---
# <a name="document-windows"></a>문서 창
Visual Studio에서 *문서 창은* MDI (다중 문서 인터페이스) 창과 연결 된 프레임 있는 자식 창입니다. 문서 창은 일반적으로 소스 코드 또는 텍스트를 표시 하 고 수정 하는 데 사용 되지만 다른 기능 형식을 호스팅할 수도 있습니다. 문서 창:

- 여러 파일을 동시에 볼 수 있도록 부모 MDI에서 별도의 가로 또는 세로 탭 그룹으로 구성할 수 있습니다.

- 부모 MDI에서 임의의 순서로 도킹할 수 있습니다.

- 자유롭게 사용할 수 있습니다.

- 탭 순서에 따라 다른 MDI 창에 연결 됩니다.

  그룹화, 도킹 및 부동을 위한 명령은 문서 창 탭의 바로 가기 메뉴에서 찾을 수 있습니다.

  Visual Studio의 창 동작에 대 한 자세한 내용은 [창 레이아웃 사용자 지정](../../ide/customizing-window-layouts-in-visual-studio.md)을 참조 하세요.

## <a name="document-window-implementation"></a>문서 창 구현
 문서 창은 편집기를 구현 하 여 만듭니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>인터페이스는 편집기를 인스턴스화하는의 일부로 문서 창을 만듭니다. 자세한 내용은 [편집기의 레거시 인터페이스](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)를 참조 하세요.

> [!NOTE]
> 창에서 뒤로 및 앞으로 탐색 위치를 제공 하려면 인터페이스를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> 합니다. 텍스트 편집기는 텍스트 표식을 사용 하 여 문서의 탐색 위치를 식별 합니다.

## <a name="the-running-document-table"></a>실행 중인 문서 테이블
 IDE는 RT (실행 중인 문서 테이블)를 사용 하 여 모든 문서 창의 상태를 추적 합니다. RDT는 솔루션이 닫히거나 파일이 편집 된 경우와 같은 이벤트 알림이 문서 창에 표시 되는 메커니즘입니다. 자세한 내용은 [문서 테이블 실행](../../extensibility/internals/running-document-table.md)을 참조 하세요.

## <a name="see-also"></a>참조
- [지연 된 문서 로드](../../extensibility/internals/delayed-document-loading.md)
