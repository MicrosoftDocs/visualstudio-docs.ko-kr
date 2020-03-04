---
title: MIDL 작업 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.TypeLibFormat
- vc.task.midl
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild (C++), MIDL task
- MIDL task (MSBuild (C++))
ms.assetid: 727efa8c-3336-40b8-8bef-ae6cbd77a422
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a43975244eaf064c9ed7608fa41c16854ca140f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633475"
---
# <a name="midl-task"></a>MIDL 작업

MIDL(Microsoft 인터페이스 정의 언어) 컴파일러 도구인 *midl.exe*를 래핑합니다. 자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)를 참조하세요.

## <a name="parameters"></a>매개 변수

 다음에서는 **MIDL** 작업의 매개 변수에 대해 설명합니다. 대부분의 작업 매개 변수 및 몇 가지 매개 변수 집합은 명령줄 옵션에 해당합니다.

- **AdditionalIncludeDirectories**

     선택적 **String[]** 매개 변수입니다.

     가져온 IDL 파일, 포함된 헤더 파일 및 ACF(애플리케이션 구성 파일)가 검색되는 디렉터리 목록에 디렉터리를 추가합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/I** 옵션을 참조하세요.

- **AdditionalOptions**

     선택적 **문자열** 매개 변수입니다.

     명령줄 옵션의 목록입니다. 예: /\<option1> /\<option2> /\<option#>. 이 매개 변수를 사용하여 다른 MIDL 작업 매개 변수로 표현되지 않는 명령줄 옵션을 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)를 참조하세요.

- **ApplicationConfigurationMode**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 IDL 파일에서 일부 ACF 키워드를 사용할 수 있습니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/app_config** 옵션을 참조하세요.

- **ClientStubFile**

     선택적 **문자열** 매개 변수입니다.

     RPC 인터페이스에 대한 클라이언트 스텁 파일의 이름을 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/cstub** 옵션을 참조하세요. 이 표의 **ServerStubFile** 매개 변수도 참조하세요.

- **CPreprocessOptions**

     선택적 **문자열** 매개 변수입니다.

     C/C++ 전처리기로 전달될 옵션을 지정합니다. 전처리기 옵션 목록을 공백으로 구분하여 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/cpp_opt** 옵션을 참조하세요.

- **DefaultCharType**

     선택적 **문자열** 매개 변수입니다.

     C 컴파일러에서 생성된 코드를 컴파일하는 데 사용할 기본 문자 형식을 지정합니다.

     각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

    |값|명령줄 옵션|
    |-----------|--------------------------|
    |**Signed**|**/char signed**|
    |**Unsigned**|**/char unsigned**|
    |**Ascii**|**/char ascii7**|

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/char** 옵션을 참조하세요.

- **DllDataFileName**

     선택적 **문자열** 매개 변수입니다.

     프록시 DLL에 대해 생성된 *dlldata* 파일의 파일 이름을 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/dlldata** 옵션을 참조하세요.

- **EnableErrorChecks**

     선택적 **문자열** 매개 변수입니다.

     생성된 스텁이 런타임에 수행할 오류 검사의 유형을 지정합니다.

     각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

    |값|명령줄 옵션|
    |-----------|--------------------------|
    |**없음**|**/error none**|
    |**EnableCustom**|**/error**|
    |**All**|**/error all**|

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/error** 옵션을 참조하세요.

- **ErrorCheckAllocations**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 메모리 부족 오류를 검사합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/error allocation** 옵션을 참조하세요.

- **ErrorCheckBounds**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 전송 길이 사양에 대해 규칙에 맞는 다양한 배열의 크기를 확인합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/error bounds_check** 옵션을 참조하세요.

- **ErrorCheckEnumRange**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 열거형 값이 허용되는 범위에 있는지 확인합니다.

     자세한 내용은 *midl.exe*에 대한 명령줄 도움말( **/?** )에서 **/error enum** 옵션을 참조하세요.

- **ErrorCheckRefPointers**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 null 참조 포인터가 클라이언트 스텁에 전달되지 않았는지 확인합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/error ref** 옵션을 참조하세요.

- **ErrorCheckStubData**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 서버 쪽에서 역 마샬링 예외를 catch하는 스텁을 생성하여 클라이언트에 다시 전파합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/error stub_data** 옵션을 참조하세요.

