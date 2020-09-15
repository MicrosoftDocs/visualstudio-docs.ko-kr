---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 6fd0fc6fd4f2e54c0d15f649139b649797f8336f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89042866"
---
### <a name="tooltaskextension-parameters"></a>ToolTaskExtension 매개 변수

이 작업은 <xref:Microsoft.Build.Utilities.Task> 클래스에서 상속되는 <xref:Microsoft.Build.Utilities.ToolTask> 클래스에서 상속되는 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 클래스에서 상속됩니다. 이 상속 체인은 매개 변수에서 파생되는 작업에 해당 매개 변수 몇 개를 추가합니다.

다음 표에서는 기본 클래스의 매개 변수에 대해 설명합니다.

| 매개 변수 | 설명 |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | 선택적 `bool` 매개 변수입니다.<br /><br /> `true`로 설정된 경우 이 작업은 명령줄이 stdout으로 복사되지 않도록 **/Q**를 *cmd.exe* 명령줄로 전달합니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | 선택적 `String` 배열 매개 변수입니다.<br /><br /> 세미콜론으로 구분된 환경 변수 정의의 배열입니다. 각 정의는 환경 변수 이름 및 값을 등호로 구분하여 지정해야 합니다. 이 변수는 생성된 실행 파일에 전달되면서 일반 환경 블록에 추가되거나 일부 일반 환경 블록을 재정의합니다. 예들 들어 `Variable1=Value1;Variable2=Value2`입니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | 선택적 `Int32` 읽기 전용 출력 매개 변수입니다.<br /><br /> 실행한 명령에서 제공하는 종료 코드를 지정합니다. 작업에서 오류를 기록했지만 프로세스가 종료 코드 0(성공)을 반환한 경우 이는 -1로 설정됩니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | 선택적 `bool` 매개 변수입니다.<br /><br /> `true`인 경우 표준 오류 스트림에서 받은 모든 메시지가 오류로 기록됩니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | 선택적 `bool` 매개 변수입니다.<br /><br /> `true`인 경우 표준 오류 스트림에서 받은 모든 메시지가 오류로 기록됩니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | 선택적 `String` 매개 변수입니다.<br /><br /> 표준 출력 스트림의 텍스트를 기록할 때 적용할 중요도입니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | 선택적 `String` 매개 변수입니다.<br /><br /> 표준 출력 스트림의 텍스트를 기록할 때 적용할 중요도입니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | 선택적 `Int32` 매개 변수입니다.<br /><br /> 작업 실행 파일이 얼마 후에 종료될 지를 밀리초 단위로 지정합니다. 기본값은 시간 제한이 없음을 나타내는 `Int.MaxValue`입니다. 제한 시간(밀리초)입니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | 선택적 `string` 매개 변수입니다.<br /><br /> 프로젝트에서 작업의 ToolName을 재정의하기 위해 이를 구현할 수 있습니다. 작업에서는 ToolName을 유지하기 위해 이를 재정의할 수 있습니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | 선택적 `string` 매개 변수입니다.<br /><br /> 작업에서 내부 실행 파일을 로드할 위치를 지정합니다. 이 매개 변수를 지정하지 않으면 작업에서는 MSBuild를 실행하고 있는 프레임워크 버전에 해당하는 SDK 설치 경로가 사용됩니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | 선택적 `bool` 매개 변수입니다.<br /><br /> `true`로 설정된 경우 이 작업은 명령줄에 대한 배치 파일을 만들고 명령을 직접 실행하는 대신 명령 처리기를 사용하여 실행합니다. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | 선택적 `bool` 매개 변수입니다.<br /><br /> `true`로 설정된 경우 작업이 실행 중이면 이 작업이 노드를 발생시킵니다. |
