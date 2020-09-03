---
title: Windows 유니버설 앱에서 CPU 사용량 분석 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: def581f547db19a8db4cebc4d63739ff09bb5fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531666"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Windows 유니버설 앱에서 CPU 사용량 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 및 Windows Phone]에 적용 됩니다. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 앱 성능 문제를 검토해야 하는 경우 앱에서 CPU를 사용하는 방식을 파악하는 것부터 시작하는 것이 좋습니다. **CPU 사용량** 도구는 CPU가 코드 실행 시간을 어디에 소모하는지를 보여 줍니다. 특정 시나리오에 초점을 맞추기 위해 단일 진단 세션에서 [XAML UI 응답성](https://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) 도구, [cpu 사용량 도구](../profiling/cpu-usage.md) 도구 또는 두 도구를 사용 하 여 cpu 사용량을 실행할 수 있습니다.  
  
> [!NOTE]
> **CPU 사용량** 도구는 Windows Phone Silverlight 8.1 앱과 함께 사용할 수 없습니다.  
  
 이 연습에서는 간단한 Windows 유니버설 XAML 앱의 CPU 사용량을 수집 및 분석하는 방법을 설명합니다.  
  
## <a name="create-the-cpuusedemo-project"></a><a name="BKMK_Create_the_CpuUseDemo_project"></a> CpuUseDemo 프로젝트 만들기  
 **CpuUseDemo**는 CPU 사용량 데이터를 수집 및 분석하는 방법을 보여 주기 위해 만든 앱입니다. 단추는 함수에 대한 여러 호출에서 최대값을 선택하는 메서드를 호출하여 숫자를 생성합니다. 호출된 함수는 임의의 값을 굉장히 많이 만든 다음 마지막 값을 반환합니다. 데이터는 텍스트 상자에 표시됩니다.  
  
