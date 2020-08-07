---
title: NuGet을 사용하여 TypeScript 코드 컴파일 및 빌드
description: Visual Studio에서 TypeScript를 컴파일하고 빌드하는 방법을 알아봅니다.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ac917248915129b8d93dc776ac7d35a2ed227069
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87454622"
---
# <a name="compile-typescript-code-aspnet-core"></a>TypeScript 코드 컴파일(ASP.NET Core)

Visual Studio 설치 프로그램에서 기본적으로 제공하는 TypeScript SDK를 사용하거나 NuGet 패키지를 사용하여 프로젝트에 TypeScript 지원을 추가할 수 있습니다. Visual Studio 2019에서 개발된 프로젝트의 경우 다양한 플랫폼과 환경에 대한 이식성을 높이려면 TypeScript NuGet을 사용하는 것이 좋습니다.

ASP.NET Core 프로젝트의 경우 NuGet 패키지의 일반적인 용도 중 하나는 .NET Core CLI를 사용하여 TypeScript를 컴파일하는 것입니다. TypeScript SDK 설치에서 빌드 대상을 가져오도록 프로젝트 파일을 수동으로 편집하지 않는 이상, NuGet 패키지는 `dotnet build` 및 `dotnet publish`와 같은 .NET Core CLI 명령을 사용하여 TypeScript 컴파일을 사용하도록 설정할 유일한 방법입니다. ASP.NET Core 및 TypeScript와의 [MSBuild 통합](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html)에는 npm 패키지 대신 NuGet 패키지를 선택하세요.

## <a name="add-typescript-support-with-nuget"></a>NuGet을 사용하여 TypeScript 지원 추가

[TypeScript NuGet 패키지](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild)는 TypeScript 지원을 추가합니다. TypeScript 3.2 이상용 NuGet 패키지가 프로젝트에 설치되면 해당 버전의 TypeScript 언어 서비스가 편집기에 로드됩니다.

