---
title: 포함 된 언어 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184285"
---
# <a name="contained-languages"></a>포함된 언어
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

*포함 된 언어* 는 다른 언어에 포함 된 언어입니다. 예를 들어 페이지의 HTML에 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 또는 스크립트가 포함 될 수 있습니다 [!INCLUDE[csprcs](../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . .Aspx 파일 편집기는 HTML과 스크립팅 언어에 대해 IntelliSense, 색 지정 및 기타 편집 기능을 제공 하기 위해 이중 언어 아키텍처가 필요 합니다.  
  
## <a name="implementation"></a>구현  
 포함 된 언어에 대해 구현 해야 하는 가장 중요 한 인터페이스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 인터페이스입니다. 이 인터페이스는 주 언어 내에서 호스팅될 수 있는 모든 언어에 의해 구현 됩니다. 언어 서비스의 svc, 텍스트 뷰 필터 및 주 언어 서비스 ID에 대 한 액세스를 제공 합니다. 를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> 사용 하면 인터페이스를 만들 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> . 다음 단계는 포함 된 언어를 구현 하는 방법을 보여 줍니다.  
  
1. 를 사용 `QueryService()` 하 여의 언어 서비스 id와 인터페이스 id를 가져옵니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> .  
  
2. 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> 하 여 인터페이스를 만듭니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>인터페이스, 하나 이상의 [항목 id](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) 및 인터페이스를 전달 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> 합니다.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>텍스트 버퍼 코디네이터 개체인 인터페이스는 주 파일의 위치를 보조 언어의 버퍼로 매핑하는 데 필요한 기본 서비스를 제공 합니다.  
  
     예를 들어 단일 .aspx 파일의 경우 기본 파일에는 ASP, HTML 및 포함 된 모든 코드가 포함 됩니다. 그러나 보조 버퍼에는 보조 버퍼를 유효한 코드 파일로 만들기 위해 클래스 정의와 함께 포함 된 코드만 포함 됩니다. 버퍼 코디네이터는 버퍼 간에 편집 내용을 조정 하는 작업을 처리 합니다.  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>주 언어인 메서드는 버퍼 코디네이터에 게 보조 버퍼의 해당 텍스트에 매핑되는 버퍼 내의 텍스트를 알려 줍니다.  
  
     이 언어는 <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> 현재 주 및 보조 범위를 포함 하는 구조체의 배열에 전달 됩니다.  
  
5. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>메서드와 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> 메서드는 주 버퍼에서 보조 버퍼로의 매핑을 제공 합니다.
