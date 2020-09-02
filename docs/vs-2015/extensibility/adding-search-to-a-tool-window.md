---
title: 도구 창에 검색 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 81043cc87dd659f14ec634dc14990956a0864f9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66263573"
---
# <a name="adding-search-to-a-tool-window"></a>도구 창에 검색 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

확장에서 도구 창을 만들거나 업데이트 하는 경우 Visual Studio의 다른 위치에 표시 되는 것과 동일한 검색 기능을 추가할 수 있습니다. 이 기능에는 다음과 같은 기능이 포함 됩니다.  
  
- 항상 도구 모음의 사용자 지정 영역에 있는 검색 상자입니다.  
  
- 검색 상자 자체에 겹쳐서 표시 되는 진행률 표시기입니다.  
  
- 각 문자 (즉시 검색)를 입력 하는 즉시 또는 Enter 키 (요청 시 검색)를 선택한 후에만 결과를 표시 하는 기능입니다.  
  
- 가장 최근에 검색 한 용어를 표시 하는 목록입니다.  
  
- 검색 대상의 특정 필드나 측면을 기준으로 검색을 필터링 하는 기능입니다.  
  
  이 연습을 수행 하 여 다음 작업을 수행 하는 방법을 배웁니다.  
  
1. VSPackage 프로젝트를 만듭니다.  
  
2. 읽기 전용 TextBox를 사용 하 여 UserControl을 포함 하는 도구 창을 만듭니다.  
  
3. 도구 창에 검색 상자를 추가 합니다.  
  
4. 검색 구현을 추가 합니다.  
  
5. 즉시 검색을 사용 하 고 진행률 표시줄을 표시 합니다.  
  
6. **대/소문자 구분** 옵션을 추가 합니다.  
  
7. 검색을 추가 합니다. **줄만** 필터를 추가 합니다.  
  
## <a name="to-create-a-vsix-project"></a>VSIX 프로젝트를 만들려면  
  
1. `TestToolWindowSearch` **Testsearch**라는 도구 창을 사용 하 여 라는 VSIX 프로젝트를 만듭니다. 이 작업에 대한 도움이 필요한 경우 [Creating an Extension with a Tool Window](../extensibility/creating-an-extension-with-a-tool-window.md)를 참조하세요.  
  
## <a name="to-create-a-tool-window"></a>도구 창을 만들려면  
  
1. 프로젝트에서 `TestToolWindowSearch` TestSearchControl .xaml 파일을 엽니다.  
  
2. 기존 블록을 `<StackPanel>` 다음 블록으로 바꿉니다 .이 블록은 도구 창의에 읽기 전용을 추가 합니다 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.UserControl> .  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3. TestSearchControl.xaml.cs 파일에서 다음 using 문을 추가 합니다.  
  
    ```csharp  
    using System.Text;  
    ```  
  
