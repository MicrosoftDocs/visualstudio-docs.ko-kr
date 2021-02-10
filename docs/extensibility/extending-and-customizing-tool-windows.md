---
title: 도구 창 확장 및 사용자 지정 | Microsoft Docs
description: 속성 창, 출력 창 및 작업 목록 창을 포함 하 여 Visual Studio에서 제공 하는 도구 창을 확장 하 고 사용자 지정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9f17c16d051bdb42750d91971d2be0d3c09b47f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953086"
---
# <a name="extend-and-customize-tool-windows"></a>도구 창 확장 및 사용자 지정
Visual Studio는 도구 창, 문서 창 및 대화 상자 창과 같은 여러 가지 종류의 창을 제공 합니다. **속성** 창, **출력** 창 및 **작업 목록** 창과 같은 다른 창에는 도구 창의 형식이 있습니다.

## <a name="tool-windows"></a>도구 창
 Visual Studio 도구 창은 일반적으로 파일 기반이 아닌 읽기 전용 창입니다. 이런 점에서 파일을 읽기/쓰기 모드로 표시하는 문서 창과는 다릅니다. **도구 상자**, **솔루션 탐색기**, **속성** 창 및 **웹 브라우저** 는 도구 창의 예입니다.

 간단한 도구 창을 만드는 방법을 알아보려면 [도구 창 추가](../extensibility/adding-a-tool-window.md)를 참조 하세요.

 Visual Studio를 사용 하 여 도구 창을 등록 하려면 [도구 창 등록](../extensibility/registering-a-tool-window.md)을 참조 하세요.

 도구 창은 기본적으로 단일 인스턴스입니다. 즉, 도구 창의 인스턴스를 한 번에 하나만 열 수 있습니다. 단일 인스턴스 도구 창이 열린 후 IDE를 닫을 때까지 열린 상태로 유지됩니다. 단일 인스턴스 도구 창을 닫으면 해당 표시만 변경 됩니다. 창의 여러 인스턴스가 동시에 열릴 수 있도록 다중 인스턴스 도구 창도 만들 수 있습니다. 자세한 내용은 [다중 인스턴스 도구 창 만들기](../extensibility/creating-a-multi-instance-tool-window.md) 를 참조 하세요.

 도구 창은 *동적* 일 수 있습니다. 즉, 관련 된 UI 컨텍스트가 적용 될 때마다 표시 됩니다. 자동 표시를 사용하면 IDE에서 창의 혼잡함을 줄일 수 있습니다. 자세한 내용은 [동적 도구 창 열기](../extensibility/opening-a-dynamic-tool-window.md)를 참조 하세요.

 도구 창을 문서 프레임에서 도킹, 부동 또는 탭할 수 있습니다. 도구 창 프레임이 IDE에서 제공되고 크기, 위치, 도킹 상태 및 기타 영구적 속성을 제어하는 데 사용됩니다. 도구 창에서 내용을 표시합니다. 기본 크기 및 위치는 도구 창이 처음 열릴 때만 적용되고 이후에는 도구 창 상태가 유지됩니다.

 도구 창에서 WPF 사용자 컨트롤을 호스트하고 도구 모음을 지원할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> 속성을 재정의하여 호스트된 컨트롤의 핸들을 반환할 수 있습니다.

 도구 창에 다양 한 기능을 추가할 수 있습니다. 예를 들어 도구 모음을 추가할 수 있습니다. 도구 창에 도구 [모음](../extensibility/adding-a-toolbar-to-a-tool-window.md) 을 추가 하거나 바로 가기 메뉴를 추가 합니다. [도구 창에 바로 가기 메뉴](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)를 추가 합니다. 도구 창 내에서 항목을 검색 하는 데 사용할 수 있는 검색 컨트롤 ( [도구 창에 검색 추가](../extensibility/adding-search-to-a-tool-window.md))을 추가할 수 있습니다.

 [이벤트 구독](../extensibility/subscribing-to-an-event.md)을 구독 하는 도구 창 이벤트를 구독할 수 있습니다.

## <a name="extend-existing-tool-windows"></a>기존 도구 창 확장
 새 **옵션** 페이지에 도구 창에 대 한 정보를 추가 하 고 **속성** 페이지에서 새 설정에 대 한 정보를 추가 하 여 **작업 목록** 및 **출력** 창에 쓸 수 있습니다. 자세한 내용은 [속성, 작업 목록, 출력 및 옵션 창 확장](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)을 참조 하세요.

## <a name="modal-dialog-boxes"></a>모달 대화 상자
 Visual Studio 확장에서 모달 대화 상자를 만들어야 합니다 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> .이 대화 상자를 사용 하 여 UI의 나머지 부분을 제어할 수 있습니다. 자세한 내용은 [모달 대화 상자 만들기 및 관리](../extensibility/creating-and-managing-modal-dialog-boxes.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [도구 창을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-tool-window.md)
- [프로젝트 확장](../extensibility/extending-projects.md)
- [솔루션 확장](../extensibility/extending-solutions.md)
