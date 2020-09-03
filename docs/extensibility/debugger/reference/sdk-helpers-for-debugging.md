---
title: 디버깅을 위한 SDK 도우미 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9edb7c508fdea6736a71c0f70c0d2ff305d4a399
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713645"
---
# <a name="sdk-helpers-for-debugging"></a>디버깅을 위한 SDK 도우미
이러한 함수와 선언에는 c + +에서 디버그 엔진, 식 계산기 및 기호 공급자를 구현 하기 위한 전역 도우미 함수가 있습니다.

> [!NOTE]
> 지금은 이러한 함수 및 선언에 대 한 관리 되는 버전이 없습니다.

## <a name="overview"></a>개요
 디버그 엔진, 식 계산기 및 기호 공급자를 Visual Studio에서 사용 하려면 등록 해야 합니다. 이렇게 하려면 레지스트리 하위 키와 항목을 설정 합니다. 그렇지 않으면 "설정 메트릭" 이라고 합니다. 다음 전역 함수는 이러한 메트릭을 업데이트 하는 과정을 용이 하 게 하기 위해 설계 되었습니다. 이러한 기능으로 업데이트 되는 각 레지스트리 하위 키의 레이아웃을 확인 하려면 레지스트리 위치에 대 한 섹션을 참조 하세요.

## <a name="general-metric-functions"></a>일반 메트릭 함수
 이러한 함수는 디버그 엔진에서 사용 하는 일반 함수입니다. 식 계산기 및 기호 공급자에 대 한 특수 함수는 나중에 자세히 설명 합니다.

### <a name="getmetric-method"></a>GetMetric 메서드
 레지스트리에서 메트릭 값을 검색 합니다.

```cpp
HRESULT GetMetric(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   DWORD * pdwValue,
   LPCWSTR pszAltRoot
);
```

|매개 변수|설명|
|---------------|-----------------|
|pszMachine|진행 등록을 쓸 수 있는 원격 컴퓨터의 이름 `NULL` 입니다 (로컬 컴퓨터).|
|pszType|진행 메트릭 유형 중 하나입니다.|
|guidSection|진행 특정 엔진, 평가기, 예외 등의 GUID입니다. 특정 요소에 대 한 메트릭 형식의 하위 섹션을 지정 합니다.|
|pszMetric|진행 가져올 메트릭입니다. 이 값은 특정 값 이름에 해당 합니다.|
|pdwValue|진행 메트릭에 있는 값의 저장소 위치입니다. DWORD (이 예제에서는), BSTR, GUID 또는 Guid 배열을 반환할 수 있는 GetMetric의 여러 가지 종류가 있습니다.|
|pszAltRoot|진행 사용할 대체 레지스트리 루트입니다. 기본값을 `NULL` 사용 하려면로 설정 합니다.|

### <a name="setmetric-method"></a>SetMetric 메서드
 레지스트리에서 지정 된 메트릭 값을 설정 합니다.

```cpp
HRESULT SetMetric(
         LPCWSTR pszType,
         REFGUID guidSection,
         LPCWSTR pszMetric,
   const DWORD   dwValue,
         bool    fUserSpecific,
         LPCWSTR pszAltRoot
);
```

|매개 변수|설명|
|---------------|-----------------|
|pszType|진행 메트릭 유형 중 하나입니다.|
|guidSection|진행 특정 엔진, 평가기, 예외 등의 GUID입니다. 특정 요소에 대 한 메트릭 형식의 하위 섹션을 지정 합니다.|
|pszMetric|진행 가져올 메트릭입니다. 이 값은 특정 값 이름에 해당 합니다.|
|dwValue|진행 메트릭에 있는 값의 저장소 위치입니다. DWORD (이 예에서는), BSTR, GUID 또는 Guid 배열을 저장할 수 있는 여러 가지 SetMetric 종류가 있습니다.|
|fUserSpecific|진행 메트릭이 사용자 전용 이며 로컬 컴퓨터 hive 대신 사용자의 hive에 써야 하는 경우 TRUE입니다.|
|pszAltRoot|진행 사용할 대체 레지스트리 루트입니다. 기본값을 `NULL` 사용 하려면로 설정 합니다.|

### <a name="removemetric-method"></a>RemoveMetric 메서드
 레지스트리에서 지정 된 메트릭을 제거 합니다.

```cpp
HRESULT RemoveMetric(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   LPCWSTR pszAltRoot
);
```

