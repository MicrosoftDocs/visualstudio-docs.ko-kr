---
title: VS텍스트버퍼 객체 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697721"
---
# <a name="vstextbuffer-object"></a>VS텍스트버퍼 개체
텍스트 버퍼 개체는 일반적으로 파일과 연결된 유니코드 텍스트 스트림을 나타냅니다. 마법사와 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 마찬가지로 코어 편집기의 컨텍스트 외부에서 개체를 사용할 수 있습니다.

 다음 표에서는 의 `VSTextBuffer`인터페이스를 보여 줍니다.

|방법|설명|
|------------|-----------------|
|[아이올레커맨드타겟](/windows/desktop/api/docobj/nn-docobj-iolecommandtarget)|표준 OLE 인터페이스. 버퍼에서 처리 취소/다시 수행에 사용됩니다.|
|[I지속 파일](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|표준 OLE 인터페이스.|
|[IPersistStream](/windows/desktop/api/objidl/nn-objidl-ipersiststream)|표준 OLE 인터페이스.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|복합 작업(즉, 단일 미수행/다시 작업 단위로 그룹화된 작업)을 만들 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|텍스트 버퍼에서 관리하는 문서 데이터의 지속성을 활성화합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|기본 서비스를 제공합니다. 많은 클라이언트에서 사용할 수 있습니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|버퍼를 검색하는 데 사용됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|2차원 좌표를 사용하여 읽기 및 쓰기 기능을 제공합니다. `IVsTextBuffer`에서 상속됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|1차원 좌표를 사용하여 읽기 및 쓰기 기능을 제공합니다. `IVsTextBuffer`에서 상속됩니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|버퍼의 텍스트에 대한 빠른 스트림 지향 순차적 액세스를 제공합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|속성의 일반 컬렉션에 대 한 액세스를 제공합니다. 가장 중요한 속성은 버퍼의 이름 또는 모니커입니다. GUID를 만들고 이를 키로 사용하여 이 인터페이스를 사용하여 버퍼에 고유한 임의데이터를 저장할 수 있습니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|이벤트에 대한 연결 점을 지원합니다.|

## <a name="remarks"></a>설명
 은 `VSTextBuffer` 일반적으로 에 `QueryInterface` `IVsTextBuffer`대한 호출로 찾을 수 있습니다. 자세한 내용은 [텍스트 버퍼](/visualstudio/extensibility/accessing-the-text-buffer-by-using-the-legacy-api?view=vs-2015)를 참조하십시오.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>
- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>
- [그림 편집](https://www.microsoft.com/download/details.aspx?id=55984)
