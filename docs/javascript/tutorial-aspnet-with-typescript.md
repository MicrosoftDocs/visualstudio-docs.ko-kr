---
title: TypeScript를 사용하여 ASP.NET Core 앱 만들기
description: 이 자습서에서는 ASP.NET Core와 TypeScript를 사용하여 앱을 만듭니다.
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e212aec6d2d3aa7e20cb0ca08c9ea604f32bb08c
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988553"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>자습서: Visual Studio에서 TypeScript를 사용하여 ASP.NET Core 앱 만들기

Visual Studio 개발 ASP.NET Core 및 TypeScript에 대한 이 자습서에서는 간단한 웹 애플리케이션을 만들고 일부 TypeScript 코드를 추가한 다음 앱을 실행합니다. 

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range="vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

이 자습서에서는 다음 작업 방법을 알아봅니다.
> [!div class="checklist"]
> * ASP.NET Core 프로젝트 만들기
> * TypeScript 지원을 위해 NuGet 패키지 추가
> * 일부 TypeScript 코드 추가
> * 앱 실행
> * npm을 사용하여 타사 라이브러리 추가

## <a name="prerequisites"></a>사전 요구 사항

* Visual Studio가 설치되고 ASP.NET 웹 개발 워크로드가 있어야 합니다.

    ::: moniker range=">=vs-2019"
    아직 Visual Studio 2019를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/) 페이지로 이동하여 체험용으로 설치합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    아직 Visual Studio 2017을 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/) 페이지로 이동하여 체험용으로 설치합니다.
    ::: moniker-end

    워크로드는 설치해야 하지만 Visual Studio는 이미 있는 경우 **도구** > **도구 및 기능 가져오기...** 로 이동하면 Visual Studio 설치 관리자가 열립니다. **ASP.NET 및 웹 개발** 워크로드를 선택한 후 **수정**을 선택합니다.

## <a name="create-a-new-aspnet-core-mvc-project"></a>새 ASP.NET Core MVC 프로젝트 만들기

Visual Studio는 *프로젝트*에서 단일 애플리케이션에 대한 파일을 관리합니다. 프로젝트에는 소스 코드, 리소스 및 구성 파일이 포함됩니다.

>[!NOTE]
> 빈 ASP.NET Core 프로젝트로 시작하여 TypeScript 프런트 엔드를 추가하려면 이 문서 대신 [ASP.NET Core with TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)(TypeScript를 사용한 ASP.NET Core)를 참조하세요.

이 자습서에서는 ASP.NET Core MVC 앱에 대한 코드를 포함한 간단한 프로젝트부터 시작합니다.

1. Visual Studio를 엽니다.

