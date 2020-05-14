---
title: 도구 창 확장 및 사용자 지정 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76c094ec73a69baa46a5e8313dd26febd57e5887
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711811"
---
# <a name="extend-and-customize-tool-windows"></a>공구 창 확장 및 사용자 지정
Visual Studio는 도구 창, 문서 창 및 대화 창과 같은 여러 유형의 창을 제공합니다. **속성** 창, **출력** 창 및 **작업 목록** 창과 같은 다른 창은 도구 창 유형입니다.

## <a name="tool-windows"></a>도구 창
 Visual Studio 도구 창은 일반적으로 파일 기반이 아닌 읽기 전용 창입니다. 이런 점에서 파일을 읽기/쓰기 모드로 표시하는 문서 창과는 다릅니다. **도구 상자**, **솔루션 탐색기**, **속성** 창 및 **웹 브라우저** 는 도구 창의 예입니다.

 간단한 도구 창을 만드는 방법을 알아보려면 [도구 창 추가를](../extensibility/adding-a-tool-window.md)참조하십시오.

 Visual Studio에 도구 창을 등록하려면 [도구 창 등록을](../extensibility/registering-a-tool-window.md)참조하십시오.

 도구 창은 기본적으로 단일 인스턴스입니다. 즉, 도구 창의 인스턴스를 한 번에 하나만 열 수 있습니다. 단일 인스턴스 도구 창이 열린 후 IDE를 닫을 때까지 열린 상태로 유지됩니다. 단일 인스턴스 도구 창을 닫으면 가시성만 변경됩니다. 창의 여러 인스턴스가 동시에 열릴 수 있도록 다중 인스턴스 도구 창도 만들 수 있습니다. 자세한 내용은 [다중 인스턴스 도구 창 만들기를](../extensibility/creating-a-multi-instance-tool-window.md) 참조하십시오.

 도구 창은 *동적일*수 있으며, 이는 관련 UI 컨텍스트가 적용될 때마다 표시됩니다. 자동 표시를 사용하면 IDE에서 창의 혼잡함을 줄일 수 있습니다. 자세한 내용은 [동적 도구 창 열기를](../extensibility/opening-a-dynamic-tool-window.md)참조하십시오.

 도구 창을 문서 프레임에서 도킹, 부동 또는 탭할 수 있습니다. 도구 창 프레임이 IDE에서 제공되고 크기, 위치, 도킹 상태 및 기타 영구적 속성을 제어하는 데 사용됩니다. 도구 창에서 내용을 표시합니다. 기본 크기 및 위치는 도구 창이 처음 열릴 때만 적용되고 이후에는 도구 창 상태가 유지됩니다.

 도구 창에서 WPF 사용자 컨트롤을 호스트하고 도구 모음을 지원할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> 속성을 재정의하여 호스트된 컨트롤의 핸들을 반환할 수 있습니다.

 도구 창에 다양한 기능을 추가할 수 있습니다. 예를 들어 도구 모음 추가: 도구 모음 또는 바로 가기 메뉴에 도구 [모음 추가:](../extensibility/adding-a-toolbar-to-a-tool-window.md) [도구 창에서 바로 가기 메뉴 추가.](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md) 도구 창 내의 항목을 검색할 수 있는 검색 [컨트롤을](../extensibility/adding-search-to-a-tool-window.md)추가할 수 있습니다.

 도구 창 이벤트: [이벤트 구독을 구독할](../extensibility/subscribing-to-an-event.md)수 있습니다.

## <a name="extend-existing-tool-windows"></a>기존 공구 창 확장
 도구 창에 대한 정보를 새 **옵션** 페이지에 추가하고 **속성** 페이지의 새 설정을 추가하고 **작업 목록** 및 **출력** 창에 쓸 수 있습니다. 자세한 내용은 [속성, 작업 목록, 출력 및 옵션 창 확장을](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)참조하십시오.

## <a name="modal-dialog-boxes"></a>모달 대화 상자
 Visual Studio 확장에서 모달 대화 상자와 UI의 나머지 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>부분을 제어할 수 있는 에서 모달 대화 상자를 만들어야 합니다. 자세한 내용은 [모달 대화 상자 만들기 및 관리를](../extensibility/creating-and-managing-modal-dialog-boxes.md)참조하십시오.

## <a name="see-also"></a>참조
- [도구 창을 사용하여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)
- [프로젝트 확장](../extensibility/extending-projects.md)
- [솔루션 확장](../extensibility/extending-solutions.md)
