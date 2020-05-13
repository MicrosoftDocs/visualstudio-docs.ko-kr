---
title: 개체 관리자에 제공된 기호 목록 노출 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsSimpleLibrary2 interface, lists of symbols
- IVsLibrary2 interface, lists of symbols
- symbols, call browser
- lists, symbols for the object manager
- symbols, exposing lists to the object manager
ms.assetid: 19757068-bdaa-4e7e-85d6-f8ce5026a859
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb15b7d9b29c578a0acf43fd1aa9cfdea88e23ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708084"
---
# <a name="how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager"></a>방법: 라이브러리에서 제공하는 기호 목록을 개체 관리자에 노출
기호 검색 도구, **클래스 보기**, 개체 **브라우저,** **브라우저 호출** 및 기호 결과 **찾기,** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개체 관리자에 새 데이터에 대 한 요청을 전달 합니다. 개체 관리자는 적절한 라이브러리를 찾아 새 기호 목록을 요청합니다. 라이브러리는 인터페이스를 통해 개체 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 관리자에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 요청된 데이터를 제공하여 응답합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개체 관리자는 인터페이스에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 메서드를 호출하여 데이터를 가져오고 이를 사용하여 기호 검색 도구의 보기를 채우거나 업데이트합니다.

 라이브러리는 도구가 호출되거나 노드가 확장되거나 뷰를 새로 고칠 때 데이터에 대한 요청을 받을 수 있습니다. 기호 검색 도구가 처음으로 호출되면 개체 관리자는 라이브러리에 최상위 목록을 제공하도록 요청합니다. 사용자가 목록 노드를 확장하면 라이브러리는 해당 노드 아래의 자식 목록을 제공합니다. 모든 개체 관리자 문의에는 관심 항목의 인덱스가 포함됩니다. 새 목록을 표시하려면 개체 관리자는 목록에 있는 항목 수, 항목 유형, 이름, 접근성 및 기타 속성을 결정해야 합니다.

> [!NOTE]
> 다음 관리 코드 예제에서는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 인터페이스 구현을 통해 기호 목록을 제공하는 방법을 보여 줍니다. 개체 관리자는 이 인터페이스의 메서드를 호출하고 가져온 데이터를 사용하여 기호 검색 도구를 채우거나 업데이트합니다.
>
> 네이티브 코드 기호 공급자 구현의 경우 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> 사용합니다.

