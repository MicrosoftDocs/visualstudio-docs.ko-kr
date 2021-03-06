---
title: VSCodeWindow 개체 | Microsoft Docs
description: 하나 이상의 텍스트 뷰 (일반적으로 VsTextView 개체)를 포함할 수 있는 특수화 된 문서 창에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9803132605ee81c67785c8c0154861b26730ca5f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905334"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 개체
코드 창은 하나 이상의 텍스트 뷰 (일반적으로 개체)를 포함할 수 있는 특수 문서 창입니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .

 아키텍처 측면에서 코드 창은 창 프레임 안에 있는 문서 창입니다. 기능적으로 코드 창은 추가 기능이 있는 문서 창입니다. MDI (다중 문서 인터페이스) 모드에서 코드 창은 MDI 자식 프레임입니다. 자세한 내용은 [레거시 API를 사용 하 여 코드 창 사용자 지정](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)을 참조 하세요.

 다음 표에서는 개체의 인터페이스를 포함 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> .

|메서드|설명|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|GUID (globally unique identifier)가 식별 하는 서비스를 찾기 위한 일반 액세스 메커니즘을 제공 합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|하나 이상의 코드 뷰를 포함 하는 MDI (다중 문서 인터페이스) 자식을 나타냅니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|창 프레임을 채웁니다.|

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [그림 편집](https://www.microsoft.com/download/details.aspx?id=55984)