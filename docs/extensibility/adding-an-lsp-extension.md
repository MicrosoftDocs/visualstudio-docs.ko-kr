---
title: 언어 서버 프로토콜 확장 추가 | 마이크로 소프트 문서
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740239"
---
# <a name="add-a-language-server-protocol-extension"></a>언어 서버 프로토콜 확장 추가

언어 서버 프로토콜(LSP)은 JSON RPC v2.0의 형태로 다양한 코드 편집기에게 언어 서비스 기능을 제공하는 데 사용되는 일반적인 프로토콜입니다. 개발자는 프로토콜을 사용하여 단일 언어 서버를 작성하여 INtelliSense, 오류 진단, 모든 참조 찾기 등과 같은 언어 서비스 기능을 LSP를 지원하는 다양한 코드 편집기에게 제공할 수 있습니다. 일반적으로 Visual Studio의 언어 서비스는 TextMate 문법 파일을 사용하여 구문 강조 표시와 같은 기본 기능을 제공하거나 Visual Studio 확장성 API의 전체 집합을 사용하여 풍부한 데이터를 제공하는 사용자 지정 언어 서비스를 작성하여 추가할 수 있습니다. LSP에 대한 Visual Studio 지원을 사용하면 세 번째 옵션이 있습니다.

![비주얼 스튜디오에서 언어 서버 프로토콜 서비스](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>언어 서버 프로토콜

![언어 서버 프로토콜 구현](media/lsp-implementation.png)

이 문서에서는 LSP 기반 언어 서버를 사용하는 Visual Studio 확장을 만드는 방법에 대해 설명합니다. 이미 LSP 기반 언어 서버를 개발했으며 Visual Studio에 통합하려고 한다고 가정합니다.

Visual Studio 내에서 지원을 위해 언어 서버는 스트림 기반 전송 메커니즘을 통해 클라이언트(Visual Studio)와 통신할 수 있습니다.

* 표준 입력/출력 스트림
* 명명된 파이프
* 소켓(TCP만)

비주얼 스튜디오에서 LSP 및 지원의 의도는 Visual Studio 제품의 일부가 아닌 언어 서비스를 온보딩하는 것입니다. Visual Studio에서 기존 언어 서비스(예: C#)를 확장하기 위한 것이 아닙니다. 기존 언어를 확장하려면 언어 서비스의 확장성 가이드(예: ["Roslyn" .NET 컴파일러 플랫폼)를](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)참조하거나 [편집기 및 언어 서비스 확장을](../extensibility/extending-the-editor-and-language-services.md)참조하십시오.

프로토콜 자체에 대한 자세한 내용은 [여기의](https://github.com/Microsoft/language-server-protocol)설명서를 참조하십시오.

샘플 언어 서버를 만드는 방법 또는 기존 언어 서버를 Visual Studio 코드에 통합하는 방법에 대한 자세한 내용은 [여기의](https://code.visualstudio.com/docs/extensions/example-language-server)설명서를 참조하십시오.

## <a name="language-server-protocol-supported-features"></a>언어 서버 프로토콜 지원 기능

다음 표에서는 Visual Studio에서 지원되는 LSP 기능을 보여 주며 있습니다.

메시지 | 비주얼 스튜디오에서 지원
--- | ---
initialize | 예
초기화됨 | 예
shutdown | 예
exit | 예
$/취소요청 | 예
창/쇼메시지 | 예
창/표시메시지요청 | 예
창/로그메시지 | 예
원격 분석/이벤트 |
클라이언트/레지스터기능 |
클라이언트/레지스터 취소기능 |
작업 영역/did변경 구성 | 예
작업 영역/didChange감시파일 | 예
작업 영역/기호 | 예
작업 영역/실행 명령 | 예
작업 영역/적용편집 | 예
텍스트문서/게시진단 | 예
텍스트 문서/디오픈 | 예
텍스트문서/디변경 | 예
텍스트문서/저장 예정 |
텍스트문서/세이브웨이트 |
텍스트 문서/디세이브 | 예
텍스트문서/디닫기 | 예
텍스트 문서/완료 | 예
완료/해결 | 예
텍스트 문서/가리키기 | 예
텍스트 문서/서명도움말 | 예
텍스트 문서/참조 | 예
텍스트문서/문서강조표시 | 예
텍스트문서/문서 기호 | 예
텍스트 문서/서식 지정 | 예
텍스트문서/범위서식 | 예
텍스트 문서/형식 형식 형식 지정 |
텍스트문서/정의 | 예
텍스트 문서/코드작업 | 예
텍스트문서/코드렌즈 |
코드렌즈/확인 |
텍스트 문서/문서링크 |
문서 링크/확인 |
텍스트문서/이름 바꾸기 | 예

## <a name="get-started"></a>시작하기

> [!NOTE]
> Visual Studio 2017 버전 15.8부터 는 공통 언어 서버 프로토콜에 대한 지원이 Visual Studio에 기본제공됩니다. 미리 보기 [언어 서버 클라이언트 VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) 버전을 사용하여 LSP 확장을 빌드한 경우 버전 15.8 이상으로 업그레이드하면 작업이 중지됩니다. LSP 확장을 다시 작동하려면 다음을 수행해야 합니다.
>
> 1. Microsoft 비주얼 스튜디오 언어 서버 프로토콜 미리 보기 VSIX를 제거합니다.
>
>    버전 15.8부터 Visual Studio에서 업그레이드를 수행할 때마다 미리 보기 VSIX가 자동으로 감지되고 제거됩니다.
>
> 2. NUget 참조를 [LSP 패키지의](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)최신 비미리 버전으로 업데이트합니다.
>
> 3. VSIX 매니페스트에서 Microsoft 비주얼 스튜디오 언어 서버 프로토콜 미리 보기 VSIX에 대한 종속성을 제거합니다.
>
> 4. VSIX가 Visual Studio 2017 버전 15.8 미리 보기 3을 설치 대상의 하한으로 지정했는지 확인합니다.
>
> 5. 다시 빌드하고 다시 배포합니다.

### <a name="create-a-vsix-project"></a>VSIX 프로젝트 만들기

LSP 기반 언어 서버를 사용하여 언어 서비스 확장을 만들려면 먼저 VS 인스턴스에 **대해 Visual Studio 확장 개발** 워크로드가 설치되어 있는지 확인합니다.

다음으로 새 **File** > **프로젝트** > **Visual C#** > **확장성** > **VSIX 프로젝트로**이동하여 새 VSIX 프로젝트를 만듭니다.

![vsix 프로젝트 만들기](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>언어 서버 및 런타임 설치

기본적으로 Visual Studio에서 LSP 기반 언어 서버를 지원하기 위해 만든 확장에는 언어 서버 자체 또는 실행 에 필요한 런타임이 포함되지 않습니다. 확장 개발자는 언어 서버와 필요한 런타임을 배포할 책임이 있습니다. 이렇게 하는 방법에는 여러 가지가 있습니다.

* 언어 서버는 VSIX에 콘텐츠 파일로 포함할 수 있습니다.
* MSI를 만들어 언어 서버 및/또는 필요한 런타임을 설치합니다.
* 마켓플레이스에서 런타임 및 언어 서버를 가져오는 방법을 사용자에게 알리는 지침을 제공합니다.

### <a name="textmate-grammar-files"></a>텍스트 메이트 문법 파일

LSP는 언어에 대한 텍스트 색상 지정을 제공하는 방법에 대한 사양을 포함하지 않습니다. Visual Studio에서 언어에 대한 사용자 지정 색상 지정을 제공하기 위해 확장 개발자는 TextMate 문법 파일을 사용할 수 있습니다. 사용자 지정 TextMate 문법 또는 테마 파일을 추가하려면 다음 단계를 따르십시오.

1. 확장 프로그램 내에서 "문법"이라는 폴더를 만듭니다(또는 선택한 이름이 될 수 있음).

2. *문법* 폴더 * \*안에는 .tmlanguage,* * \*.plist,* * \*.tmtheme*또는 * \*.json* 파일을 포함하면 사용자 지정 색상지정을 제공할 수 있습니다.

   > [!TIP]
   > *.tmtheme* 파일은 범위가 Visual Studio 분류(명명된 색상 키)에 매핑하는 방법을 정의합니다. 지침에 대 한, *%ProgramFiles (x86)%\마이크로소프트 비주얼\\\<스튜디오 버전>\\ \<SKU>\일반 7\IDE\일반 확장\마이크로소프트\TextMate\Starterkit\Themesg* 디렉토리에서 전역 *.tmtheme* 파일을 참조할 수 있습니다.

3. *.pkgdef* 파일을 만들고 다음과 유사한 선을 추가합니다.

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. 파일을 마우스 오른쪽 단추로 클릭하고 **속성을**선택합니다. **빌드** 작업을 **콘텐츠로** 변경하고 **VSIX에 포함** 속성을 **true로**변경합니다.

이전 단계를 완료하면 *문법* 폴더가 패키지의 설치 디렉터리에 'MyLang'이라는 리포지토리 소스로 추가됩니다('MyLang'은 동음이의의 이름일 뿐이며 고유한 문자열일 수 있음). 이 디렉토리의 모든 문법 *(.tmlanguage* 파일)과 테마 파일 *(.tmtheme* 파일)은 잠재력으로 포착되고 TextMate와 함께 제공되는 기본 제공 문법을 대체합니다. 문법 파일의 선언된 확장명이 열려 있는 파일의 확장과 일치하는 경우 TextMate가 들어오게 됩니다.

## <a name="create-a-simple-language-client"></a>간단한 언어 클라이언트 만들기

### <a name="main-interface---ilanguageclient"></a>메인 인터페이스 - [ILanguage클라이언트](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

VSIX 프로젝트를 만든 후 프로젝트에 다음 NuGet 패키지를 추가합니다.

* [마이크로소프트.비주얼 스튜디오.언어 서버.클라이언트](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> 이전 단계를 완료한 후 NuGet 패키지에 대한 종속성을 취하면 Newtonsoft.Json 및 StreamJsonRpc 패키지도 프로젝트에 추가됩니다. **확장이 대상으로 하는 Visual Studio 버전에 새 버전이 설치될 것이라고 확신하지 않는 한 이러한 패키지를 업데이트하지 마십시오.** 어셈블리는 VSIX에 포함되지 않습니다. 대신 Visual Studio 설치 디렉토리에서 선택합니다. 사용자 컴퓨터에 설치된 어셈블리보다 최신 버전의 어셈블리를 참조하는 경우 확장이 작동하지 않습니다.

그런 다음 LSP 기반 언어 서버에 연결하는 언어 클라이언트에 필요한 기본 인터페이스인 [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) 인터페이스를 구현하는 새 클래스를 만들 수 있습니다.

다음은 샘플입니다.

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

구현해야 하는 주요 방법은 [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) 및 [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)입니다. [OnLoadedAsync는](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) Visual Studio에서 확장을 로드하고 언어 서버를 시작할 준비가 되면 호출됩니다. 이 메서드에서는 [즉시 StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) 대리자를 호출하여 언어 서버가 시작되어야 한다는 신호를 표시하거나 추가 논리를 수행하여 나중에 [StartAsync를](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) 호출할 수 있습니다. **언어 서버를 활성화하려면 언제든지 StartAsync를 호출해야 합니다.**

[ActivateAsync는](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) 대리자를 호출하여 결국 호출되는 메서드입니다. 여기에는 언어 서버를 시작하고 연결을 설정하는 논리가 포함되어 있습니다. 서버에 쓰고 서버에서 읽기 위한 스트림이 포함된 연결 개체를 반환해야 합니다. 여기에 throw된 모든 예외는 Visual Studio의 InfoBar 메시지를 통해 사용자에게 catch되고 표시됩니다.

### <a name="activation"></a>활성화

언어 클라이언트 클래스가 구현되면 Visual Studio에 로드되고 활성화되는 방법을 정의하기 위해 두 가지 특성을 정의해야 합니다.

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio는 [MEF(관리되는](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) 확장성 프레임워크)를 사용하여 확장성 지점을 관리합니다. [내보내기](/dotnet/api/system.componentmodel.composition.exportattribute) 특성은 Visual Studio에 이 클래스를 확장 지점으로 선택하여 적절한 시간에 로드해야 한다는 것을 나타냅니다.

MEF를 사용하려면 MEF를 VSIX 매니페스트의 자산으로 정의해야 합니다.

VSIX 매니페스트 디자이너를 열고 **자산** 탭으로 이동합니다.

![MEF 자산 추가](media/lsp-add-asset.png)

새 자산을 만들려면 **새** 를 클릭합니다.

![MEF 자산 정의](media/lsp-define-asset.png)

* **유형**: 마이크로소프트.비주얼스튜디오.Mef컴포넌트
* **출처**: 현재 솔루션의 프로젝트
* **프로젝트**: [프로젝트]

### <a name="content-type-definition"></a>콘텐츠 유형 정의

현재 LSP 기반 언어 서버 확장자만 로드하는 유일한 방법은 파일 콘텐츠 형식입니다. 즉, 언어 클라이언트 [클래스(ILanguageClient를](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)구현하는)를 정의할 때 열면 확장이 로드되는 파일 형식을 정의해야 합니다. 정의된 콘텐츠 유형과 일치하는 파일이 열리지 않으면 확장이 로드되지 않습니다.

이 작업은 하나 이상의 `ContentTypeDefinition` 클래스를 정의하여 수행됩니다.

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;

        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

이전 예제에서는 *.bar* 파일 확장명으로 끝나는 파일에 대해 콘텐츠 형식 정의가 만들어집니다. 콘텐츠 형식 정의에는 "bar"라는 이름이 지정되며 [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)에서 파생되어야 합니다.

콘텐츠 형식 정의를 추가한 후 언어 클라이언트 클래스에서 언어 클라이언트 확장을 로드할 시기를 정의할 수 있습니다.

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

LSP 언어 서버에 대한 지원을 추가해도 Visual Studio에서 자체 프로젝트 시스템을 구현할 필요가 없습니다. 고객은 Visual Studio에서 단일 파일 또는 폴더를 열어 언어 서비스를 시작할 수 있습니다. 실제로 LSP 언어 서버에 대한 지원은 열려 있는 폴더/파일 시나리오에서만 작동하도록 설계되었습니다. 사용자 지정 프로젝트 시스템이 구현되면 일부 기능(예: 설정)이 작동하지 않습니다.

## <a name="advanced-features"></a>고급 기능

### <a name="settings"></a>설정

사용자 지정 언어 서버별 설정에 대한 지원을 사용할 수 있지만 여전히 개선 중입니다. 설정은 언어 서버가 지원하는 것과 관련이 있으며 일반적으로 언어 서버가 데이터를 내보전하는 방법을 제어합니다. 예를 들어 언어 서버에보고된 최대 오류 수에 대한 설정이 있을 수 있습니다. 확장 작성자는 특정 프로젝트에 대해 사용자가 변경할 수 있는 기본값을 정의합니다.

LSP 언어 서비스 확장에 설정에 대한 지원을 추가하려면 아래 단계를 따르십시오.

1. 설정 및 기본값을 포함하는 프로젝트에 JSON 파일(예: *MockLanguageExtensionSettings.json)을*추가합니다. 다음은 그 예입니다.

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. JSON 파일을 마우스 오른쪽 단추로 클릭하고 **속성을**선택합니다. **빌드** 작업을 "콘텐츠"로 변경하고 "VSIX에 포함" 속성을 **true로**변경합니다.

3. ConfigurationSection을 구현하고 JSON 파일에 정의된 설정에 대한 접두사 목록을 반환합니다(Visual Studio 코드에서는 package.json의 구성 섹션 이름으로 매핑됨).

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. 프로젝트에 .pkgdef 파일을 추가합니다(새 텍스트 파일을 추가하고 파일 확장을 .pkgdef로 변경). pkgdef 파일에는 다음 정보가 포함되어야 합니다.

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    샘플:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. .pkgdef 파일을 마우스 오른쪽 버튼으로 클릭하고 **속성을**선택합니다. **빌드** 작업을 **콘텐츠로** 변경하고 **VSIX에 포함** 속성을 **true로**변경합니다.

6. *source.extension.vsixmanifest* 파일을 열고 **자산** 탭에 에셋을 추가합니다.

   ![편집 vs 패키지 에셋](media/lsp-add-vspackage-asset.png)

   * **유형**: 마이크로소프트.비주얼스튜디오.Vs패키지
   * **출처**: 파일 시스템에 파일
   * **경로**: *[.pkgdef* 파일로가는 길]

### <a name="user-editing-of-settings-for-a-workspace"></a>작업 영역의 설정 사용자 편집

1. 사용자가 서버가 소유한 파일이 포함된 작업 영역을 엽니다.
2. 사용자는 *VSWorkspaceSettings.json이라는* *.vs* 폴더에 파일을 추가합니다.
3. 사용자가 서버가 제공하는 설정에 대해 *VSWorkspaceSettings.json* 파일에 줄을 추가합니다. 다음은 그 예입니다.

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>진단 추적 사용

진단 추적을 활성화하여 클라이언트와 서버 간에 모든 메시지를 출력할 수 있으며, 이는 디버깅 시 유용할 수 있습니다. 진단 추적을 사용하려면 다음을 수행합니다.

1. 작업 영역 설정 파일 *VSWorkspaceSettings.json을* 열거나 만듭니다("작업 영역에 대한 설정 의 사용자 편집"참조).
2. 설정 json 파일에 다음 줄을 추가합니다.

```json
{
    "foo.trace.server": "Off"
}
```

추적 세부성에 대한 세 가지 가능한 값이 있습니다.

* "꺼져": 추적이 완전히 꺼져 있습니다.
* "메시지": 추적이 켜져 있지만 메서드 이름과 응답 ID만 추적됩니다.
* "자세한 내용": 추적이 켜져 있습니다. 전체 rpc 메시지가 추적됩니다.

추적이 켜져 있으면 콘텐츠가 *%temp%\VisualStudio\LSP* 디렉토리의 파일에 기록됩니다. 로그는 명명 형식 *[LanguageClientName]-[Datetime 스탬프].log*를 따릅니다. 현재 추적은 열려 있는 폴더 시나리오에만 사용할 수 있습니다. 언어 서버를 활성화하기 위해 단일 파일을 열면 진단 추적 지원이 없습니다.

### <a name="custom-messages"></a>사용자 지정 메시지

표준 언어 서버 프로토콜에 속하지 않는 언어 서버로 메시지를 전달하고 받는 것을 용이하게 하기 위한 API가 있습니다. 사용자 지정 메시지를 처리하려면 언어 클라이언트 클래스에서 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) 인터페이스를 구현합니다. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) 라이브러리는 언어 클라이언트와 언어 서버 간에 사용자 지정 메시지를 전송하는 데 사용됩니다. LSP 언어 클라이언트 확장은 다른 Visual Studio 확장과 마찬가지로 사용자 지정 메시지를 통해 확장의 Visual Studio에 추가 기능(LSP에서 지원되지 않음)을 추가하도록 결정할 수 있습니다.

#### <a name="receive-custom-messages"></a>사용자 지정 메시지 받기

언어 서버에서 사용자 지정 메시지를 받으려면 [ILanguageClientCustomMessage에서](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) 속성을 구현 하고 사용자 지정 메시지를 처리하는 방법을 알고 있는 개체를 반환합니다. 아래 예:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="send-custom-messages"></a>사용자 지정 메시지 보내기

언어 서버에 사용자 지정 메시지를 보내려면 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)에서 [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) 메서드를 구현합니다. 이 메서드는 언어 서버가 시작되고 메시지를 받을 준비가 되면 호출됩니다. [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) 개체는 매개 변수로 전달되며 [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API를 사용하여 언어 서버로 메시지를 보낼 수 있습니다. 아래 예:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>중간 레이어

경우에 따라 확장 개발자가 언어 서버에서 주고받은 LSP 메시지를 가로챌 수 있습니다. 예를 들어 확장 개발자는 특정 LSP 메시지에 대해 전송된 메시지 매개 변수를 변경하거나 LSP 기능(예: 완료)에 대해 언어 서버에서 반환된 결과를 수정할 수 있습니다. 필요한 경우 확장 개발자는 MiddleLayer API를 사용하여 LSP 메시지를 가로챌 수 있습니다.

각 LSP 메시지에는 가로채기를 위한 자체 중간 계층 인터페이스가 있습니다. 특정 메시지를 가로채려면 해당 메시지에 대한 중간 계층 인터페이스를 구현하는 클래스를 만듭니다. 그런 다음 언어 클라이언트 클래스에서 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) 인터페이스를 구현하고 [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) 속성에서 개체의 인스턴스를 반환합니다. 아래 예:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

중간 계층 기능은 아직 개발 중이며 아직 포괄적이지 않습니다.

## <a name="sample-lsp-language-server-extension"></a>샘플 LSP 언어 서버 확장

Visual Studio에서 LSP 클라이언트 API를 사용하여 샘플 확장의 소스 코드를 보려면 VSSDK-확장성-샘플 [LSP 샘플을](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)참조하십시오.

## <a name="faq"></a>FAQ

**나는 Visual Studio에서 풍부한 기능 지원을 제공하기 위해 LSP 언어 서버를 보완하는 사용자 지정 프로젝트 시스템을 구축하고 싶습니다.**

Visual Studio의 LSP 기반 언어 서버에 대한 지원은 열려 있는 [폴더 기능에](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) 의존하며 사용자 지정 프로젝트 시스템이 필요하지 않도록 설계되었습니다. [여기에](https://github.com/Microsoft/VSProjectSystem)지침에 따라 사용자 지정 프로젝트 시스템을 빌드할 수 있지만 설정과 같은 일부 기능은 작동하지 않을 수 있습니다. LSP 언어 서버의 기본 초기화 논리는 현재 열려 있는 폴더의 루트 폴더 위치를 전달하는 것이므로 사용자 지정 프로젝트 시스템을 사용하는 경우 언어 서버가 제대로 시작할 수 있도록 초기화 중에 사용자 지정 논리를 제공해야 할 수 있습니다.

**디버거 지원을 추가하려면 어떻게 해야 합니까?**

향후 릴리스에서 일반적인 [디버깅 프로토콜에](https://code.visualstudio.com/docs/extensionAPI/api-debugging) 대한 지원을 제공할 예정입니다.

**이미 VS 지원 언어 서비스(예: JavaScript)가 설치되어 있는 경우 추가 기능(예: linting)을 제공하는 LSP 언어 서버 확장을 설치할 수 있습니까?**

예, 하지만 모든 기능이 제대로 작동 하지 않습니다. LSP 언어 서버 확장의 궁극적인 목표는 Visual Studio에서 기본적으로 지원되지 않는 언어 서비스를 사용하도록 설정하는 것입니다. LSP 언어 서버를 사용하여 추가 지원을 제공하는 확장을 만들 수 있지만 IntelliSense와 같은 일부 기능(예: IntelliSense)은 원활한 환경이 아닙니다. 일반적으로 LSP 언어 서버 확장은 기존 언어 를 확장하지 않고 새로운 언어 환경을 제공하는 데 사용하는 것이 좋습니다.

**완성된 LSP 언어 서버 VSIX는 어디에서 게시하나요?**

마켓플레이스 지침은 [여기를](walkthrough-publishing-a-visual-studio-extension.md)참조하십시오.

## <a name="see-also"></a>참조

- [다른 언어에 대한 Visual Studio 편집기 지원 추가](../ide/adding-visual-studio-editor-support-for-other-languages.md)
