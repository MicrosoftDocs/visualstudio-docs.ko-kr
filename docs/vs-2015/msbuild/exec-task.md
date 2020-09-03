---
title: Exec 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a69fc64c3371a2970c03ec0129d4c733f5ae9cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201758"
---
# <a name="exec-task"></a>Exec 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

지정된 인수를 사용하여 지정한 프로그램 또는 명령을 실행합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `Exec` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`Command`|필수 `String` 매개 변수입니다.<br /><br /> 실행할 명령입니다. Attrib와 같은 시스템 명령이나 program.exe, runprogram.bat 또는 setup.msi와 같은 실행 파일일 수 있습니다.<br /><br /> 이 매개 변수는 여러 줄의 명령을 포함할 수 있습니다. 또는 여러 개의 명령을 하나의 배치 파일에 추가하고 이 매개 변수를 사용하여 실행할 수 있습니다.|  
|`CustomErrorRegularExpression`|선택적 `String` 매개 변수입니다.<br /><br /> 도구 출력에서 오류 줄을 찾는 데 사용되는 정규식을 지정합니다. 예외적으로 형식이 지정된 출력을 생성하는 도구에 유용합니다.|  
|`CustomWarningRegularExpression`|선택적 `String` 매개 변수입니다.<br /><br /> 도구 출력에서 경고 줄을 찾는 데 사용되는 정규식을 지정합니다. 예외적으로 형식이 지정된 출력을 생성하는 도구에 유용합니다.|  
|`ExitCode`|선택적 `Int32` 읽기 전용 출력 매개 변수입니다.<br /><br /> 실행한 명령에서 제공하는 종료 코드를 지정합니다.|  
|`IgnoreExitCode`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 이 작업은 실행한 명령에서 제공하는 종료 코드를 무시합니다. 그렇지 않고 실행된 명령이 0이 아닌 종료 코드를 반환하는 경우 이 작업은 `false`를 반환합니다.|  
|`IgnoreStandardErrorWarningFormat`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `false`이면 표준 오류/경고 형식과 일치하는 줄을 출력에서 선택하고 오류/경고로 로깅합니다. `true`이면 이 동작을 사용하지 않도록 설정하세요.|  
|`Outputs`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 작업의 출력 항목을 포함합니다. `Exec` 작업은 자체적으로 이를 설정하지 않습니다. 대신 마치 설정된 것처럼 사용자가 제공하여 나중에 프로젝트에서 사용되도록 할 수 있습니다.|  
|`StdErrEncoding`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 캡처된 작업 표준 오류 스트림의 인코딩을 지정합니다. 기본값은 현재 콘솔 출력 인코딩입니다.|  
|`StdOutEncoding`|선택적 `String` 출력 매개 변수입니다.<br /><br /> 캡처된 작업 표준 출력 스트림의 인코딩을 지정합니다. 기본값은 현재 콘솔 출력 인코딩입니다.|  
|`WorkingDirectory`|선택적 `String` 매개 변수입니다.<br /><br /> 명령이 실행될 디렉터리를 지정합니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 수행하려는 작업에 대한 특정 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 작업을 사용할 수 없을 때 유용합니다. 그러나 좀 더 구체적인 작업과 달리 `Exec` 작업은 실행하는 도구 또는 명령에서 출력을 수집할 수 없습니다.  
  
 `Exec` 작업은 프로세스를 직접 호출하지 않고 cmd.exe를 호출합니다.  
  
 이 작업은 이 문서에 나와 있는 매개 변수 외에도 <xref:Microsoft.Build.Utilities.ToolTask> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Tooltaskextension 기본 클래스](../msbuild/tooltaskextension-base-class.md)를 참조 하세요.  
  
## <a name="example"></a>예제  
 다음 예제에서는 `Exec` 작업을 사용하여 명령을 실행합니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
