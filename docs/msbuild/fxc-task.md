---
title: FXC 작업 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.fxc
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), FXC task
- FXC task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 67958a1a1ebb2ff382d0896e2fbaec6105c0c785
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279288"
---
# <a name="fxc-task"></a>FXC 작업

빌드 프로세스에서 HLSL 셰이더 컴파일러를 사용합니다.

## <a name="parameters"></a>매개 변수

다음 표에서는 **FXC** 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|선택적 **string[]** 매개 변수입니다.<br/><br/>포함 경로에 추가할 디렉터리를 하나 이상 지정합니다. 항목이 여러 개일 때에는 세미콜론으로 구분합니다.<br/><br/>대신 `/I[path]`를|
|**AdditionalOptions**|선택적 **string** 매개 변수입니다.|
|**AllResourcesBound**|선택적 **bool** 매개 변수입니다.<br/><br/>컴파일러에서는 셰이더가 참조할 수 있는 모든 리소스가 바인딩되어 있으며 셰이더 실행 기간에 정상 상태인 것으로 간주합니다. 셰이더 모델 5.1 이상에 사용할 수 있습니다.<br/><br/>대신 `/all_resources_bound`를|
|**AssemblerOutput**|선택적 **string** 매개 변수입니다.<br/><br/>어셈블리 언어 출력 파일의 콘텐츠를 지정합니다.<br/><br/>대신 `/Fc, /Fx`를<br/><br/>**NoListing**<br/>**AssemblyCode** - `Fc`를 사용합니다.<br/>**AssemblyCodeAndHex** - `Fx`를 사용합니다.|
|**AssemblerOutputFile**|선택적 **string** 매개 변수입니다.<br/><br/>어셈블리 코드 목록 파일의 파일 이름을 지정합니다.|
|**CompileD2DCustomEffect**|선택적 **bool** 매개 변수입니다.<br/><br/>픽셀 셰이더가 포함된 Direct2D 사용자 지정 효과를 컴파일합니다. 꼭짓점 또는 컴퓨팅 사용자 지정 효과에는 사용하지 마세요.|
|**ConsumeExportFile**|선택적 **string** 매개 변수입니다.|
|**DisableOptimizations**|선택적 **bool** 매개 변수입니다.<br/><br/>최적화를 사용하지 않도록 설정합니다.<br/><br/>`/Od`는 `/Gfp`를 의미하지만 출력은 `/Od /Gfp`와 동일하지 않을 수 있습니다.|
|**EnableDebuggingInformation**|선택적 **bool** 매개 변수입니다.<br/><br/>디버깅 정보를 사용하도록 설정합니다.|
|**EnableUnboundedDescriptorTables**|선택적 **bool** 매개 변수입니다.<br/><br/>셰이더에 범위가 제한되지 않은 리소스 배열의 선언이 포함될 수 있음을 컴파일러에 알립니다. 셰이더 모델 5.1 이상에 사용할 수 있습니다.<br/><br/>대신 `/enable_unbounded_descriptor_tables`를|
|**EntryPointName**|선택적 **string** 매개 변수입니다.<br/><br/>셰이더 진입점의 이름을 지정합니다.<br/><br/>대신 `/E[name]`를|
|**GenerateExportFile**|선택적 **string** 매개 변수입니다.|
|**GenerateExportShaderProfile**|선택적 **string** 매개 변수입니다.|
|**HeaderFileOutput**|선택적 **string** 매개 변수입니다.<br/><br/>개체 코드를 포함하는 헤더 파일의 이름을 지정합니다.<br/><br/>대신 `/Fh [name]`를|
|**ObjectFileOutput**|선택적 **string** 매개 변수입니다.<br/><br/>개체 파일의 이름을 지정합니다.<br/><br/>대신 `/Fo [name]`를|
|**PreprocessorDefinitions**|선택적 **string[]** 매개 변수입니다.<br/><br/>소스 파일에 대한 전처리 기호를 정의합니다.|
|**SetRootSignature**|선택적 **string** 매개 변수입니다.<br/><br/>셰이더 바이트코드에 루트 시그니처를 연결합니다. 셰이더 모델 5.0 이상에 사용할 수 있습니다.<br/><br/>대신 `/setrootsignature`를|
|**ShaderModel**|선택적 **string** 매개 변수입니다.<br/><br/>셰이더 모델을 지정합니다. 일부 셰이더 형식은 최신 셰이더 모델에서만 사용할 수 있습니다.<br/><br/>대신 `/T [type]_[model]`를|
|**ShaderType**|선택적 **string** 매개 변수입니다.<br/><br/>셰이더의 형식을 지정합니다.<br/><br/>대신 `/T [type]_[model]`를<br/><br/>**Effect** - `fx`를 사용합니다.<br/>**Vertex** - `vs`를 사용합니다.<br/>**Pixel** - `ps`를 사용합니다.<br/>**Geometry** - `gs`를 사용합니다.<br/>**Hull** - `hs`를 사용합니다.<br/>**Domain** - `ds`를 사용합니다.<br/>**Compute** - `cs`를 사용합니다.<br/>**Library** - `lib`를 사용합니다.<br/>**RootSignature** - 루트 시그니처 개체를 생성합니다.|
|**원본**|필수 **ITaskItem** 매개 변수입니다.|
|**SuppressStartupBanner**|선택적 **bool** 매개 변수입니다.<br/><br/>시작 배너 및 정보 메시지를 표시하지 않습니다.<br/><br/>대신 `/nologo`를|
|**TrackerLogDirectory**|선택적 **string** 매개 변수입니다.|
|**TreatWarningAsError**|선택적 **bool** 매개 변수입니다.<br/><br/>모든 컴파일러 경고를 오류로 처리합니다.<br/><br/>새 프로젝트인 경우 모든 컴파일에서 `/WX`를 사용하는 것이 좋습니다. 모든 경고를 해결하면 찾기 어려운 코드 오류를 최소화할 수 있습니다.|
|**VariableName**|선택적 **string** 매개 변수입니다.<br/><br/>헤더 파일의 변수 이름에 대한 이름을 지정합니다.<br/><br/>대신 `/Vn [name]`를|

## <a name="see-also"></a>참고 항목

[작업 참조](../msbuild/msbuild-task-reference.md)