|매개 변수|설명|
|---------------|-----------------|
|pszType|진행 메트릭 유형 중 하나입니다.|
|guidSection|진행 특정 엔진, 평가기, 예외 등의 GUID입니다. 특정 요소에 대 한 메트릭 형식의 하위 섹션을 지정 합니다.|
|pszMetric|진행 제거할 메트릭입니다. 이 값은 특정 값 이름에 해당 합니다.|
|pszAltRoot|진행 사용할 대체 레지스트리 루트입니다. 기본값을 `NULL` 사용 하려면로 설정 합니다.|

### <a name="enummetricsections-method"></a>EnumMetricSections 메서드
 레지스트리의 다양 한 메트릭 섹션을 열거 합니다.

```cpp
HRESULT EnumMetricSections(
   LPCWSTR pszMachine,
   LPCWSTR pszType,
   GUID *  rgguidSections,
   DWORD * pdwSize,
   LPCWSTR pszAltRoot
);
```

|매개 변수|설명|
|---------------|-----------------|
|pszMachine|진행 등록을 쓸 수 있는 원격 컴퓨터의 이름 `NULL` 입니다 (로컬 컴퓨터).|
|pszType|진행 메트릭 유형 중 하나입니다.|
|rgguidSections|[in, out] 채워질 미리 할당 된 Guid의 배열입니다.|
|pdwSize|진행 배열에 저장할 수 있는 최대 Guid 수입니다 `rgguidSections` .|
|pszAltRoot|진행 사용할 대체 레지스트리 루트입니다. 기본값을 `NULL` 사용 하려면로 설정 합니다.|

## <a name="expression-evaluator-functions"></a>식 계산기 함수

|함수|설명|
|--------------|-----------------|
|GetEEMetric|레지스트리에서 메트릭 값을 검색 합니다.|
|SetEEMetric|레지스트리에서 지정 된 메트릭 값을 설정 합니다.|
|RemoveEEMetric|레지스트리에서 지정 된 메트릭을 제거 합니다.|
|GetEEMetricFile|지정 된 메트릭에서 파일 이름을 가져오고이를 로드 하 여 파일 내용을 문자열로 반환 합니다.|

## <a name="exception-functions"></a>예외 함수

|함수|설명|
|--------------|-----------------|
|GetExceptionMetric|레지스트리에서 메트릭 값을 검색 합니다.|
|SetExceptionMetric|레지스트리에서 지정 된 메트릭 값을 설정 합니다.|
|RemoveExceptionMetric|레지스트리에서 지정 된 메트릭을 제거 합니다.|
|RemoveAllExceptionMetrics|레지스트리에서 모든 예외 메트릭을 제거 합니다.|

## <a name="symbol-provider-functions"></a>기호 공급자 함수

|함수|설명|
|--------------|-----------------|
|GetSPMetric|레지스트리에서 메트릭 값을 검색 합니다.|
|SetSPMetric|레지스트리에서 지정 된 메트릭 값을 설정 합니다.|
|RemoveSPMetric|레지스트리에서 지정 된 메트릭을 제거 합니다.|

## <a name="enumeration-functions"></a>열거 함수

|함수|설명|
|--------------|-----------------|
|EnumMetricSections|지정 된 메트릭 유형에 대 한 모든 메트릭을 열거 합니다.|
|EnumDebugEngine|등록 된 디버그 엔진을 열거 합니다.|
|EnumEEs|등록 된 식 계산기를 열거 합니다.|
|EnumExceptionMetrics|모든 예외 메트릭을 열거 합니다.|

## <a name="metric-definitions"></a>메트릭 정의
 이러한 정의는 미리 정의 된 메트릭 이름에 사용할 수 있습니다. 이름은 다양 한 레지스트리 키와 값 이름에 해당 하며 모두 와이드 문자열로 정의 됩니다 (예:) `extern LPCWSTR metrictypeEngine` .

|미리 정의 된 메트릭 유형|설명: ... .의 기본 키입니다.|
|-----------------------------|---------------------------------------|
|metrictypeEngine|모든 디버그 엔진 메트릭입니다.|
|metrictypePortSupplier|모든 포트 공급자 메트릭입니다.|
|metrictypeException|모든 예외 메트릭입니다.|
|metricttypeEEExtension|모든 식 계산기 확장입니다.|

