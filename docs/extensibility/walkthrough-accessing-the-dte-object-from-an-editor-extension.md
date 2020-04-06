---
title: 편집기 확장에서 DTE 개체에 액세스
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697653"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>연습: 편집기 확장에서 DTE 개체에 액세스

VSPackages에서는 DTE 개체의 형식을 사용하여 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> 메서드를 호출하여 DTE 개체를 얻을 수 있습니다. 관리되는 확장성 프레임워크(MEF) 확장에서 메서드를 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> 가져온 다음 <xref:EnvDTE.DTE>의 형식을 사용하여 메서드를 호출할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

## <a name="get-the-dte-object"></a>DTE 개체 받기

1. C # VSIX 프로젝트를 만들고 **DTETest**이름을 지정합니다. **편집기 분류자** 항목 템플릿을 추가하고 **DTETest**이름을 지정합니다.

   자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

::: moniker range=">=vs-2019"

2. 프로젝트에 다음 어셈블리 참조를 추가합니다.

    - 마이크로소프트.비주얼 스튜디오.쉘.프레임워크
    - 마이크로소프트.비주얼스튜디오.쉘.불변.10.0

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

5. 메서드에서 `GetClassifier()` 문 앞에 다음 코드를 `return` 추가합니다.

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. 프로젝트에 다음 어셈블리 참조를 추가합니다.

   - EnvDTE
   - 마이크로소프트.비주얼 스튜디오.쉘.프레임워크

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

5. 메서드에서 `GetClassifier()` 문 앞에 다음 코드를 `return` 추가합니다.

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>참조

- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
- [DTE를 사용하여 Visual Studio 시작](launch-visual-studio-dte.md)
