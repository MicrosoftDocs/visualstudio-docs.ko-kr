---
title: 레거시 API를 사용 하 여 텍스트 버퍼에 액세스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184990"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>레거시 API를 사용하여 텍스트 버퍼에 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트는 텍스트 스트림과 파일 지 속성을 관리 하는 일을 담당 합니다. 버퍼는 다른 형식을 읽거나 쓸 수 있지만 버퍼와의 모든 일반 통신은 유니코드를 사용 하 여 수행 됩니다. 레거시 Api에서 텍스트 버퍼는 1 또는 2 차원 좌표계를 사용 하 여 버퍼의 문자 위치를 식별할 수 있습니다.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>1 차원 및 2 차원 좌표계  
 1 차원 좌표 위치는 버퍼의 첫 번째 문자 (예: 147)에서 문자 위치를 기준으로 합니다. 인터페이스를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> 버퍼의 1 차원 위치에 액세스 합니다. 2 차원 좌표계는 선 및 인덱스 쌍을 기반으로 합니다. 예를 들어 43의 버퍼에 있는 문자는 43 줄에 있고 해당 줄에서 첫 번째 문자 오른쪽에 5 자를 갖습니다. 인터페이스를 사용 하 여 버퍼에서 2 차원 위치에 액세스 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>및 인터페이스는 모두 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> 텍스트 버퍼 개체 ()에 의해 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 되며를 사용 하 여 서로 액세스할 수 있습니다 `QueryInterface` . 다음 다이어그램에서는의 이러한 및 기타 키 인터페이스를 보여 줍니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 ![텍스트 버퍼 개체](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
텍스트 버퍼 개체  
  
 좌표계는 텍스트 버퍼에서 작동 하지만 2 차원 좌표를 사용 하도록 최적화 되어 있습니다. 1 차원 좌표계는 성능 오버 헤드를 만들 수 있습니다. 따라서 가능 하면 항상 2 차원 좌표계를 사용 합니다.  
  
 텍스트 버퍼의 두 번째 역할은 파일 지 속성입니다. 이렇게 하기 위해 텍스트 버퍼 개체는를 구현 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 고 지 속성에 관련 된 프로젝트 항목 및 기타 환경 구성 요소에 대 한 문서 데이터 개체 구성 요소 역할을 합니다. 자세한 내용은 [프로젝트 항목 열기 및 저장](../extensibility/internals/opening-and-saving-project-items.md)을 참조 하세요.  
  
## <a name="in-this-section"></a>섹션 내용  
 [레거시 API를 사용하여 보기 설정 변경](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 레거시 API를 사용 하 여 보기 설정을 변경 하는 방법을 설명 합니다.  
  
 [텍스트 관리자를 사용하여 글로벌 설정 모니터링](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 텍스트 관리자를 사용 하 여 전역 설정을 모니터링 하는 방법을 설명 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [핵심 편집기 내부](../extensibility/inside-the-core-editor.md)