|디버그 엔진 속성|설명|
|-----------------------------|-----------------|
|metricAddressBP|주소 중단점에 대 한 지원을 나타내려면 0이 아닌 값으로 설정 합니다.|
|metricAlwaysLoadLocal|항상 디버그 엔진을 로컬로 로드 하려면 0이 아닌 값으로 설정 합니다.|
|metricLoadInDebuggeeSession|사용 되지 않음|
|metricLoadedByDebuggee|0이 아닌 값으로 설정 하면 디버그 엔진은 항상 디버깅 중인 프로그램을 사용 하 여 로드 됩니다.|
|metricAttach|기존 프로그램에 대 한 첨부 파일 지원을 표시 하려면 0이 아닌 값으로 설정 합니다.|
|metricCallStackBP|호출 스택 중단점에 대 한 지원을 나타내려면 0이 아닌 값으로 설정 합니다.|
|metricConditionalBP|조건부 중단점의 설정에 대 한 지원을 나타내려면 0이 아닌 값으로 설정 합니다.|
|metricDataBP|데이터 변경에 대 한 중단점의 설정에 대 한 지원을 나타내려면 0이 아닌 값으로 설정 합니다.|
|metricDisassembly|디스어셈블리 목록의 프로덕션에 대 한 지원을 나타내려면 0이 아닌 값으로 설정 합니다.|
|metricDumpWriting|덤프 쓰기에 대 한 지원 (출력 장치에 메모리 덤프)을 지정 하려면 0이 아닌 값으로 설정 합니다.|
|metricENC|편집 하며 계속 하기에 대 한 지원을 나타내려면 0이 아닌 값으로 설정 합니다. **참고:**  사용자 지정 디버그 엔진은이를 설정 하거나 항상 0으로 설정 하면 안 됩니다.|
|metricExceptions|예외에 대 한 지원을 나타내려면 0이 아닌 값으로 설정 합니다.|
|metricFunctionBP|명명 된 중단점에 대 한 지원을 나타내려면 0이 아닌 값으로 설정 합니다 (특정 함수 이름이 호출 될 때 중단 되는 중단점).|
|metricHitCountBP|0이 아닌 값으로 설정 하면 특정 횟수 만큼 적중 된 후에만 트리거되는 중단점이 "적중 지점" 중단점의 설정에 대 한 지원을 표시 합니다.|
|metricJITDebug|Just-in-time 디버깅을 지원 하도록 지정 하려면 0이 아닌 값으로 설정 합니다. 실행 중인 프로세스에서 예외가 발생 하면 디버거가 시작 됩니다.|
|metricMemory|사용 되지 않음|
|metricPortSupplier|구현 된 경우 포트 공급자의 CLSID로 설정 합니다.|
|metricRegisters|사용 되지 않음|
|metricSetNextStatement|다음 문 (중간 문의 실행을 건너뛰는)의 설정에 대 한 지원을 나타내려면 0이 아닌 값으로 설정 합니다.|
|metricSuspendThread|스레드 실행 일시 중단에 대 한 지원을 나타내려면 0이 아닌 값으로 설정 합니다.|
|metricWarnIfNoSymbols|기호가 없는 경우 사용자에 게 알리도록 지정 하려면 0이 아닌 값으로 설정 합니다.|
|metricProgramProvider|프로그램 공급자의 CLSID로 설정 합니다.|
|metricAlwaysLoadProgramProviderLocal|프로그램 공급자가 항상 로컬로 로드 되어야 함을 나타내려면이 값을 0이 아닌 값으로 설정 합니다.|
|metricEngineCanWatchProcess|디버그 엔진이 프로그램 공급자 대신 프로세스 이벤트를 감시 함을 나타내려면이 값을 0이 아닌 값으로 설정 합니다.|
|metricRemoteDebugging|원격 디버깅에 대 한 지원을 나타내려면이 값을 0이 아닌 값으로 설정 합니다.|
|metricEncUseNativeBuilder|이 값을 0이 아닌 값으로 설정 하면 편집 하며 계속 하기 관리자에서 디버그 엔진의 encbuild.dll를 사용 하 여 편집 하며 계속 하기를 위해 빌드해야 함을 나타낼 수 있습니다. **참고:**  사용자 지정 디버그 엔진은이를 설정 하거나 항상 0으로 설정 하면 안 됩니다.|
|metricLoadUnderWOW64|이 값을 0이 아닌 값으로 설정 하 여 디버그 엔진을 64 비트 프로세스를 디버그할 때 WOW의 디버기 프로세스에서 로드 해야 함을 표시 합니다. 그렇지 않으면 디버그 엔진이 w o w 64에서 실행 되는 Visual Studio 프로세스에 로드 됩니다.|
|metricLoadProgramProviderUnderWOW64|WOW에서 64 비트 프로세스를 디버그 하는 경우이 값을 0이 아닌 값으로 설정 하 여 디버기 프로세스에서 프로그램 공급자를 로드 해야 함을 표시 합니다. 그렇지 않으면 Visual Studio 프로세스에 로드 됩니다.|
|metricStopOnExceptionCrossingManagedBoundary|관리 되지 않는 코드 경계에서 처리 되지 않은 예외가 throw 되는 경우 프로세스를 중지 해야 함을 나타내려면 0이 아닌 값으로 설정 합니다.|
|metricAutoSelectPriority|이 값을 디버그 엔진의 자동 선택에 대 한 우선 순위로 설정 합니다 .이 값이 높을수록 우선 순위가 높습니다.|
|metricAutoSelectIncompatibleList|자동 선택에서 무시 되는 디버그 엔진의 Guid를 지정 하는 항목을 포함 하는 레지스트리 키입니다. 이러한 항목은 문자열로 표현 된 GUID를 사용 하는 숫자 (0, 1, 2 등)입니다.|
|metricIncompatibleList|이 디버그 엔진과 호환 되지 않는 디버그 엔진에 대 한 Guid를 지정 하는 항목을 포함 하는 레지스트리 키입니다.|
|metricDisableJITOptimization|디버깅 하는 동안 just-in-time 최적화 (관리 코드의 경우)를 사용 하지 않도록 설정 하려면이 값을 0이 아닌 값으로 설정 합니다.|

