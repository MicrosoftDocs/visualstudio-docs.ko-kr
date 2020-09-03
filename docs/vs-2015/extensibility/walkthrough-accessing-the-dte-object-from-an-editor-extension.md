---
title: '연습: 편집기 확장에서 DTE 개체에 액세스 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b14b59465b94ddd0a09748f0e309166bf3d4114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148884"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>연습: 편집기 확장에서 DTE 개체 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage에서 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> dte 개체의 형식을 사용 하 여 메서드를 호출 하 여 dte 개체를 가져올 수 있습니다. MEF (Managed Extensibility Framework) 확장에서를 가져온 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 다음 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 형식을 사용 하 여 메서드를 호출할 수 있습니다 <xref:EnvDTE.DTE> .  
  
## <a name="prerequisites"></a>사전 준비 사항  
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="getting-the-dte-object"></a>DTE 개체 가져오기  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>ServiceProvider에서 DTE 개체를 가져오려면  
  
1. 이라는 c # VSIX 프로젝트를 만듭니다 `DTETest` . 편집기 분류자 항목 템플릿을 추가 하 고 이름을로 추가 `DTETest` 합니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.  
  
2. 프로젝트에 다음 어셈블리 참조를 추가 합니다.  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - VisualStudio를 변경할 수 없습니다.  
  
3. DTETest.cs 파일로 이동 하 여 다음 지시문을 추가 합니다 `using` .  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4. 클래스에서 `GetDTEProvider` 을 가져옵니다 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5. `GetClassifier()` 메서드에 다음 코드를 추가합니다.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6. 인터페이스를 사용 해야 하는 경우 <xref:EnvDTE80.DTE2> DTE 개체를 캐스팅할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
