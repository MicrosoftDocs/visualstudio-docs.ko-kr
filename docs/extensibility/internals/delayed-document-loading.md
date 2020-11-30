---
title: 지연 된 문서 로드 | Microsoft Docs
description: Visual Studio에서 지연 된 문서 로드에 대해 알아보고 문서를 로드 하기 전에 문서에서 요소를 쿼리하지 않도록 확장을 코딩 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6489c819efe0fd29cd2d120c08414cf0532ad6f
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328394"
---
# <a name="delayed-document-loading"></a>지연 된 문서 로드

사용자가 Visual Studio 솔루션을 다시 열면 연결 된 문서 대부분이 즉시 로드 되지 않습니다. 문서 창 프레임은 보류 중인 초기화 상태에서 만들어지고, 자리 표시자 문서 (스텁 프레임)는 RDT (실행 문서 테이블)에 배치 됩니다.

문서를 로드 하기 전에 문서에서 요소를 쿼리하여 프로젝트 문서를 불필요 하 게 로드할 수 있습니다. 그러면 Visual Studio에 대 한 전체 메모리 공간이 늘어날 수 있습니다.

## <a name="document-loading"></a>문서 로드

예를 들어 창 프레임의 탭을 선택 하 여 사용자가 문서에 액세스할 때 스텁 프레임 및 문서가 완전히 초기화 됩니다. 문서 데이터를 얻기 위해 RDT에 직접 액세스 하거나 다음 호출 중 하나를 수행 하 여 RT에 간접적으로 액세스 하 여 문서 데이터를 요청 하는 확장을 통해 문서를 초기화할 수도 있습니다.

- 창 프레임 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 메서드입니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>다음 속성 중 하나에 대 한 창 프레임 메서드입니다.

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- 확장에서 관리 코드를 사용 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 문서가 보류 중인 초기화 상태에 있지 않거나 문서를 완전히 초기화 하려는 경우가 아니면를 호출 하면 안 됩니다. 그 이유는 메서드가 항상 doc 데이터 개체를 반환 하 여 필요한 경우 생성 하기 때문입니다. 대신 인터페이스에서 메서드 중 하나를 호출 해야 합니다 `IVsRunningDocumentTable4` .

- 확장에서 c + +를 사용 하는 경우 `null` 원하지 않는 매개 변수에 대해을 전달할 수 있습니다.

- 다른 속성을 요청 하기 전에 관련 속성을 요청 하기 전에 다음 방법 중 하나를 호출 하 여 불필요 한 문서 로드를 방지할 수 있습니다.

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>[__VSFPROPID6 사용. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. 이 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> _VSRDTFLAGS4 값을 포함 하는 개체를 반환 [합니다. ](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) 문서를 아직 초기화 하지 않은 경우 RDT_PendingInitialization 합니다.

문서가 완전히 초기화 될 때 발생 하는 RDT 이벤트를 구독 하 여 문서가 로드 된 시기를 확인할 수 있습니다. 다음과 같은 두 가지 가능성이 있습니다.

- 이벤트 싱크가를 구현 하는 경우 다음을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> 구독할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>

- 그렇지 않으면를 구독할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .

다음 예제는 가상 문서 액세스 시나리오입니다. Visual Studio 확장에서 열린 문서에 대 한 일부 정보 (예: 편집 잠금 수 및 문서 데이터에 대 한 항목)를 표시 하려고 합니다. 를 사용 하 여 RDT의 문서를 열거 <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> 한 다음 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 편집 잠금 수와 문서 데이터를 검색 하기 위해 각 문서에 대해를 호출 합니다. 문서가 보류 중인 초기화 상태에 있는 경우 문서 데이터를 요청 하면 해당 문서가 불필요 하 게 초기화 됩니다.

문서에 액세스 하는 보다 효율적인 방법은를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> 편집 잠금 횟수를 가져온 다음를 사용 하 여 문서가 초기화 되었는지 여부를 확인 하는 것입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> . 플래그에 _VSRDTFLAGS4 포함 되어 있지 않으면 [입니다. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)문서가 이미 초기화 되었으며를 사용 하 여 문서 데이터를 요청 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> 해도 불필요 한 초기화가 발생 하지 않습니다. 플래그에 _VSRDTFLAGS4 포함 되어 있으면이 고, [ RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), 확장은 문서가 초기화 될 때까지 문서 데이터를 요청 하지 않아야 합니다. 이 초기화는 이벤트 처리기에서 검색할 수 있습니다 `OnAfterAttributeChange(Ex)` .

## <a name="test-extensions-to-see-if-they-force-initialization"></a>초기화를 강제로 실행 하는지 확인 하는 테스트 확장

문서가 초기화 되었는지 여부를 나타내는 표시 된 큐가 없으므로 확장이 강제로 초기화 되는지 확인 하기 어려울 수 있습니다. 완전 하 게 초기화 되지 않은 모든 문서의 제목이 제목에 *[스텁]* 텍스트를 포함 하도록 하는 레지스트리 키를 설정 하 여 더 쉽게 확인할 수 있습니다.

**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad** 에서 **StubTabTitleFormatString** 을 *{0} [스텁]* 으로 설정 합니다.