|식 계산기 속성|설명|
|-------------------------------------|-----------------|
|metricEngine|이는 지정 된 식 계산기를 지 원하는 디버그 엔진 수를 포함 합니다.|
|metricPreloadModules|프로그램에 대해 식 계산기가 시작 될 때 모듈을 미리 로드 해야 함을 나타내려면이 값을 0이 아닌 값으로 설정 합니다.|
|metricThisObjectName|이를 "this" 개체 이름으로 설정 합니다.|

|식 계산기 확장 속성|설명|
| - |-----------------|
|metricExtensionDll|이 확장을 지 원하는 dll의 이름입니다.|
|metricExtensionRegistersSupported|지원 되는 레지스터 목록입니다.|
|metricExtensionRegistersEntryPoint|레지스터에 액세스 하기 위한 진입점입니다.|
|metricExtensionTypesSupported|지원 되는 형식 목록입니다.|
|metricExtensionTypesEntryPoint|형식에 액세스 하기 위한 진입점입니다.|

|포트 공급자 속성|설명|
|------------------------------|-----------------|
|metricPortPickerCLSID|포트 선택의 CLSID (사용자가 포트를 선택 하 고 디버깅에 사용할 포트를 추가 하는 데 사용할 수 있는 대화 상자)입니다.|
|metricDisallowUserEnteredPorts|사용자가 입력 한 포트를 포트 공급자에 추가할 수 없는 경우 0이 아닌 포트 선택 대화 상자가 기본적으로 읽기 전용으로 설정 됩니다.|
|metricPidBase|프로세스 Id를 할당할 때 포트 공급자에서 사용 하는 기본 프로세스 ID입니다.|

|미리 정의 된 SP 저장소 유형|설명|
|-------------------------------|-----------------|
|Stor파일 파일|기호는 별도 파일에 저장 됩니다.|
|storetypeMetadata|기호는 어셈블리에 메타 데이터로 저장 됩니다.|

|기타 속성|설명|
|------------------------------|-----------------|
|metricShowNonUserCode|사용자 코드가 아닌 코드를 표시 하려면이 값을 0이 아닌 값으로 설정 합니다.|
|metricJustMyCodeStepping|이 값을 0이 아닌 값으로 설정 하 여 단계별 실행이 사용자 코드 에서만 발생할 수 있음을 표시 합니다.|
|metricCLSID|특정 메트릭 형식의 개체에 대 한 CLSID입니다.|
|metricName|특정 메트릭 유형의 개체에 대 한 사용자에 게 친숙 한 이름입니다.|
|metricLanguage|언어 이름입니다.|

## <a name="registry-locations"></a>레지스트리 위치
 메트릭은 하위 키에서 특히 레지스트리에서 읽고 씁니다 `VisualStudio` .

