---
title: C++ 관련 MSBuild 작업 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 6393e771f9e9ed862d21397dabacdb3f3808c386
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633150"
---
# <a name="msbuild-tasks-specific-to-c"></a>C++ 관련 MSBuild 작업

작업은 빌드 프로세스 동안 실행되는 코드를 제공합니다. C++가 설치되면 MSBuild와 함께 설치되는 작업 외에 다음 작업을 사용할 수 있습니다. 자세한 내용은 [MSBuild(C++) 개요](/cpp/build/msbuild-visual-cpp-overview)를 참조하세요.

 각 작업에 대한 매개 변수 외에도 모든 작업에는 다음과 같은 매개 변수가 있습니다.

| 매개 변수 | 설명 |
|-------------------| - |
| `Condition` | 선택적 `String` 매개 변수입니다.<br /><br /> MSBuild 엔진이 이 작업의 실행 여부를 결정하는 데 사용하는 `Boolean` 식입니다. MSBuild에서 지원되는 조건에 대한 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요. |
| `ContinueOnError` | 선택적 매개 변수입니다. 다음 값 중 하나를 포함할 수 있습니다.<br /><br /> -   **WarnAndContinue** 또는 **true**. 작업이 실패할 경우 [Target](../msbuild/target-element-msbuild.md) 요소의 후속 작업과 빌드가 계속 실행되고 작업에서 발생한 모든 오류가 경고로 처리됩니다.<br />-   **ErrorAndContinue**. 작업이 실패할 경우 `Target` 요소의 후속 작업과 빌드가 계속 실행되고 작업에서 발생한 모든 오류가 오류로 처리됩니다.<br />-   **ErrorAndStop** 또는 **false**(기본값). 작업이 실패할 경우 `Target` 요소의 나머지 작업이 실행되지 않고 전체 `Target` 요소와 빌드가 실패한 것으로 간주됩니다.<br /><br /> .NET Framework 4.5 이전 버전은 `true` 및 `false` 값만 지원합니다.<br /><br /> 자세한 내용은 [방법: 작업의 오류 무시](../msbuild/how-to-ignore-errors-in-tasks.md)를 참조하세요. |

### <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[BscMake 작업](../msbuild/bscmake-task.md)|Microsoft Browse Information Maintenance Utility 도구(*bscmake.exe*)를 래핑합니다.|
|[CL 작업](../msbuild/cl-task.md)|C++ 컴파일러 도구(*cl.exe*)를 래핑합니다.|
|[CPPClean 작업](../msbuild/cppclean-task.md)|C++ 프로젝트가 빌드될 때 MSBuild가 만드는 임시 파일을 삭제합니다.|
|[ClangCompile 작업](../msbuild/clangcompile-task.md)|C++ 컴파일러 도구(*clang.exe*)를 래핑합니다.|
|[CustomBuild 작업](../msbuild/custombuild-task.md)|C++ 컴파일러 도구(*cmd.exe*)를 래핑합니다.|
|[FXC 작업](../msbuild/fxc-task.md)|빌드 프로세스에서 HLSL 셰이더 컴파일러를 사용합니다.|
|[GetOutOfDateItems](../msbuild/getoutofdateitems-task.md)|이전 tlog를 읽고, 새 tlog를 쓰며, 최신 상태가 아닌 항목 집합을 반환합니다. (도우미 작업)|
|[GetOutputFileName](../msbuild/getoutputfilename-task.md)|출력 디렉터리 또는 전체 파일 이름만 지정하거나 아무것도 지정하지 않는 cl 및 기타 도구의 출력 파일 이름을 가져옵니다. (도우미 작업)|
|[LIB 작업](../msbuild/lib-task.md)|Microsoft 32비트 라이브러리 관리자 도구(*lib.exe*)를 래핑합니다.|
|[링크 작업](../msbuild/link-task.md)|C++ 링커 도구(*link.exe*)를 래핑합니다.|
|[MIDL 작업](../msbuild/midl-task.md)|MIDL(Microsoft 인터페이스 정의 언어) 컴파일러 도구(*midl.exe*)를 래핑합니다.|
|[MT 작업](../msbuild/mt-task.md)|Microsoft 매니페스트 도구(*mt.exe*)를 래핑합니다.|
|[MultiToolTask 작업](../msbuild/multitooltask-task.md)|설명이 없습니다.|
|[ParallelCustomBuild 작업](../msbuild/parallelcustombuild-task.md)|[CustomBuild 작업](../msbuild/custombuild-task.md)의 병렬 인스턴스를 실행합니다.|
|[RC 작업](../msbuild/rc-task.md)|Microsoft Windows 리소스 컴파일러 도구(*rc.exe*)를 래핑합니다.|
|[SetEnv 작업](../msbuild/setenv-task.md)|지정된 환경 변수의 값을 설정하거나 삭제합니다.|
|[TrackedVCToolTask 기본 클래스](../msbuild/trackedvctooltask-base-class.md)|[VCToolTask](../msbuild/vctooltask-base-class.md)에서 상속됩니다.|
|[VCMessage 작업](../msbuild/vcmessage-task.md)|빌드 중에 경고 메시지 및 오류 메시지를 로깅합니다. (확장할 수 없습니다. 내부 전용입니다.)|
|[VCToolTask 기본 클래스](../msbuild/vctooltask-base-class.md)|[ToolTask](/dotnet/api/microsoft.build.utilities.tooltask)에서 상속됩니다.|
|[XDCMake 작업](../msbuild/xdcmake-task.md)|XML 문서 주석( *.xdc*) 파일을 *.xml* 파일에 병합하는 XML 문서 도구(*xdcmake.exe*)를 래핑합니다.|
|[XSD 작업](../msbuild/xsd-task.md)|소스에서 스키마 또는 클래스 파일을 생성하는 XML 스키마 정의 도구(*xsd.exe*)를 래핑합니다. *다음 참고를 참조하세요.*|
|[MSBuild 참조](../msbuild/msbuild-reference.md)|MSBuild 시스템 요소에 대해 설명합니다.|
|[작업](../msbuild/msbuild-tasks.md)|결합되어 빌드를 생성할 수 있는 코드 단위인 작업에 대해 설명합니다.|
|[작업 작성](../msbuild/task-writing.md)|작업을 만드는 방법을 설명합니다.|

> [!NOTE]
> Visual Studio 2017부터 *xsd.exe*에 대한 C++ 프로젝트 지원이 사용되지 않습니다. *CppCodeProvider.dll*을 수동으로 GAC에 추가하여 **Microsoft.VisualC.CppCodeProvider** API를 계속 사용할 수 있습니다.
