---
title: 편집기 확장에서 DTE 개체 액세스
description: 이 연습의 코드 예제를 사용하여 편집기 확장에서 DTE 개체에 액세스하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 094a37960fa5b32d018eebe3becee4fde43cc392
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905126"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>연습: 편집기 확장에서 DTE 개체 액세스

VSPackages에서 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 메서드를 DTE 개체 형식과 함께 호출하여 DTE 개체를 가져올 수 있습니다. MEF(Managed Extensibility Framework) 확장에서 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>를 가져온 다음, <xref:EnvDTE.DTE> 형식과 함께 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 메서드를 호출할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하세요.

## <a name="get-the-dte-object"></a>DTE 개체 가져오기

1. C# VSIX 프로젝트를 만들고 이름을 **DTETest** 로 지정합니다. **편집기 분류자** 항목 템플릿을 추가하고 이름을 **DTETest** 로 지정합니다.

   자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조하세요.

::: moniker range=">=vs-2019"

2. 프로젝트에 다음 어셈블리 참조를 추가합니다.

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. *DTETestProvider.cs* 파일에서 다음 `using` 지시문을 추가합니다.

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. `DTETestProvider` 클래스에서 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>를 가져옵니다.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. `GetClassifier()` 메서드에서 `return` 문 앞에 다음 코드를 추가합니다.

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. 프로젝트에 다음 어셈블리 참조를 추가합니다.

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. *DTETestProvider.cs* 파일에서 다음 `using` 지시문을 추가합니다.

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. `DTETestProvider` 클래스에서 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>를 가져옵니다.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. `GetClassifier()` 메서드에서 `return` 문 앞에 다음 코드를 추가합니다.

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>참조

- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
- [DTE를 사용하여 Visual Studio 시작](launch-visual-studio-dte.md)