> [!NOTE]
> 대부분의 경우 메트릭이 HKEY_LOCAL_MACHINE 키에 기록 됩니다. 그러나 경우에 따라 HKEY_CURRENT_USER 대상 키가 될 수도 있습니다. Dbgmetric는 두 키를 모두 처리 합니다. 메트릭을 가져올 때 먼저 HKEY_CURRENT_USER를 검색 한 다음 HKEY_LOCAL_MACHINE 합니다. 메트릭을 설정 하는 경우 매개 변수는 사용할 최상위 키를 지정 합니다.

 *[레지스트리 키]*\

 `Software`\

 `Microsoft`\

 `VisualStudio`\

 *[버전 루트]*\

 *[메트릭 루트]*\

 *[메트릭 유형]*\

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

|자리 표시자|Description|
|-----------------|-----------------|
|*[레지스트리 키]*|`HKEY_CURRENT_USER` 또는 `HKEY_LOCAL_MACHINE`|
|*[버전 루트]*|Visual Studio의 버전입니다 (예:, `7.0` `7.1` 또는 `8.0` ). 그러나 **/rootsuffix** 스위치를 사용 하 여이 루트를 수정할 수도 있습니다 **devenv.exe**합니다. VSIP의 경우이 한정자는 일반적으로 **Exp**이므로 버전 루트는 8.0 Exp와 같이 됩니다.|
|*[메트릭 루트]*|이는 `AD7Metrics` `AD7Metrics(Debug)` dbgmetric의 디버그 버전이 사용 되는지 여부에 따라 또는입니다. **참고:**  Dbgmetric 사용 여부에 관계 없이이 명명 규칙은 레지스트리에 반영 해야 하는 디버그 버전과 릴리스 버전 간에 차이가 있는 경우 준수 해야 합니다.|
|*[메트릭 유형]*|작성할 메트릭 형식 (,, 등) `Engine` `ExpressionEvaluator` 입니다. `SymbolProvider` 이는 모두 dbgmetric에서로 정의 됩니다. `metricTypeXXXX` 여기서 `XXXX` 는 특정 형식 이름입니다.|
|*수치*|메트릭을 설정 하기 위해 값을 할당할 항목의 이름입니다. 메트릭의 실제 구성은 메트릭 유형에 따라 달라 집니다.|
|*[메트릭 값]*|메트릭에 할당 된 값입니다. 값에 포함 되는 형식 (문자열, 숫자 등)은 메트릭에 따라 달라 집니다.|

> [!NOTE]
> 모든 Guid는 형식으로 저장 됩니다 `{GUID}` . 예: `{123D150B-FA18-461C-B218-45B3E4589F9B}`

### <a name="debug-engines"></a>디버그 엔진
 다음은 레지스트리의 디버그 엔진 메트릭에 대 한 구성입니다. `Engine` 는 디버그 엔진의 메트릭 유형 이름이 고 위의 레지스트리 하위 트리의 *[메트릭 유형]* 에 해당 합니다.

 `Engine`\

 *[엔진 guid]*\

 `CLSID` = *[클래스 guid]*

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

 `PortSupplier`\

 `0` = *[포트 공급자 guid]*

 `1` = *[포트 공급자 guid]*

|자리 표시자|Description|
|-----------------|-----------------|
|*[엔진 guid]*|디버그 엔진의 GUID입니다.|
|*[클래스 guid]*|이 디버그 엔진을 구현 하는 클래스의 GUID입니다.|
|*[포트 공급자 guid]*|포트 공급자의 GUID입니다 (있는 경우). 대부분의 디버그 엔진은 기본 포트 공급자를 사용 하므로 자체 공급자를 지정 하지 않습니다. 이 경우 하위 키 `PortSupplier` 가 존재 하지 않습니다.|

### <a name="port-suppliers"></a>포트 공급자
 다음은 레지스트리의 포트 공급자 메트릭에 대 한 구성입니다. `PortSupplier` 포트 공급자에 대 한 메트릭 유형 이름으로 *[메트릭 유형]* 에 해당 합니다.

 `PortSupplier`\

 *[포트 공급자 guid]*\

 `CLSID` = *[클래스 guid]*

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

|자리 표시자|Description|
|-----------------|-----------------|
|*[포트 공급자 guid]*|포트 공급자의 GUID입니다.|
|*[클래스 guid]*|이 포트 공급자를 구현 하는 클래스의 GUID입니다.|

