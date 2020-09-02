---
title: GenerateResource 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 712d0de957ff7f780567c927fb1b18b100f8f6ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703526"
---
# <a name="generateresource-task"></a>GenerateResource 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.txt 및 .rest(XML 기반 리소스 형식) 파일과 런타임 이진 실행 파일에 포함되거나 위성 어셈블리로 컴파일할 수 있는 공용 언어 런타임 이진 .resources 파일 간을 변환합니다. 이 작업은 일반적으로 .txt 또는 .resx 파일을 .resource 파일로 변환하는 데 사용됩니다. `GenerateResource` 작업은 [resgen.exe](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)와 기능적으로 비슷합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 `GenerateResource` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|Description|  
|---------------|-----------------|  
|`AdditionalInputs`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 이 작업에 의해 수행되는 종속성 검사에 대한 추가 입력을 포함합니다. 예를 들어, 프로젝트 및 대상 파일은 일반적으로 입력에 해당하므로 이러한 항목이 업데이트되면 모든 리소스가 다시 생성됩니다.|  
|`EnvironmentVariables`|선택적 `String[]` 매개 변수입니다.<br /><br /> 일반 환경 블록 외에(또는 선택적으로 재정의) 생성된 resgen.exe에 전달되어야 하는 환경 변수의 이름-값 쌍 배열을 지정합니다.|  
|`ExcludedInputPaths`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 최신 검사를 하는 동안 추적된 입력이 무시되는 경로를 지정하는 항목의 배열을 지정합니다.|  
|`ExecuteAsTool`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 해당 대상 프레임워크 out-of-proc에서 tlbimp.exe 및 aximp.exe를 실행하여 필요한 래퍼 어셈블리를 생성합니다. 이 매개 변수는 `ResolveComReferences`의 멀티 타기팅을 허용합니다.|  
|`FilesWritten`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 디스크에 기록된 모든 파일의 이름을 포함합니다. 여기에는 캐시 파일(있는 경우)이 포함됩니다. 이 매개 변수는 Clean 구현에 유용합니다.|  
|`MinimalRebuildFromTracking`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 추적된 증분 빌드가 사용될지 여부를 지정하는 스위치를 가져오거나 설정합니다. `true`이면 증분 빌드가 켜지고 그렇지 않으면 다시 빌드가 강제로 실행됩니다.|  
|`NeverLockTypeAssemblies`|선택적 `Boolean` 매개 변수입니다.<br /><br /> .resources 파일과 같은 생성된 파일의 이름을 지정합니다. 이름을 지정하지 않는 경우 일치하는 입력 파일의 이름이 사용되고, 만들어진 .resources 파일이 입력 파일을 포함하는 디렉터리에 배치됩니다.|  
|`OutputResources`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> .resources 파일과 같은 생성된 파일의 이름을 지정합니다. 이름을 지정하지 않는 경우 일치하는 입력 파일의 이름이 사용되고, 만들어진 .resources 파일이 입력 파일을 포함하는 디렉터리에 배치됩니다.|  
|`PublicClass`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 강력한 형식의 리소스 클래스를 공용 클래스로 만듭니다.|  
|`References`|선택적 `String[]` 매개 변수입니다.<br /><br /> .resx 파일에서 형식을 로드할 참조입니다. Resx 파일 데이터 요소는 .NET 형식일 수 있습니다. .resx 파일이 읽힐 때 이 항목이 확인되어야 합니다. 일반적으로 표준 형식 로드 규칙을 사용하여 확인됩니다. `References`에 어셈블리를 제공하는 경우 우선적으로 적용됩니다.<br /><br /> 강력한 형식의 리소스에는 이 매개 변수가 필요하지 않습니다.|  
|`SdkToolsPath`|선택적 `String` 매개 변수입니다.<br /><br /> resgen.exe와 같은 SDK 도구에 대한 경로를 지정합니다.|  
|`Sources`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 변환할 항목을 지정합니다. 이 매개 변수에 전달된 항목은 다음 파일 확장명 중 하나를 사용해야 합니다.<br /><br /> -   `.txt`: 변환할 텍스트 파일의 확장명을 지정합니다. 텍스트 파일에는 문자열 리소스만 포함될 수 있습니다.<br />-   `.resx`: 변환할 XML 기반 리소스 파일의 확장명을 지정합니다.<br />-   `.restext`: .txt와 같은 형식을 지정합니다. 빌드 프로세스의 다른 소스 파일과 리소스를 포함하는 소스 파일 간을 명확히 구분하려는 경우에 이러한 다른 확장명이 도움이 됩니다.<br />-   `.resources`: 변환할 리소스 파일의 확장명을 지정합니다.|  
|`StateFile`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> .resx 입력 파일의 종속성 검사 속도를 향상시키는 데 사용할 선택적 캐시 파일의 경로를 지정합니다.|  
|`StronglyTypedClassName`|선택적 `String` 매개 변수입니다.<br /><br /> 강력한 형식의 리소스 클래스에 대한 클래스 이름을 지정합니다. 이 매개 변수를 지정하지 않으면 리소스 파일의 기본 이름이 사용됩니다.|  
|`StronglyTypedFilename`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 소스 파일의 파일 이름을 지정합니다. 이 매개 변수를 지정하지 않으면 클래스의 이름이 언어별 확장명을 포함하는 기본 파일 이름으로 사용됩니다. 예: `MyClass.cs`|  
|`StronglyTypedLanguage`|선택적 `String` 매개 변수입니다.<br /><br /> 강력한 형식의 리소스에 대한 클래스 소스를 생성할 때 사용할 언어를 지정합니다. 이 매개 변수는 CodeDomProvider에서 사용하는 언어 중 하나와 정확히 일치해야 합니다. 예를 들어 `VB` 또는 `C#`입니다.<br /><br /> 이 매개 변수에 값을 전달하여 강력한 형식의 리소스를 생성하도록 작업에 지시할 수 있습니다.|  
|`StronglyTypedManifestPrefix`|선택적 `String` 매개 변수입니다.<br /><br /> 강력한 형식의 리소스에 대해 생성된 클래스 소스에 사용할 리소스 네임스페이스 또는 매니페스트 접두사를 지정합니다.|  
|`StronglyTypedNamespace`|선택적 `String` 매개 변수입니다.<br /><br /> 강력한 형식의 리소스에 대해 생성된 클래스 소스에 사용할 네임스페이스를 지정합니다. 이 매개 변수를 지정하지 않으면 모든 강력한 형식의 리소스는 전역 네임스페이스에 있습니다.|  
|`TLogReadFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 매개 변수입니다.<br /><br /> 읽기 추적 로그를 나타내는 항목의 배열을 가져옵니다.|  
|`TLogWriteFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 매개 변수입니다.<br /><br /> 쓰기 추적 로그를 나타내는 항목의 배열을 가져옵니다.|  
|`ToolArchitecture`|선택적 [String](<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) 매개 변수입니다.<br /><br /> Tracker.exe를 ResGen.exe를 생성하는 데 사용해야 하는지 여부를 결정하는 데 사용됩니다.<br /><br /> <xref:Microsoft.Build.Utilities.ExecutableType> 열거형의 멤버로 구문 분석할 수 있어야 합니다. `String.Empty`이면 추론을 사용하여 기본 아키텍처를 결정합니다. Microsoft.Build.Utilities.ExecutableType 열거형의 멤버로 구문 분석할 수 있어야 합니다.|  
|`TrackerFrameworkPath`|선택 사항 <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> 필요합니다.<br /><br /> FileTracker.dll을 포함하는 적절한 .NET Framework 위치의 경로를 지정합니다.<br /><br /> 설정되면 사용자가 전달하는 FileTracker.dll의 비트가 사용하려는 ResGen.exe의 비트와 일치하는지 확인해야 합니다. 설정되지 않으면 작업이 현재 .NET Framework 버전에 따라 적절한 위치를 결정합니다.|  
|`TrackerLogDirectory`|선택 사항 <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> 필요합니다.<br /><br /> 이 작업 실행 시 발생하는 추적 로그를 추가할 중간 디렉터리를 지정합니다.|  
|`TrackerSdkPath`|선택 사항 <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> 필요합니다.<br /><br /> Tracker.exe를 포함하는 적절한 Windows SDK의 경로를 지정합니다.<br /><br /> 설정되면 사용자가 전달하는 Tracker.exe의 비트가 사용하려는 ResGen.exe의 비트와 일치하는지 확인해야 합니다. 설정되지 않으면 작업이 현재 Windows SDK에 따라 적절한 위치를 결정합니다.|  
|`TrackFileAccess`|선택적 [부울](<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) 매개 변수입니다.<br /><br /> true이면 입력 파일의 디렉터리가 상대 파일 경로를 확인하는 데 사용됩니다.|  
|`UseSourcePath`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 입력 파일의 디렉터리가 상대 파일 경로를 확인하는 데 사용되도록 지정합니다.|  
  