4. 메서드를 제거 `button1_Click()` 합니다.  
  
     **Testsearchcontrol** 클래스에서 다음 코드를 추가 합니다.  
  
     이 코드는 <xref:System.Windows.Controls.TextBox> 이름이 **SearchResultsTextBox** 인 Public 속성과 **searchcontent**라는 공용 문자열 속성을 추가 합니다. 생성자에서 SearchResultsTextBox은 입력란으로 설정 되 고 SearchContent는 줄 바꿈 구분 문자열 집합으로 초기화 됩니다. 텍스트 상자의 콘텐츠도 문자열 집합으로 초기화 됩니다.  
  
    ```csharp  
    public partial class TestSearchControl : UserControl  
    {  
        public TextBox SearchResultsTextBox { get; set; }  
        public string SearchContent { get; set; }  
  
        public TestSearchControl()  
        {  
            InitializeComponent();  
  
            this.SearchResultsTextBox = resultsTextBox;  
            this.SearchContent = BuildContent();  
  
            this.SearchResultsTextBox.Text = this.SearchContent;  
        }  
  
        private string BuildContent()  
        {  
            StringBuilder sb = new StringBuilder();  
            sb.AppendLine("1 go");  
            sb.AppendLine("2 good");  
            sb.AppendLine("3 Go");  
            sb.AppendLine("4 Good");  
            sb.AppendLine("5 goodbye");  
            sb.AppendLine("6 Goodbye");  
  
            return sb.ToString();  
        }  
    }  
    ```  
  
     [!code-csharp[ToolWindowSearch#1](../snippets/csharp/VS_Snippets_VBCSharp/toolwindowsearch/cs/mycontrol.xaml.cs#1)]
     [!code-vb[ToolWindowSearch#1](../snippets/visualbasic/VS_Snippets_VBCSharp/toolwindowsearch/vb/mycontrol.xaml.vb#1)]  
  
5. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스가 나타납니다.  
  
6. 메뉴 모음에서 **보기**, **다른 창**, **testsearch**를 선택 합니다.  
  
     도구 창이 나타나지만 검색 컨트롤이 아직 표시 되지 않습니다.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>도구 창에 검색 상자를 추가 하려면  
  
1. TestSearch.cs 파일에서 다음 코드를 클래스에 추가 합니다 `TestSearch` . 코드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> get 접근자가를 반환 하도록 속성을 재정의 합니다 `true` .  
  
     검색을 사용 하려면 속성을 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> . <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>클래스는을 구현 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> 고 검색을 사용 하지 않는 기본 구현을 제공 합니다.  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다.  
  
3. Visual Studio의 실험적 인스턴스에서 **Testsearch**를 엽니다.  
  
     도구 창의 맨 위에 검색 워터 마크와 돋보기 아이콘이 포함 **된 검색 컨트롤이** 나타납니다. 그러나 검색 프로세스가 아직 구현 되지 않았기 때문에 검색은 아직 작동 하지 않습니다.  
  
## <a name="to-add-the-search-implementation"></a>검색 구현을 추가 하려면  
 이전 절차에서와 같이에서 검색을 사용 하도록 설정 하면 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 도구 창이 검색 호스트를 만듭니다. 이 호스트는 항상 백그라운드 스레드에서 발생 하는 검색 프로세스를 설정 하 고 관리 합니다. 클래스는 검색 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 호스트의 생성과 검색을 설정 하는 작업을 관리 하기 때문에 검색 작업만 만들고 검색 방법을 제공 해야 합니다. 검색 프로세스는 백그라운드 스레드에서 발생 하며 도구 창 컨트롤에 대 한 호출은 UI 스레드에서 발생 합니다. 따라서 컨트롤을 처리 하기 위해 수행 하는 모든 호출을 관리 하려면 [Threadhelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) 메서드를 사용 해야 합니다.  
  
1. TestSearch.cs 파일에서 다음 문을 추가 합니다 `using` .  
  
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
  
2. 클래스에서 다음 `TestSearch` 작업을 수행 하는 다음 코드를 추가 합니다.  
  
    - 메서드를 재정의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> 하 여 검색 작업을 만듭니다.  
  
    - 메서드를 재정의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 하 여 텍스트 상자의 상태를 복원 합니다. 사용자가 검색 작업을 취소 하 고 사용자가 옵션 또는 필터를 설정 하거나 설정 취소 하면이 메서드가 호출 됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 는 모두 UI 스레드에서 호출 됩니다. 따라서 [Threadhelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) 메서드를 사용 하 여 텍스트 상자에 액세스할 필요가 없습니다.  
  
    - `TestSearchTask` <xref:Microsoft.VisualStudio.Shell.VsSearchTask> 의 기본 구현을 제공 하는에서 상속 되는 라는 클래스를 만듭니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> .  
  
         에서 `TestSearchTask` 생성자는 도구 창을 참조 하는 전용 필드를 설정 합니다. 검색 메서드를 제공 하려면 및 메서드를 재정의 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> 합니다. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>메서드는 검색 프로세스를 구현 하는 위치입니다. 이 프로세스에는 검색을 수행 하 고, 텍스트 상자에 검색 결과를 표시 하 고, 검색이 완료 되었음을 보고 하기 위해이 메서드의 기본 클래스 구현을 호출 하는 작업이 포함 됩니다.  
  
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
  
3. 다음 단계를 수행 하 여 검색 구현을 테스트 합니다.  
  
    1. 프로젝트를 다시 빌드하고 디버깅을 시작 합니다.  
  
    2. Visual Studio의 실험적 인스턴스에서 도구 창을 다시 열고 검색 창에 일부 검색 텍스트를 입력 한 다음 ENTER 키를 누릅니다.  
  
         올바른 결과가 표시 됩니다.  
  
## <a name="to-customize-the-search-behavior"></a>검색 동작을 사용자 지정 하려면  
 검색 설정을 변경 하 여 검색 컨트롤이 표시 되는 방법과 검색을 수행 하는 방법을 다양 하 게 변경할 수 있습니다. 예를 들어 워터 마크 (검색 상자에 표시 되는 기본 텍스트), 검색 컨트롤의 최소 및 최대 너비 및 진행률 표시줄을 표시할지 여부를 변경할 수 있습니다. 검색 결과가 표시 되기 시작 하는 시점 (주문형 또는 인스턴트 검색)과 최근 검색 된 용어 목록을 표시할지 여부를 변경할 수도 있습니다. 전체 설정 목록은 클래스에서 찾을 수 있습니다 <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> .  
  
1. TestSearch.cs 파일에서 다음 코드를 클래스에 추가 합니다 `TestSearch` . 이 코드는 요청 시 검색 대신 즉시 검색을 사용 하도록 설정 합니다. 즉, 사용자가 ENTER 키를 클릭할 필요가 없습니다. 이 코드는 `ProvideSearchSettings` `TestSearch` 기본 설정을 변경 하는 데 필요한 클래스의 메서드를 재정의 합니다.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2. 솔루션을 다시 빌드하고 디버거를 다시 시작 하 여 새 설정을 테스트 합니다.  
  
     검색 상자에 문자를 입력할 때마다 검색 결과가 표시 됩니다.  
  
3. `ProvideSearchSettings`메서드에서 진행률 표시줄을 표시할 수 있도록 하는 다음 줄을 추가 합니다.  
  
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
  
     진행률 표시줄이 표시 되려면 진행 상황을 보고 해야 합니다. 진행률을 보고 하려면 클래스의 메서드에서 다음 코드의 주석 처리를 제거 합니다 `OnStartSearch` `TestSearchTask` .  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4. 진행률 표시줄이 표시 되는 만큼 처리 속도를 저하 시키려면 클래스의 메서드에서 다음 줄의 주석 처리를 제거 합니다 `OnStartSearch` `TestSearchTask` .  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5. 솔루션을 다시 빌드하고 debugb를 시작 하 여 새 설정을 테스트 합니다.  
  
     검색을 수행할 때마다 검색 창 (검색 텍스트 상자 아래 파란색 선)에 진행률 표시줄이 나타납니다.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>사용자가 검색을 구체화할 수 있도록 하려면  
 **대/소문자 구분** 또는 **전체 단어 일치**등의 옵션을 사용 하 여 사용자가 검색을 구체화할 수 있습니다. 옵션은 확인란과 같이 표시 되는 부울 이거나 단추로 표시 되는 명령입니다. 이 연습에서는 부울 옵션을 만듭니다.  
  
1. TestSearch.cs 파일에서 다음 코드를 클래스에 추가 합니다 `TestSearch` . 이 코드는 메서드를 재정의 합니다 `SearchOptionsEnum` .이 메서드를 사용 하면 검색 구현에서 지정 된 옵션의 설정 또는 해제 여부를 검색할 수 있습니다. 의 코드는 `SearchOptionsEnum` 대/소문자를 열거자와 일치 시키는 옵션을 추가 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> . 케이스를 일치 시키는 옵션도 속성으로 사용할 수 있습니다 `MatchCaseOption` .  
  
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
  
2. 클래스의 `TestSearchTask` 메서드에서 matchCase 줄의 주석 처리를 제거 합니다 `OnStartSearch` .  
  
    ```csharp  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
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
  
3. 옵션을 테스트 합니다.  
  
    1. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스가 나타납니다.  
  
    2. 도구 창에서 텍스트 상자의 오른쪽에 있는 아래쪽 화살표를 선택 합니다.  
  
         **대/소문자 구분** 확인란이 표시 됩니다.  
  
    3. **대/소문자 구분** 확인란을 선택 하 고 검색을 수행 합니다.  
  
## <a name="to-add-a-search-filter"></a>검색 필터를 추가 하려면  
 사용자가 검색 대상 집합을 구체화할 수 있도록 하는 검색 필터를 추가할 수 있습니다. 예를 들어 파일 탐색기에서 가장 최근에 수정 된 날짜 및 파일 이름 확장명을 기준으로 파일을 필터링 할 수 있습니다. 이 연습에서는 짝수 줄에 대해서만 필터를 추가 합니다. 사용자가 해당 필터를 선택 하면 검색 호스트가 지정 하는 문자열을 검색 쿼리에 추가 합니다. 검색 메서드 내에서 이러한 문자열을 식별 하 고 그에 따라 검색 대상을 필터링 할 수 있습니다.  
  
1. TestSearch.cs 파일에서 다음 코드를 클래스에 추가 합니다 `TestSearch` . 이 코드는 `SearchFiltersEnum` <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> 짝수 줄만 표시 되도록를 지정 하는를 추가 하 여를 구현 합니다.  
  
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
  
     이제 검색 컨트롤이 검색 필터를 표시 합니다 `Search even lines only` . 사용자가 필터를 선택 하면 `lines:"even"` 검색 상자에 문자열이 표시 됩니다. 다른 검색 조건은 필터와 동시에 표시 될 수 있습니다. 검색 문자열은 필터 앞, 필터 또는 양쪽 모두에 나타날 수 있습니다.  
  
2. TestSearch.cs 파일에서 클래스에 있는 클래스에 다음 메서드를 추가 합니다 `TestSearchTask` `TestSearch` . 이러한 메서드는 `OnStartSearch` 다음 단계에서 수정할 수 있는 메서드를 지원 합니다.  
  
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
  
3. 클래스에서 `TestSearchTask` `OnStartSearch` 다음 코드를 사용 하 여 메서드를 업데이트 합니다. 이 변경 내용은 필터를 지원 하도록 코드를 업데이트 합니다.  
  
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
  
4. 코드를 테스트 합니다.  
  
5. 프로젝트를 빌드하고 디버깅을 시작합니다. Visual Studio의 실험적 인스턴스에서 도구 창을 열고 검색 컨트롤에서 아래쪽 화살표를 선택 합니다.  
  
     **대/소문자 구분** 확인란 및 **검색 짝수 줄** 필터만 필터를 표시 합니다.  
  
6. 필터를 선택 합니다.  
  
     검색 상자에 **"짝수" 줄**이 포함 되 고 다음과 같은 결과가 나타납니다.  
  
     2 양호  
  
     4 양호  
  
     6  
  
7. `lines:"even"`검색 상자에서 **대/소문자 구분** 확인란을 선택 하 고 `g` 검색 상자에를 입력 합니다.  
  
     다음과 같은 결과가 나타납니다.  
  
     1 개 이동  
  
     2 양호  
  
     5  
  
8. 검색 상자의 오른쪽에 있는 X를 선택 합니다.  
  
     검색이 지워지고 원래 내용이 표시 됩니다. 하지만 **대/소문자 구분** 확인란이 계속 선택 되어 있습니다.
