---
title: 솔루션 탐색기 필터 확장 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af0824edd4188481bec8c0703d71043354f5dbcc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711567"
---
# <a name="extend-the-solution-explorer-filter"></a>솔루션 탐색기 필터 확장
**솔루션 탐색기** 필터 기능을 확장 하 여 다른 파일을 표시 하거나 숨길 수 있습니다. 예를 들어이 연습에서 설명 하는 대로 **솔루션 탐색기**에서 c # 클래스 팩터리 파일만 표시 하는 필터를 만들 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

### <a name="create-a-visual-studio-package-project"></a>Visual Studio 패키지 프로젝트 만들기

1. 이라는 VSIX 프로젝트를 만듭니다 `FileFilter` . **FileFilter**라는 사용자 지정 명령 항목 템플릿을 추가 합니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

2. 및에 대 한 참조를 추가 `System.ComponentModel.Composition` `Microsoft.VisualStudio.Utilities` 합니다.

3. 메뉴 명령이 **솔루션 탐색기** 도구 모음에 표시 되도록 합니다. *Filefilterpackage. vsct* 파일을 엽니다.

4. 블록을 `<Button>` 다음과 같이 변경 합니다.

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>매니페스트 파일 업데이트

1. *Source.extension.vsixmanifest* 파일에서 MEF 구성 요소인 자산을 추가 합니다.

2. **자산** 탭에서 **새로 만들기** 단추를 선택 합니다.

3. **형식** 필드에서 **VisualStudio**를 선택 합니다.

4. **원본** 필드에서 **현재 솔루션의 프로젝트**를 선택 합니다.

5. **프로젝트** 필드에서 **FileFilter**를 선택한 다음 **확인** 단추를 선택 합니다.

### <a name="add-the-filter-code"></a>필터 코드 추가

1. *FileFilterPackageGuids.cs* 파일에 일부 guid를 추가 합니다.

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. *FileNameFilter.cs*이라는 FileFilter 프로젝트에 클래스 파일을 추가 합니다.

3. 빈 네임 스페이스와 빈 클래스를 아래 코드로 바꿉니다.

     `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)`메서드는 솔루션 ()의 루트를 포함 하는 컬렉션을 사용 하 `rootItems` 고 필터에 포함할 항목의 컬렉션을 반환 합니다.

     `ShouldIncludeInFilter`메서드는 지정한 조건에 따라 **솔루션 탐색기** 계층의 항목을 필터링 합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;

    namespace FileFilter
    {
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider
        {
            SVsServiceProvider svcProvider;
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

            // Constructor required for MEF composition
            [ImportingConstructor]
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)
            {
                this.svcProvider = serviceProvider;
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;
            }

            // Returns an instance of Create filter class.
            protected override HierarchyTreeFilter CreateFilter()
            {
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);
            }

            // Regex pattern for CSharp factory classes
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";

            // Implementation of file filtering
            private sealed class FileNameFilter : HierarchyTreeFilter
            {
                private readonly Regex regexp;
                private readonly IServiceProvider svcProvider;
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

                public FileNameFilter(
                    IServiceProvider serviceProvider,
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,
                    string fileNamePattern)
                {
                    this.svcProvider = serviceProvider;
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);
                }

                // Gets the items to be included from this filter provider.
                // rootItems is a collection that contains the root of your solution
                // Returns a collection of items to be included as part of the filter
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)
                {
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(
                                        root.HierarchyIdentity.NestedHierarchy,
                                        CancellationToken);

                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(
                        sourceItems,
                        ShouldIncludeInFilter,
                        CancellationToken);
                    return includedItems;
                }

                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)
                {
                    if (hierarchyItem == null)
                    {
                        return false;
                    }
                    return this.regexp.IsMatch(hierarchyItem.Text);
                }
            }
        }
    }

    ```

4. *FileFilter.cs*에서 명령 배치를 제거 하 고 FileFilter 생성자에서 코드를 처리 합니다. 결과는 다음과 같습니다.

    ```csharp
    private FileFilter(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;
    }
    ```

     메서드도 제거 `ShowMessageBox()` 합니다.

5. *FileFilterPackage.cs*에서 메서드의 코드를 다음 코드로 바꿉니다 `Initialize()` .

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>코드 테스트

1. 프로젝트를 빌드하고 실행합니다. 두 번째 Visual Studio 인스턴스가 표시됩니다. 이를 실험적 인스턴스 라고 합니다.

2. Visual Studio의 실험적 인스턴스에서 c # 프로젝트를 엽니다.

3. **솔루션 탐색기** 도구 모음에서 추가한 단추를 찾습니다. 왼쪽의 네 번째 단추 여야 합니다.

4. 단추를 클릭 하면 모든 파일이 필터링 되어야 하며 **모든 항목이 보기에서 필터링 된** 것을 볼 수 있습니다. **솔루션 탐색기**합니다.
