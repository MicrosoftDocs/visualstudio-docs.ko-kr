---
title: 레거시 API를 사용 하 여 언어 서비스 컨텍스트 제공 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193878"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>레거시 API를 사용하여 언어 서비스 컨텍스트 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

언어 서비스에서 핵심 편집기를 사용 하 여 사용자 컨텍스트를 제공 하는 두 가지 옵션은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 텍스트 표식 컨텍스트 제공 또는 모든 사용자 컨텍스트 제공입니다. 각각의 차이점은 여기에 설명 되어 있습니다.  
  
 편집기에 연결 된 언어 서비스에 컨텍스트를 제공 하는 방법에 대 한 자세한 내용은 [방법: 편집기에 대 한 컨텍스트 제공](../extensibility/how-to-provide-context-for-editors.md)을 참조 하세요.  
  
## <a name="provide-text-marker-context-to-the-editor"></a>편집기에 텍스트 표식 컨텍스트 제공  
 핵심 편집기에서 텍스트 표식으로 표시 되는 컴파일러 오류에 대 한 컨텍스트를 제공 하려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인터페이스를 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 합니다. 이 시나리오에서 언어 서비스는 커서가 텍스트 표식에 있는 경우에만 컨텍스트를 제공 합니다. 이를 통해 편집기는 커서의 키워드를 특성 없이 **동적 도움말** 창에 제공할 수 있습니다.  
  
## <a name="provide-all-user-context-to-the-editor"></a>편집기에 모든 사용자 컨텍스트 제공  
 언어 서비스를 만들고 핵심 편집기를 사용 하는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 인터페이스를 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 하 여 언어 서비스에 대 한 컨텍스트를 제공할 수 있습니다.  
  
 구현 시 컨텍스트 모음 `IVsLanguageContextProvider` (컬렉션)은 컨텍스트 모음 업데이트를 담당 하는 편집기에 연결 됩니다. **동적 도움말** 창이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> 유휴 시간에이 컨텍스트 모음에서 인터페이스를 호출 하면 컨텍스트 모음에서 업데이트를 위해 편집기에 쿼리 합니다. 그러면 편집기에서 편집기를 업데이트 하도록 언어 서비스에 알리고 컨텍스트 모음에 포인터를 전달 합니다. 편집기에서 언어 서비스로 메서드를 호출 하 여이 작업을 수행 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> 합니다. 이제는 컨텍스트 모음에 대 한 포인터를 사용 하 여 언어 서비스에서 특성과 키워드를 추가 하 고 제거할 수 있습니다. 자세한 내용은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>를 참조하세요.  
  
 다음 두 가지 방법으로를 구현할 수 있습니다 `IVsLanguageContextProvider` .  
  
- 컨텍스트 모음에 키워드를 제공 합니다.  
  
   컨텍스트 모음을 업데이트 하기 위해 편집기를 호출 하는 경우 적절 한 키워드 및 특성을 전달 하 고를 반환 `S_OK` 합니다. 이 반환 값은 커서의 키워드를 컨텍스트 모음에 제공 하는 대신 키워드 및 특성 컨텍스트를 유지 하도록 편집기에 지시 합니다.  
  
- 커서의 키워드에서 키워드를 가져옵니다.  
  
   컨텍스트 모음을 업데이트 하기 위해 편집기가 호출 되 면 적절 한 특성을 전달 하 고를 반환 `E_FAIL` 합니다. 이 반환 값은 컨텍스트 모음에서 특성을 유지 하도록 편집기에 지시 하지만 커서에서 키워드를 사용 하 여 컨텍스트 모음을 업데이트 합니다.  
  
  다음 다이어그램에서는을 구현 하는 언어 서비스에 대해 컨텍스트를 제공 하는 방법을 보여 줍니다 `IVsLanguageContextProvider` .  
  
  ![LangServiceImplementation2 그래픽](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  언어 서비스에 대 한 컨텍스트  
  
  다이어그램에서 볼 수 있듯이 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 핵심 텍스트 편집기에는 연결 된 컨텍스트 모음이 있습니다. 이 컨텍스트 모음은 언어 서비스, 기본 편집기 및 텍스트 표식의 세 가지 개별 subcontext 모음을 가리킵니다. 언어 서비스 및 텍스트 표식 subcontext 모음은 인터페이스가 구현 된 경우 언어 서비스의 특성과 키워드를 포함 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 하 고 인터페이스를 구현 하는 경우 텍스트 표식을 포함 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> . 이러한 인터페이스 중 하나를 구현 하지 않는 경우 편집기는 기본 편집기 subcontext 모음에서 커서의 키워드에 대 한 컨텍스트를 제공 합니다.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>편집기 및 디자이너에 대 한 컨텍스트 지침  
 디자이너와 편집기는 편집기 또는 디자이너 창에 대해 일반 키워드를 제공 해야 합니다. 이 작업을 수행 하면 사용자가 F1 키를 누를 때 디자이너 또는 편집기에 대 한 일반 도움말 항목이 표시 됩니다. 편집기는이 외에도 커서에 현재 키워드를 제공 하거나 현재 선택 항목을 기반으로 키 용어를 제공 해야 합니다. 이 작업은 사용자가 F1 키를 누를 때 표시 되거나 선택 된 텍스트 또는 UI 요소에 대 한 도움말 항목이 표시 되도록 하기 위한 것입니다. 디자이너는 폼의 단추와 같이 디자이너에서 선택한 항목에 대 한 컨텍스트를 제공 합니다. 편집기 및 디자이너는 [레거시 언어 서비스 Essentials](../extensibility/internals/legacy-language-service-essentials.md)에 설명 된 대로 언어 서비스에도 연결 해야 합니다.