1. **BlankApp** 템플릿을 사용하여 **CpuUseDemo**라는 새로운 C# Windows 유니버설 앱을 만듭니다.  
  
     ![CpuUseDemoProject 만들기](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2. MainPage.xaml을 [이 코드](#BKMK_MainPage_xaml)로 바꿉니다.  
  
3. MainPage.xaml.cs를 [이 코드](#BKMK_MainPage_xaml_cs)로 바꿉니다.  
  
4. 앱을 빌드하고 사용해 보세요. 앱은 CPU 사용 데이터 분석의 일반적인 사례를 보여 줄 수 있을 정도로 간단 합니다.  
  
## <a name="collect-cpu-usage-data"></a><a name="BKMK_Collect_CPU_usage_data"></a> CPU 사용량 데이터 수집  
 ![시뮬레이터에서 앱의 릴리스 빌드 실행](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1. Visual Studio에서 배포 대상을 **시뮬레이터**로, 솔루션 구성을 **릴리스**로 설정합니다.  
  
   - 시뮬레이터에서 앱을 실행하면 앱과 Visual Studio IDE를 서로 쉽게 전환할 수 있습니다.  
  
   - **릴리스** 모드에서 이 앱을 실행하면 앱의 실제 성능을 더 잘 파악할 수 있습니다.  
  
2. **디버그** 메뉴에서 **성능 프로파일러...** 를 선택합니다.  
  
3. 성능 및 진단 허브에서 **CPU 사용량**을 선택한 다음 **시작**을 선택합니다.  
  
    ![CpuUsage 진단 세션 시작](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4. 앱이 시작되면 **최대 수 가져오기**를 클릭합니다. 출력이 표시되면 약 1초간 기다린 다음 **Get Max Number Async**(비동기적으로 최대 수 가져오기)를 선택합니다. 단추를 클릭하는 시간 사이에 대기하면 진단 보고서에서 단추 클릭 루틴을 좀 더 쉽게 격리할 수 있습니다.  
  
5. 두 번째 출력 줄이 나타나면 성능 및 진단 허브에서 **수집 중지** 를 선택합니다.  
  
   ![CpuUsage 데이터 컬렉션 중지](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   CPU 사용량 도구에서 데이터를 분석하고 보고서를 표시합니다.  
  
   ![CpuUsage 보고서](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="analyze-the-cpu-usage-report"></a><a name="BKMK_Analyze_the_CPU_Usage_report"></a> CPU 사용량 보고서 분석  
  
### <a name="cpu-utilization-timeline-graph"></a><a name="BKMK_CPU_utilization_timeline_graph"></a> CPU 사용률 타임라인 그래프  
 ![CpuUtilization &#40;% &#41; 타임 라인 그래프](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 CPU 사용률 그래프는 디바이스의 모든 프로세서 코어에서의 전체 CPU 시간 백분율로 앱의 CPU 활동을 보여 줍니다. 이 보고서의 데이터는 듀얼 코어 컴퓨터에서 수집되었습니다. 대용량 스파이크 두 개는 단추를 두 번 클릭할 경우의 CPU 활동을 보여 줍니다. `GetMaxNumberButton_Click`은 단일 코어에서 동기적으로 수행되므로 메서드 그래프의 높이가 50%를 초과하지 않습니다. `GetMaxNumberAsycButton_Click`은 두 코어에서 비동기적으로 실행되므로 다시 해당 스파이크가 두 코어에서 거의 모든 CPU 리소스를 활용하는 것처럼 보입니다.  
  
#### <a name="select-timeline-segments-to-view-details"></a><a name="BKMK_Select_timeline_segments_to_view_details"></a> 세부 정보를 볼 타임라인 세그먼트 선택  
 **진단 세션** 타임라인에서 선택 막대를 사용하여 GetMaxNumberButton_Click 데이터에 초점을 맞춥니다.  
  
 ![Getmax번호 단추&#95;선택 클릭](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 이제 **진단 세션** 타임라인은 선택한 세그먼트에 소요된 시간을 표시(이 보고서에서는 2초보다 약간 김)하고 선택 세그먼트에서 실행된 해당 메서드에 대한 호출 트리를 필터링합니다.  
  
 여기에서 `GetMaxNumberAsyncButton_Click` 세그먼트를 선택합니다.  
  
 ![Getmax번호 Asyncbutton&#95;보고서 선택 영역 클릭](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 이 메서드는 `GetMaxNumberButton_Click`보다 약 1초 더 빨리 완료되었지만 호출 트리 항목의 의미는 덜 명확합니다.  
  
### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> CPU 사용량 호출 트리  
 호출 트리 정보 파악을 시작하려면 `GetMaxNumberButton_Click` 세그먼트를 다시 선택하고 호출 트리 세부 정보를 확인합니다.  
  
#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> 호출 트리 구조  
 ![Getmax번호 단추&#95;클릭 호출 트리](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|이미지|설명|  
|-|-|  
|![1단계](../profiling/media/procguid-1.png "ProcGuid_1")|CPU 사용량 호출 트리의 최상위 노드는 의사 노드입니다.|  
|![2단계](../profiling/media/procguid-2.png "ProcGuid_2")|대다수 앱에서 **외부 코드 포시** 옵션이 사용하지 않도록 설정되어 있는 경우 두 번째 수준 노드는 앱을 시작/중지하고, UI를 그리며, 스레드 일정을 제어하고, 앱에 다른 낮은 수준 서비스를 제공하는 시스템과 프레임워크 코드가 포함된 **[External Code]** 노드입니다.|  
|![3단계](../profiling/media/procguid-3.png "ProcGuid_3")|두 번째 수준 노드의 자식은 두 번째 수준 시스템과 프레임워크 코드가 호출하거나 만드는 사용자 코드 메서드 및 비동기 루틴입니다.|  
|![4단계](../profiling/media/procguid-4.png "ProcGuid_4")|메서드의 자식 노드에는 부모 메서드 호출에 대한 데이터만 포함되어 있습니다. **외부 코드 표시** 가 사용하지 않도록 설정되어 있으면 앱 메서드에 **[External Code]** 노드를 포함할 수 있습니다.|  
  
#### <a name="external-code"></a><a name="BKMK_External_Code"></a> 외부 코드  
 외부 코드는 사용자가 작성한 코드에서 실행된 시스템 및 프레임워크 구성 요소의 함수로 구성됩니다. 외부 코드에는 앱을 시작 및 중지하고, UI를 그리며, 스레딩을 제어하고, 앱에 다른 낮은 수준 서비스를 제공하는 함수가 포함되어 있습니다. 대부분의 경우 외부 코드에 관심이 없으므로 CPU 사용량 호출 트리에서 사용자 메서드의 외부 함수를 하나의 **[External code]** 노드로 수집 합니다.  
  
 외부 코드의 호출 경로를 보려면 **필터 뷰** 목록에서 **외부 코드 보기** 를 선택한 다음 **적용**을 선택합니다.  
  
 ![필터 뷰 선택 후 외부 코드 표시](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 여러 외부 코드 호출 체인은 깊이 중첩되어 있으므로 함수 이름 열의 너비가 컴퓨터 모니터의 거의 최대 화면 너비를 초과할 수 있습니다. 이런 경우 함수 이름은 다음과 같이 **[...]** 로 표시 됩니다.  
  
 ![호출 트리에 중첩된 외부 코드](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 검색 상자를 사용하여 검색 중인 노드를 찾은 다음, 가로 스크롤 막대를 사용하여 데이터를 뷰로 가져옵니다.  
  
 ![중첩된 외부 코드 검색](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="call-tree-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> 호출 트리 데이터 열  
  
|속성|설명|  
|-|-|  
|**총 CPU(%)**|![총 % 데이터 수식](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> 함수 호출 및 함수가 호출한 함수에 사용된 선택한 시간 범위의 앱 CPU 활동에 대한 백분율입니다. 이 값은 시간 범위에서 앱의 총 활동을 사용 가능한 총 CPU 용량과 비교하는 **CPU 사용률** 타임라인 그래프와 다릅니다.|  
|**셀프 CPU(%)**|![자체 % 수식](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> 함수 호출에 사용된 선택한 시간 범위의 앱 CPU 활동에 대한 백분율로, 함수가 호출한 함수의 활동은 제외됩니다.|  
|**총 CPU(밀리초)**|선택한 시간 범위에서의 함수 호출과 함수가 호출한 함수에 소요된 시간(밀리초)입니다.|  
|**셀프 CPU(밀리초)**|선택한 시간 범위에서의 함수 호출과 함수가 호출한 함수에 소요된 시간(밀리초)입니다.|  
|**모듈**|함수가 포함된 모듈의 이름 또는 [External Code] 노드에 함수가 포함된 모듈의 수입니다.|  
  
### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> CPU 사용량 호출 트리의 비동기 함수  
 컴파일러에서 비동기 메서드가 발생하면 메서드 실행을 제어하는 숨겨진 클래스를 만듭니다. 개념적으로 클래스는 원래 메서드의 연산을 비동기적으로 호출하고, 이러한 연산에 필요한 콜백, 스케줄러 및 반복기를 올바르게 호출하는 컴파일러 생성 함수 목록을 포함하는 상태 시스템입니다. 부모 메서드가 원래 메서드를 호출하면 런타임에서 부모의 실행 컨텍스트에서 메서드를 제거하고, 앱의 실행을 제어하는 시스템과 프레임워크 코드의 컨텍스트에서 숨겨진 클래스의 메서드를 실행합니다. 비동기 메서드는 일반적으로 하나 이상의 서로 다른 스레드에서 실행되지만 항상 그렇지는 않습니다. 이 코드는 트리의 상단 노드 바로 아래의 **[External Code]** 노드의 자식으로 CPU 사용량 호출 트리에 표시됩니다.  
  
 이 예제에서 이 코드를 보려면 타임라인에서 `GetMaxNumberAsyncButton_Click` 세그먼트를 다시 선택합니다.  
  
 ![Getmax번호 Asyncbutton&#95;보고서 선택 영역 클릭](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 **[External Code]** 아래에 있는 처음 두 노드는 상태 시스템 클래스의 컴파일러 생성 메서드입니다. 세 번째 노드는 원래 메서드에 대한 호출입니다. 생성된 메서드를 확장하면 진행 상황이 표시됩니다.  
  
 ![확장 된 Getmax번호 Asyncbutton&#95;클릭 호출 트리](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click` 은 CPU를 매우 조금 사용합니다. 이 메서드는 작업 값 목록을 관리하고, 결과의 최대값을 계산하고, 출력을 표시합니다.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` 는 `GetNumberAsync`에 대한 호출을 래핑하는 48개 작업을 예약 및 시작하는 데 필요한 활동을 보여 줍니다.  
  
- `MainPage::<GetNumberAsync>b__b` 는 `GetNumber`를 호출하는 작업의 활동을 보여 줍니다.  
  
## <a name="next-steps"></a><a name="BKMK_Next_steps"></a> 다음 단계  
 CpuUseDemo 앱이 가장 뛰어나지는 않지만, 성능 및 진단 허브에서 비동기 작업 및 기타 도구로 실험하는 데 사용하여 이 앱의 활용성을 확장할 수 있습니다.  
  
- `MainPage::<GetNumberAsync>b__b`는 GetNumber 메서드를 실행하는 것보다 [External Code]에서 더 많은 시간을 소모합니다. 이러한 시간의 상당 부분은 비동기 작업의 오버헤드가 차지합니다. 작업 수를 늘리고(MainPage.xaml.cs의 `NUM_TASKS` 상수에서 설정) `GetNumber`의 반복 횟수를 줄여 보세요(`MIN_ITERATIONS` 값 변경). 수집 시나리오를 실행하고 `MainPage::<GetNumberAsync>b__b`의 CPU 활동을 원래 CPU 사용량 진단 세션의 CPU 활동과 비교합니다. 작업 수를 줄이고 반복 횟수를 늘려 보세요.  
  
- 사용자는 앱의 실제 성능에는 크게 관심이 없고 앱의 인지 성능과 응답성에 관심 있는 경우가 많습니다. XAML UI 응답성 도구는 인지되는 응답성에 영향을 주는 UI 스레드의 활동 세부 정보를 보여 줍니다.  
  
     진단 및 성능 허브에서 새 세션을 만들고, XAML UI 응답성 도구와 CPU 사용량 도구를 모두 추가합니다. 컬렉션 시나리오를 실행합니다. 여기까지 읽었다면 보고서 내용을 대부분 파악했겠지만, 두 메서드에 대한 **UI 스레드 사용률** 타임라인 그래프의 차이는 현저합니다. 복잡한 실제 앱에서 두 도구를 함께 사용하면 매우 유용할 수 있습니다.  
  
## <a name="mainpagexaml"></a><a name="BKMK_MainPage_xaml"></a> MainPage .xaml  
  
```csharp  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
## <a name="mainpagexamlcs"></a><a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```
