---
title: '자습서: Azure Functions'
description: Mac용 Visual Studio에서 Azure Functions 사용
author: sayedihashimi
ms.author: sayedha
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.topic: tutorial
ms.openlocfilehash: 99373d7da8c7f83c8703b237ff83c63f9d1b6a53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85939093"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>자습서: Azure Functions 시작

이 연습에서는 Mac용 Visual Studio를 사용하여 Azure Functions 빌드를 시작하는 방법을 알아봅니다. 또한 Azure Functions 개발자가 사용할 수 있는 여러 바인딩 및 트리거 종류 중 하나를 나타내는 Azure 스토리지 테이블에 통합합니다.

## <a name="objectives"></a>목표

> [!div class="checklist"]
> * 로컬 Azure Functions 만들기 및 디버그
> * 웹 및 Azure 스토리지 리소스와 통합
> * 여러 Azure Functions가 포함된 워크플로 조정

## <a name="requirements"></a>요구 사항

- Mac용 Visual Studio 7.5 이상
- Azure 구독([https://azure.com/free](https://azure.com/free?ref=visualstudio)부터 무료로 사용 가능)

## <a name="exercise-1-creating-an-azure-functions-project"></a>연습 1: Azure Functions 프로젝트 만들기

1. **Mac용 Visual Studio**를 시작합니다.

2. **파일 > 새 솔루션**을 선택합니다.

3. **클라우드 > 일반** 범주에서 **Azure Functions** 템플릿을 선택합니다. C#을 사용하여 Azure Functions를 호스트하는 .NET 클래스 라이브러리를 만듭니다. **다음**을 클릭합니다.

    ![Azure Functions 템플릿 선택](media/azure-functions-lab-image1.png)

4. **프로젝트 이름**을 **"AzureFunctionsLab"** 을 설정하고 **만들기**를 클릭합니다.

    ![Azure 함수 프로젝트 이름 지정 및 만들기](media/azure-functions-lab-image2.png)

5. **솔루션 패드**의 노드를 확장합니다. 기본 프로젝트 템플릿에는 Newtonsoft.Json 패키지뿐 아니라 여러 Azure WebJobs 패키지에 대한 NuGet 참조가 포함됩니다.

     또한 호스트에 대한 전역 구성 옵션을 설명하는 **host.json**과, 서비스 설정 구성을 위한 **local.settings.json** 등 3개 파일이 포함됩니다.
        - 프로젝트 템플릿은 기본 HttpTrigger도 만듭니다. 이 연습을 위해 프로젝트에서 **HttpTrigger.cs** 파일을 삭제해야 합니다.

    **local.settings.json**을 엽니다. 기본적으로 두 개의 빈 연결 문자열 설정을 갖습니다.

    ![local.settings.json 파일을 표시하는 솔루션 패드](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>연습 2: Azure 스토리지 계정 만들기

1. [https://portal.azure.com](https://portal.azure.com)에서 Azure 계정에 로그온합니다.

1. **즐겨찾기** 섹션에서 화면 왼쪽에 있는 **스토리지 계정**을 선택합니다.

    ![스토리지 계정 항목을 나타내는 Azure Portal의 즐겨찾기 섹션](media/azure-functions-lab-image4.png)

1. **추가**를 선택하여 새 스토리지 계정을 만듭니다.

    ![새 스토리지 계정을 추가하는 단추](media/azure-functions-lab-image5.png)

1. **이름**에 전역으로 고유한 이름을 입력하고 **리소스 그룹**에 다시 사용합니다. 다른 모든 항목은 기본값으로 유지할 수 있습니다.

    ![새 스토리지 계정 세부 정보](media/azure-functions-lab-image6.png)

1. **만들기**를 클릭합니다. 스토리지 계정을 만드는 데 몇 분 정도 걸릴 수 있습니다. 만들어진 후에는 알림이 표시됩니다.

    ![배포 성공 알림](media/azure-functions-lab-image7.png)

1. 알림에서 **리소스로 이동** 단추를 선택합니다.

1. **선택키** 탭을 선택합니다.

    ![선택키 설정](media/azure-functions-lab-image8.png)

1. 첫 번째 **연결 문자열**을 복사합니다. 이 문자열은 나중에 Azure Functions에 Azure 스토리지를 통합하는 데 사용합니다.

    ![키 1에 대한 정보](media/azure-functions-lab-image9.png)

1. **Mac용 Visual Studio**로 돌아와 **local.settings.json**의 **AzureWebJobsStorage** 설정으로 전체 연결 문자열을 붙여 넣습니다. 이제 해당 리소스에 액세스가 필요한 함수에 대한 속성에서 설정 이름을 참조할 수 있습니다.

    ![연결 키를 입력한 로컬 설정 파일](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>예제 3: Azure Function 만들기 및 디버깅

1. 이제 일부 코드를 추가할 준비가 되었습니다. .NET 클래스 라이브러리를 사용할 때 Azure Functions는 고정 메서드로 추가됩니다. **Solution Pad**에서 **AzureFunctions** 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가 > 함수 추가**를 선택합니다.

    ![함수 추가 옵션](media/azure-functions-lab-image11.png)

1. 새 Azure Functions 대화 상자에서 일반 웹후크 템플릿을 선택합니다. **이름**을 **추가**로 설정하고 **확인**을 클릭하여 함수를 만듭니다.

    ![새 Azure Functions 대화 상자](media/azure-functions-lab-image12.png)

1. 새 파일의 맨 위에 아래 **using** 지시문을 추가합니다.

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. 기존 제거 `Run` 메서드를 제거하고 아래 메서드를 클래스에 Azure 함수로 추가합니다.

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```

1. 메서드 정의를 하나씩 살펴보겠습니다.

    가장 먼저 표시되는 것은 이 메서드를 Azure 함수라 표시하는 **FunctionName** 특성입니다. 이 특성은 함수의 공개 이름을 지정합니다. 특성 이름이 반드시 실제 메서드 이름과 일치할 필요는 없습니다.

    ![FunctionName이 강조 표시된 새 실행 메서드](media/azure-functions-lab-image13.png)

1. 다음으로, 메서드가 필수인 **public static** 메서드로 표시됩니다. 반환 값도 **int**임을 확인할 수 있습니다. 메서드 특성을 사용하여 달리 지정하지 않은 한 void가 아닌 Azure 함수의 반환 값은 클라이언트에 텍스트로 반환됩니다. 기본적으로 **XML**로 반환되나 **JSON**으로 변경할 수 있으며 나중에 이 연습에서 해 볼 것입니다.

    ![메서드 초기화가 강조 표시된 새 run 메서드](media/azure-functions-lab-image14.png)

1. 첫 번째 매개 변수는 **HttpTrigger** 특성으로 표시됩니다. 이 메서드가 HTTP 요청에 의해 호출됨을 나타냅니다. 이 특성은 메서드의 권한 부여 수준과 지원하는 동사도 지정합니다(이 경우 **"GET"** 만). 선택적으로 메서드까지의 경로를 재정의하고 자동으로 경로에서 변수를 추출하는 방법을 제공하는 **Route**를 정의할 수도 있습니다. 여기서는 **Route**가 null이므로 이 메서드의 경로는 기본적으로 **/api/Add**입니다.

    ![매개 변수가 강조 표시된 새 run 메서드](media/azure-functions-lab-image15.png)

1. 메서드에 대한 마지막 매개 변수는 진단 및 오류의 메시지를 기록하는 데 사용할 수 있는 **TraceWriter**입니다.

    ![TraceWriter가 강조 표시된 새 run 메서드](media/azure-functions-lab-image16.png)

1. 줄의 여백을 클릭하여 메서드의 **반환** 줄에 중단점을 설정합니다.

    ![반환 줄에 중단점 설정](media/azure-functions-lab-image17.png)

1. **F5** 키를 누르거나 **실행 > 디버깅 시작**을 선택하여 디버그 세션에서 프로젝트를 빌드하고 실행합니다. 또는 **실행** 단추를 클릭할 수 있습니다. 이 옵션은 모두 동일한 작업을 수행 합니다. 이 연습의 나머지 부분에서는 **F5**를 언급하지만 본인에게 가장 편안한 방법을 사용하면 됩니다.

    ![프로젝트 빌드 및 실행](media/azure-functions-lab-image18.png)

1. 프로젝트를 실행하면 터미널 애플리케이션이 자동으로 열립니다.

1. 프로젝트는 이 문서의 뒷부분에서 설명하는 메서드 속성과 파일 규칙에 따라 Azure Functions를 검색하는 프로세스를 거칩니다. 이 경우 단일 Azure 함수를 검색하며 1개 작업 함수를 "생성"합니다.

    ![터미널의 Azure 함수 출력](media/azure-functions-lab-image19.png)

1. 시작 메시지의 맨 아래에 Azure Functions 호스트가 HTTP 트리거 API의 URL을 출력합니다. 하나만 있어야 합니다. 해당 URL을 복사하고 새 브라우저 탭에 붙여 넣습니다.

    ![Azure 함수 API URL](media/azure-functions-lab-image20.png)

1. 중단점은 즉시 트리거됩니다. 웹 요청은 함수에 전달되었으며 이제 디버그할 수 있습니다. **x** 변수 위에 마우스를 놓아 값을 확인합니다.

    ![중단점 트리거됨](media/azure-functions-lab-image21.png)

1. 앞에서 추가에 사용한 것과 같은 메서드를 사용하여 중단점을 제거합니다(여백을 클릭하거나 줄을 선택하고 **F9** 누르기).

1. **F5**를 눌러 실행을 계속합니다.

1. 브라우저에서 메서드의 XML 결과가 렌더링됩니다. 예상대로 하드 코드된 더하기 연산에서 적당한 합계가 생성됩니다. Safari에 “3”만 표시되면 **Safari > 기본 설정 > 고급**으로 이동하여 "**메뉴 모음에 개발 메뉴 표시**" 확인란을 선택하고 페이지를 다시 로드합니다.

1. **Mac용 Visual Studio**에서 **중지** 단추를 클릭하여 디버그 세션을 종료합니다. 새 변경 내용이 반드시 적용되도록 디버깅 세션을 다시 시작합니다(중지한 뒤 실행).

    ![디버깅 중지 옵션](media/azure-functions-lab-image22.png)

1. **Run** 메서드에서 **x** 및 **y** 정의를 아래 코드로 바꿉니다. 이 코드는 더하기 연산을 제공된 매개 변수에 따라 동적으로 수행할 수 있게 URL의 쿼리 문자열에서 값을 추출합니다.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. 애플리케이션을 실행합니다.

1. 브라우저 창으로 돌아가 `/?x=2&y=3` 문자열을 URL에 추가합니다. 이제 전체 URL은 `http://localhost:7071/api/Add?x=2&y=3`입니다. 새 URL로 이동합니다.

1. 이제 결과가 새 매개 변수를 반영할 것입니다. 다른 값으로 프로젝트를 실행해 봅니다. 오류 검사가 없으므로 올바르지 않거나 누락된 매개 변수에서는 오류가 throw됩니다.

1. 디버깅 세션을 중지합니다.

## <a name="exercise-4-working-with-functionjson"></a>연습 4: function.json 작업

1. 이전 연습에서 Mac용 Visual Studio이 라이브러리에 정의된 Azure 함수에 대해 작업 함수를 "생성"한다고 했습니다. 이것은 사실 Azure Functions가 런타임에서 메서드 특성을 사용하는 것이 아니라 컴파일 시점 파일 시스템 규칙을 사용하여 Azure Functions를 제공할 방법과 위치를 구성하기 때문입니다. **Solution Pad**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **Finder에 표시**를 선택합니다.

     ![Finder에 표시 메뉴 옵션](media/azure-functions-lab-image23.png)

1. **bin/Debug/netstandard2.0**이 나올 때까지 파일 시스템에서 아래로 이동합니다. 이름이 **Add**인 폴더가 있어야 합니다. 이 폴더는 C# 코드의 함수 이름 특성과 일치하도록 만들어졌습니다. 단일 **function.json** 파일을 표시하기 위해 Add 폴더를 확장합니다. 이 파일은 런타임에서 Azure 함수의 호스트 및 관리를 위해 사용됩니다. 컴파일 시점 지원이 없는 다른 언어 모델(예: C# 스크립트 또는 JavaScript)의 경우 이 폴더를 수동으로 만들어 유지 관리해야 합니다. C# 개발자의 경우 빌드 시 특성 메타데이터에서 자동으로 생성됩니다. **function.json**을 마우스 오른쪽 단추로 클릭하고 선택하여 Visual Studio에서 엽니다.

    ![파일 디렉터리의 function.json](media/azure-functions-lab-image24.png)

1. 이 자습서의 이전 단계를 살펴보았으므로 C# 특성에 대한 기본적인 이해가 있을 것입니다. 이를 고려하면 이 JSON에 익숙해야 합니다. 그러나 이전 연습에서 다루지 않은 몇 가지 항목이 있습니다. 예를 들어 각 **바인딩**에는 **direction** 설정이 있어야 합니다. 유추하듯이 **"in"** 은 매개 변수가 입력임을, **"out"** 은 매개 변수가 메서드에 대한 반환 값( **$return** 사용) 또는 **out** 매개 변수임을 나타냅니다. 어셈블리 안에서 **scriptFile**(이 최종 위치에 상대적) 및 **entryPoint** 메서드(공개 및 고정)를 지정해야 합니다. 다음 몇 단계에서는 이 모델을 사용하여 사용자 지정 함수 경로를 추가하게 되므로 이 파일의 콘텐츠를 클립보드에 복사합니다.

    ![Visual Studio for Mac에서 function.json 파일 열기](media/azure-functions-lab-image25.png)

1. **Solution Pad**에서 **AzureFunctionsLab** 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가 > 폴더 추가...** 를 선택합니다. 새 폴더 이름을 **Adder**로 지정합니다. 기본 규칙에서 이 폴더의 이름은 **api/Adder**처럼 API에 대한 경로를 정의합니다.

    ![새 폴더 옵션](media/azure-functions-lab-image26.png)

1. **Adder** 폴더를 마우스 오른쪽 단추로 클릭하고**추가 > 새 파일**을 선택합니다.

    ![새 파일 옵션](media/azure-functions-lab-image27.png)

1. **웹** 범주 및 **빈 JSON 파일** 템플릿을 선택합니다. **이름**을 **function**으로 설정하고 **새로 만들기**를 클릭합니다.

    ![빈 JSON 파일 옵션](media/azure-functions-lab-image28.png)

1. 다른 **function.json**의 콘텐츠(3단계)를 붙여 넣어 새로 만든 파일의 기본 콘텐츠를 변경합니다.

1. json 파일의 위쪽에서 다음 줄을 제거합니다.

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. 첫 번째 바인딩의 끝( **"name": "req"** 줄 다음)에 아래 속성을 추가합니다. 앞줄에 쉼표를 포함해야 합니다. 이 속성은 이제 기본 경로를 재정의하며 경로에서 **int** 매개 변수를 추출하여 이름이 **x** 및 **y**인 메서드 매개 변수에 배치합니다.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. 첫 번째 아래 다른 바인딩을 추가합니다. 이 바인딩은 함수의 반환 값을 처리합니다. 앞줄에 쉼표를 포함해야 합니다.

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. 파일 맨 아래의 **entryPoint** 속성을 아래처럼 **"Add2"** 라는 메서드를 사용하도록 업데이트합니다. 이것은 **api/Adder...** 경로가 모든 이름(여기서는 **Add2**)의 적합한 메서드에 매핑할 수 있음을 설명하기 위한 것입니다.

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. 최종 **function.json** 파일은 다음 json과 비슷합니다.

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. 이것이 제대로 작동하기 위해 필요한 마지막 단계는 Mac용 Visual Studio에게 이 파일이 바뀔 때마다 출력 디렉터리의 동일한 상대 경로에 해당 파일을 복사하도록 지시하는 것입니다. 파일을 선택한 상태에서 오른쪽 표시줄에 있는 속성 탭을 선택하고 **출력 디렉터리에 복사**에서 **변경된 내용만 복사**를 선택합니다.

    ![json 파일 속성 옵션](media/azure-functions-lab-image30.png)

1. 예상되는 기능을 수행할 수 있게 **Add.cs**에서 `Run` 메서드(특성 포함)를 다음 메서드로 바꿉니다. 특성을 사용하지 않으며 **x** 및 **y**에 대한 명시적 매개 변수가 있다는 점을 제외하고 `Run`과 매우 유사합니다.

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```

1. **F5**를 눌러 프로젝트를 빌드하고 실행합니다.

1. 빌드가 완료되고 플랫폼이 작동을 시작했으므로 이제 새로 추가된 메서드에 매핑되는 요청에 사용할 수 있는 두 번째 경로가 있음을 표시합니다.

    ![HTTP 함수 URL](media/azure-functions-lab-image31.png)

1. 브라우저 창으로 돌아와 **http://localhost:7071/api/Adder/3/5** 로 이동합니다.

1. 이번에는 메서드가 다시 한 번 경로에서 매개 변수를 가져오고 합계를 생성합니다.

1. **Mac용 Visual Studio**로 돌아와 디버깅 세션을 종료합니다.

## <a name="exercise-5-working-with-azure-storage-tables"></a>연습 5: Azure 스토리지 테이블 작업

빌드하는 서비스가 지금까지 연습한 빌드보다는 훨씬 복잡하여 실행을 위해 상당한 시간 및/또는 인프라가 소요되는 경우가 많습니다. 이 경우 리소스가 사용 가능하게 될 때 처리 대기 중인 요청을 수락하도록 하는 것이 효과적일 수 있으며 Azure Functions에서 이를 지원합니다. 다른 경우 데이터를 중앙 집중식으로 저장하려 할 수 있습니다. Azure Storage 테이블에서는 이를 신속하게 수행할 수 있습니다.

1. 아래 클래스를 **Add.cs**에 추가합니다. 네임스페이스 내부이면서 기존 클래스의 외부에 있어야 합니다.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. **Add** 클래스 안에 아래 코드를 추가하여 다른 함수를 넣습니다. 이 함수는 지금까지 고유하므로 HTTP 응답을 포함하지 않습니다. 마지막 줄은 나중에 검색하기 쉽게 일부 키 정보(**PartitionKey** 및 **RowKey**)가 입력된 새 **TableRow**와 해당 매개 변수 및 합계를 반환합니다. 메서드의 코드는 또한 사용 하 여는 **TraceWriter** 쉽게 함수 실행 하는 경우에 대해 알아야 합니다.

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");

        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```

1. **F5**를 눌러 프로젝트를 빌드하고 실행합니다.

1. 브라우저 탭에서 **http://localhost:7071/api/Process/4/6** 로 이동합니다. 그러면 큐에 다른 메시지가 추가되고 이에 따라 테이블에 다른 행이 추가됩니다.

1. **터미널**로 돌아와 **4 + 6**을 위한 수신 요청을 찾아봅니다.

    ![더하기 요청을 표시하는 터미널 출력](media/azure-functions-lab-image32.png)

1. 브라우저로 돌아와 같은 URL에 대한 요청을 새로 고칩니다. 이제 **Process** 메서드 다음에 오류가 표시됩니다. 이 코드가 이미 존재하는 파티션과 행 키 조합을 사용하는 Azure Table Storage 테이블에 행을 추가하려 시도하기 때문입니다.

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. 디버깅 세션을 종료합니다.

1. 오류를 해결하려면 다음 매개 변수를 **TraceWriter** 매개 변수 바로 앞의 메서드 정의에 추가합니다. 이 매개 변수는 Azure Functions에게 결과를 저장하는 데 사용한 **PartitionKey**의 **Results**에서 **TableRow**을 검색하도록 지시합니다. 그러나 여기서 놀라운 사실은 **RowKey**는 같은 메서드에 대한 다른 **x** 및 **y** 매개 변수를 기준으로 동적으로 생성된다는 점입니다. 행이 이미 있을 경우 개발자의 추가적인 작업 없이도 메서드가 시작될 때 **tableRow**에 해당 행이 있게 됩니다. 행이 없으면 null뿐입니다. 이러한 종류의 효율성을 통해 개발자는 인프라가 아닌 중요한 비즈니스 논리에 집중할 수 있습니다.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. 메서드의 시작 부분에 다음 코드를 추가합니다. **tableRow**이 null이 아니라면 요청된 작업에 대한 결과가 이미 있고 즉시 반환할 수 있습니다. 그렇지 않으면 함수는 전과 같이 진행됩니다. 데이터를 반환하는 가장 강력한 방법은 아닐 수 있으나 코드가 거의 없이 여러 확장성 있는 계층에서 매우 정교한 작업을 조정할 수 있다는 점을 시사합니다.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. **F5**를 눌러 프로젝트를 빌드하고 실행합니다.

1. 브라우저 탭에서 **http://localhost:7071/api/Process/4/6** 의 URL을 새로 고칩니다. 이 레코드에 대한 테이블 행이 있으므로 즉시 오류 없이 반환할 것입니다. HTTP 출력이 없으므로 터미널에서 출력을 확인할 수 있습니다.

    ![테이블 행이 있음을 표시하는 터미널 출력](media/azure-functions-lab-image33.png)

1. URL을 업데이트하여 아직 테스트하지 않은 조합을 반영합니다(예: **http://localhost:7071/api/Process/5/7** ). 테이블 행이 없음을 표시하는(예상한 대로) 터미널의 메시지를 확인합니다.

    ![새 프로세스를 표시하는 터미널 출력](media/azure-functions-lab-image34.png)

1. **Mac용 Visual Studio**로 돌아와 디버깅 세션을 종료합니다.

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON.

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>요약

이 연습에서는 Mac용 Visual Studio를 사용하여 Azure Functions 빌드를 시작하는 방법을 살펴보았습니다.
