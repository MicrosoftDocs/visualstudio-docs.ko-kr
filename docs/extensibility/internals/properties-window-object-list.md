---
title: 속성 창 개체 목록 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706145"
---
# <a name="properties-window-object-list"></a>속성 창 개요 목록
**속성** 창의 개체 목록은 하나 이상의 선택한 창 내에서 사용할 수 있는 다른 개체로 선택을 변경할 수 있는 드롭다운 목록입니다. 이 목록 내에서 다른 개체를 선택하면 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> 새 개체가 선택되었음을 환경에 알리는 호출이 트리거됩니다. 그러면 **속성** 창에 표시되는 정보가 변경되어 새로 선택한 객체와 연결된 속성을 표시합니다.

## <a name="the-object-list"></a>개체 목록
 개체 목록은 개체 이름(굵게 표시)과 개체 유형이라는 두 개의 필드로 구성됩니다.

 굵게 개체 유형의 왼쪽에 표시 된 개체 이름은 `Name` <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> 인터페이스에서 제공 하는 속성을 사용 하 여 개체 자체에서 검색 됩니다. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>에서 유일한 메서드가 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> 해당 인터페이스의 공동 클래스에 대해 반환됩니다. **속성** 창은 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> 드롭다운 목록에 개체 이름으로 표시되는 공동 클래스의 이름을 가져옵니다.

 개체에 `Name` 속성이 없는 경우 이름은 개체 목록의 Name 영역에 표시되지 않습니다. 개체 목록에 이름을 표시하려는 경우 개체에 Name 속성을 추가할 수 있습니다.

 COM 개체가 구현되지 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>않으면 **속성** 창은 목록의 왼쪽에 있는 개체 이름 대신 인터페이스 이름을 표시합니다.

## <a name="see-also"></a>참조
- [속성 확장](../../extensibility/internals/extending-properties.md)
