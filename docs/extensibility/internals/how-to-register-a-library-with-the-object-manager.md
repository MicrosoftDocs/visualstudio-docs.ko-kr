---
title: '방법: 개체 관리자에 라이브러리 등록 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bd1032d2ba67a0c0f3338560a80038ed3215531
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707939"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>방법: 개체 관리자와 라이브러리 등록
**클래스 보기,** **개체 브라우저,** **브라우저 호출** 및 기호 **결과 찾기와**같은 기호 검색 도구를 사용하면 프로젝트 또는 외부 구성 요소에서 기호를 볼 수 있습니다. 기호에는 네임스페이스, 클래스, 인터페이스, 메서드 및 기타 언어 요소가 포함됩니다. 라이브러리는 이러한 기호를 추적하고 도구를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 데이터로 채우는 개체 관리자에 노출합니다.

 개체 관리자는 사용 가능한 모든 라이브러리를 추적합니다. 각 라이브러리는 기호 검색 도구에 대한 기호를 제공하기 전에 개체 관리자에 등록해야 합니다.

 일반적으로 VSPackage가 로드될 때 라이브러리를 등록합니다. 그러나 필요에 따라 다른 시간에 수행 할 수 있습니다. VSPackage가 종료되면 라이브러리를 등록 취소합니다.

 라이브러리를 등록하려면 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> 사용합니다. 관리 되는 코드 라이브러리에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 대 한 메서드를 사용 합니다.

 라이브러리를 등록 취소하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> 메서드를 사용합니다.

 개체 관리자에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>대한 참조를 얻으려면 <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> 서비스 ID를 메서드에 전달합니다. `GetService`

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>개체 관리자에 라이브러리 등록 및 등록 취소

### <a name="to-register-a-library-with-the-object-manager"></a>개체 관리자에 라이브러리를 등록하려면

1. 라이브러리를 만듭니다.

    ```vb
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing
    Private m_nLibraryCookie As UInteger = 0
    ' Create Library.
    m_CallBrowserLibrary = New CallBrowser.Library()
    ```

    ```csharp
    private CallBrowser.Library m_CallBrowserLibrary = null;
    private uint m_nLibraryCookie = 0;
    // Create Library.
    m_CallBrowserLibrary = new CallBrowser.Library();

    ```

2. 형식의 개체에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> 참조를 가져오고 메서드를 호출합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>

    ```vb
    Private Sub RegisterLibrary()
        If m_nLibraryCookie <> 0 Then
            Throw New Exception("Library already registered with Object Manager")
        End If

        ' Obtain a reference to IVsObjectManager2 type object.
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
        If objManager Is Nothing Then
            Throw New NullReferenceException("GetService failed for SVsObjectManager")
        End If

        Try
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)
        Catch e As Exception
            ' Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message)
            Throw
        End Try
    End Sub
    ```

    ```csharp
    private void RegisterLibrary()
    {
        if (m_nLibraryCookie != 0)
            throw new Exception("Library already registered with Object Manager");

        // Obtain a reference to IVsObjectManager2 type object.
        IVsObjectManager2 objManager =
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
        if (objManager == null)
            throw new NullReferenceException("GetService failed for SVsObjectManager");

        try
        {
            int hr =
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,
                                                 out m_nLibraryCookie);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
        }
        catch (Exception e)
        {
            // Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message);
            throw;
        }
    }

    ```

### <a name="to-unregister-a-library-with-the-object-manager"></a>개체 관리자에 라이브러리를 등록 취소하려면

1. 형식의 개체에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> 참조를 가져오고 메서드를 호출합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A>

    ```vb
    Private Sub UnregisterLibrary()
        If m_nLibraryCookie <> 0 Then
            ' Obtain a reference to IVsObjectManager2 type object.
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
            If objManager Is Nothing Then
                Throw New NullReferenceException("GetService failed for SVsObjectManager")
            End If

            Try
                objManager.UnregisterLibrary(m_nLibraryCookie)
            Catch e As Exception
                ' Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message)
                Throw
            Finally
                m_nLibraryCookie = 0
            End Try
        End If
    End Sub
    ```

    ```csharp
    private void UnregisterLibrary()
    {
        if (m_nLibraryCookie != 0)
        {
            // Obtain a reference to IVsObjectManager2 type object.
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
            if (objManager == null)
                throw new NullReferenceException("GetService failed for SVsObjectManager");

            try
            {
                objManager.UnregisterLibrary(m_nLibraryCookie);
            }
            catch (Exception e)
            {
                // Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message);
                throw;
            }
            finally
            {
                m_nLibraryCookie = 0;
            }
        }
    }

    ```

## <a name="see-also"></a>참조
- [레거시 언어 서비스 확장성](../../extensibility/internals/legacy-language-service-extensibility.md)
- [심볼 브라우징 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [방법: 라이브러리에서 제공하는 기호 목록을 개체 관리자에 노출](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