- **GenerateClientFiles**

     선택적 **문자열** 매개 변수입니다.

     컴파일러에서 RPC 인터페이스에 대해 클라이언트 쪽 C 소스 파일을 생성하는지 여부를 지정합니다.

     각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

    |값|명령줄 옵션|
    |-----------|--------------------------|
    |**없음**|**/client none**|
    |**Stub**|**/client stub**|

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/client** 옵션을 참조하세요.

- **GenerateServerFiles**

     선택적 **문자열** 매개 변수입니다.

     컴파일러에서 RPC 인터페이스에 대해 서버 쪽 C 소스 파일을 생성하는지 여부를 지정합니다.

     각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

    |값|명령줄 옵션|
    |-----------|--------------------------|
    |**없음**|**/server none**|
    |**Stub**|**/server stub**|

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/server** 옵션을 참조하세요.

- **GenerateStublessProxies**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 개체 인터페이스에 대해 스텁 없는 프록시와 함께 완전하게 해석된 스텁을 생성합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/Oicf** 옵션을 참조하세요.

- **GenerateTypeLibrary**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 형식 라이브러리 파일( *.tlb*)이 생성되지 않습니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/notlb** 옵션을 참조하세요.

- **HeaderFileName**

     선택적 **문자열** 매개 변수입니다.

     생성된 헤더 파일의 이름을 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/h** 또는 **/header** 옵션을 참조하세요.

- **IgnoreStandardIncludePath**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 MIDL 작업은 **AdditionalIncludeDirectories** 스위치를 사용하여 지정한 디렉터리만 검색하고 현재 디렉터리 및 INCLUDE 환경 변수에 지정된 디렉터리는 무시합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/no_def_idir** 옵션을 참조하세요.

- **InterfaceIdentifierFileName**

     선택적 **문자열** 매개 변수입니다.

     COM 인터페이스에 대한 *인터페이스 식별자 파일*의 이름을 지정합니다. 이 이름은 IDL 파일 이름에 "_i.c"를 추가하여 얻은 기본 이름을 재정의합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/iid** 옵션을 참조하세요.

- **LocaleID**

     선택적 **int** 매개 변수입니다.

     입력 파일, 파일 이름 및 디렉터리 경로에서 국가별 문자를 사용할 수 있도록 하는 *로캘 식별자*를 지정합니다. 10진수 로캘 식별자를 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/lcid** 옵션을 참조하세요. [로캘 식별자](/windows/desktop/intl/locale-identifiers)도 참조하세요.

- **MkTypLibCompatible**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 입력 파일의 형식이 *mktyplib.exe* 버전 2.03과 호환되어야 합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/mktyplib203** 옵션을 참조하세요. MSDN 웹 사이트에서 [ODL 파일 구문](/previous-versions/windows/desktop/automat/odl-file-syntax)도 참조하세요.

- **OutputDirectory**

     선택적 **문자열** 매개 변수입니다.

     MIDL 작업이 출력 파일을 쓰는 기본 디렉터리를 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/out** 옵션을 참조하세요.

- **PreprocessorDefinitions**

     선택적 **String[]** 매개 변수입니다.

     하나 이상의 *defines*;를 지정합니다. 즉, 이름 및 선택적 값이 `#define` 지시문을 사용하는 것처럼 C 전처리기에 전달 되도록 지정합니다. 각 define의 형식은 *name[=value]* 입니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/D** 옵션을 참조하세요. 이 표의 **UndefinePreprocessorDefinitions** 매개 변수도 참조하세요.

- **ProxyFileName**

     선택적 **문자열** 매개 변수입니다.

     COM 인터페이스에 대한 인터페이스 프록시 파일의 이름을 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/proxy** 옵션을 참조하세요.

- **RedirectOutputAndErrors**

     선택적 **문자열** 매개 변수입니다.

     오류 메시지 및 경고와 같은 출력을 표준 출력에서 지정된 파일로 리디렉션합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/o** 옵션을 참조하세요.

- **ServerStubFile**

     선택적 **문자열** 매개 변수입니다.

     RPC 인터페이스에 대한 서버 스텁 파일의 이름을 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/sstub** 옵션을 참조하세요. 이 표의 **ClientStubFile** 매개 변수도 참조하세요.

- **Source**

     필수 `ITaskItem[]` 매개 변수입니다.

     공백으로 구분된 소스 파일 목록을 지정합니다.

