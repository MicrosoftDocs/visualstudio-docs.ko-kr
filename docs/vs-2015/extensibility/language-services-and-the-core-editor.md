---
title: 언어 서비스 및 핵심 편집기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language services
ms.assetid: e03199a6-ad5f-4075-bfba-8d36865112b7
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e708ffe796bfc9342bc20c3e7f20d5cf0d05058
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180298"
---
# <a name="language-services-and-the-core-editor"></a>언어 서비스 및 핵심 편집기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 편집기는 언어 서비스와 자주 연결 됩니다. 무엇 보다도 언어 서비스는 구문 색 지정, 문 완성, IntelliSense 및 텍스트 서식 지정을 제공 합니다.  
  
## <a name="core-editors-and-document-data-objects"></a>핵심 편집기 및 문서 데이터 개체  
 핵심 편집기에 액세스할 때 문서 데이터와 문서 뷰 개체를 만들지 않습니다. IDE는 이러한 두 개체를 만들고 제어 하며 편집기 팩터리 구현에서 적절 한 호출을 수행 하 여 핸들을 가져옵니다.  
  
 자세한 내용은 [프로젝트에서 파일을 여는 편집기 확인](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)을 참조 하세요.  
  
## <a name="language-services-and-the-core-editor"></a>언어 서비스 및 핵심 편집기  
 언어 서비스를 구현 하 여 문서 보기에 데이터가 표시 되는 방식을 제어할 수 있습니다. 언어 서비스는 Visual C++와 같은 지정 된 언어와 관련 된 정보 및 동작을 제공 합니다. 텍스트 버퍼를 만들고 여는 문서에 대 한 파일 이름 확장명을 결정할 때, 텍스트 버퍼는 레지스트리 키에서이 파일 이름 확장명과 연결 된 언어 서비스를 결정 합니다. HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Editors \\ {YOURLANGUAGESERVICE GUID} \Extensionss 그런 다음 표준 VSPackage 로딩 프로시저는 VSPackage를 로드 하 고 언어 서비스의 인스턴스를 만듭니다.  
  
 기본 언어 서비스는 다음 그림에 나와 있습니다.  
  
 ![언어 서비스 모델 그래픽](../extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
핵심 편집기 및 언어 서비스 개체  
  
 핵심 편집기에 대 한 문서 데이터 개체를 텍스트 버퍼 라고 하며 개체로 표시 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> . 문서 뷰 개체는 텍스트 뷰 라고 하며 개체로 표현 됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> . 이러한 두 개체는 언어 서비스를 통해 함께 작동 하 여 핵심 편집기의 통합 된 보기를 제공 합니다. 텍스트 버퍼 및 텍스트 뷰의 정보는 코드 창 이라는 문서 창에 표시 됩니다. 코드 창 문서는 코드 창 관리자를 통해 관리 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 [레거시 API를 사용 하 여 언어 서비스 컨텍스트 제공](../extensibility/providing-a-language-service-context-by-using-the-legacy-api.md)   
 [IntelliSense 호스팅](../extensibility/intellisense-hosting.md)   
 [포함 된 언어](../extensibility/contained-languages.md)   
 [레거시 언어 서비스 개발](../extensibility/internals/developing-a-legacy-language-service.md)
