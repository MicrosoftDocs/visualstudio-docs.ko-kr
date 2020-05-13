---
title: 프로젝트 파일에 데이터 저장 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fd6cfaa450bc268665ae0f58109c99002da6152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701350"
---
# <a name="save-data-in-project-files"></a>프로젝트 파일에 데이터 저장
프로젝트 하위 유형은 프로젝트 파일에서 하위 유형별 데이터를 저장하고 검색할 수 있습니다. MPF(관리되는 패키지 프레임워크)는 이 작업을 수행하는 두 가지 인터페이스를 제공합니다.

- 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 사용하면 프로젝트 파일의 **MSBuild** 섹션에서 속성 값에 액세스할 수 있습니다. 사용자가 빌드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 관련 데이터를 로드하거나 저장해야 할 때마다 모든 사용자가 제공하는 메서드를 호출할 수 있습니다.

- 는 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 비 빌드 관련 데이터를 자유 형식 XML에서 유지 하는 데 사용 됩니다. 제공된 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 메서드는 프로젝트 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 파일에서 빌드되지 않은 관련 데이터를 유지해야 할 때마다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 호출됩니다.

  빌드 및 비빌드 관련 데이터를 유지하는 방법에 대한 자세한 내용은 [MSBuild 프로젝트 파일의 데이터 유지를](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)참조하십시오.

## <a name="save-and-retrieve-build-related-data"></a>빌드 관련 데이터 저장 및 검색

### <a name="to-save-a-build-related-data-in-the-project-file"></a>프로젝트 파일에 빌드 관련 데이터를 저장하려면

- 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> 호출하여 프로젝트 파일의 전체 경로를 저장합니다.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string newFullPath = GetNewFullPath();
    // Set a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));
    ```

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>프로젝트 파일에서 빌드 관련 데이터를 검색하려면

- 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> 호출하여 프로젝트 파일의 전체 경로를 검색합니다.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string fullPath;
    // Get a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));
    ```

## <a name="save-and-retrieve-non-build-related-data"></a>비빌드 관련 데이터 저장 및 검색

### <a name="to-save-non-build-related-data-in-the-project-file"></a>프로젝트 파일에 빌드되지 않은 관련 데이터를 저장하려면

1. XML <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> 조각이 현재 파일에 마지막으로 저장된 이후 변경되었는지 여부를 확인하는 메서드를 구현합니다.

    ```
    public int IsFragmentDirty(uint storage, out int pfDirty)
    {
        pfDirty = 0;
        switch (storage)
        {
            case (uint)_PersistStorageType.PST_PROJECT_FILE:
            {
                if (isDirty)
                    pfDirty |= 1;
                break;
            }
            case (uint)_PersistStorageType.PST_USER_FILE:
            {
                // We do not store anything in the user file.
                break;
            }
        }

        // Forward the call to inner flavor(s)
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);

        return VSConstants.S_OK;

    }
    ```

2. 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> 파일에 XML 데이터를 저장하는 메서드를 구현합니다.

    ```
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)
    {
        pbstrXMLFragment = null;

        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Create XML for our data.
                    XmlDocument doc = new XmlDocument();
                    XmlNode root = doc.CreateElement(this.GetType().Name);

                    XmlNode node = doc.CreateElement(targetsTag);
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));
                    root.AppendChild(node);

                    node = doc.CreateElement(updateTargetsTag);
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));
                    root.AppendChild(node);

                    doc.AppendChild(root);
                    // Get XML fragment representing our data
                    pbstrXMLFragment = doc.InnerXml;

                    if (fClearDirty != 0)
                        isDirty = false;
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);

        return VSConstants.S_OK;
    }
    ```

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>프로젝트 파일에서 빌드되지 않은 관련 데이터를 검색하려면

1. 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> 확장 속성 및 기타 빌드 독립적 데이터를 초기화하는 메서드를 구현합니다. 이 메서드는 프로젝트 파일에 XML 구성 데이터가 없는 경우 호출됩니다.

    ```
    public int InitNew(ref Guid guidFlavor, uint storage)
    {
        //Return,if it is our guid.
        if (IsMyFlavorGuid(ref guidFlavor))
            return VSConstants.S_OK;

        //Forward the call to inner flavor(s).
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);

        return VSConstants.S_OK;
    ```

2. 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> 파일에서 XML 데이터를 로드하는 메서드를 구현합니다.

    ```
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)
    {
        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Load our data from the XML fragment.
                    XmlDocument doc = new XmlDocument();
                    XmlNode node = doc.CreateElement(this.GetType().Name);
                    node.InnerXml = pszXMLFragment;
                    if (node == null
                        || node.FirstChild == null
                        || node.FirstChild.ChildNodes.Count == 0
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)
                        break;
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;

                    if (node.FirstChild.ChildNodes.Count <= 1
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)
                        break;
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);

        return VSConstants.S_OK;
    }
    ```

> [!NOTE]
> 이 항목에서 제공되는 모든 코드 예제는 [VSSDK 샘플에서](https://github.com/Microsoft/VSSDK-Extensibility-Samples)더 큰 예제의 일부입니다.

## <a name="see-also"></a>참조
- [MSBuild 프로젝트 파일에 데이터 유지](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
