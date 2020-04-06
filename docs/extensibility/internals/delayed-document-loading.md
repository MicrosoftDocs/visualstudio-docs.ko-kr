---
title: 문서 로드 지연 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708807"
---
# <a name="delayed-document-loading"></a>문서 로드 지연

사용자가 Visual Studio 솔루션을 다시 열면 대부분의 관련 문서가 즉시 로드되지 않습니다. 문서 창 프레임은 보류 중인 초기화 상태로 만들어지고 자리 표시자 문서(스텁 프레임이라고 함)는 RDT 실행 중인 문서 테이블(RDT)에 배치됩니다.

확장으로 인해 프로젝트 문서가 로드되기 전에 문서의 요소를 쿼리하여 프로젝트 문서를 불필요하게 로드할 수 있으며, 이로 인해 Visual Studio의 전체 메모리 사용 공간이 증가할 수 있습니다.

## <a name="document-loading"></a>문서 로드

스텁 프레임과 문서는 사용자가 문서에 액세스할 때(예: 창 프레임의 탭을 선택)를 완전히 초기화합니다. 또한 문서 데이터를 얻기 위해 RDT에 직접 액세스하거나 다음 호출 중 하나를 수행하여 RDT에 간접적으로 액세스하여 문서의 데이터를 요청하는 확장에 의해 문서를 초기화할 수도 있습니다.

- 창 프레임 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 메서드입니다.

- 다음 속성 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 중 어느 한 부분의 창 프레임 메서드는 다음과 같은 특성입니다.

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- 확장 프로그램이 관리 코드를 사용하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 문서가 보류 중인 초기화 상태에 있지 않거나 문서를 완전히 초기화하려는 경우가 아니면 호출해서는 안 됩니다. 그 이유는 메서드가 항상 doc 데이터 개체를 반환하여 필요한 경우 생성하기 때문입니다. 대신 `IVsRunningDocumentTable4` 인터페이스의 메서드 중 하나를 호출해야 합니다.

- 확장에서 C++를 사용하는 경우 `null` 원하지 않는 매개 변수를 전달할 수 있습니다.

- 다른 속성을 요청하기 전에 관련 속성을 요청하기 전에 다음 방법 중 하나를 호출하여 불필요한 문서 로드를 방지할 수 있습니다.

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>[__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. 이 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> _VSRDTFLAGS4 대 한 값을 포함 하는 개체를 반환 [합니다. ](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)문서가 아직 초기화되지 않은 경우 RDT_PendingInitialization.

문서가 완전히 초기화될 때 발생하는 RDT 이벤트에 가입하여 문서가 로드된 시기를 확인할 수 있습니다. 두 가지 가능성이 있습니다.

- 이벤트 싱크가 구현되면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>을 구독할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>수 있습니다.

- 그렇지 않으면 에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>가입할 수 있습니다.

다음 예제는 가상문서 액세스 시나리오입니다. 편집 잠금 개수 및 문서 데이터를 <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>검색하기 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 위해 각 문서를 호출하는 다음 RDT의 문서를 여과합니다. 문서가 초기화 보류 중인 상태인 경우 문서 데이터를 요청하면 문서가 불필요하게 초기화됩니다.

문서에 액세스하는 보다 효율적인 방법은 편집 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> 잠금 수를 얻은 다음 문서가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> 초기화되었는지 여부를 확인하는 데 사용하는 것입니다. 플래그가 _VSRDTFLAGS4 포함하지 않는 [경우. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)문서가 이미 초기화되었으며 문서 데이터를 요청해도 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> 불필요한 초기화가 발생하지 않습니다. 플래그가 _VSRDTFLAGS4 포함하는 [경우. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)확장은 문서가 초기화될 때까지 문서 데이터를 요청하지 않아야 합니다. 이 초기화는 `OnAfterAttributeChange(Ex)` 이벤트 처리기에서 검색할 수 있습니다.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>확장 을 테스트하여 초기화를 강제하는지 확인합니다.

문서가 초기화되었는지 여부를 나타내는 표시가 없으므로 확장이 초기화를 강제하는지 확인하기어려울 수 있습니다. 완전히 초기화되지 않은 모든 문서의 제목이 제목에 *[Stub]을* 갖도록 하므로 확인을 더 쉽게 할 수 있는 레지스트리 키를 설정할 수 있습니다.

**HKEY_CURRENT_USER\소프트웨어\Microsoft\VisualStudio\14.0\배경 솔루션로드,** * {0} [스텁]으로* **스텁타이틀타이틀 문자열을** 설정합니다.