Visual Studio가 설치된 경우 Visual Studio에서 번들로 포함된 node.exe를 자동으로 선택합니다. Node.js를 설치하지 않은 경우 [Node.js](https://nodejs.org/en/download/) 웹 사이트에서 LTS 버전을 설치하는 것을 권장합니다.

1. Visual Studio에서 ASP.NET Core 프로젝트를 엽니다.

1. 솔루션 탐색기(오른쪽 창)에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리**를 선택합니다. **찾아보기** 탭에서 **Microsoft.TypeScript.MSBuild**를 검색한 다음 오른쪽에 있는 **설치**를 클릭하여 패키지를 설치합니다.

   ![NuGet 패키지 추가](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio가 솔루션 탐색기의 **종속성** 노드에 NuGet 패키지를 추가합니다. 다음 패키지 참조는 *.csproj 파일에 추가됩니다.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가 > 새 항목**을 선택합니다. **TypeScript JSON 구성 파일**을 선택하고 **추가**를 클릭합니다.

   Visual Studio가 프로젝트 루트에 *tsconfig.json* 파일을 추가합니다. 이 파일을 사용하여 TypeScript 컴파일러에 대한 [옵션을 구성](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)할 수 있습니다.

1. *tsconfig.json*을 열고 업데이트해 원하는 컴파일러 옵션을 설정합니다.

   다음은 간단한 *tsconfig.json* 파일 예제입니다.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   이 예제에 대한 설명:
   - 포함은 TypeScript(*.ts) 파일을 찾을 수 있는 위치를 컴파일러에 알려줍니다.
   - *outDir* 옵션은 TypeScript 컴파일러에 의해 트랜스파일된 일반 JavaScript 파일의 출력 폴더를 지정합니다.
   - *sourceMap* 옵션은 컴파일러에서 *sourceMap* 파일을 생성할지 여부를 나타냅니다.

   이전 구성은 TypeScript 구성에 대한 기본 사항만 제공합니다. 다른 옵션에 대한 자세한 내용은 [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)을 참조하세요.

### <a name="build-the-application"></a>애플리케이션 빌드

1. TypeScript( *.ts*) 또는 TypeScript JSX( *.tsx*) 파일을 프로젝트에 추가한 다음 TypeScript 코드를 추가합니다. 간단한 TypeScript 예제를 보려면 다음을 사용합니다.

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. 이전의 비 SDK 스타일 프로젝트를 사용하는 경우 빌드하기 전에 [기본 가져오기 제거](#remove-default-imports)의 지침을 따르세요.

1. **빌드 > 솔루션 빌드**를 선택합니다.

   앱은 실행할 때 자동으로 빌드되지만, 빌드 프로세스 도중 발생하는 작업을 살펴보겠습니다.

   소스 맵을 생성한 경우 *outDir* 옵션에 지정된 폴더를 열고 생성된 *js 파일과 생성된 *js.map 파일을 찾습니다.

   소스 맵 파일은 디버깅에 필요합니다.

1. 프로젝트를 저장할 때마다 컴파일하려면 *.tsconfig에서 *compileOnSave* 옵션을 사용합니다.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Task Runner에서 gulp를 사용하여 앱을 빌드하는 예제는 [ASP.NET Core 및 TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)를 참조하세요.

Visual Studio에서 예상한 버전이 아닌 Node.js 또는 타사 도구를 사용하는 문제가 발생하는 경우 Visual Studio가 사용할 경로를 설정해야 할 수 있습니다. **도구** > **옵션**을 선택합니다. **프로젝트 및 솔루션**에서 **웹 패키지 관리** > **외부 웹 도구**를 선택합니다.

### <a name="nuget-package-structure-details"></a>NuGet 패키지 구조 세부 정보

`Microsoft.TypeScript.MSBuild.nupkg`에는 두 개의 기본 폴더가 있습니다.

- *build* 폴더

    이 폴더에는 두 개의 파일이 있습니다.
    두 파일은 각각 기본 TypeScript 대상 파일 및 props 파일에 대한 진입점입니다.

    1. *Microsoft.TypeScript.MSBuild.targets*

        이 파일은 *tools* 폴더에서 *Microsoft.TypeScript.targets*를 가져오기 전에 *TypeScript.Tasks.dll* 경로와 같은 런타임 플랫폼을 지정하는 변수를 설정합니다.

    2. *Microsoft.TypeScript.MSBuild.props*

        이 파일은 *tools* 폴더에서 *Microsoft.TypeScript.Default.props*를 가져오며, NuGet을 통해 빌드를 시작했음을 나타내는 속성을 설정합니다.

- *tools* 폴더

    2\.3보다 이전 버전의 패키지에는 tsc 폴더만 포함되어 있습니다. *Microsoft.TypeScript.targets* 및 *TypeScript.Tasks.dll*은 루트 수준에 있습니다.

    패키지 버전 2.3 이상에서는 루트 수준에 `Microsoft.TypeScript.targets` 및 `Microsoft.TypeScript.Default.props`가 포함되어 있습니다. 이러한 파일에 대한 자세한 내용은 [MSBuild 구성](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html)을 참조하세요.

    또한 이 폴더에는 세 개의 하위 폴더가 있습니다.

    1. *net45*

        이 폴더에는 `TypeScript.Tasks.dll` 및 이 DLL이 종속된 다른 DLL이 포함되어 있습니다.
        Windows 플랫폼에서 프로젝트를 빌드할 때 MSBuild는 이 폴더의 DLL을 사용합니다.

    2. *netstandard1.3*

        이 폴더에는 Windows 이외의 컴퓨터에서 프로젝트를 빌드할 때 사용되는 버전의 `TypeScript.Tasks.dll`이 포함되어 있습니다.

    3. *tsc*

        이 폴더에는 노드 스크립트로 실행하는 데 필요한 `tsc.js`, `tsserver.js` 및 모든 종속성 파일이 포함되어 있습니다.

        > [!NOTE]
        > Visual Studio가 설치된 경우 번들로 포함된 *node.exe*가 자동으로 선택됩니다. 설치하지 않은 경우 컴퓨터에 Node.js를 설치해야 합니다.

        3\.1보다 이전 버전에서는 컴파일을 실행하기 위한 `tsc.exe` 실행 파일이 포함되어 있습니다. 버전 3.1에서는 `node.exe`를 사용하기 위해 해당 파일은 제거되었습니다.

### <a name="remove-default-imports"></a>기본 가져오기 제거

[비 SDK 스타일 형식](https://docs.microsoft.com/nuget/resources/check-project-format)을 사용하는 이전 ASP.NET Core 프로젝트에서는 몇몇 프로젝트 파일 요소를 제거해야 할 수 있습니다.

프로젝트에서 MSBuild 지원을 위해 NuGet 패키지를 사용하는 경우 프로젝트 파일이 `Microsoft.TypeScript.Default.props` 또는 `Microsoft.TypeScript.targets`를 가져와야 합니다. 파일은 NuGet 패키지가 가져오기 때문에 개별적으로 포함할 경우 의도하지 않은 동작이 발생할 수 있습니다.

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **프로젝트 언로드**를 선택합니다.

1. 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **편집\<*project file name*\>** 을 선택합니다.

   프로젝트 파일이 열립니다.

1. `Microsoft.TypeScript.Default.props` 및 `Microsoft.TypeScript.targets`에 대한 참조를 제거합니다.

   제거해야 하는 가져오기는 다음과 비슷하게 표시됩니다.

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
