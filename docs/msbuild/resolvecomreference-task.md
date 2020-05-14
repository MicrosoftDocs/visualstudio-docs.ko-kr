---
title: ResolveComReference 작업 | Microsoft Docs
ms.date: 07/25/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fdc6c6ccd58bcc83cc37ff3a9f7888af837ed6e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595204"
---
# <a name="resolvecomreference-task"></a>ResolveComReference 작업

하나 이상의 형식 라이브러리 이름 또는 *.tlb* 파일 목록을 가져온 후 해당 형식 라이브러리를 디스크의 위치로 확인합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `ResolveCOMReference` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`DelaySign`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 공개 키를 어셈블리에 배치합니다. `false`인 경우 어셈블리에 완전히 서명합니다.|
|`EnvironmentVariables`|선택적 `String[]` 매개 변수입니다.<br /><br /> 등호로 구분된 환경 변수 쌍의 배열입니다. 이러한 변수는 생성된 *tlbimp.exe* 및 *aximp.exe*에 전달되면서 일반 환경 블록에 추가되거나 일부 일반 환경 블록을 재정의합니다.|
|`ExecuteAsTool`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 해당 대상 프레임워크 out-of-proc에서 *tlbimp.exe* 및 *aximp.exe*를 실행하여 필요한 래퍼 어셈블리를 생성합니다. 이 매개 변수는 멀티 타기팅을 허용합니다.|
|`IncludeVersionInInteropName`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`인 경우 typelib 버전이 래퍼 이름이 포함됩니다. 기본값은 `false`입니다.|
|`KeyContainer`|선택적 `String` 매개 변수입니다.<br /><br /> 퍼블릭/프라이빗 키 쌍을 보관할 컨테이너를 지정합니다.|
|`KeyFile`|선택적 `String` 매개 변수입니다.<br /><br /> 퍼블릭/프라이빗 키 쌍을 포함할 항목을 지정합니다.|
|`NoClassMembers`|선택적 `Boolean` 매개 변수입니다.|
|`ResolvedAssemblyReferences`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 확인된 어셈블리 참조를 지정합니다.|
|`ResolvedFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 디스크에서 이 작업에 대한 입력으로 제공된 형식 라이브러리의 물리적 위치에 해당하는 정규화된 파일을 지정합니다.|
|`ResolvedModules`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.|
|`SdkToolsPath`|선택적 <xref:System.String?displayProperty=fullName> 매개 변수입니다.<br /><br /> `ExecuteAsTool`이 `true`인 경우 이 매개 변수를 대상이 되는 프레임워크 버전의 SDK 도구 경로로 설정해야 합니다.|
|`StateFile`|선택적 `String` 매개 변수입니다.<br /><br /> COM 구성 요소 타임스탬프에 대한 캐시 파일을 지정합니다. 이 매개 변수가 없으면 실행할 때마다 모든 래퍼가 다시 생성됩니다.|
|`TargetFrameworkVersion`|선택적 `String` 매개 변수입니다.<br /><br /> 프로젝트 대상 프레임워크 버전을 지정합니다.<br /><br /> 기본값은 `String.Empty`입니다. 대상 프레임워크를 기반으로 하는 참조에 대한 필터링이 없음을 의미합니다.|
|`TargetProcessorArchitecture`|선택적 `String` 매개 변수입니다.<br /><br /> 기본 대상 프로세서 아키텍처를 지정합니다. 변환 후에 *tlbimp.exe*/machine 플래그에 전달됩니다.<br /><br /> 매개 변수 값은 <xref:Microsoft.Build.Utilities.ProcessorArchitecture>의 멤버여야 합니다.|
|`TypeLibFiles`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> COM 참조에 대한 형식 라이브러리 파일 경로를 지정합니다. 이 매개 변수에 포함된 항목에는 항목 메타데이터가 포함될 수 있습니다. 자세한 내용은 아래 [TypeLibFiles 항목 메타데이터](#typelibfiles-item-metadata) 섹션을 참조하세요.|
|`TypeLibNames`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> 확인할 형식 라이브러리 이름을 지정합니다. 이 매개 변수에 포함된 항목에는 일부 항목 메타데이터가 포함되어야 합니다. 자세한 내용은 아래 [TypeLibNames 항목 메타데이터](#typelibnames-item-metadata) 섹션을 참조하세요.|
|`WrapperOutputDirectory`|선택적 `String` 매개 변수입니다.<br /><br /> 생성된 interop 어셈블리를 배치할 디스크의 위치입니다. 이 항목 메타데이터를 지정하지 않으면 작업은 프로젝트 파일이 있는 디렉터리의 절대 경로를 사용합니다.|

## <a name="typelibnames-item-metadata"></a>TypeLibNames 항목 메타데이터

 다음 표에서는 `TypeLibNames` 매개 변수에 전달된 항목에 사용 가능한 항목 메타데이터를 설명합니다.

|메타데이터|Description|
|--------------|-----------------|
|`GUID`|필수 항목 메타데이터입니다.<br /><br /> 형식 라이브러리의 GUID입니다. 이 항목 메타데이터를 지정하지 않으면 작업이 실패합니다.|
|`VersionMajor`|필수 항목 메타데이터입니다.<br /><br /> 형식 라이브러리의 주 버전입니다. 이 항목 메타데이터를 지정하지 않으면 작업이 실패합니다.|
|`VersionMinor`|필수 항목 메타데이터입니다.<br /><br /> 형식 라이브러리의 부 버전입니다. 이 항목 메타데이터를 지정하지 않으면 작업이 실패합니다.|
|`EmbedInteropTypes`|선택적 `Boolean` 메타데이터입니다.<br /><br />  `true`인 경우 interop DLL을 생성하지 않고 이 참조의 interop 형식을 어셈블리에 직접 포함합니다.|
|`LocaleIdentifier`|선택적 항목 메타데이터입니다.<br /><br /> 형식 라이브러리의 로캘 식별자(또는 LCID)입니다. 이 항목 메타데이터는 사용자, 지역 또는 애플리케이션에서 선호되는 인간 언어를 나타내는 32비트 값으로 지정됩니다. 이 항목 메타데이터를 지정하지 않으면 작업에서 기본 로캘 식별자 “0”이 사용됩니다.|
|`WrapperTool`|선택적 항목 메타데이터입니다.<br /><br /> 이 형식 라이브러리의 어셈블리 래퍼를 생성하는 데 사용되는 래퍼 도구를 지정합니다. 이 항목 메타데이터를 지정하지 않으면 작업에서 기본 래퍼 도구 “tlbimp”가 사용됩니다. 사용 가능한 typelib(대/소문자 구분)는 다음과 같습니다.<br /><br /> -   `Primary`: COM 구성 요소에 대한 이미 생성된 주 interop 어셈블리를 사용하려면 이 래퍼 도구를 사용합니다. 이 래퍼 도구를 사용할 경우 래퍼 출력 디렉터리를 지정하지 마세요. 지정하면 작업이 실패합니다.<br />-   `TLBImp`: COM 구성 요소에 대한 interop 어셈블리를 생성하려면 이 래퍼 도구를 사용합니다.<br />-   `AXImp`: ActiveX 컨트롤에 대한 interop 어셈블리를 생성하려면 이 래퍼 도구를 사용합니다.|

## <a name="typelibfiles-item-metadata"></a>TypeLibFiles 항목 메타데이터

 다음 표에서는 `TypeLibFiles` 매개 변수에 전달된 항목에 사용 가능한 항목 메타데이터를 설명합니다.

|메타데이터|Description|
|--------------|-----------------|
|`EmbedInteropTypes`|선택적 `Boolean` 매개 변수입니다.<br /><br />  `true`인 경우 interop DLL을 생성하지 않고 이 참조의 interop 형식을 어셈블리에 직접 포함합니다.|
|`WrapperTool`|선택적 항목 메타데이터입니다.<br /><br /> 이 형식 라이브러리의 어셈블리 래퍼를 생성하는 데 사용되는 래퍼 도구를 지정합니다. 이 항목 메타데이터를 지정하지 않으면 작업에서 기본 래퍼 도구 “tlbimp”가 사용됩니다. 사용 가능한 typelib(대/소문자 구분)는 다음과 같습니다.<br /><br /> -   `Primary`: COM 구성 요소에 대한 이미 생성된 주 interop 어셈블리를 사용하려면 이 래퍼 도구를 사용합니다. 이 래퍼 도구를 사용할 경우 래퍼 출력 디렉터리를 지정하지 마세요. 지정하면 작업이 실패합니다.<br />-   `TLBImp`: COM 구성 요소에 대한 interop 어셈블리를 생성하려면 이 래퍼 도구를 사용합니다.<br />-   `AXImp`: ActiveX 컨트롤에 대한 interop 어셈블리를 생성하려면 이 래퍼 도구를 사용합니다.|

> [!NOTE]
> 형식 라이브러리를 고유하게 식별하기 위해 더 많은 정보를 제공할수록 작업이 디스크에서 올바른 파일로 확인될 가능성이 커집니다.

## <a name="remarks"></a>설명

이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [Task 기본 클래스](../msbuild/task-base-class.md)를 참조하세요.

이 작업을 수행하기 위해 COM DLL을 컴퓨터에 등록할 필요가 없습니다.

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
