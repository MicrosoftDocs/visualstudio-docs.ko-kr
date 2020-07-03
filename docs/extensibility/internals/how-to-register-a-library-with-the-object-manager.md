---
title: '방법: 개체 관리자를 사용 하 여 라이브러리 등록 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 7179bd87fdfd9a2c3fc36958a9d964ec4f790dbd
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905232"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>방법: 개체 관리자를 사용 하 여 라이브러리 등록
기호-검색 도구 (예: **클래스 뷰**, **개체 브라우저**, **호출 브라우저** 및 **찾기 결과**)를 사용 하 여 프로젝트 또는 외부 구성 요소에서 기호를 볼 수 있습니다. 기호에는 네임 스페이스, 클래스, 인터페이스, 메서드 및 기타 언어 요소가 포함 됩니다. 라이브러리는 이러한 기호를 추적 하 고 도구를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 데이터로 채우는 개체 관리자에 게 노출 합니다.

 개체 관리자는 사용 가능한 모든 라이브러리를 추적 합니다. 각 라이브러리는 기호 검색 도구에 대 한 기호를 제공 하기 전에 개체 관리자에 등록 해야 합니다.

 일반적으로 VSPackage 로드 될 때 라이브러리를 등록 합니다. 그러나 필요에 따라 다른 시간에이 작업을 수행할 수 있습니다. VSPackage가 종료 되 면 라이브러리의 등록을 취소 합니다.

 라이브러리를 등록 하려면 메서드를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> 합니다. 관리 코드 라이브러리의 경우 메서드를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 합니다.

 라이브러리의 등록을 취소 하려면 메서드를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> 합니다.

 개체 관리자에 대 한 참조를 가져오려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> 서비스 ID를 `GetService` 메서드에 전달 합니다.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>개체 관리자를 사용 하 여 라이브러리 등록 및 등록 취소

### <a name="to-register-a-library-with-the-object-manager"></a>개체 관리자를 사용 하 여 라이브러리를 등록 하려면

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

2. 형식의 개체에 대 한 참조를 가져오고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 합니다.

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

### <a name="to-unregister-a-library-with-the-object-manager"></a>개체 관리자를 사용 하 여 라이브러리의 등록을 취소 하려면

1. 형식의 개체에 대 한 참조를 가져오고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> 합니다.

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
- [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [방법: 라이브러리에서 제공 하는 기호 목록을 개체 관리자에 게 노출](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
