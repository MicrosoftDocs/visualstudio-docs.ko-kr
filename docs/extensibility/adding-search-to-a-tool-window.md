---
title: 도구 창에 검색 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9112a3368ba604c4291f9018e763022e953c4fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740142"
---
# <a name="add-search-to-a-tool-window"></a>도구 창에 검색 추가
확장에서 도구 창을 만들거나 업데이트할 때 Visual Studio의 다른 위치에 나타나는 것과 동일한 검색 기능을 추가할 수 있습니다. 이 기능에는 다음과 같은 기능이 포함됩니다.

- 도구 모음의 사용자 지정 영역에 항상 있는 검색 상자입니다.

- 검색 상자 자체에 중첩된 진행률 표시기입니다.

- 각 문자(즉석 검색)를 입력하거나 **Enter** 키(주문형 검색)를 선택한 후에만 결과를 표시할 수 있습니다.

- 가장 최근에 검색한 용어를 표시하는 목록입니다.

- 검색 대상의 특정 필드 또는 측면별로 검색을 필터링하는 기능입니다.

이 연습에 따라 다음 작업을 수행하는 방법을 배웁니다.

1. VSPackage 프로젝트를 만듭니다.

2. 읽기 전용 텍스트 상자를 사용하여 UserControl이 포함된 도구 창을 만듭니다.

3. 도구 창에 검색 상자를 추가합니다.

4. 검색 구현을 추가합니다.

5. 진행률 표시줄의 즉각적인 검색 및 표시를 활성화합니다.

6. 사례 **일치** 옵션을 추가합니다.

7. 검색 **짝수 줄만 필터를 추가합니다.**

## <a name="to-create-a-vsix-project"></a>VSIX 프로젝트를 만들려면

1. **테스트 서치라는** `TestToolWindowSearch` 도구 창으로 명명된 VSIX 프로젝트를 만듭니다. 이 작업을 수행하는 데 도움이 필요한 경우 [도구 창을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-tool-window.md)참조하십시오.

## <a name="to-create-a-tool-window"></a>도구 창을 만들려면

1. `TestToolWindowSearch` 프로젝트에서 *TestSearchControl.xaml* 파일을 엽니다.

2. 기존 `<StackPanel>` 블록을 도구 창에 읽기 전용을 <xref:System.Windows.Controls.TextBox> 추가하는 다음 <xref:System.Windows.Controls.UserControl> 블록으로 바꿉습니다.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. *TestSearchControl.xaml.cs* 파일에서 지시문을 사용하여 다음을 추가합니다.

    ```csharp
    using System.Text;
    ```

4. 메서드를 `button1_Click()` 제거합니다.

     **TestSearchControl** 클래스에서 다음 코드를 추가합니다.

     이 코드는 <xref:System.Windows.Controls.TextBox> **SearchResultsTextBox라는** 공용 속성과 SearchContent 라는 공용 문자열 속성을 **추가합니다.** 생성자에서 SearchResultsTextBox는 텍스트 상자로 설정되고 SearchContent는 줄 줄 구분된 문자열 집합으로 초기화됩니다. 텍스트 상자의 내용도 문자열 집합으로 초기화됩니다.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험 인스턴스가 나타납니다.

6. 메뉴 모음에서**다른 Windows** > **테스트 검색** **보기를** > 선택합니다.

     도구 창이 나타나지만 검색 컨트롤이 아직 나타나지 않습니다.

## <a name="to-add-a-search-box-to-the-tool-window"></a>도구 창에 검색 상자를 추가하려면

1. *TestSearch.cs* 파일에서 클래스에 다음 코드를 `TestSearch` 추가합니다. 코드는 get <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> 접근자가 반환되도록 `true`속성을 재정의합니다.

     검색을 사용하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> 속성을 재정의해야 합니다. 클래스는 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> 검색을 사용하도록 설정하지 않는 기본 구현을 구현하고 제공합니다.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

3. Visual Studio의 실험 인스턴스에서 **테스트 검색을**엽니다.

     도구 창 상단에 검색 워터마크와 돋보기 아이콘이 있는 **검색** 컨트롤이 나타납니다. 그러나 검색 프로세스가 구현되지 않았기 때문에 검색이 아직 작동하지 않습니다.

