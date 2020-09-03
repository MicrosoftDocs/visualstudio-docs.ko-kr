---
title: MSBuild 명령줄 참조 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, msbuild.exe
- MSBuild, command line reference
- msbuild.exe
ms.assetid: edaa65ec-ab8a-42a1-84cb-d76d5b2f4584
caps.latest.revision: 61
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d40bfefb1f89496b538612dfa1819cc6d65c76c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181062"
---
# <a name="msbuild-command-line-reference"></a>MSBuild 명령줄 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild.exe를 사용하여 프로젝트 또는 솔루션 파일을 빌드할 경우 여러 스위치를 포함하여 프로세스의 다양한 측면을 지정할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>인수  
  
|인수|설명|  
|--------------|-----------------|  
|`ProjectFile`|지정한 프로젝트 파일에 대상을 빌드합니다. 프로젝트 파일을 지정하지 않으면 MSBuild는 현재 작업 디렉터리에서 "proj"로 끝나는 파일 이름 확장명을 검색하고 해당 파일을 사용합니다. 이 인수에 대해 Visual Studio 솔루션 파일을 지정할 수도 있습니다.|  
  
## <a name="switches"></a>스위치  
  
|스위치|약식|설명|  
|------------|----------------|-----------------|  
|/help|/? 또는 /h|사용 정보를 표시합니다. 다음 명령을 예로 들 수 있습니다.<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/ds|빌드된 구성과 노드에 대한 해당 구성의 예약 상태와 관련된 자세한 정보를 빌드 로그 끝에 표시합니다.|  
|/ignoreprojectextensions: `extensions`|/ignore: `extensions`|빌드할 프로젝트 파일을 결정할 때 지정된 확장명을 무시합니다. 다음 예제에서와 같이 여러 확장명은 세미콜론이나 쉼표로 구분합니다.<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/maxcpucount[:`number`]|/m[:`number`]|빌드할 때 사용할 동시 프로세스의 최대 수를 지정합니다. 이 스위치를 포함하지 않으면 기본값은 1입니다. 값을 지정하지 않고 이 스위치를 포함하는 경우, MSBuild는 컴퓨터의 최대 프로세서 수만큼 사용합니다. 자세한 내용은 [병렬로 여러 프로젝트 빌드](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)를 참조 하세요.<br /><br /> 다음 예제에서는 세 가지 MSBuild 프로세스를 사용해서 빌드하도록 MSBuild에 지시하여 세 프로젝트를 동시에 빌드할 수 있도록 합니다.<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/noautoresponse|/noautorsp|MSBuild.rsp 파일을 자동으로 포함하지 않도록 합니다.|  
|/nodeReuse:`value`|/nr:`value`|MSBuild 노드를 다시 사용하거나 다시 사용하지 않도록 설정합니다. 다음 값을 지정할 수 있습니다.<br /><br /> -   **True**. 노드는 후속 빌드에 사용될 수 있도록 빌드가 완료된 후에도 남습니다(기본값).<br />-   **False**. 빌드가 완료된 후에는 노드가 남지 않습니다.<br /><br /> 노드는 실행되고 있는 프로젝트에 해당됩니다. **/Maxcpucount** 스위치를 포함 하는 경우 여러 노드가 동시에 실행 될 수 있습니다.|  
|/nologo||시작 배너 또는 저작권 메시지를 표시하지 않습니다.|  
|/preprocess[:`filepath`]|/pp[:`filepath`]|가져올 모든 파일을 인라인하고 해당 경계를 표시하여 집계된 단일 프로젝트 파일을 만듭니다. 이 스위치를 사용하여 가져올 파일, 파일을 가져올 위치 및 빌드에 사용할 파일을 보다 쉽게 확인할 수 있습니다. 이 스위치를 사용하면 프로젝트가 빌드되지 않습니다.<br /><br /> `filepath`를 지정하는 경우 집계된 프로젝트 파일은 파일에 출력됩니다. 그렇지 않은 경우 출력이 콘솔 창에 나타납니다.<br /><br /> 요소를 사용 하 여 `Import` 프로젝트 파일을 다른 프로젝트 파일에 삽입 하는 방법에 대 한 자세한 내용은 [Import 요소 (MSBuild)](../msbuild/import-element-msbuild.md) 및 [방법: 여러 프로젝트 파일에서 동일한 대상 사용](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)을 참조 하세요.|  
|/property:`name`=`value`|/p:`name`=`value`|지정된 프로젝트 수준 속성을 설정하거나 재정의합니다. 여기서 `name`은 속성 이름이고 `value`는 속성 값입니다. 각 속성을 개별적으로 지정하거나 다음 예제에서와 같이 세미콜론 또는 쉼표를 사용하여 여러 속성을 구분합니다.<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/target:`targets`|/t:`targets`|프로젝트에서 지정된 대상을 빌드합니다. 각 대상을 개별적으로 지정하거나 다음 예제에서와 같이 세미콜론 또는 쉼표를 사용하여 여러 대상을 구분합니다.<br /><br /> `/target:Resources;Compile`<br /><br /> 이 스위치를 사용하여 대상을 지정하는 경우 프로젝트 파일의 `DefaultTargets` 특성에서 다른 대상 대신 이 대상이 실행됩니다. 자세한 내용은 [대상 빌드 순서](../msbuild/target-build-order.md) 및 [방법: 먼저 빌드할 대상 지정](../msbuild/how-to-specify-which-target-to-build-first.md)을 참조 하세요.<br /><br /> 대상은 작업 그룹입니다. 자세한 내용은 [대상](../msbuild/msbuild-targets.md)을 참조하세요.|  
|/toolsversion:`version`|/tv:`version`|다음 예제에서와 같이 프로젝트 빌드에 사용할 도구 집합 버전을 지정합니다. `/toolsversion:3.5`<br /><br /> 이 스위치를 사용 하면 프로젝트를 빌드하고 [프로젝트 요소 (MSBuild)](../msbuild/project-element-msbuild.md)에 지정 된 버전과 다른 버전을 지정할 수 있습니다. 자세한 내용은 [ToolsVersion 설정 재정의](../msbuild/overriding-toolsversion-settings.md)를 참조 하세요.<br /><br /> MSBuild 4.5의 경우 `version`에 대해 2.0, 3.5 및 4.0 값을 지정할 수 있습니다. 4\.0을 지정하는 경우 `VisualStudioVersion` 빌드 속성은 사용할 하위 도구 집합을 지정합니다. 자세한 내용은의 [MSBuild 도구 집합(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)의 하위 도구 집합 섹션을 참조하세요.<br /><br /> 도구 집합은 애플리케이션을 빌드하는 데 사용되는 작업, 대상 및 도구로 구성됩니다. 도구에는 csc.exe 및 vbc.exe와 같은 컴파일러가 포함됩니다. 도구 집합에 대 한 자세한 내용은 [도구 집합 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [표준 및 사용자 지정 도구 집합 구성](../msbuild/standard-and-custom-toolset-configurations.md)및 [다중 대상](../msbuild/msbuild-multitargeting-overview.md)지정을 참조 하세요. **참고:**  도구 집합 버전은 프로젝트가 실행 되도록 빌드된 .NET Framework 버전인 대상 프레임 워크와 동일 하지 않습니다. 자세한 내용은 [대상 프레임 워크 및 대상 플랫폼](../msbuild/msbuild-target-framework-and-target-platform.md)을 참조 하세요.|  
|/validate:[`schema`]|/val[`schema`]|프로젝트 파일의 유효성을 검사하고 유효성 검사에 통과하면 프로젝트를 빌드합니다.<br /><br /> `schema`를 지정하지 않으면 기본 스키마에 대해 프로젝트의 유효성을 검사합니다.<br /><br /> `schema`를 지정하는 경우 지정한 스키마에 대해 프로젝트의 유효성을 검사합니다.<br /><br /> 설정 예: `/validate:MyExtendedBuildSchema.xsd`|  
|/verbosity:`level`|/v:`level`|빌드 로그에 표시할 정보의 양을 지정합니다. 각 로거는 해당 로거에 대해 설정한 자세한 정도를 기준으로 이벤트를 표시합니다.<br /><br /> 자세한 정도를 `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` 및 `diag[nostic]`으로 지정할 수 있습니다.<br /><br /> 설정 예: `/verbosity:quiet`|  
|/version|/ver|버전 정보만 표시합니다. 프로젝트는 빌드되지 않았습니다.|  
|@`file`||텍스트 파일에서 명령줄 스위치를 삽입합니다. 여러 파일을 사용하는 경우 별도로 지정합니다. 자세한 내용은 [지시 파일](../msbuild/msbuild-response-files.md)을 참조 하세요.|  
  
### <a name="switches-for-loggers"></a>로거 스위치  
  
|스위치|약식|설명|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/clp:`parameters`|지정한 매개 변수를 콘솔 로거에 전달하면 콘솔 창에 빌드 정보가 표시됩니다. 다음 매개 변수를 지정할 수 있습니다.<br /><br /> -   **PerformanceSummary**. 작업, 대상 및 프로젝트에 소요된 시간을 표시합니다.<br />-   **Summary**. 끝에 오류 및 경고 요약을 표시합니다.<br />-   **NoSummary**. 끝에 오류 및 경고 요약을 표시하지 않습니다.<br />-   **ErrorsOnly**. 오류만 표시합니다.<br />-   **WarningsOnly**. 경고만 표시합니다.<br />-   **NoItemAndPropertyList**. 자세한 정도를 `diagnostic`으로 설정한 경우 각 프로젝트 빌드의 시작 부분에 표시될 항목 및 속성 목록을 표시하지 않습니다.<br />-   **ShowCommandLine**. `TaskCommandLineEvent` 메시지를 표시합니다.<br />-   **ShowTimestamp**. 원하는 메시지에 접두사로 타임스탬프를 표시합니다.<br />-   **ShowEventId**. 각각 시작된 이벤트, 완료된 이벤트 및 메시지에 대한 이벤트 ID를 표시합니다.<br />-   **ForceNoAlign**. 텍스트를 콘솔 버퍼 크기에 맞추지 않습니다.<br />-   **DisableConsoleColor**. 모든 로깅 메시지에 기본 콘솔 색을 사용합니다.<br />-   **DisableMPLogging**. 다중 프로세서가 아닌 모드에서 실행할 때 출력의 다중 프로세서 로깅 스타일을 사용하지 않습니다.<br />-   **EnableMPLogging**. 다중 프로세서가 아닌 모드에서 실행할 때도 다중 프로세서 로깅 스타일을 사용합니다. 이 로깅 스타일은 기본적으로 설정되어 있습니다.<br />-   **Verbosity**. 이로 거에 대 한 **/verbosity** 설정을 재정의 합니다.<br /><br /> 다음 예제에서와 같이 여러 매개 변수는 세미콜론이나 쉼표로 구분합니다.<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/dfl|MSBuild 노드의 빌드 출력을 자체 파일에 로깅합니다. 이러한 파일의 초기 위치는 현재 디렉터리입니다. 기본적으로 파일 이름은 "MSBuild*NodeId*.log"입니다. **/FileLoggerParameters** 스위치를 사용 하 여 파일의 위치와 fileLogger 거에 대 한 기타 매개 변수를 지정할 수 있습니다.<br /><br /> **/FileLoggerParameters** 스위치를 사용 하 여 로그 파일의 이름을로 하는 경우 배포 된로 거는 해당 이름을 템플릿으로 사용 하 고 각 노드에 대 한 로그 파일을 만들 때 해당 이름에 노드 ID를 추가 합니다.|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|/dl:`central logger`*`forwarding logger`|MSBuild의 이벤트를 로그하고 각 노드에 다른 로거 인스턴스를 연결합니다. 여러 로거를 지정하려면 각 로거를 개별적으로 지정합니다.<br /><br /> 로거 구문을 사용하여 로거를 지정합니다. 로 거 구문에 대해서는 아래의 **/logger** 스위치를 참조 하세요.<br /><br /> 다음 예에서는 이 스위치의 사용 방법을 보여 줍니다.<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *[number]*|/fl[`number`]|현재 디렉터리의 단일 파일에 빌드 출력을 로깅합니다. `number`를 지정하지 않으면 출력 파일 이름은 msbuild.log로 지정됩니다. `number`를 지정하는 경우 출력 파일 이름은 msbuild`n`.log로 지정됩니다. 여기서 n은 `number`입니다. `Number`는 1에서 9의 숫자일 수 있습니다.<br /><br /> **/FileLoggerParameters** 스위치를 사용 하 여 파일의 위치와 fileLogger 거에 대 한 기타 매개 변수를 지정할 수 있습니다.|  
|/fileloggerparameters:[number]<br /><br /> `parameters`|/flp:[ `number`] `parameters`|파일 로거 및 분산된 파일 로거에 대해 추가 매개 변수를 지정합니다. 이 스위치가 있으면 해당/**filelogger [** `number` **]** 스위치가 있음을 의미 합니다. `Number`는 1에서 9의 숫자일 수 있습니다.<br /><br /> **/Consoleloggerparameters**에 대해 나열 된 모든 매개 변수를 사용할 수 있습니다. 다음 매개 변수 중 하나 이상을 사용할 수도 있습니다.<br /><br /> -   **LogFile**. 빌드 로그가 기록되는 로그 파일의 경로입니다. 분산된 파일 로거는 해당 로그 파일의 이름 앞에 이 경로를 추가합니다.<br />-   **Append**. 빌드 로그가 로그 파일에 추가될지 또는 로그 파일을 덮어쓸지를 결정합니다. 이 스위치를 설정하면 빌드 로그가 로그 파일에 추가됩니다. 이 스위치가 없으면 기존 로그 파일의 내용을 덮어씁니다.<br />     append 스위치를 포함하면 true 또는 false의 설정에 관계없이 로그가 추가됩니다. append 스위치를 포함하지 않으면 로그를 덮어씁니다.<br />     이 경우 파일을 덮어씁니다. `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     이 경우 파일에 추가됩니다. `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     이 경우 파일에 추가됩니다. `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Encoding**. 파일에 대한 인코딩을 지정합니다(예: UTF-8, 유니코드 또는 ASCII).<br /><br /> 다음 예제에서는 경고 및 오류에 대한 별도의 로그 파일을 생성합니다.<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> 다음 예제에서는 다른 가능성을 보여 줍니다.<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|/logger:<br /><br /> `logger`|/l:`logger`|MSBuild의 이벤트를 로그하는 데 사용할 로거를 지정합니다. 여러 로거를 지정하려면 각 로거를 개별적으로 지정합니다.<br /><br /> `logger`에 대해 다음 구문을 사용합니다. `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> `LoggerClass`에 대해 다음 구문을 사용합니다. `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> 어셈블리가 정확히 하나의 로거를 포함하는 경우 로거 클래스를 지정할 필요가 없습니다.<br /><br /> `LoggerAssembly`에 대해 다음 구문을 사용합니다. `{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> 로거 매개 변수는 선택적이며 정확히 입력한 대로 로거에 전달됩니다.<br /><br /> 다음 예에서는 **/logger** 스위치를 사용 합니다.<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/noconlog|기본 콘솔 로거를 사용하지 않도록 설정하고 콘솔에 이벤트를 로깅하지 않습니다.|  
  
## <a name="example"></a>예제  
 다음 예제에서는 `rebuild` 프로젝트의 `MyProject.proj` 대상을 빌드합니다.  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>예  
 MSBuild.exe를 사용하여 보다 복잡한 빌드를 수행할 수 있습니다. 예를 들어 이 프로그램을 사용하여 솔루션에 특정 프로젝트의 특정 대상을 빌드할 수 있습니다. 다음 예제에서는 `NotInSolutionFolder` 프로젝트를 다시 빌드하고, `InSolutionFolder` 솔루션 폴더에 있는 `NewFolder` 프로젝트를 정리합니다.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>관련 항목  
 [MSBuild 참조](../msbuild/msbuild-reference.md)   
 [일반적인 MSBuild 프로젝트 속성](../msbuild/common-msbuild-project-properties.md)
