---
title: 속성 창 개체 목록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffe11ae6ebb4e692686c884b663a4f93d1466535
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706145"
---
# <a name="properties-window-object-list"></a>속성 창 개요 목록
**속성** 창의 개체 목록은 하나 이상의 선택 된 창에서 사용할 수 있는 다른 개체로 선택 항목을 변경할 수 있는 드롭다운 목록입니다. 이 목록에서 다른 개체를 선택 하면에 대 한 호출이 트리거되어 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> 새 개체가 선택 되었음을 환경에 알립니다. 그러면 **속성** 창에 표시 되는 정보가 변경 되어 새로 선택한 개체와 연결 된 속성을 표시 합니다.

## <a name="the-object-list"></a>개체 목록
 개체 목록은 개체 이름 (굵게 표시 됨)과 개체 형식의 두 필드로 구성 됩니다.

 굵게 표시 된 개체 형식의 왼쪽에 표시 되는 개체 이름은 인터페이스에서 제공 하는 속성을 사용 하 여 개체 자체에서 검색 됩니다 `Name` <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> . <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>의 유일한 메서드인 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> 는 해당 인터페이스의 coclass에 대해를 반환 합니다. **속성** 창은를 사용 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> 드롭다운 목록에 개체 이름으로 표시 되는 coclass의 이름을 가져옵니다.

 개체에 속성이 없는 경우 `Name` 개체 목록의 이름 영역에 이름이 표시 되지 않습니다. 개체 목록에 이름을 표시 하려는 경우 개체에 이름 속성을 추가할 수 있습니다.

 COM 개체가를 구현 하지 않는 경우 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> **속성** 창에는 목록 왼쪽에 있는 개체 이름 대신 인터페이스 이름이 표시 됩니다.

## <a name="see-also"></a>추가 정보
- [속성 확장](../../extensibility/internals/extending-properties.md)
