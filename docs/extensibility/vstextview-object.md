---
title: VS텍스트뷰 객체 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697706"
---
# <a name="vstextview-object"></a>VS텍스트뷰 개체

텍스트 보기는 사용자가 텍스트 버퍼의 유니코드 텍스트를 보고 편집할 수 있는 창입니다. 기본적으로 뷰는 대부분의 사용자가 편집기로 참조하는 것입니다. 뷰는 다양한 텍스트 레이어(단어 줄 바꿈, 텍스트 개요 등)에 의해 버퍼에서 분리되므로 뷰가 버퍼의 텍스트를 정확하게 표현하는 것은 아닙니다. 텍스트 보기에 대한 자세한 내용은 [레거시 API를 사용하여 텍스트 보기 액세스](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015)를 참조하십시오.

다음 표에서는 개체의 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 보여 줍니다.

|인터페이스|설명|
|---------------|-----------------|
|[아이드롭소스](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|표준 OLE 인터페이스.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|표준 OLE 인터페이스.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|표준 OLE 인터페이스.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|표준 OLE 인터페이스.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|복합 작업(즉, 단일 미수행/다시 작업 단위로 그룹화된 작업)을 만들 수 있습니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|뷰를 관리하고 액세스하기 위한 기본 방법을 제공합니다. `IVsTextView`나사로 연결되지 않았습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|창 창을 만들고 관리합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|텍스트 레이어와 상호 작용합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|다른 스레드에서 뷰에 대한 작업을 수행합니다.|

## <a name="see-also"></a>참조

- [그림 편집](https://www.microsoft.com/download/details.aspx?id=55984)
- [VS텍스트버퍼 개체](../extensibility/vstextbuffer-object.md)
