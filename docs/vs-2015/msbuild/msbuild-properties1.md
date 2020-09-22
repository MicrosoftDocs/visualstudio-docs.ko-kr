---
title: MSBuild Properties1 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2399ff36639732f20babef368a1d9e2f6758a1c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841906"
---
# <a name="msbuild-properties1"></a>MSBuild Properties1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

빌드를 구성하는 데 사용될 수 있는 이름/값 쌍인 속성은 작업에 값을 전달하고, 조건을 평가하고, 프로젝트 파일 전체에서 참조할 값을 저장하는 데 유용합니다.  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>프로젝트 파일에서 속성 정의 및 참조  
 속성 이름을 포함하는 요소를 [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) 요소의 자식으로 만들어 속성을 선언합니다. 예를 들어 다음 XML은 값이 `Build`인 `BuildDir` 속성을 만듭니다.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 프로젝트 파일 전체에서 $(`PropertyName`) 구문을 사용하여 속성을 참조합니다. 예를 들어 이전 예제의 속성은 $(BuildDir)을 사용하여 참조합니다.  
  
 속성을 다시 정의하여 속성값을 변경할 수 있습니다. 다음 XML을 사용하면 `BuildDir` 속성에 새 값을 제공할 수 있습니다.  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 속성은 프로젝트 파일에 표시되는 순서대로 평가됩니다. 이전 값을 할당한 후에 `BuildDir`의 새 값을 선언해야 합니다.  
  
## <a name="reserved-properties"></a>예약된 속성  
 MSBuild는 몇 개의 속성 이름을 예약하여 프로젝트 파일과 MSBuild 이진 파일에 대한 정보를 저장합니다. 이러한 속성은 다른 속성과 마찬가지로 $ 표기법을 사용하여 참조됩니다. 예를 들어 $(MSBuildProjectFile)은 파일 확장명을 포함한 프로젝트 파일의 전체 파일 이름을 반환합니다.  
  
 자세한 내용은 [방법: 프로젝트 파일의 이름 또는 위치 참조](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) 및 [MSBuild 예약 된 속성 및 잘 알려진 속성](../msbuild/msbuild-reserved-and-well-known-properties.md)을 참조 하세요.  
  
## <a name="environment-properties"></a>환경 속성  
 예약된 속성을 참조하는 것과 같이 프로젝트 파일에서 환경 변수를 참조할 수 있습니다. 예를 들어 프로젝트 파일에서 `PATH` 환경 변수를 사용하려면 $(Path)를 사용합니다. 프로젝트에 환경 속성과 이름이 같은 속성 정의가 포함되어 있으면 프로젝트의 속성이 환경 변수의 값을 재정의합니다.  
  
 각 MSBuild 프로젝트에는 격리된 환경 블록을 가지고 있습니다. 오직 읽거나 자체 블록에 기록만 합니다.  MSBuild는 프로젝트 파일을 평가하거나 빌드하기 전에 속성 컬렉션을 초기화하는 경우에만 환경 변수를 읽습니다. 그 후 환경 속성은 고정됩니다. 즉, 각 생성된 도구가 같은 이름과 값으로 시작합니다.  
  
 생성 된 도구 내에서 환경 변수의 현재 값을 가져오려면 GetEnvironmentVariable [속성 함수](../msbuild/property-functions.md) 를 사용 합니다. 그러나 작업 매개 변수 <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>를 사용하는 메서드가 좋습니다. 이 문자열 배열에 설정된 환경 속성은 시스템 환경 변수에 영향을 주지 않고 생성된 도구에 전달할 수 있습니다.  
  
> [!TIP]
> 모든 환경 변수가 읽어들여져 초기 속성이 되는 것은 아닙니다. "386" 같은 유효한 MSBuild 속성 이름이 아닌 모든 환경 변수는 무시됩니다.  
  
 자세한 내용은 [방법: 빌드 시 환경 변수 사용](../msbuild/how-to-use-environment-variables-in-a-build.md)을 참조 하세요.  
  