## <a name="to-add-the-search-implementation"></a>검색 구현을 추가하려면
 이전 절차에서와 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>같이 에서 검색을 사용하도록 설정하면 도구 창에서 검색 호스트가 만들어집니다. 이 호스트는 백그라운드 스레드에서 항상 발생하는 검색 프로세스를 설정하고 관리합니다. 클래스는 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 검색 호스트 만들기 및 검색 설정을 관리하므로 검색 작업을 만들고 검색 메서드만 제공하면 됩니다. 검색 프로세스는 백그라운드 스레드에서 발생하며 UI 스레드에서 도구 창 컨트롤에 대한 호출이 발생합니다. 따라서 [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) 메서드를 사용 하 여 컨트롤을 처리 하는 모든 호출을 관리 해야 합니다.

1. *TestSearch.cs* 파일에서 다음 `using` 지시문을 추가합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. `TestSearch` 클래스에서 다음 작업을 수행하는 다음 코드를 추가합니다.

    - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> 검색 작업을 만드는 메서드를 재정의합니다.

    - 텍스트 상자의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 상태를 복원하는 메서드를 재정의합니다. 이 메서드는 사용자가 검색 작업을 취소할 때 와 사용자가 옵션 또는 필터를 설정 하거나 취소 할 때 호출 됩니다. 둘 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 다 UI 스레드에서 호출됩니다. 따라서 [ThreadHelper.Invoke*](https://msdn.microsoft.com/data/ee197798(v=vs.85)) 메서드를 통해 텍스트 상자에 액세스할 필요가 없습니다.

    - 에서 `TestSearchTask` <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>상속하는 <xref:Microsoft.VisualStudio.Shell.VsSearchTask>이름의 클래스를 만듭니다.

         에서 `TestSearchTask`생성자는 도구 창을 참조하는 전용 필드를 설정합니다. 검색 메서드를 제공 하려면 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> 메서드및 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> 메서드를 재정의 합니다. 메서드는 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> 검색 프로세스를 구현하는 위치입니다. 이 프로세스에는 검색 수행, 텍스트 상자에 검색 결과 표시, 이 메서드의 기본 클래스 구현 호출을 수행하여 검색이 완료된 것으로 보고하는 프로세스가 포함됩니다.

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. 다음 단계를 수행하여 검색 구현을 테스트합니다.

    1. 프로젝트를 다시 빌드하고 디버깅을 시작합니다.

    2. Visual Studio의 실험 인스턴스에서 도구 창을 다시 열고 검색 창에 일부 검색 텍스트를 입력하고 **ENTER**를 클릭합니다.

         올바른 결과가 나타납니다.

## <a name="to-customize-the-search-behavior"></a>검색 동작을 사용자 지정하려면
 검색 설정을 변경하여 검색 컨트롤이 표시되는 방식과 검색 수행 방법을 다양하게 변경할 수 있습니다. 예를 들어 워터마크(검색 상자에 표시되는 기본 텍스트), 검색 컨트롤의 최소 및 최대 너비 및 진행률 표시줄 표시줄을 표시할지 여부를 변경할 수 있습니다. 또한 요청 시 또는 즉시 검색에서 검색 결과가 표시되기 시작하는 지점과 최근에 검색한 용어 목록을 표시할지 여부를 변경할 수 있습니다. <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> 클래스에서 전체 설정 목록을 찾을 수 있습니다.

1. * TestSearch.cs* 파일에서 클래스에 다음 `TestSearch` 코드를 추가합니다. 이 코드를 사용하면 온디맨드 검색 대신 즉시 검색할 수 있습니다(사용자가 **ENTER를**클릭할 필요가 없습니다). 코드는 기본 `ProvideSearchSettings` 설정을 변경하는 `TestSearch` 데 필요한 클래스의 메서드를 재정의합니다.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. 솔루션을 다시 빌드하고 디버거를 다시 시작하여 새 설정을 테스트합니다.

     검색 결과에 문자를 입력할 때마다 검색 결과가 표시됩니다.

3. 메서드에서 `ProvideSearchSettings` 진행률 표시줄을 표시할 수 있는 다음 줄을 추가합니다.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     진행률 표시줄이 나타나려면 진행률을 보고해야 합니다. 진행률을 보고하려면 클래스의 메서드에서 `OnStartSearch` 다음 `TestSearchTask` 코드의 주석을 주석 해제합니다.

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. 진행률 표시줄이 표시될 정도로 처리 속도를 늦추려면 `OnStartSearch` 클래스의 `TestSearchTask` 메서드에서 다음 줄의 주석을 해제합니다.

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. 솔루션을 다시 빌드하고 디버깅을 시작하여 새 설정을 테스트합니다.

     검색창은 검색을 수행할 때마다 검색 창(검색 텍스트 상자 아래의 파란색 선)에 나타납니다.

## <a name="to-enable-users-to-refine-their-searches"></a>사용자가 검색을 구체화할 수 있도록 하려면
 사용자가 **일치 사례** 또는 **전체 단어 일치와**같은 옵션을 사용하여 검색을 구체화하도록 허용할 수 있습니다. 옵션은 확인란으로 표시되는 부울 또는 단추로 표시되는 명령일 수 있습니다. 이 연습에서는 부울 옵션을 만듭니다.

1. *TestSearch.cs* 파일에서 클래스에 다음 코드를 `TestSearch` 추가합니다. 코드는 메서드를 `SearchOptionsEnum` 재정의하여 검색 구현에서 지정된 옵션이 켜졌는지 또는 꺼져 있는지 여부를 검색할 수 있습니다. 의 `SearchOptionsEnum` 코드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> 케이스를 열거형에 일치하는 옵션을 추가합니다. 케이스와 일치하는 옵션도 `MatchCaseOption` 속성으로 사용할 수 있습니다.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. `TestSearchTask` 클래스에서 메서드에서 다음 줄의 `OnStartSearch` 주석을 주석 해제합니다.

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. 다음 옵션을 테스트합니다.

    1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스가 나타납니다.

    2. 도구 창에서 텍스트 상자의 오른쪽에 있는 아래쪽 화살표를 선택합니다.

         **케이스 일치** 확인란이 나타납니다.

    3. 케이스 **일치** 확인란을 선택한 다음 일부 검색을 수행합니다.

## <a name="to-add-a-search-filter"></a>검색 필터를 추가하려면
 사용자가 검색 대상 집합을 구체화할 수 있도록 검색 필터를 추가할 수 있습니다. 예를 들어 파일 탐색기에서 파일을 가장 최근에 수정한 날짜와 파일 이름 확장명으로 필터링할 수 있습니다. 이 연습에서는 짝수 줄에 대해서만 필터를 추가합니다. 사용자가 해당 필터를 선택하면 검색 호스트는 검색 쿼리에 지정한 문자열을 추가합니다. 그런 다음 검색 메서드 내에서 이러한 문자열을 식별하고 그에 따라 검색 대상을 필터링할 수 있습니다.

1. *TestSearch.cs* 파일에서 클래스에 다음 코드를 `TestSearch` 추가합니다. 코드는 검색 `SearchFiltersEnum` 결과를 <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> 필터링하도록 지정하는 것을 추가하여 줄만 표시되도록 구현합니다.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     이제 검색 컨트롤에 검색 `Search even lines only`필터가 표시됩니다. 사용자가 필터를 선택하면 문자열이 `lines:"even"` 검색 상자에 나타납니다. 다른 검색 기준은 필터와 동시에 나타날 수 있습니다. 검색 문자열은 필터 앞, 필터 다음 또는 둘 다 나타날 수 있습니다.

2. *TestSearch.cs* 파일에서 클래스에 있는 클래스에 `TestSearchTask` 다음 메서드를 `TestSearch` 추가합니다. 이러한 메서드는 `OnStartSearch` 다음 단계에서 수정할 메서드를 지원합니다.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. `TestSearchTask` 클래스에서 `OnStartSearch` 다음 코드로 메서드를 업데이트합니다. 이 변경 사항은 필터를 지원하도록 코드를 업데이트합니다.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. 코드를 테스트합니다.

5. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험 인스턴스에서 도구 창을 연 다음 검색 컨트롤에서 아래쪽 화살표를 선택합니다.

     **일치 케이스** 확인란과 **검색 짝수 줄 필터만** 나타납니다.

6. 필터를 선택합니다.

     검색 **상자에는 줄이 포함되어 있습니다: "짝수",** 다음 결과가 나타납니다.

     2 좋은

     4 좋

     6 작별 인사

7. 검색 `lines:"even"` 상자에서 삭제하고 **사례 일치** 확인란을 `g` 선택한 다음 검색 상자에 입력합니다.

     다음 결과가 나타납니다.

     1 이동

     2 좋은

     5 작별 인사

8. 검색 상자의 오른쪽에 있는 X를 선택합니다.

     검색이 지워지고 원본 내용이 나타납니다. 그러나 **대/소문자 일치** 확인란은 여전히 선택되어 있습니다.
