---
title: 원본 제어 패키지에 대 한 모델 | Microsoft Docs
description: 이 모델은 소스 제어 구현을 나타냅니다. 이 문서에서는 소스 제어를 수행 하는 방법을 쉽게 확인할 수 있도록 클래스의 이름을 보여 줍니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4e437afdfa0d3de03da6814e221840cbd0763fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063203"
---
# <a name="model-for-source-control-packages"></a>소스 제어 패키지 모델
다음 모델은 소스 제어 구현의 예를 나타냅니다. 모델에는 구현 해야 하는 인터페이스와 사용자가 호출 해야 하는 환경 서비스가 표시 됩니다. 모든 서비스와 마찬가지로 실제로 서비스를 통해 가져오는 특정 인터페이스의 메서드를 호출 합니다. 클래스의 이름은 소스 제어의 수행 방법을 더 쉽게 확인할 수 있도록 식별 됩니다.

 ![SCC&#95;TUP 예제](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") 소스 제어 프로젝트 예제

## <a name="interfaces"></a>인터페이스
 다음 표에 표시 된 인터페이스의 목록을 사용 하 여 Visual Studio에서 새 프로젝트 형식에 대 한 소스 제어를 구현할 수 있습니다.

|인터페이스|Windows Server Update Services와 함께|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|파일을 저장 하거나 변경 하기 전에 프로젝트 및 편집기에서 호출 됩니다. 이 인터페이스는 서비스를 사용 하 여 액세스 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|파일이 나 디렉터리를 추가, 제거 또는 이름을 바꿀 권한을 요청 하기 위해 프로젝트에서 호출 됩니다. 이 인터페이스는 승인 된 추가, 제거 또는 이름 바꾸기 작업이 완료 되 면 환경에 알리기 위해 프로젝트에서 호출 됩니다. 서비스를 사용 하 여 액세스할 수 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|프로젝트에서 파일 또는 디렉터리를 추가 하거나, 이름을 바꾸거나, 제거할 때 알리도록 등록 하는 모든 엔터티에 의해 구현 됩니다. 이벤트 알림을 등록 하려면를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A> 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|소스 제어 패키지에 등록 하 고 소스 제어 상태에 대 한 정보를 얻기 위해 프로젝트에서 호출 됩니다. 이 인터페이스는 서비스를 사용 하 여 액세스 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|파일에 대 한 정보에 대 한 소스 제어 요청에 응답 하 고 프로젝트 파일에 필요한 소스 제어 설정을 가져오는 프로젝트에 의해 구현 됩니다.|

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
