---
title: Visual Studio에서 작업 영역 빌드 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62553330"
---
# <a name="workspace-build"></a>작업 영역 빌드

[Open Folder](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 시나리오에서 빌드를 지원 하려면 [작업 영역](workspaces.md)에 대 한 [인덱싱된](workspace-indexing.md) 및 [파일 컨텍스트](workspace-file-contexts.md) 데이터 뿐만 아니라 실행할 빌드 작업을 제공 하는 extender가 필요 합니다.

다음은 확장에서 필요한 항목에 대 한 개요입니다.

## <a name="build-file-context"></a>빌드 파일 컨텍스트

- 공급자 팩터리
  - `ExportFileContextProviderAttribute``supportedContextTypeGuids`에서 적용 가능한 모든 상수로 사용 되는 특성 `string``BuildContextTypes`
  - `IWorkspaceProviderFactory<IFileContextProvider>`을 구현합니다.
  - 파일 컨텍스트 공급자
    - `FileContext`각 빌드 작업 및 지원 되는 구성에 대해를 반환 합니다.
      - <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>의 `contextType`
      - `context` 는 <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> 빌드 구성으로 속성을 사용 하 여을 구현 `Configuration` 합니다 (예: `"Debug|x86"` `"ret"` 또는 `null` 해당 하지 않는 경우). 또는 인스턴스를 사용 <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> 합니다. 구성 값은 인덱싱된 파일 데이터 값의 구성과 일치 **해야** 합니다.

## <a name="indexed-build-file-data-value"></a>인덱싱된 빌드 파일 데이터 값

- 공급자 팩터리
  - `ExportFileScannerAttribute``IReadOnlyCollection<FileDataValue>`지원 되는 형식의 특성
  - `IWorkspaceProviderFactory<IFileScanner>`을 구현합니다.
- 파일 스캐너 `ScanContentAsync<T>`
  - 가 형식 인수인 경우 데이터를 반환 합니다. `FileScannerTypeConstants.FileDataValuesType`
  - 로 생성 된 각 구성에 대 한 파일 데이터 값을 반환 합니다.
    - `type` 는 `BuildConfigurationContext.ContextTypeGuid`
    - `context` 빌드 구성으로 (예:, `"Debug|x86"` `"ret"` 또는 `null` 해당 하지 않는 경우). 이 값은 파일 컨텍스트의 구성과 일치 **해야 합니다** .

## <a name="build-file-context-action"></a>빌드 파일 컨텍스트 작업

- 공급자 팩터리
  - `ExportFileContextActionProvider``supportedContextTypeGuids`에서 적용 가능한 모든 상수로 사용 되는 특성 `string``BuildContextTypes`
  - `IWorkspaceProviderFactory<IFileContextActionProvider>`을 구현합니다.
- 작업 공급자 `IFileContextActionProvider.GetActionsAsync`
  - 지정 된 `IFileContextAction` 값과 일치 하는를 반환 합니다. `FileContext.ContextType`
- 파일 컨텍스트 작업
  - 을 구현 합니다. `IFileContextAction`<xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` 속성 반환 `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId``0x1000`빌드, `0x1010` 다시 빌드 또는 정리에 대 한입니다. `0x1020`

>[!NOTE]
>는 `FileDataValue` 인덱싱해야 하므로 작업 영역을 여는 시간과 전체 빌드 기능을 위해 파일을 검색 하는 시점 사이에 약간의 시간이 걸립니다. 이전에 캐시 된 인덱스가 없기 때문에 폴더를 처음 열 때 지연 시간이 표시 됩니다.

## <a name="reporting-messages-from-a-build"></a>빌드에서 메시지 보고

빌드는 두 가지 방법 중 하나를 통해 정보, 경고 및 오류 메시지를 사용자에 게 노출 시킬 수 있습니다. 간단한 방법은 다음과 같이를 사용 하 고를 제공 하는 것입니다 <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> .

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` 그리고 `BuildMessage.LogMessage` 사용자에 게 정보가 표시 되는 동작을 제어 합니다. `BuildMessage.TaskType`이외의 값 `None` 은 지정 된 세부 정보를 사용 하 여 **오류 목록** 항목을 생성 합니다. `LogMessage`는 항상 **출력** 도구 창의 **빌드** 창에 출력 됩니다.

또는 확장이 **오류 목록** 또는 **빌드** 창과 직접 상호 작용할 수 있습니다. `pszProjectUniqueName`의 인수가 무시 되는 Visual Studio 2017 버전 15.7 이전 버전에 버그가 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> .

>[!WARNING]
>호출자는 `IFileContextAction.ExecuteAsync` 인수에 대 한 임의의 기본 구현을 제공할 수 있습니다 `IProgress<IFileContextActionProgressUpdate>` . 직접 호출 하지 않습니다 `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` . 현재이 인수를 사용 하기 위한 일반적인 지침은 없지만 이러한 지침은 변경 될 수 있습니다.

## <a name="build-related-apis"></a>빌드 관련 Api

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> 빌드 구성 정보를 제공 합니다.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService><xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>사용자에 게를 표시 합니다.

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.js설정 및 launch.vs.js

파일에 대 한 tasks.vs.js또는 launch.vs.js를 작성 하는 방법에 대 한 자세한 내용은 [빌드 및 디버그 작업 사용자 지정](../ide/customize-build-and-debug-tasks-in-visual-studio.md)을 참조 하세요.

## <a name="next-steps"></a>다음 단계

* [언어 서버 프로토콜](language-server-protocol.md) -언어 서버를 Visual Studio에 통합 하는 방법에 대해 알아봅니다.