## <a name="registry-properties"></a>레지스트리 속성  
 다음 구문을 사용하여 시스템 레지스트리 값을 읽을 수 있습니다. 여기서 `Hive`는 HKEY_LOCAL_MACHINE과 같은 레지스트리 하이브, `Key`는 키 이름, `SubKey`는 하위 키 이름, `Value`는 하위 키의 값입니다.  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 기본 하위 키 값을 가져오려면 `Value`를 생략합니다.  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 이 레지스트리 값을 사용하여 빌드 속성을 초기화할 수 있습니다. 예를 들어 Visual Studio 웹 브라우저 홈 페이지를 나타내는 빌드 속성을 만들려면 다음 코드를 사용합니다.  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>전역 속성  
 MSBuild를 사용 하면 **/property** (또는 **/p**) 스위치를 사용 하 여 명령줄에서 속성을 설정할 수 있습니다. 이러한 전역 속성값은 프로젝트 파일에서 설정되는 속성값을 재정의합니다. 여기에는 환경 속성이 포함되지만 변경할 수 없는 예약된 속성은 포함되지 않습니다.  
  
 다음 예제에서는 전역 `Configuration` 속성을 `DEBUG`로 설정합니다.  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 MSBuild 작업의 `Properties` 특성을 사용하여 다중 프로젝트 빌드의 자식 프로젝트에 대해 전역 속성을 설정하거나 수정할 수도 있습니다. 자세한 내용은 [MSBuild 작업](../msbuild/msbuild-task.md)을 참조 하세요.  
  
 프로젝트 태그에 `TreatAsLocalProperty` 특성을 사용하여 속성을 지정할 경우, 해당 전역 속성 값은 프로젝트 파일에 설정된 속성 값을 재정의하지 않습니다. 자세한 내용은 [Project 요소 (MSBuild)](../msbuild/project-element-msbuild.md) 및 [방법: 여러 옵션을 사용 하 여 동일한 소스 파일 빌드](../msbuild/how-to-build-the-same-source-files-with-different-options.md)를 참조 하세요.  
  
## <a name="property-functions"></a>속성 함수  
 .NET Framework 버전 4부터는 속성 함수를 사용하여 MSBuild 스크립트를 평가할 수 있습니다. MSBuild 작업을 사용하지 않고도 시스템 시간을 읽고 문자열을 비교하며 정규식을 일치시키고 빌드 스크립트 내에서 여러 가지 다른 작업을 수행할 수 있습니다.  
  
 문자열(인스턴스) 메서드를 사용하면 모든 속성값에 대해 작업을 수행할 수 있으며 대부분의 시스템 클래스에 대해 정적 메서드를 호출할 수 있습니다. 예를 들어 다음과 같이 빌드 속성을 오늘 날짜로 설정할 수 있습니다.  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 자세한 내용 및 속성 함수 목록은 [속성 함수](../msbuild/property-functions.md)를 참조 하세요.  
  
## <a name="creating-properties-during-execution"></a>실행 중에 속성 만들기  
 `Target` 요소 외부에 배치되는 속성의 경우 빌드의 평가 단계에서 값이 할당됩니다. 후속 실행 단계 중에 다음과 같이 속성을 만들거나 수정할 수 있습니다.  
  
- 모든 작업에서 속성을 내보낼 수 있습니다. 속성을 내보내려면 [Task](../msbuild/task-element-msbuild.md) 요소에 `PropertyName` 특성이 포함된 자식 [Output](../msbuild/output-element-msbuild.md) 요소가 있어야 합니다.  
  
- [CreateProperty](../msbuild/createproperty-task.md) 작업에서 속성을 내보낼 수 있습니다. 이러한 사용법은 더 이상 사용되지 않습니다.  
  
- .NET Framework 3.5부터는 `Target` 요소가 속성 선언이 들어 있을 수 있는 `PropertyGroup` 요소를 포함할 수 있습니다.  
  
## <a name="storing-xml-in-properties"></a>속성에 XML 저장  
 속성은 작업에 값을 전달하거나 로깅 정보를 표시하는 데 사용할 수 있는 임의의 XML을 포함할 수 있습니다. 다음 예제에서는 XML 및 기타 속성 참조를 포함하는 값이 있는 `ConfigTemplate` 속성을 보여 줍니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 개별 속성값을 사용하여 속성 참조를 바꿉니다. 속성값은 나타나는 순서대로 할당됩니다. 따라서 이 예제의 경우 `$(MySupportedVersion)`, `$(MyRequiredVersion)`, `$(MySafeMode)`가 이미 정의되어 있어야 합니다.  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>참고 항목  
 [MSBuild 개념](../msbuild/msbuild-concepts.md)  
 [MSBuild](msbuild.md)  
 [방법: 빌드 시 환경 변수 사용](../msbuild/how-to-use-environment-variables-in-a-build.md)   
 [방법: 프로젝트 파일의 이름 또는 위치 참조](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)   
 [방법: 동일한 소스 파일을 다른 옵션을 사용 하 여 빌드](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [MSBuild의 예약 된 속성 및 잘 알려진 속성](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Property 요소 (MSBuild)](../msbuild/property-element-msbuild.md)
