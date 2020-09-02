---
title: 소스 제어 디자인 결정 Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89d125dc52340e8528ee9692d5de00784632e6f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187894"
---
# <a name="source-control-design-decisions"></a>소스 제어 디자인 결정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스 제어를 구현할 때 프로젝트에 대 한 다음 디자인 결정 사항을 고려해 야 합니다.  
  
## <a name="will-information-be-shared-or-private"></a>정보를 공유 하거나 비공개로 설정할 수 있나요?  
 가장 중요 한 디자인 결정은 공유할 수 있는 정보와 개인 정보를 결정 하는 것입니다. 예를 들어, 프로젝트에 대 한 파일 목록이 공유 되지만이 파일 목록 내에서 일부 사용자는 전용 파일을 포함할 수 있습니다. 컴파일러 설정은 공유 되지만 일반적으로 시작 프로젝트는 전용입니다. 설정은 순수 하 게 공유 되거나 재정의를 사용 하 여 공유 되거나 전용 전용입니다. 기본적으로 솔루션 사용자 옵션 (.suo) 파일과 같은 개인 항목은 체크 인 되지 않습니다 [!INCLUDE[vsvss](../../includes/vsvss-md.md)] . .Suo 파일, 사용자가 만드는 특정 개인 파일 (예: Visual c #의 경우 .csproj. 사용자 파일) 또는 Visual Basic에 대 한 .vbproj 사용자 파일 등의 개인 파일에 개인 정보를 저장 해야 합니다.  
  
 이 결정은 모두 포함 되는 것은 아니므로 항목을 기준으로 수행할 수 있습니다.  
  
## <a name="will-the-project-include-special-files"></a>프로젝트에 특수 파일이 포함 됩니까?  
 또 다른 중요 한 디자인 결정은 프로젝트 구조에서 특수 파일을 사용 하는지 여부입니다. 특수 파일은 솔루션 탐색기 및 체크 아웃 대화 상자에 표시 되는 파일의 기반이 되는 숨겨진 파일입니다. 특수 파일을 사용 하는 경우 다음 지침을 따르세요.  
  
1. 프로젝트 파일 자체를 사용 하 여 프로젝트 루트 노드와 특수 파일을 연결 하지 마십시오. 프로젝트 파일은 단일 파일 이어야 합니다.  
  
2. 프로젝트에서 특수 파일을 추가, 제거 또는 이름을 변경한 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> 파일이 특수 파일 임을 나타내는 플래그 집합을 사용 하 여 적절 한 이벤트를 발생 시켜야 합니다. 이러한 이벤트는 적절 한 메서드를 호출 하는 프로젝트에 대 한 응답으로 환경에서 호출 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> .  
  
3. 프로젝트 또는 편집기에서 파일에 대해를 호출 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 해당 파일에 연결 된 특수 파일은 자동으로 체크 아웃 되지 않습니다. 에서 특수 파일을 부모 파일과 함께 전달 합니다. 환경은 전달 된 모든 파일 간의 관계를 감지 하 고 체크 아웃 UI에서 특수 파일을 적절 하 게 숨깁니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
