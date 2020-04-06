---
title: 소스 제어 패키지 모델 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707065"
---
# <a name="model-for-source-control-packages"></a>소스 제어 패키지 모델
다음 모델은 소스 제어 구현의 예를 나타냅니다. 모델에서 구현해야 하는 인터페이스와 호출해야 하는 환경 서비스가 표시됩니다. 모든 서비스와 마찬가지로 실제로 서비스를 통해 얻은 특정 인터페이스의 메서드를 호출합니다. 클래스의 이름은 소스 제어가 수행되는 방식을 보다 쉽게 확인할 수 있도록 식별됩니다.

 ![SCC&#95;TUP 예제](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") 소스 제어 프로젝트 예제

## <a name="interfaces"></a>인터페이스
 다음 표에 표시된 인터페이스 목록을 사용하여 Visual Studio에서 새 프로젝트 유형에 대한 소스 제어를 구현할 수 있습니다.

|인터페이스|사용|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|프로젝트 및 편집자가 파일을 저장하거나 변경하기 전에 호출합니다. 이 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 서비스를 사용하여 액세스됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|파일 또는 디렉터리 이름을 추가, 제거 또는 이름을 바꿀 수 있는 권한을 요청하는 프로젝트에서 호출됩니다. 이 인터페이스는 승인된 추가, 제거 또는 이름 바꾸기 작업이 완료되면 환경에 알리기 위해 프로젝트에서 호출됩니다. 서비스를 사용하여 액세스할 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|프로젝트가 파일이나 디렉터리를 추가, 이름 변경 또는 제거할 때 알림을 받을 등록하는 모든 엔터티에 의해 구현됩니다. 이벤트 알림을 등록하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>를 호출합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|소스 제어 패키지에 등록하고 소스 제어 상태에 대한 정보를 얻기 위해 프로젝트에서 호출합니다. 이 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 서비스를 사용하여 액세스됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|프로젝트에 의해 구현된 파일에 대한 정보에 대한 소스 제어 요청에 응답하고 프로젝트 파일에 필요한 소스 제어 설정을 얻습니다.|

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
