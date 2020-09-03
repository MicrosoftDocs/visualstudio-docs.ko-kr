---
title: 언어 서버 프로토콜 확장 추가 | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740239"
---
# <a name="add-a-language-server-protocol-extension"></a>언어 서버 프로토콜 확장 추가

LSP (언어 서버 프로토콜)는 다양 한 코드 편집기에 언어 서비스 기능을 제공 하는 데 사용 되는 JSON RPC v 2.0 형식의 일반적인 프로토콜입니다. 개발자는 프로토콜을 사용 하 여 단일 언어 서버를 작성 하 여 해당 LSP를 지 원하는 다양 한 코드 편집기에 IntelliSense, 오류 진단, 모든 참조 찾기 등과 같은 언어 서비스 기능을 제공할 수 있습니다. 일반적으로 Visual Studio의 언어 서비스는 TextMate 문법 파일을 사용 하 여 구문 강조 표시와 같은 기본 기능을 제공 하거나 전체 Visual Studio 확장성 Api 집합을 사용 하 여 다양 한 데이터를 제공 하는 사용자 지정 언어 서비스를 작성 하 여 추가할 수 있습니다. LSP에 대 한 Visual Studio 지원을 통해 세 번째 옵션이 있습니다.

![Visual Studio의 언어 서버 프로토콜 서비스](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>언어 서버 프로토콜

![언어 서버 프로토콜 구현](media/lsp-implementation.png)

이 문서에서는 LSP 기반 언어 서버를 사용 하는 Visual Studio 확장을 만드는 방법을 설명 합니다. 이미 LSP 기반 언어 서버를 개발 했으며 Visual Studio에 통합 하려는 것으로 가정 합니다.

Visual Studio 내에서 지원 하기 위해 언어 서버는 모든 스트림 기반 전송 메커니즘을 통해 클라이언트 (Visual Studio)와 통신할 수 있습니다. 예를 들면 다음과 같습니다.

* 표준 입력/출력 스트림
* 명명된 파이프
* 소켓 (TCP 전용)

Visual Studio에서 LSP 및이에 대 한 지원은 Visual Studio 제품에 포함 되지 않은 언어 서비스를 등록 하는 것입니다. Visual Studio에서 기존 언어 서비스 (예: c #)를 확장 하는 것은 아닙니다. 기존 언어를 확장 하려면 언어 서비스의 확장성 가이드 (예: ["Roslyn" .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md))를 참조 하거나 [편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)을 참조 하세요.

프로토콜 자체에 대 한 자세한 내용은 [여기](https://github.com/Microsoft/language-server-protocol)에서 설명서를 참조 하세요.

샘플 언어 서버를 만드는 방법 또는 기존 언어 서버를 Visual Studio Code에 통합 하는 방법에 대 한 자세한 내용은 [여기](https://code.visualstudio.com/docs/extensions/example-language-server)에서 설명서를 참조 하세요.

## <a name="language-server-protocol-supported-features"></a>언어 서버 프로토콜 지원 기능

다음 표에서는 Visual Studio에서 지원 되는 LSP 기능을 보여 줍니다.

메시지 | Visual Studio에서 지원
--- | ---
initialize | 예
초기화됨 | 예
shutdown | 예
exit | 예
$/cancelrequest | 예
창/showMessage | 예
창/showMessageRequest | 예
창/logMessage | 예
원격 분석/이벤트 |
클라이언트/registerCapability |
client/unregisterCapability |
작업 영역/didChangeConfiguration | 예
작업 영역/didChangeWatchedFiles | 예
작업 영역/기호 | 예
작업 영역/executeCommand | 예
작업 영역/applyEdit | 예
textDocument/정보 진단 | 예
textDocument/didOpen | 예
textDocument/didChange | 예
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | 예
textDocument/didClose | 예
textDocument/완료 | 예
완료/해결 | 예
textDocument/가리키기 | 예
textDocument/서명 도움말 | 예
textDocument/참조 | 예
textDocument/documentHighlight | 예
textDocument/documentSymbol | 예
textDocument/서식 지정 | 예
textDocument/범위 서식 지정 | 예
textDocument/onTypeFormatting 지정 |
textDocument/정의 | 예
textDocument/codeAction | 예
textDocument/codeLens |
codeLens/해결 |
textDocument/documentLink |
documentLink/resolve |
textDocument/이름 바꾸기 | 예

## <a name="get-started"></a>시작하기

> [!NOTE]
> Visual Studio 2017 버전 15.8부터 공용 언어 서버 프로토콜에 대 한 지원은 Visual Studio에 기본 제공 됩니다. Preview [Language Server 클라이언트 VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) 버전을 사용 하 여 LSP 확장을 빌드한 경우 15.8 이상 버전으로 업그레이드 하면 작동이 중지 됩니다. 다음 작업을 수행 하 여 LSP 확장이 다시 작동 하도록 해야 합니다.
>
> 1. Microsoft Visual Studio Language Server Protocol Preview VSIX를 제거 합니다.
>
>    버전 15.8부터 Visual Studio에서 업그레이드를 수행할 때마다 미리 보기 VSIX가 자동으로 검색 되 고 제거 됩니다.
>
> 2. Nuget 참조를 [LSP 패키지](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)의 미리 보기가 아닌 최신 버전으로 업데이트 합니다.
>
> 3. VSIX 매니페스트에서 Microsoft Visual Studio 언어 서버 프로토콜 미리 보기 VSIX에 대 한 종속성을 제거 합니다.
>
> 4. VSIX가 설치 대상에 대해 Visual Studio 2017 버전 15.8 Preview 3을 하한값으로 지정 하는지 확인 합니다.
>
> 5. 다시 빌드하고 다시 배포합니다.

### <a name="create-a-vsix-project"></a>VSIX 프로젝트 만들기

LSP 기반 언어 서버를 사용 하 여 언어 서비스 확장을 만들려면 먼저 인스턴스에 대해 **Visual Studio 확장 개발** 워크 로드를 설치 했는지 확인 합니다.

다음으로 **파일**  >  **새로 만들기 프로젝트**  >  **Visual c #**  >  **확장성**  >  **VSIX 프로젝트**로 이동 하 여 새 VSIX 프로젝트를 만듭니다.

![vsix 프로젝트 만들기](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>언어 서버 및 런타임 설치

기본적으로 Visual Studio에서 LSP 기반 언어 서버를 지원 하기 위해 만든 확장에는 언어 서버 자체 또는 실행 하는 데 필요한 런타임이 포함 되지 않습니다. 확장 개발자는 필요에 따라 언어 서버와 런타임을 배포할 책임이 있습니다. 이 작업을 수행 하는 방법에는 여러 가지가 있습니다.

* 언어 서버는 VSIX에 콘텐츠 파일로 포함 될 수 있습니다.
* MSI를 만들어 언어 서버 및/또는 필요한 런타임을 설치 합니다.
* 사용자에 게 런타임 및 언어 서버를 얻는 방법을 알려 주는 Marketplace에 대 한 지침을 제공 합니다.

### <a name="textmate-grammar-files"></a>TextMate 문법 파일

LSP는 언어에 대해 텍스트 색 지정을 제공 하는 방법에 대 한 사양을 포함 하지 않습니다. Visual Studio에서 언어에 대 한 사용자 지정 색 지정을 제공 하기 위해 확장 개발자는 TextMate 문법 파일을 사용할 수 있습니다. 사용자 지정 TextMate 문법 또는 테마 파일을 추가 하려면 다음 단계를 수행 합니다.

1. 확장 내에 "문법" 이라는 폴더를 만듭니다 .이 폴더는 사용자가 선택 하는 모든 이름일 수 있습니다.

2. *문법* 폴더 안에 사용자 지정 색 지정을 제공 하는 모든 * \* tmlanguage*, * \* . info.plist*, * \* tmlanguage*또는 * \* json* 파일을 포함 합니다.

   > [!TIP]
   > *. Tmtheme* 파일은 범위가 Visual Studio 분류 (명명 된 색 키)에 매핑되는 방식을 정의 합니다. 지침을 보려면 *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \\ \<SKU> \Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg* 디렉터리에서 전역 *tmtheme* 파일을 참조할 수 있습니다.

3. .Pkgdef 파일을 만들고 다음과 비슷한 줄을 추가 *합니다* .

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. 파일을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다. **빌드** 작업을 **내용** 으로 변경 하 고 **VSIX에 포함** 속성을 **true**로 변경 합니다.

이전 단계를 완료 한 후에는 ' MyLang ' 라는 리포지토리 원본 (' MyLang '은 명확성을 위한 이름이 며 임의의 고유 문자열일 수 있음)으로 *문법* 폴더가 패키지의 설치 디렉터리에 추가 됩니다. 이 디렉터리의 모든 문법 (*tmlanguage* 파일) 및 테마 파일 (잠재력*테마* 파일)은로 선택 되며 textmate에 제공 된 기본 제공 문법을 대체 합니다. 문법 파일의 선언 된 확장이 열려 있는 파일의 확장명과 일치 하는 경우 TextMate은에서 한 단계씩 실행 됩니다.

## <a name="create-a-simple-language-client"></a>간단한 언어 클라이언트 만들기

### <a name="main-interface---ilanguageclient"></a>기본 인터페이스- [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

VSIX 프로젝트를 만든 후에 다음 NuGet 패키지를 프로젝트에 추가 합니다.

* [VisualStudio. LanguageServer](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> 이전 단계를 완료 한 후 NuGet 패키지에 대 한 종속성을 사용 하면 Newtonsoft.Js및 StreamJsonRpc 패키지도 프로젝트에 추가 됩니다. **이러한 패키지는 확장이 대상으로 하는 Visual Studio 버전에 설치 될 것이 확실 하지 않는 한 업데이트 하지 마십시오**. 어셈블리는 VSIX에 포함 되지 않습니다. 대신 Visual Studio 설치 디렉터리에서 선택 됩니다. 사용자의 컴퓨터에 설치 된 것 보다 최신 버전의 어셈블리를 참조 하는 경우에는 확장이 작동 하지 않습니다.

그러면 [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) 인터페이스를 구현 하는 새 클래스를 만들 수 있습니다 .이 인터페이스는 LSP 기반 언어 서버에 연결 하는 언어 클라이언트에 필요한 기본 인터페이스입니다.

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

구현 해야 하는 주요 메서드는 [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) 및 지 속성과 [async](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)입니다. [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) 는 Visual Studio에서 확장을 로드 하 고 언어 서버를 시작할 준비가 되었을 때 호출 됩니다. 이 메서드에서는 [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) 대리자를 즉시 호출 하 여 언어 서버를 시작 해야 함을 알리거나 추가 논리를 수행 하 고 [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) 를 나중에 호출할 수 있습니다. **언어 서버를 활성화 하려면 특정 지점에서 StartAsync를 호출 해야 합니다.**

[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) [async](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) 는 궁극적으로 호출 된 메서드를 호출 하 여 호출 합니다. 언어 서버를 시작 하 고이에 대 한 연결을 설정 하는 논리를 포함 합니다. 서버에 쓰고 서버에서 읽기 위한 스트림을 포함 하는 연결 개체를 반환 해야 합니다. 여기에서 throw 되는 모든 예외는 Visual Studio의 정보 표시줄 메시지를 통해 사용자에 게 표시 되 고 표시 됩니다.

### <a name="activation"></a>활성화

언어 클라이언트 클래스를 구현한 후에는 Visual Studio로 로드 되 고 활성화 되는 방법을 정의 하는 두 가지 특성을 정의 해야 합니다.

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio는 [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework)를 사용 하 여 해당 확장 요소를 관리 합니다. [Export](/dotnet/api/system.componentmodel.composition.exportattribute) 특성은이 클래스를 확장 지점으로 선택 하 고 적절 한 시간에 로드 해야 함을 Visual Studio에 나타냅니다.

MEF를 사용 하려면 VSIX 매니페스트에 자산으로 MEF를 정의 해야 합니다.

VSIX 매니페스트 디자이너를 열고 **자산** 탭으로 이동 합니다.

![MEF 자산 추가](media/lsp-add-asset.png)

새로 **만들기를 클릭 하** 여 새 자산을 만듭니다.

![MEF 자산 정의](media/lsp-define-asset.png)

* **유형**: VisualStudio
* **원본**: 현재 솔루션의 프로젝트
* **프로젝트**: [프로젝트]

### <a name="content-type-definition"></a>콘텐츠 형식 정의

현재는 파일 콘텐츠 유형별로 LSP 기반 언어 서버 확장을 로드 하는 유일한 방법입니다. 즉, [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)를 구현 하는 언어 클라이언트 클래스를 정의 하는 경우 확장을 로드 하는 데 사용할 파일 형식을 정의 해야 합니다. 정의 된 콘텐츠 형식과 일치 하는 파일이 열려 있지 않으면 확장이 로드 되지 않습니다.

이 작업은 하나 이상의 클래스를 정의 하 여 수행 됩니다 `ContentTypeDefinition` .

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

이전 예제에서는 파일 확장명이 *bar* 로 끝나는 파일에 대해 콘텐츠 형식 정의가 생성 됩니다. 콘텐츠 형식 정의에는 "bar" 라는 이름이 지정 되며 [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)에서 파생 되어야 합니다.

콘텐츠 형식 정의를 추가한 후 언어 클라이언트 클래스에서 언어 클라이언트 확장을 로드 하는 시기를 정의할 수 있습니다.

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

LSP 언어 서버에 대 한 지원을 추가 하는 경우 Visual Studio에서 사용자 고유의 프로젝트 시스템을 구현 하지 않아도 됩니다. 고객은 Visual Studio에서 단일 파일 또는 폴더를 열어 언어 서비스 사용을 시작할 수 있습니다. 실제로 LSP 언어 서버에 대 한 지원은 오픈 폴더/파일 시나리오 에서만 작동 하도록 설계 되었습니다. 사용자 지정 프로젝트 시스템을 구현 하는 경우 일부 기능 (예: 설정)이 작동 하지 않습니다.

## <a name="advanced-features"></a>고급 기능

### <a name="settings"></a>설정

사용자 지정 언어 서버 특정 설정에 대 한 지원도 사용할 수 있지만 여전히 향상 되 고 있습니다. 설정은 언어 서버에서 지 원하는 항목에 따라 달라 지 며 일반적으로 언어 서버에서 데이터를 내보내는 방식을 제어 합니다. 예를 들어 언어 서버에는 보고 된 최대 오류 수에 대 한 설정이 있을 수 있습니다. 확장 작성자는 특정 프로젝트에 대해 사용자가 변경할 수 있는 기본값을 정의 합니다.

다음 단계를 수행 하 여 설정에 대 한 지원을 LSP 언어 서비스 확장에 추가 합니다.

1. 설정 및 해당 기본값을 포함 하는 JSON 파일을 프로젝트에 추가 합니다 (예: *MockLanguageExtensionSettings.js*). 예를 들면 다음과 같습니다.

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. JSON 파일을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다. **빌드** 작업을 "콘텐츠"로 변경 하 고 "VSIX에 포함" 속성을 **true**로 변경 합니다.

3. ConfigurationSections을 구현 하 고 JSON 파일에 정의 된 설정에 대 한 접두사 목록을 반환 합니다 .이는 Visual Studio Code package.js의 구성 섹션 이름에 매핑됩니다.

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. .Pkgdef 파일을 프로젝트에 추가 합니다. 새 텍스트 파일을 추가 하 고 파일 확장명을 .pkgdef로 변경 합니다. .Pkgdef 파일에는 다음 정보가 포함 되어야 합니다.

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    샘플:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. .Pkgdef 파일을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다. **빌드** 작업을 **내용** 으로 변경 하 고 **VSIX에 포함** 속성을 **true**로 변경 합니다.

6. *Source.extension.vsixmanifest* 파일을 열고 **자산** 탭에서 자산을 추가 합니다.

   ![vspackage 자산 편집](media/lsp-add-vspackage-asset.png)

   * **유형**: VisualStudio. VsPackage
   * **원본**: 파일 시스템의 파일
   * **경로**: [ *.pkgdef* 파일 경로]

### <a name="user-editing-of-settings-for-a-workspace"></a>사용자가 작업 영역에 대 한 설정 편집

1. 사용자가 서버가 소유 하는 파일이 포함 된 작업 영역을 엽니다.
2. 사용자가 *. vs* 폴더에 *VSWorkspaceSettings.js의*파일을 추가 합니다.
3. 사용자가 서버에서 제공 하는 설정에 대 한 줄을 파일 * 의VSWorkspaceSettings.js* 에 추가 합니다. 예를 들면 다음과 같습니다.

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>진단 추적 사용

진단 추적을 사용 하도록 설정 하 여 클라이언트와 서버 간의 모든 메시지를 출력할 수 있으며,이는 문제를 디버깅할 때 유용할 수 있습니다. 진단 추적을 사용 하도록 설정 하려면 다음을 수행 합니다.

1. *에서VSWorkspaceSettings.js* 작업 영역 설정 파일을 열거나 만듭니다 ("작업 영역에 대 한 설정 편집" 참조).
2. 설정 json 파일에 다음 줄을 추가 합니다.

```json
{
    "foo.trace.server": "Off"
}
```

추적의 자세한 정도에는 세 가지 값을 사용할 수 있습니다.

* "Off": 추적이 완전히 해제 되어 있습니다.
* "Messages": 추적이 켜져 있지만 메서드 이름과 응답 ID만 추적 됩니다.
* "Verbose": 추적이 설정 되었습니다. 전체 rpc 메시지를 추적 합니다.

추적 기능이 설정 되 면 콘텐츠는 *%temp%\VisualStudio\LSP* 디렉터리의 파일에 기록 됩니다. 로그는 명명 형식 *[LanguageClientName]-[Datetime 스탬프] .log*를 따릅니다. 현재는 폴더 열기 시나리오에 대해서만 추적을 사용 하도록 설정할 수 있습니다. 단일 파일을 열어 언어 서버를 활성화 하는 경우 진단 추적을 지원 하지 않습니다.

### <a name="custom-messages"></a>사용자 지정 메시지

표준 언어 서버 프로토콜의 일부가 아닌 언어 서버에서 메시지를 전달 하 고 메시지를 수신 하는 데 사용할 수 있는 Api가 있습니다. 사용자 지정 메시지를 처리 하려면 언어 클라이언트 클래스에서 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) 인터페이스를 구현 합니다. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) library는 언어 클라이언트와 언어 서버 간에 사용자 지정 메시지를 전송 하는 데 사용 됩니다. LSP 언어 클라이언트 확장이 다른 Visual Studio 확장과 동일 하기 때문에 사용자 지정 메시지를 통해 확장에서 Visual Studio (다른 Visual Studio Api 사용)에 추가 기능 (LSP에서 지원 되지 않음)을 추가 하도록 결정할 수 있습니다.

#### <a name="receive-custom-messages"></a>사용자 지정 메시지 받기

언어 서버에서 사용자 지정 메시지를 수신 하려면 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) 에서 [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) 속성을 구현 하 고 사용자 지정 메시지를 처리 하는 방법을 알고 있는 개체를 반환 합니다. 예는 다음과 같습니다.

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

언어 서버에 사용자 지정 메시지를 보내려면 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)에서 [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) 메서드를 구현 합니다. 이 메서드는 언어 서버가 시작 되 고 메시지를 받을 준비가 되었을 때 호출 됩니다. [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) 개체는 매개 변수로 전달 됩니다. 그러면 [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) api를 사용 하 여 언어 서버에 메시지를 보낼 수 있습니다. 예는 다음과 같습니다.

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

### <a name="middle-layer"></a>중간 계층

확장 개발자가 언어 서버에서 보내고 받은 LSP 메시지를 가로챌 수 있는 경우가 있습니다. 예를 들어 확장 개발자는 특정 LSP 메시지에 대해 전송 되는 메시지 매개 변수를 변경 하거나 LSP 기능에 대해 언어 서버에서 반환 된 결과를 수정할 수 있습니다 (예: 완성). 이 작업이 필요한 경우 확장 개발자는 MiddleLayer API를 사용 하 여 LSP 메시지를 가로챌 수 있습니다.

각 LSP 메시지에는 가로채기를 위한 자체 중간 계층 인터페이스가 있습니다. 특정 메시지를 가로채는 메시지에 대 한 중간 계층 인터페이스를 구현 하는 클래스를 만듭니다. 그런 다음 언어 클라이언트 클래스에서 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) 인터페이스를 구현 하 고 [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) 속성에서 개체의 인스턴스를 반환 합니다. 예는 다음과 같습니다.

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

중간 계층 기능은 아직 개발 중 이며 포괄적이 지 않습니다.

## <a name="sample-lsp-language-server-extension"></a>샘플 LSP 언어 서버 확장

Visual Studio의 LSP 클라이언트 API를 사용 하 여 샘플 확장의 소스 코드를 확인 하려면 고가 중-확장성-샘플 [LSP 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)을 참조 하세요.

## <a name="faq"></a>FAQ

**Visual Studio에서 다양 한 기능 지원을 제공 하기 위해 사용자 지정 프로젝트 시스템을 빌드하여 사용자의 LSP 언어 서버를 보완 하 고 싶습니다. 어떻게 해야 하나요?**

Visual Studio의 LSP 기반 언어 서버에 대 한 지원은 [폴더 열기 기능](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) 을 사용 하며 사용자 지정 프로젝트 시스템을 요구 하지 않도록 설계 되었습니다. [여기](https://github.com/Microsoft/VSProjectSystem)에 설명 된 지침에 따라 사용자 지정 프로젝트 시스템을 빌드할 수 있지만 설정 등의 일부 기능은 작동 하지 않을 수 있습니다. LSP 언어 서버에 대 한 기본 초기화 논리는 현재 열려 있는 폴더의 루트 폴더 위치를 전달 하 여 사용자 지정 프로젝트 시스템을 사용 하는 경우 언어 서버가 제대로 시작 될 수 있도록 초기화 하는 동안 사용자 지정 논리를 제공 해야 할 수 있습니다.

**디버거 지원을 추가 어떻게 할까요??**

이후 릴리스에서는 [일반적인 디버깅 프로토콜](https://code.visualstudio.com/docs/extensionAPI/api-debugging) 에 대 한 지원을 제공 합니다.

**VS 지원 언어 서비스 (예: JavaScript)가 이미 설치 되어 있는 경우 추가 기능을 제공 하는 LSP 언어 서버 확장 (예: lint)을 계속 설치할 수 있나요?**

예, 하지만 모든 기능이 제대로 작동 하는 것은 아닙니다. LSP 언어 서버 확장의 궁극적인 목표는 Visual Studio에서 기본적으로 지원 되지 않는 언어 서비스를 사용 하도록 설정 하는 것입니다. LSP 언어 서버를 사용 하 여 추가 지원을 제공 하는 확장을 만들 수 있지만 일부 기능 (예: IntelliSense)은 원활한 환경이 아닙니다. 일반적으로는 LSP 언어 서버 확장을 사용 하 여 기존 항목을 확장 하지 않고 새로운 언어 환경을 제공 하는 것이 좋습니다.

**완료 된 LSP 언어 서버 VSIX는 어디에 게시 하나요?**

Marketplace 지침은 [여기](walkthrough-publishing-a-visual-studio-extension.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [다른 언어에 대한 Visual Studio 편집기 지원 추가](../ide/adding-visual-studio-editor-support-for-other-languages.md)
