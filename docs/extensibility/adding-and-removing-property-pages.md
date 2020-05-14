---
title: 속성 페이지 추가 및 제거 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- property pages, adding
- property pages, project subtypes
- property pages, removing
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 4c3df3104e48ca0ee972e1a27f2c32fd0661088b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740210"
---
# <a name="add-and-remove-property-pages"></a>속성 페이지 추가 및 제거

프로젝트 디자이너는 에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]프로젝트 속성, 설정 및 리소스를 관리하기 위한 중앙 집중식 위치를 제공합니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 통합 개발 환경(IDE)의 단일 창으로 나타나며 왼쪽의 탭을 통해 액세스되는 오른쪽의 여러 창이 포함되어 있습니다. 프로젝트 디자이너의 창(속성 페이지라고도 함)은 프로젝트 유형 및 언어에 따라 다릅니다. 프로젝트 디자이너는 **프로젝트** 메뉴에서 **속성** 명령을 통해 액세스할 수 있습니다.

프로젝트 하위 유형은 프로젝트 디자이너에 추가 속성 페이지를 표시해야 하는 경우가 종종 있습니다. 마찬가지로 일부 프로젝트 하위 유형에서는 기본 제공 속성 페이지를 제거해야 할 수 있습니다. 둘 중 하나를 수행하려면 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 하위 유형이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 인터페이스를 구현하고 메서드를 재정의해야 합니다. 이 메서드를 재정의하고 `propId` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 열거값 중 하나를 포함하는 매개 변수를 사용하여 프로젝트 속성을 필터링, 추가 또는 제거할 수 있습니다. 예를 들어 구성 종속 속성 페이지에 페이지를 추가해야 할 수 있습니다. 이렇게 하려면 구성 종속 속성 페이지를 필터링한 다음 기존 목록에 새 페이지를 추가해야 합니다.

## <a name="add-and-remove-property-pages-in-project-designer"></a>프로젝트 디자이너의 속성 페이지 추가 및 제거

### <a name="remove-a-property-page"></a>속성 페이지 제거

1. 속성 페이지를 `GetProperty(uint itemId, int propId, out object property)` 필터링하고 목록을 가져오는 `clsids` 메서드를 재정의합니다.

    ```vb
    Protected Overrides int GetProperty(uint itemId, int propId, out object property)
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer
        'Use propId to filter configuration-independent property pages.
        Select Case propId
            ....
            Case CInt(Fix(__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList))
                'Get a semicolon-delimited list of clsids of the configuration-independent property pages
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))
                   Dim propertyPagesList As String = ((String)[property]).ToUpper(CultureInfo.InvariantCulture)
                'Remove the property page here
                   ....
            ....
        End Select
            ....
        Return MyBase.GetProperty(itemId, propId, [property])
    End Function

    ```

    ```csharp
    protected override int GetProperty(uint itemId, int propId, out object property)
    {
        //Use propId to filter configuration-independent property pages.
        switch (propId)
        {
            . . . .

            case (int)__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList:
                {
                    //Get a semicolon-delimited list of clsids of the configuration-independent property pages
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));
                    string propertyPagesList = ((string)property).ToUpper(CultureInfo.InvariantCulture);
                    //Remove the property page here
                    . . . .
                }
             . . . .
         }
            . . . .
        return base.GetProperty(itemId, propId, out property);
    }
    ```

2. 가져온 목록에서 **이벤트 빌드** `clsids` 페이지를 제거합니다.

    ```vb
    Private buildEventsPageGuid As String = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}"
    Private index As Integer = propertyPagesList.IndexOf(buildEventsPageGuid)
    If index <> -1 Then
        ' GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'
        Dim index2 As Integer = index + buildEventsPageGuid.Length + 1
        If index2 >= propertyPagesList.Length Then
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(";"c)
        Else
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2)
        End If
    End If
    'New property value
    property = propertyPagesList
    ```

    ```csharp
    string buildEventsPageGuid = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}";
    int index = propertyPagesList.IndexOf(buildEventsPageGuid);
    if (index != -1)
    {
        // GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'
        int index2 = index + buildEventsPageGuid.Length + 1;
        if (index2 >= propertyPagesList.Length)
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(';');
        else
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2);
    }
    //New property value
    property = propertyPagesList;
    ```

### <a name="add-a-property-page"></a>속성 페이지 추가

1. 추가할 속성 페이지를 만듭니다.

    ```vb
    Class DeployPropertyPage
            Inherits Form
            Implements Microsoft.VisualStudio.OLE.Interop.IPropertyPage
        'Summary: Return a stucture describing your property page.
        ....
        Public Sub GetPageInfo(ByVal pPageInfo As Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO())
            Dim info As PROPPAGEINFO = New PROPPAGEINFO()
            info.cb = CUInt(Marshal.SizeOf(GetType(PROPPAGEINFO)))
            info.dwHelpContext = 0
            info.pszDocString = Nothing
            info.pszHelpFile = Nothing
            info.pszTitle = "Deployment" 'Assign tab name
            info.SIZE.cx = Me.Size.Width
            info.SIZE.cy = Me.Size.Height
            If Not pPageInfo Is Nothing AndAlso pPageInfo.Length > 0 Then
                pPageInfo(0) = info
            End If
        End Sub
    End Class
    ```

    ```csharp
    class DeployPropertyPage : Form, Microsoft.VisualStudio.OLE.Interop.IPropertyPage
    {
        . . . .
        //Summary: Return a stucture describing your property page.
        public void GetPageInfo(Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO[] pPageInfo)
        {
            PROPPAGEINFO info = new PROPPAGEINFO();
            info.cb = (uint)Marshal.SizeOf(typeof(PROPPAGEINFO));
            info.dwHelpContext = 0;
            info.pszDocString = null;
            info.pszHelpFile = null;
            info.pszTitle = "Deployment";  //Assign tab name
            info.SIZE.cx = this.Size.Width;
            info.SIZE.cy = this.Size.Height;
            if (pPageInfo != null && pPageInfo.Length > 0)
                pPageInfo[0] = info;
        }
    }
    ```

2. 새 속성 페이지를 등록합니다.

    ```vb
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>
    ```

    ```csharp
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]
    ```

3. 속성을 필터링하고 `GetProperty(uint itemId, int propId, out object property)` `clsids` 목록을 가져오고 새 속성 페이지를 추가하는 메서드를 재정의합니다.

    ```vb
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer
        'Use propId to filter configuration-dependent property pages.
        Select Case propId
            ....
            case CInt(Fix(__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList)):
                'Get a semicolon-delimited list of clsids of the configuration-dependent property pages.
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))
                'Add the Deployment property page.
                [property] &= ";"c + GetType(DeployPropertyPage).GUID.ToString("B")
        End Select
            ....
            Return MyBase.GetProperty(itemId, propId, [property])
    End Function
    ```

    ```csharp
    protected override int GetProperty(uint itemId, int propId, out object property)
    {
        //Use propId to filter configuration-dependent property pages.
        switch (propId)
        {
            . . . .
            case (int)__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList:
                {
                    //Get a semicolon-delimited list of clsids of the configuration-dependent property pages.
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));
                    //Add the Deployment property page.
                    property += ';' + typeof(DeployPropertyPage).GUID.ToString("B");
                }
         }
            . . . .
        return base.GetProperty(itemId, propId, out property);
    }
    ```

## <a name="see-also"></a>참조

- [프로젝트 하위 유형](../extensibility/internals/project-subtypes.md)