## <a name="remarks"></a>설명  
 .resx 파일에는 다른 리소스 파일에 대한 링크가 포함될 수 있으므로 .resx 및 .resource 파일 타임스탬프를 비교하는 것만으로는 출력이 최신인지 확인할 수 없습니다. 대신 `GenerateResource` 작업은 .resx 파일에 있는 링크를 따라 이동하여 연결된 파일의 타임스탬프도 확인합니다. 즉, `GenerateResource` 작업을 포함하는 `Inputs` 및 `Outputs` 특성은 일반적으로 사용하지 않아야 합니다. 실제로 실행되어야 할 때 건너뛸 수 있기 때문입니다.  
  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
 MSBuild 4.0을 사용하여 .NET 3.5 프로젝트를 대상으로 지정하면 x86 리소스에 대해 빌드가 실패할 수 있습니다. 이 문제를 해결하려면 대상을 AnyCPU 어셈블리로 빌드할 수 있습니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 `GenerateResource` 작업을 사용하여 `Resx` 항목 컬렉션으로 지정된 파일에서 .resources 파일을 생성합니다.  
  
```  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 `GenerateResource`작업은 \<LogicalName> 항목의 메타 데이터를 사용 하 여 \<EmbeddedResource> 어셈블리에 포함 된 리소스의 이름을로 합니다.  
  
 어셈블리 이름이 myAssembly라고 가정할 경우 다음 코드는 someQualifier.someResource.resources라는 포함된 리소스를 생성합니다.  
  
```  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 \<LogicalName>메타 데이터가 없으면 리소스 이름이 myAssembly. myresource .resources로 지정 됩니다.  이 예제는 Visual Basic 및 Visual C# 빌드 프로세스에만 적용됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
