---
title: 프로젝트 시스템에 웹 서비스 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002659"
---
# <a name="adding-web-services-to-project-systems"></a>프로젝트 시스템에 웹 서비스 추가
일반적으로 XML Web services는 SOAP (Simple Object Access Protocol) 프로토콜을 사용 하 여 프로젝트 시스템에 프로그래밍 정보를 반환 하는 URL 주소 지정 가능 리소스입니다. 인터페이스를 사용 하 여 웹 서비스를 VSPackage 프로젝트 시스템에 통합할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> .  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>프로젝트 시스템에 웹 서비스를 추가 하려면  
  
1. `QueryService`서비스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> 통해 인터페이스를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> 합니다.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 메서드를 호출합니다. 매개 변수를로 전달 하는 경우 `pDiscoverySession` `NULL` 검색 세션이 생성 되 고, 나중에 인터페이스에서 사용할 수 있도록 세션이 캐시 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 메서드는에 대 한 포인터를 반환 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> 합니다.  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> 메서드를 호출합니다. 웹 서비스 참조 폴더에 대 한 자동화 개체를 `pUnkWebReferenceFolder` 매개 변수로 전달 합니다. 그러면 Visual Studio 환경에서 웹 서비스가 이미 있는지 여부를 확인 합니다. 웹 서비스가 없는 경우 환경에서 해당 웹 서비스를 다운로드 하 여 폴더에 추가 파일 (예: .wsdl 파일)을 폴더의 자식 노드에 추가 합니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>