## <a name="to-provide-lists-of-symbols-to-the-object-manager"></a>개체 관리자에 기호 목록을 제공하려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> 메서드를 구현 하 여 기호 목록에서 항목 수를 가져옵니다. 다음 예제에서는 개체 관리자가 목록의 항목 수에 대한 정보를 가져오는 방법을 보여 줍니다.

    ```vb
    Protected m_Methods As System.Collections.Generic.SortedList(Of String, Method) = New System.Collections.Generic.SortedList(Of String, Method)()

    Public Function GetItemCount(ByRef pCount As UInteger) As Integer
        pCount = CUInt(m_Methods.Count)
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    protected System.Collections.Generic.SortedList<string, Method> m_Methods = new System.Collections.Generic.SortedList<string, Method>();

    public int GetItemCount(out uint pCount)
    {
        pCount = (uint)m_Methods.Count;
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

2. 메서드를 구현하여 지정된 목록 항목의 범주 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> 특성에 대한 정보를 가져옵니다. 항목 범주는 열거형에 <xref:Microsoft.VisualStudio.Shell.Interop.LIB_CATEGORY> 지정되어 있습니다. 다음 예제에서는 개체 관리자가 지정된 범주에 대한 항목의 특성을 가져오는 방법을 보여 줍니다.

    ```vb
    Public Function GetCategoryField2(ByVal index As UInteger, ByVal Category As Integer, ByRef pfCatField As UInteger) As Integer
        pfCatField = 0

        Select Case CType(Category, LIB_CATEGORY)
            Case LIB_CATEGORY.LC_MEMBERTYPE
                pfCatField = CUInt(_LIBCAT_MEMBERTYPE.LCMT_METHOD)

            Case LIB_CATEGORY.LC_MEMBERACCESS
                Dim method As Method = m_Methods.Values(CInt(Fix(index)))

                If method.IsPublic Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PUBLIC)
                ElseIf method.IsPrivate Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PRIVATE)
                ElseIf method.IsFamily Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PROTECTED)
                ElseIf method.IsFamilyOrAssembly Then
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PROTECTED) Or CUInt(_LIBCAT_MEMBERACCESS.LCMA_PACKAGE)
                Else
                    ' Show everything else as internal.
                    pfCatField = CUInt(_LIBCAT_MEMBERACCESS.LCMA_PACKAGE)
                End If

            Case LIB_CATEGORY.LC_VISIBILITY
                pfCatField = CUInt(_LIBCAT_VISIBILITY.LCV_VISIBLE)

            Case LIB_CATEGORY.LC_LISTTYPE
                pfCatField = CUInt(_LIB_LISTTYPE.LLT_MEMBERS)

            Case Else
                Return Microsoft.VisualStudio.VSConstants.S_FALSE
        End Select
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int GetCategoryField2(uint index, int Category, out uint pfCatField)
    {
        pfCatField = 0;

        switch ((LIB_CATEGORY)Category)
        {
            case LIB_CATEGORY.LC_MEMBERTYPE:
                pfCatField = (uint)_LIBCAT_MEMBERTYPE.LCMT_METHOD;
                break;

            case LIB_CATEGORY.LC_MEMBERACCESS:
                {
                    Method method = m_Methods.Values[(int)index];

                    if (method.IsPublic)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PUBLIC;
                    }
                    else if (method.IsPrivate)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PRIVATE;
                    }
                    else if (method.IsFamily)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PROTECTED;
                    }
                    else if (method.IsFamilyOrAssembly)
                    {
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PROTECTED |
                                     (uint)_LIBCAT_MEMBERACCESS.LCMA_PACKAGE;
                    }
                    else
                    {
                        // Show everything else as internal.
                        pfCatField = (uint)_LIBCAT_MEMBERACCESS.LCMA_PACKAGE;
                    }
                }
                break;

            case LIB_CATEGORY.LC_VISIBILITY:
                pfCatField = (uint)_LIBCAT_VISIBILITY.LCV_VISIBLE;
                break;

            case LIB_CATEGORY.LC_LISTTYPE:
                pfCatField = (uint)_LIB_LISTTYPE.LLT_MEMBERS;
                break;

            default:
                return Microsoft.VisualStudio.VSConstants.S_FALSE;
        }
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> 메서드를 구현 하여 지정된 목록 항목의 텍스트 표현을 가져옵니다. 다음 예제에서는 지정된 항목의 전체 이름을 가져오는 방법을 보여 줍니다.

    ```vb
    Public Function GetTextWithOwnership(<System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.ULONG")> ByVal index As UInteger, <System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS")> ByVal tto As Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS, <System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.WCHAR")> ByRef ppszText As String) As Integer
        ppszText = m_Methods.Values(CInt(Fix(index))).FullName
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int GetTextWithOwnership([System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.ULONG")] uint index, [System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS")] Microsoft.VisualStudio.Shell.Interop.VSTREETEXTOPTIONS tto, [System.Runtime.InteropServices.ComAliasNameAttribute("Microsoft.VisualStudio.OLE.Interop.WCHAR")] out string ppszText)
    {
        ppszText = m_Methods.Values[(int)index].FullName;
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> 메서드를 구현 하여 지정된 목록 항목에 대한 아이콘 정보를 가져옵니다. 아이콘은 목록 항목의 유형(클래스, 메서드 등) 및 접근성(개인, 공용 등)을 나타냅니다. 다음 예제에서는 지정된 항목 특성을 기반으로 아이콘 정보를 가져오는 방법을 보여 줍니다.

    ```vb
    Public Overridable Function GetDisplayData(ByVal index As UInteger, ByVal pData As Microsoft.VisualStudio.Shell.Interop.VSTREEDISPLAYDATA()) As Integer
        If pData Is Nothing Then
            Return Microsoft.VisualStudio.VSConstants.E_INVALIDARG
        End If

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))

        Dim iImage As Integer = 12 * 6 ' See env\inc\OMGlyphs.h.

        Const OM_GLYPH_ACC_PUBLIC As Integer = 0
        Const OM_GLYPH_ACC_INTERNAL As Integer = 1
        Const OM_GLYPH_ACC_PROTECTED As Integer = 3
        Const OM_GLYPH_ACC_PRIVATE As Integer = 4

        If method.IsPublic Then
            iImage += OM_GLYPH_ACC_PUBLIC
        ElseIf method.IsPrivate Then
            iImage += OM_GLYPH_ACC_PRIVATE
        ElseIf method.IsFamily Then
            iImage += OM_GLYPH_ACC_PROTECTED
        ElseIf method.IsFamilyOrAssembly Then
            iImage += OM_GLYPH_ACC_PROTECTED
        Else
            iImage += OM_GLYPH_ACC_INTERNAL
        End If

        pData(0).Image = CUShort(iImage)
        pData(0).SelectedImage = CUShort(iImage)

        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function
    ```

    ```csharp
    public virtual int GetDisplayData(uint index, Microsoft.VisualStudio.Shell.Interop.VSTREEDISPLAYDATA[] pData)
    {
        if (pData == null)
        {
            return Microsoft.VisualStudio.VSConstants.E_INVALIDARG;
        }

        Method method = m_Methods.Values[(int)index];

        int iImage = 12 * 6;    // See env\inc\OMGlyphs.h.

        const int OM_GLYPH_ACC_PUBLIC = 0;
        const int OM_GLYPH_ACC_INTERNAL = 1;
        const int OM_GLYPH_ACC_PROTECTED = 3;
        const int OM_GLYPH_ACC_PRIVATE = 4;

        if (method.IsPublic)
        {
            iImage += OM_GLYPH_ACC_PUBLIC;
        }
        else if (method.IsPrivate)
        {
            iImage += OM_GLYPH_ACC_PRIVATE;
        }
        else if (method.IsFamily)
        {
            iImage += OM_GLYPH_ACC_PROTECTED;
        }
        else if (method.IsFamilyOrAssembly)
        {
            iImage += OM_GLYPH_ACC_PROTECTED;
        }
        else
        {
            iImage += OM_GLYPH_ACC_INTERNAL;
        }

        pData[0].Image = (ushort)iImage;
        pData[0].SelectedImage = (ushort)iImage;

        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    ```

5. 메서드를 구현하여 지정된 목록 항목을 확장할 수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> 있는지 여부에 대한 정보를 가져옵니다. 다음 예제에서는 지정된 항목을 확장할 수 있는지 여부에 대한 정보를 가져오는 방법을 보여 줍니다.

    ```vb
    Public Function GetExpandable(ByVal index As UInteger, ByRef pfExpandable As Integer) As Integer
        pfExpandable = Microsoft.VisualStudio.VSIP.Samples.CallBrowser.Constants.TRUE
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function

    Public Function GetExpandable3(ByVal index As UInteger, ByVal ListTypeExcluded As UInteger, ByRef pfExpandable As Integer) As Integer
        Return GetExpandable(index, pfExpandable)
    End Function
    ```

    ```csharp
    public int GetExpandable(uint index, out int pfExpandable)
    {
        pfExpandable = Microsoft.VisualStudio.VSIP.Samples.CallBrowser.Constants.TRUE;
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    public int GetExpandable3(uint index, uint ListTypeExcluded, out int pfExpandable)
    {
        return GetExpandable(index, out pfExpandable);
    }

    ```

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> 메서드를 구현 하여 지정된 목록 항목의 자식 기호 목록을 가져옵니다. 다음 예제에서는 **통화** 또는 **발신자** 그래프에 대 한 지정된된 항목의 기호의 자식 목록을 가져오는 방법을 보여 줍니다.

    ```vb
    ' Call graph list.
    Public Class CallsList
        Inherits ResultsList
        Implements Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
        Public Sub New(ByVal library As Library)
            MyBase.New(library)
        End Sub

        Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
            Return MyBase.GetCallsList(index, ppList)
        End Function
    End Class

    ' Callers graph list.
    Public Class CallersList
        Inherits ResultsList
        Implements Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
        Public Sub New(ByVal library As Library)
            MyBase.New(library)
        End Sub

        Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
            Return MyBase.GetCallersList(index, ppList)
        End Function
    End Class

    ' Call graph list.
    Public Function GetCallsList(ByVal index As UInteger, ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
        ppList = Nothing
        Dim callsList As ResultsList = New CallsList(m_Library)

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))
        Dim strMethod As String = method.m_strPrototype

        Dim Calls As System.Collections.Generic.List(Of CallInstance) = m_Library.CallGraph.GetCallGraph(method)

        For i As Integer = 0 To Calls.Count - 1
            Dim caller As Method = Calls(i).m_Target
            callsList.AddMethod(caller)
        Next i

        ppList = CType(callsList, Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function

    ' Callers graph list.
    Public Function GetCallersList(ByVal index As UInteger, ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
        ppList = Nothing
        Dim callersList As ResultsList = New CallersList(m_Library)

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))
        Dim strMethod As String = method.m_strPrototype

        Dim Callers As System.Collections.Generic.List(Of CallInstance) = m_Library.CallGraph.GetCallersGraph(method)

        For i As Integer = 0 To Callers.Count - 1
            Dim caller As Method = Callers(i).m_Source
            callersList.AddMethod(caller)
        Next i

        ppList = CType(callersList, Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)
        Return Microsoft.VisualStudio.VSConstants.S_OK
    End Function

    ' Get a child list of symbols for a given list item.
    Public Function GetList2(ByVal index As UInteger, ByVal ListType As UInteger, ByVal flags As UInteger, ByVal pobSrch As Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2(), ByRef ppList As Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2) As Integer
        ppList = Nothing

        Dim method As Method = m_Methods.Values(CInt(Fix(index)))
        Dim strMethod As String = method.m_strPrototype

        ' Determine if the list belongs to Call or Callers graphs.
        If CUInt(m_nFlags And CUInt(Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSFROM)) > 0 Then
            ' Build the list for the Call graph.
            Return MyBase.GetCallsList(index, ppList)
        ElseIf CUInt(m_nFlags And CUInt(Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSTO)) > 0 Then
            ' Build the list for the Callers graph.
            Return MyBase.GetCallersList(index, ppList)
        End If

        Return Microsoft.VisualStudio.VSConstants.E_FAIL
    End Function
    ```

    ```csharp
    // Call graph list.
    public class CallsList :
        ResultsList,
        Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
    {
        public CallsList(Library library) :
            base(library)
        {
        }

        public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
        {
            return base.GetCallsList(index, out ppList);
        }
    }

    // Callers graph list.
    public class CallersList :
        ResultsList,
        Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2
    {
        public CallersList(Library library) :
            base(library)
        {
        }

        public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
        {
            return base.GetCallersList(index, out ppList);
        }
    }

    // Call graph list.
    public int GetCallsList(uint index, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
    {
        ppList = null;
        ResultsList callsList = new CallsList(m_Library);

        Method method = m_Methods.Values[(int)index];
        string strMethod = method.m_strPrototype;

        System.Collections.Generic.List<CallInstance> Calls = m_Library.CallGraph.GetCallGraph(method);

        for (int i = 0; i < Calls.Count; i++)
        {
            Method caller = Calls[i].m_Target;
            callsList.AddMethod(caller);
        }

        ppList = (Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)(callsList);
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    // Callers graph list.
    public int GetCallersList(uint index, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
    {
        ppList = null;
        ResultsList callersList = new CallersList(m_Library);

        Method method = m_Methods.Values[(int)index];
        string strMethod = method.m_strPrototype;

        System.Collections.Generic.List<CallInstance> Callers = m_Library.CallGraph.GetCallersGraph(method);

        for (int i = 0; i < Callers.Count; i++)
        {
            Method caller = Callers[i].m_Source;
            callersList.AddMethod(caller);
        }

        ppList = (Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2)(callersList);
        return Microsoft.VisualStudio.VSConstants.S_OK;
    }

    // Get a child list of symbols for a given list item.
    public int GetList2(uint index, uint ListType, uint flags, Microsoft.VisualStudio.Shell.Interop.VSOBSEARCHCRITERIA2[] pobSrch, out Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2 ppList)
    {
        ppList = null;

        Method method = m_Methods.Values[(int)index];
        string strMethod = method.m_strPrototype;

        // Determine if the list belongs to Call or Callers graphs.
        if ((uint)(m_nFlags & (uint)Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSFROM) > 0)
        {
            // Build the list for the Call graph.
            return base.GetCallsList(index, out ppList);
        }
        else if ((uint)(m_nFlags & (uint)Microsoft.VisualStudio.Shell.Interop._VSOBSEARCHOPTIONS2.VSOBSO_CALLSTO) > 0)
        {
            // Build the list for the Callers graph.
            return base.GetCallersList(index, out ppList);
        }

        return Microsoft.VisualStudio.VSConstants.E_FAIL;
    }

    ```

## <a name="see-also"></a>참조
- [심볼 브라우징 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [방법: 개체 관리자와 라이브러리 등록](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [방법: 라이브러리에서 기호 식별](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
- [레거시 언어 서비스 확장성](../../extensibility/internals/legacy-language-service-extensibility.md)