1. 새 프로젝트를 만듭니다.

    ::: moniker range=">=vs-2019"
    시작 창이 열려 있지 않으면 **파일** > **시작 창**을 선택합니다. 시작 창에서 **새 프로젝트 만들기**를 선택합니다. 언어 드롭다운 목록에서 **C#** 을 선택합니다. 검색 상자에 **ASP.NET**을 입력하고 **ASP.NET Core 웹 애플리케이션**을 선택합니다. **다음**을 선택합니다.

    프로젝트의 이름을 입력하고 **만들기**를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C#** 을 확장하고, **.NET Core**를 선택합니다. 가운데 창에서 **ASP.NET Core 웹 애플리케이션 - C#** 을 선택한 후 **확인**을 선택합니다.
    ::: moniker-end
    **ASP.NET Core 웹 애플리케이션** 프로젝트 템플릿이 표시되지 않는 경우, **ASP.NET 및 웹 개발** 워크로드를 추가해야 합니다. 자세한 지침은 [필수 조건](#prerequisites)을 참조하세요.

1. 표시되는 대화 상자에서 **웹 애플리케이션(Model-View-Controller)** 을 선택하고 **만들기**(또는 **확인**)를 선택합니다.

   ![MVC 템플릿 선택](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio가 새 솔루션을 만들고 오른쪽 창에서 프로젝트를 엽니다.

## <a name="add-some-code"></a>일부 코드를 추가합니다.

1. 솔루션 탐색기(오른쪽 창)에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리**를 선택합니다. **찾아보기** 탭에서 **Microsoft.TypeScript.MSBuild**를 검색한 다음 오른쪽에 있는 **설치**를 클릭하여 패키지를 설치합니다.

   ![NuGet 패키지 추가](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio가 솔루션 탐색기의 **종속성** 노드에 NuGet 패키지를 추가합니다.

   > [!NOTE]
   > 이 자습서에는 NuGet 패키지가 필요합니다. 또는 사용자의 앱에서 [TypeScript npm 패키지](https://www.npmjs.com/package/typescript)를 사용할 수 있습니다.

1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **새 폴더 > 추가**를 선택합니다. 새 폴더의 이름으로 *scripts*를 사용합니다.

1. *scripts* 폴더를 마우스 오른쪽 단추로 클릭하고 **추가 > 새 항목**을 선택합니다. **TypeScript JSON 구성 파일**을 선택하고 **추가**를 클릭합니다.

   Visual Studio가 *scripts* 폴더에 *tsconfig.json* 파일을 추가합니다. 이 파일을 사용하여 TypeScript 컴파일러에 대한 [옵션을 구성](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)할 수 있습니다.

1. *tsconfig.json*을 열고 기본 코드를 다음 코드로 바꿉니다.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "../wwwroot/js"
     },
     "exclude": [
       "node_modules",
       "wwwroot"
     ]
   }
   ```

   *outDir* 옵션은 TypeScript 컴파일러에 의해 트랜스파일된 계획 JavaScript 파일의 출력 폴더를 지정합니다.

   이 구성은 TypeScript 사용에 대한 기본적인 소개를 제공합니다. 예를 들어 [gulp 또는 webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)을 사용하는 경우와 같이 다른 시나리오에서는 *../wwwroot/js* 대신 도구 및 구성 기본 설정에 따라 트랜스파일된 JavaScript 파일에 다른 중간 위치를 사용하는 것이 좋습니다.

1. *scripts* 폴더를 마우스 오른쪽 단추로 클릭하고 **추가 > 새 항목**을 선택합니다. **TypeScript 파일**을 선택하고, 파일 이름에 *app.ts*를 입력한 다음 **추가**를 클릭합니다.

   Visual Studio가 *scripts* 폴더에 *app.ts*를 추가합니다.

1. *app.ts*를 열고 다음 TypeScript 코드를 추가합니다.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Visual Studio는 TypeScript 코드에 대해 IntelliSense 지원을 제공합니다.

    이를 테스트하려면 `greeter` 함수에서 `.lastName`을 제거하고 "."를 다시 입력하면 IntelliSense가 표시됩니다.

    ![IntelliSense 보기](../javascript/media/aspnet-core-ts-intellisense.png)

    `lastName`을 선택하여 마지막 이름을 코드에 다시 추가합니다.

1. *Views/Home* 폴더를 연 다음 *index.html*을 엽니다.

1. 파일 끝에 다음 HTML 코드를 추가합니다.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. *Views/Shared* 폴더를 연 다음 *_Layout.cshtml*을 엽니다.

1. `@RenderSection("Scripts", required: false)`를 호출하기 전에 다음 스크립트 참조를 추가합니다.

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>애플리케이션 빌드

1. **빌드 > 솔루션 빌드**를 선택합니다.

   앱은 실행할 때 자동으로 빌드되지만 빌드 프로세스 도중 발생하는 작업을 살펴보겠습니다.

1. *wwwroot/js* 폴더를 엽니다. 여기에 두 개의 새 파일 *app.js* 및 소스 맵 파일 *app.js.map*이 있습니다. 이러한 파일은 TypeScript 컴파일러에 의해 생성됩니다.

   소스 맵 파일은 디버깅에 필요합니다.

## <a name="run-the-application"></a>애플리케이션 실행

1. **F5**(**디버그** > **디버깅 시작**) 키를 눌러 애플리케이션을 실행합니다.

    앱이 브라우저에서 열립니다.

    브라우저 창에 **시작** 머리글과 **클릭** 단추가 표시됩니다.

    ![TypeScript가 포함된 ASP.NET Core](../javascript/media/aspnet-core-ts-running-app.png)

1. TypeScript 파일에 지정한 메시지를 표시하려면 단추를 클릭합니다.

## <a name="debug-the-application"></a>애플리케이션 디버그

1. 코드 편집기에서 왼쪽 여백을 클릭하여 `app.ts`의 `greeter` 함수에서 중단점을 설정합니다.

    ![중단점 설정](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. **F5** 키를 눌러 애플리케이션을 실행합니다.

   스크립트 디버깅을 사용하도록 설정하려면 메시지에 응답해야 할 수 있습니다.

   애플리케이션이 중단점에서 일시 중지합니다. 이제 변수를 검사하고 디버거 기능을 사용할 수 있습니다.

## <a name="add-typescript-support-for-a-third-party-library"></a>타사 라이브러리에 TypeScript 지원 추가

1. [npm 패키지 관리](../javascript/npm-package-management.md#aspnet-core-projects)의 지침에 따라 프로젝트에 `package.json` 파일을 추가합니다. 이렇게 하면 프로젝트에 npm 지원이 추가됩니다.

   >[!NOTE]
   > ASP.NET Core 프로젝트의 경우 npm 대신 [라이브러리 관리자](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) 또는 YARN을 사용하여 클라이언트 쪽 JavaScript 및 CSS 파일을 설치할 수도 있습니다.

1. 이 예제에서는 프로젝트에 jQuery에 대한 TypeScript 정의 파일을 추가합니다. *package.json* 파일에 다음을 포함합니다.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   이렇게 하면 jQuery에 대한 TypeScript 지원이 추가됩니다. jQuery 라이브러리는 그 자체가 이미 MVC 프로젝트 템플릿에 포함되어 있습니다(솔루션 탐색기에서 wwwroot/lib 확인). 다른 템플릿을 사용하는 경우에는 jquery npm 패키지도 포함해야 할 수 있습니다.

1. 솔루션 탐색기의 패키지가 설치되지 않았다면 npm 코드를 마우스 오른쪽 단추로 클릭하고 **패키지 복원**을 선택합니다.

   >[!NOTE]
   > 솔루션 탐색기에서 경우에 따라 [여기](https://github.com/aspnet/Tooling/issues/479)에서 설명하는 알려진 문제로 인해 npm 패키지가 *package.json*과 동기화되지 않았음을 안내하는 메시지를 표시할 수 있습니다. 예를 들어 패키지가 설치되었지만 설치되지 않은 것으로 보일 수 있습니다. 대부분의 경우에는 *package.json*을 삭제하고 Visual Studio를 다시 시작한 다음 이 문서의 앞부분에서 설명한 것처럼 *package.json* 파일을 다시 추가하여 솔루션 탐색기를 업데이트할 수 있습니다.

1. 솔루션 탐색기에서 scripts 폴더를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목**을 선택합니다.

1. **TypeScript 파일**을 선택하고 *library.ts*를 입력한 후 **추가**를 선택합니다.

1. *library.ts*에 다음 코드를 추가합니다.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   간단한 설명을 위해 이 코드는 jQuery를 사용한 메시지와 경고를 표시합니다.

   jQuery에 대한 TypeScript 형식 정의가 추가되었으므로 jQuery 개체 뒤에 “.”를 추가하여 입력하면 아래에서 볼 수 있듯이 jQuery 개체에 대한 IntelliSense 지원이 제공됩니다.

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. _Layout.cshtml에서 스크립트 참조가 `library.js`를 포함하도록 업데이트합니다.

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. Index.cshtml에서 파일 끝부분에 다음 HTML을 추가합니다.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. **F5**(**디버그** > **디버깅 시작**) 키를 눌러 애플리케이션을 실행합니다.

    앱이 브라우저에서 열립니다.

    경고에서 **확인**을 클릭하면 페이지가 **jQuery version is: 3.3.1!!** 로 업데이트된 것을 확인할 수 있습니다.

    ![jquery 예제](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>다음 단계

ASP.NET Core에서 TypeScript를 사용하는 방법에 대한 자세한 내용을 알아볼 수 있습니다.

> [!div class="nextstepaction"]
> [ASP.NET Core 및 TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
