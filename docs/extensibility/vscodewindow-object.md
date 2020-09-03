---
title: VSCodeWindow 개체 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697953"
---
# <a name="vscodewindow-object"></a>VSCodeWindow 개체
코드 창은 하나 이상의 텍스트 뷰 (일반적으로 개체)를 포함할 수 있는 특수 문서 창입니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .

 아키텍처 측면에서 코드 창은 창 프레임 안에 있는 문서 창입니다. 기능적으로 코드 창은 추가 기능이 있는 문서 창입니다. MDI (다중 문서 인터페이스) 모드에서 코드 창은 MDI 자식 프레임입니다. 자세한 내용은 [레거시 API를 사용 하 여 코드 창 사용자 지정](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015)을 참조 하세요.

 다음 표에서는 개체의 인터페이스를 포함 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> .

|메서드|설명|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|GUID (globally unique identifier)가 식별 하는 서비스를 찾기 위한 일반 액세스 메커니즘을 제공 합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|하나 이상의 코드 뷰를 포함 하는 MDI (다중 문서 인터페이스) 자식을 나타냅니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|창 프레임을 채웁니다.|

## <a name="see-also"></a>추가 정보
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [그림 편집](https://www.microsoft.com/download/details.aspx?id=55984)
