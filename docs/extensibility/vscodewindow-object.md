---
title: VS코드윈도우 오브젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55739b1ef577123ac0395b4c5cfb1e3c5dbc779f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697953"
---
# <a name="vscodewindow-object"></a>VS코드창 개체
코드 창은 하나 이상의 텍스트 뷰(일반적으로 개체)를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 포함할 수 있는 특수 문서 창입니다.

 구조적으로 코드 창은 창 프레임 내에 있는 문서 창입니다. 기능적으로 코드 창은 추가 기능이 있는 문서 창일 뿐입니다. 다중 문서 인터페이스(MDI) 모드에서 코드 창은 MDI 자식 프레임입니다. 자세한 내용은 [레거시 API를 사용하여 코드 창 사용자 지정을](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015)참조하세요.

 다음 표에는 개체의 인터페이스가 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> 포함되어 있습니다.

|방법|설명|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|GUID(전역 고유 식별자)가 식별하는 서비스를 찾는 일반 액세스 메커니즘을 제공합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|하나 이상의 코드 뷰를 포함하는 여러 문서 인터페이스(MDI) 자식을 나타냅니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|창 프레임을 채웁니다.|

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [그림 편집](https://www.microsoft.com/download/details.aspx?id=55984)