- **StructMemberAlignment**

     선택적 **문자열** 매개 변수입니다.

     대상 시스템에 있는 구조체의 맞춤(*압축 수준*)을 지정합니다.

     각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

    |값|명령줄 옵션|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**1**|**/Zp1**|
    |**2**|**/Zp2**|
    |**4**|**/Zp4**|
    |**8**|**/Zp8**|

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/Zp** 옵션을 참조하세요. **/Zp** 옵션은 **/pack** 옵션 및 이전의 **/align** 옵션과 동일합니다.

- **SuppressCompilerWarnings**

     선택적 **Boolean** 매개 변수입니다.

     `true`인 경우 MIDL 작업에서 경고 메시지를 표시하지 않습니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/no_warn** 옵션을 참조하세요.

- **SuppressStartupBanner**

     선택적 `Boolean` 매개 변수입니다.

     `true`인 경우 작업을 시작할 때 저작권과 버전 번호 메시지가 표시되지 않도록 합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/nologo** 옵션을 참조하세요.

- **TargetEnvironment**

     선택적 **문자열** 매개 변수입니다.

     애플리케이션이 실행되는 환경을 지정합니다.

     각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

    |값|명령줄 옵션|
    |-----------|--------------------------|
    |**NotSet**|*\<none>*|
    |**Win32**|**/env win32**|
    |**Itanium**|**/env ia64**|
    |**X64**|**/env x64**|

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/env** 옵션을 참조하세요.

- **TrackerLogDirectory**

     선택적 `String` 매개 변수입니다.

     이 작업에 대한 추적 로그를 저장할 중간 디렉터리를 지정합니다.

- **TypeLibFormat**

     선택적 **문자열** 매개 변수입니다.

     형식 라이브러리 파일의 형식을 지정합니다.

     각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

    |값|명령줄 옵션|
    |-----------|--------------------------|
    |**NewFormat**|**/newtlb**|
    |**OldFormat**|**/oldtlb**|

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/newtlb** 및 **/oldtlb** 옵션을 참조하세요.

- **TypeLibraryName**

     선택적 **문자열** 매개 변수입니다.

     형식 라이브러리 파일의 이름을 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/tlb** 옵션을 참조하세요.

- **UndefinePreprocessorDefinitions**

     선택적 **String[]** 매개 변수입니다.

     `#undefine` 지시문을 사용하는 것처럼 C 전처리기에 이름을 전달하여 이름의 이전 정의를 제거합니다. 이전에 정의된 이름을 하나 이상 지정합니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/U** 옵션을 참조하세요. 이 표의 **PreprocessorDefinitions** 매개 변수도 참조하세요.

- **ValidateAllParameters**

     선택적 `Boolean` 매개 변수입니다.

     `true`인 경우 런타임에 무결성 검사를 수행하는 데 사용되는 추가 오류 검사 정보를 생성합니다. `false`인 경우 오류 검사 정보가 생성되지 않습니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/robust** 및 **/no_robust** 옵션을 참조하세요.

- **WarnAsError**

     선택적 `Boolean` 매개 변수입니다.

     `true`인 경우 모든 경고를 오류로 처리합니다.

     **WarningLevel** MIDL 작업 매개 변수를 지정하지 않으면 기본 수준인 수준 1의 경고가 오류로 처리됩니다.

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/WX** 옵션을 참조하세요. 이 표의 **WarningLevel** 매개 변수도 참조하세요.

- **WarningLevel**

     선택적 **문자열** 매개 변수입니다.

     내보낼 경고의 심각도(*경고 수준*)를 지정합니다. 값이 0인 경우 경고를 내보내지 않습니다. 그러지 않고 경고 수준의 숫자가 지정된 값보다 작거나 같은 경우 경고를 내보냅니다.

     각 명령줄 옵션에 해당하는 다음 값 중 하나를 지정하세요.

    |값|명령줄 옵션|
    |-----------|--------------------------|
    |**0**|**/W0**|
    |**1**|**/W1**|
    |**2**|**/W2**|
    |**3**|**/W3**|
    |**4**|**/W4**|

     자세한 내용은 [MIDL 명령줄 참조](/windows/desktop/Midl/midl-command-line-reference)에서 **/W** 옵션을 참조하세요. 이 표의 **WarnAsError** 매개 변수도 참조하세요.

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
