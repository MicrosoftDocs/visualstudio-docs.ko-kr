---
title: 단순화된 임베딩 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700081"
---
# <a name="simplified-embedding"></a>간단한 포함
문서 뷰 개체가 부모(즉, 자식)에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]부모가 되고 해당 창 명령을 처리하기 위해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 인터페이스가 구현될 때 편집기에서 단순화된 포함이 활성화됩니다. 단순화된 임베디드 편집기는 활성 컨트롤을 호스트할 수 없습니다. 단순화된 포함을 사용하여 편집기를 만드는 데 사용되는 개체는 다음 그림에 나와 있습니다.

 ![단순화된 임베딩 편집기 그래픽](../extensibility/media/vssimplifiedembeddingeditor.gif "vs 단순화 엠베딩 에디터") 단순화된 임베딩이 있는 편집기

> [!NOTE]
> 이 그림의 개체 중 `CYourEditorFactory` 표준 파일 기반 편집기를 만들려면 개체만 필요합니다. 사용자 지정 편집기를 만드는 경우 편집기에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>자체 개인 지속성 메커니즘이 있을 수 있으므로 구현할 필요가 없습니다. 그러나 사용자 지정되지 않은 편집기의 경우 그렇게 해야 합니다.

 단순화된 포함을 사용하여 편집기를 만들기 위해 구현된 `CYourEditorDocument` 모든 인터페이스가 개체에 포함됩니다. 그러나 문서 데이터의 여러 뷰를 지원하려면 인터페이스를 별도의 데이터로 분할하고 다음 표에 표시된 대로 개체를 봅니다.

|인터페이스|인터페이스 위치|사용|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|View|상위 창에 대한 연결을 제공합니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|View|명령을 처리합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|View|상태 표시줄 업데이트를 사용하도록 설정합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|View|도구 상자 항목을 **활성화합니다.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|데이터|파일이 변경될 때 알림을 보냅니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|데이터|파일 형식에 대해 다른 기능으로 저장을 활성화합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|데이터|문서에 대해 지속성을 사용하도록 설정합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|데이터|다시 로드 트리거와 같은 파일 변경 이벤트를 억제할 수 있습니다.|
