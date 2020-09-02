---
title: VSTextBuffer 개체 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ea44d2b22c96d49f334f2ea33f9db8d69b5eb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697721"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer 개체
텍스트 버퍼 개체는 일반적으로 파일에 연결 되는 유니코드 텍스트 스트림을 나타냅니다. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>개체는 마법사와 같이 핵심 편집기의 컨텍스트 외부에서 사용할 수 있습니다.

 다음 표에서는의 인터페이스를 보여 줍니다 `VSTextBuffer` .

|메서드|설명|
|------------|-----------------|
|[IOleCommandTarget](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|표준 OLE 인터페이스입니다. 버퍼의 실행 취소/다시 실행 처리에 사용 됩니다.|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|표준 OLE 인터페이스입니다.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|표준 OLE 인터페이스입니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|복합어 작업 (즉, 단일 실행 취소/다시 실행 단위로 그룹화 된 작업)을 만들 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|텍스트 버퍼에서 관리 되는 문서 데이터의 지 속성을 사용 하도록 설정 합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|기본 서비스를 제공 합니다. 많은 클라이언트에서 사용 됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|버퍼를 검색 하는 데 사용 됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|2 차원 좌표를 사용 하 여 읽기 및 쓰기 기능을 제공 합니다. `IVsTextBuffer`에서 상속됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|1 차원 좌표를 사용 하 여 읽기 및 쓰기 기능을 제공 합니다. `IVsTextBuffer`에서 상속됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|버퍼의 텍스트에 대 한 빠른 스트림 지향 순차적 액세스를 제공 합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|속성의 제네릭 컬렉션에 대 한 액세스를 제공 합니다. 가장 중요 한 속성은 버퍼의 이름 또는 모니커입니다. GUID를 만들어 키로 사용 하면이 인터페이스를 사용 하 여 버퍼에 고유한 임의 데이터를 저장할 수 있습니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|이벤트에 대 한 연결 지점이 지원 됩니다.|

## <a name="remarks"></a>설명
 는 `VSTextBuffer` 일반적으로에 대 한 호출에 의해 검색 됩니다 `QueryInterface` `IVsTextBuffer` . 자세한 내용은 [텍스트 버퍼](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [그림 편집](https://www.microsoft.com/download/details.aspx?id=55984)