### <a name="symbol-providers"></a>기호 공급자
 다음은 레지스트리의 기호 공급자 메트릭에 대 한 구성입니다. `SymbolProvider` 기호 공급자의 메트릭 유형 이름이 며 *[메트릭 유형]* 에 해당 합니다.

 `SymbolProvider`\

 *[기호 공급자 guid]*\

 `file`\

 `CLSID` = *[클래스 guid]*

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

 `metadata`\

 `CLSID` = *[클래스 guid]*

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

|자리 표시자|Description|
|-----------------|-----------------|
|*[기호 공급자 guid]*|기호 공급자의 GUID입니다.|
|*[클래스 guid]*|이 기호 공급자를 구현 하는 클래스의 GUID입니다.|

### <a name="expression-evaluators"></a>식 계산기
 다음은 레지스트리의 식 계산기 메트릭에 대 한 구성입니다. `ExpressionEvaluator` 식 계산기에 대 한 메트릭 유형 이름으로 *[메트릭 유형]* 에 해당 합니다.

> [!NOTE]
> `ExpressionEvaluator`식 계산기에 대 한 모든 메트릭 변경 내용이 적절 한 식 계산기 메트릭 함수를 통과 한다고 가정 하므로에 대 한 메트릭 유형은 dbgmetric에서 정의 되지 않습니다. 하위 키의 레이아웃은 `ExpressionEvaluator` 다소 복잡 하므로 세부 정보는 dbgmetric 내에서 숨겨집니다.

 `ExpressionEvaluator`\

 *[언어 guid]*\

 *[공급 업체 guid]*\

 `CLSID` = *[클래스 guid]*

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

 `Engine`\

 `0` = *[디버그 엔진 guid]*

 `1` = *[디버그 엔진 guid]*

|자리 표시자|Description|
|-----------------|-----------------|
|*[언어 guid]*|언어의 GUID입니다.|
|*[공급 업체 guid]*|공급 업체의 GUID입니다.|
|*[클래스 guid]*|이 식 계산기를 구현 하는 클래스의 GUID입니다.|
|*[디버그 엔진 guid]*|이 식 계산기와 작동 하는 디버그 엔진의 GUID입니다.|

### <a name="expression-evaluator-extensions"></a>식 계산기 확장
 다음은 레지스트리의 식 계산기 확장 메트릭에 대 한 구성입니다. `EEExtensions` 식 계산기 확장의 메트릭 유형 이름이 며 *[메트릭 유형]* 에 해당 합니다.

 `EEExtensions`\

 *[확장 guid]*\

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

|자리 표시자|Description|
|-----------------|-----------------|
|*[확장 guid]*|식 계산기 확장의 GUID입니다.|

### <a name="exceptions"></a>예외
 다음은 레지스트리의 예외 메트릭 구성입니다. `Exception` 예외에 대 한 메트릭 유형 이름이 며 *[메트릭 유형]* 에 해당 합니다.

 `Exception`\

 *[디버그 엔진 guid]*\

 *[예외 형식]*\

 *발생할*\

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

 *발생할*\

 *[메트릭] = [메트릭 값]*

 *[메트릭] = [메트릭 값]*

|자리 표시자|Description|
|-----------------|-----------------|
|*[디버그 엔진 guid]*|예외를 지 원하는 디버그 엔진의 GUID입니다.|
|*[예외 형식]*|처리할 수 있는 예외 클래스를 식별 하는 하위 키의 일반 제목입니다. 일반적인 이름은 **c + + 예외**, **Win32 예외**, **공용 언어 런타임 예외**및 **기본 런타임 검사**입니다. 이러한 이름은 사용자에 대 한 특정 예외 클래스를 식별 하는 데도 사용 됩니다.|
|*발생할*|예외에 대 한 이름입니다 (예: **_com_error** 또는 **제어 중단)**. 이러한 이름은 사용자에 대 한 특정 예외를 식별 하는 데도 사용 됩니다.|

## <a name="requirements"></a>요구 사항
 이러한 파일은 [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK 설치 디렉터리 (기본적으로 *[drive]* FileFiles\Microsoft VISUAL Studio 2010 SDK)에 있습니다 \\ .

 헤더: includes\dbgmetric.h

 라이브러리: cdss\ad2defilelib, libs\dbgmetric.lib

## <a name="see-also"></a>추가 정보
- [API 참조](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
