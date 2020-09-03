---
title: 편집기 확장에서 DTE 개체에 액세스 합니다.
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697653"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>연습: 편집기 확장에서 DTE 개체에 액세스

Vspackage에서 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> dte 개체의 형식을 사용 하 여 메서드를 호출 하 여 dte 개체를 가져올 수 있습니다. MEF (Managed Extensibility Framework) 확장에서를 가져온 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> 다음 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 형식을 사용 하 여 메서드를 호출할 수 있습니다 <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="get-the-dte-object"></a>DTE 개체 가져오기

1. C # VSIX 프로젝트를 만들고 이름을 **DTETest**로 만듭니다. **편집기 분류자** 항목 템플릿을 추가 하 고 이름을 **DTETest**로 추가 합니다.

   자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

::: moniker range=">=vs-2019"

2. 프로젝트에 다음 어셈블리 참조를 추가 합니다.

    - VisualStudio.
    - VisualStudio를 변경할 수 없습니다.

3. *DTETestProvider.cs* 파일에서 다음 지시문을 추가 합니다 `using` .

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. 클래스에서을 `DTETestProvider` 가져옵니다 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. `GetClassifier()`메서드에서 문 앞에 다음 코드를 추가 합니다 `return` .

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. 프로젝트에 다음 어셈블리 참조를 추가 합니다.

   - EnvDTE
   - VisualStudio.

3. *DTETestProvider.cs* 파일에서 다음 지시문을 추가 합니다 `using` .

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. 클래스에서을 `DTETestProvider` 가져옵니다 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. `GetClassifier()`메서드에서 문 앞에 다음 코드를 추가 합니다 `return` .

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>추가 정보

- [언어 서비스 및 편집기 확장 위치](../extensibility/language-service-and-editor-extension-points.md)
- [DTE를 사용하여 Visual Studio 시작](launch-visual-studio-dte.md)
