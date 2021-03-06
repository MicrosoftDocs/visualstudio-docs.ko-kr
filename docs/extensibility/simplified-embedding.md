---
title: 단순화 포함 | Microsoft Docs
description: 문서 뷰 개체가 Visual Studio의 자식일 때 편집기에서 사용 하도록 설정할 수 있는 간소화 된 포함에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dca3b0c11c916a1fc47e4687bfeeabee35bcdfb4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056378"
---
# <a name="simplified-embedding"></a>간단한 포함
단순화 된 포함은 해당 문서 뷰 개체가 부모 (즉,의 자식) 인 경우 편집기에서 사용 하도록 설정 되며, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 인터페이스는 해당 창 명령을 처리 하기 위해 구현 됩니다. 단순화 된 포함 편집기는 활성 컨트롤을 호스트할 수 없습니다. 다음 그림에서는 간단한 포함 편집기를 만드는 데 사용 되는 개체를 보여 줍니다.

 ![간단한 포함 편집기 그래픽](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") 포함이 단순화 된 편집기

> [!NOTE]
> 이 그림의 개체 중에서 `CYourEditorFactory` 개체는 표준 파일 기반 편집기를 만드는 데 필요 합니다. 사용자 지정 편집기를 만드는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 편집기에 고유한 개인 지 속성 메커니즘이 있기 때문에를 구현할 필요가 없습니다. 그러나 사용자 지정이 아닌 편집기의 경우에는이 작업을 수행 해야 합니다.

 단순화 된 포함 편집기를 만들기 위해 구현 된 모든 인터페이스는 개체에 포함 되어 `CYourEditorDocument` 있습니다. 그러나 문서 데이터의 여러 보기를 지원 하려면 다음 표에 나와 있는 것 처럼 인터페이스를 별개의 데이터로 분할 하 고 개체를 확인 합니다.

|인터페이스|인터페이스 위치|Windows Server Update Services와 함께|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|보기|부모 창에 대 한 연결을 제공 합니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|보기|명령을 처리 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|보기|상태 표시줄 업데이트를 사용하도록 설정합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|보기|**도구 상자** 항목을 사용 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|데이터|파일이 변경 될 때 알림을 보냅니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|데이터|파일 형식에 대해 다른 이름으로 저장 기능을 사용 하도록 설정 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|데이터|문서에 대해 지속성을 사용하도록 설정합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|데이터|파일 변경 이벤트 (예: 다시 로드 트리거)를 해제할 수 있습니다.|
