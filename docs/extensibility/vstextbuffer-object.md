---
title: VSTextBuffer 개체 | Microsoft Docs
description: VSTextBuffer 개체는 일반적으로 파일과 연결된 유니코드 텍스트 스트림을 나타냅니다. 이 문서에서는 VSTextBuffer의 인터페이스를 나열합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b3660a8dbb4a0a1280d5a3f428f73f3498244af7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905178"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer 개체
텍스트 버퍼 개체는 일반적으로 파일과 연결된 유니코드 텍스트 스트림을 나타냅니다. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>개체는 마법사에서와 같이 핵심 편집기의 컨텍스트 외부에서 사용할 수 있습니다.

 다음 표에서는 의 인터페이스를 `VSTextBuffer` 보여줍니다.

|메서드|설명|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|표준 OLE 인터페이스. 버퍼에서 실행 취소/다시 실행 처리에 사용됩니다.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|표준 OLE 인터페이스.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|표준 OLE 인터페이스.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|복합 작업(즉, 단일 실행 취소/다시 실행 단위로 그룹화되는 작업)을 만들 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|텍스트 버퍼에서 관리하는 문서 데이터의 지속성을 사용하도록 설정합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|기본 서비스를 제공합니다. 많은 클라이언트에서 사용됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|버퍼를 검색하는 데 사용됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|2차원 좌표를 사용하여 읽기 및 쓰기 기능을 제공합니다. `IVsTextBuffer`에서 상속됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|1차원 좌표를 사용하여 읽기 및 쓰기 기능을 제공합니다. `IVsTextBuffer`에서 상속됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|버퍼의 텍스트에 대한 스트림 지향의 빠른 순차적 액세스를 제공합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|속성의 제네릭 컬렉션에 대한 액세스를 제공합니다. 가장 중요한 속성은 버퍼의 이름 또는 모니커입니다. GUID를 만들고 키로 사용하여 이 인터페이스를 사용하여 버퍼에 사용자 고유의 임의 데이터를 저장할 수 있습니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|이벤트에 대한 연결 지점을 지원합니다.|

## <a name="remarks"></a>설명
 `VSTextBuffer`는 일반적으로 에 대한 호출을 통해 찾을 수 `QueryInterface` `IVsTextBuffer` 있습니다. 자세한 내용은 텍스트 버퍼 를 [참조하세요.](/previous-versions/visualstudio/visual-studio-2015/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [그림 편집](https://www.microsoft.com/download/details.aspx?id=55984)