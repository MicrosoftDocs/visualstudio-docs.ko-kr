---
title: 변경 로그(Visual Studio Tools for Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 5/19/2020
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: e817318f7b16040ed598ac4dce8f1c6017bdf83e
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471534"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>변경 로그(Visual Studio Tools for Unity, Mac)

Visual Studio Tools for Unity에 대한 변경 로그입니다.

## <a name="2710"></a>2.7.1.0
릴리스 날짜: 2020년 8월 5일

### <a name="new-features"></a>새로운 기능

- **통합:**

  - Unity 메시지 API가 2019.4로 업데이트되었습니다.

  - `CA1823`에 대한 [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) 억제 장치가 추가되었습니다. `SerializeField` 또는 `SerializeReference` 특성이 있는 전용 필드가 사용되지 않음으로 표시되면 안 됩니다(FxCop).
  
  - `CA1822`에 대한 [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) 억제 장치가 추가되었습니다. Unity 메시지가 `static`한정자 후보로 플래그 지정되면 안 됩니다( FxCop).

  - `CA1801`에 대한 [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) 억제 장치가 추가되었습니다. 사용되지 않는 매개 변수가 Unity 메시지에서 제거되면 안 됩니다(FxCop).
  
  - [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) 억제 장치에 `MenuItem` 지원이 추가되었습니다.  

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 추가 괄호 또는 메서드 인수에서 작동하지 않던 [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) 및 [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) 억제 장치를 수정했습니다.
  
  - Unity 설정에서 자동 새로 고침이 사용하지 않도록 설정된 경우에도 필수 자산 데이터베이스가 새로 고쳐지던 것을 수정했습니다.

## <a name="2700"></a>2.7.0.0
릴리스 날짜: 2020년 6월 23일

### <a name="new-features"></a>새로운 기능

- **통합:**

  - Unity가 솔루션 및 프로젝트를 다시 생성하는 경우 솔루션 폴더를 유지하기 위한 지원이 추가되었습니다.

  - [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) 진단이 추가되었습니다. `InitializeOnLoadMethod` 또는 `RuntimeInitializeOnLoadMethod` 특성을 사용하여 잘못된 메서드 서명을 검색할 수 있습니다.

  - [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) 진단이 추가되었습니다. 첫 번째 인수를 문자열 리터럴로 지정하여 `Invoke`, `InvokeRepeating`, `StartCoroutine` 또는 `StopCoroutine`을 사용하는 것은 형식 측면에서 안전하지 않습니다.

  - [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) 진단이 추가되었습니다. `SetPixels` 호출이 느립니다.

### <a name="bug-fixes"></a>버그 수정

- **디버거:**

  - 게임이 이전 Mono 런타임에 실행되는 동안 중단점을 생성하는 것을 수정했습니다(중단점을 만드는 즉시 바인딩을 시도함). 
  
- **통합:**

  - Unity 메시지 마법사에서 메시지를 필터링할 때 선택 항목을 다시 설정하지 않습니다.
  
  - SerializeField 특성으로 데코레이팅된 모든 필드에 대해, `IDE0044` 표시 안 함(읽기 전용), `IDE0051`(사용되지 않음), `CS0649`(할당되지 않음) 규칙이 포함된 억제 장치 [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) 및 [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md)를 수정했습니다. `Unity.Object`를 확장하는 모든 형식의 공용 필드에 대해 `CS0649`(할당되지 않음)를 표시하지 않습니다.

  - [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md)에 대한 제네릭 형식 매개 변수 검사를 수정했습니다.

- **평가:**

  - 열거형에 대한 같음 비교를 수정했습니다.

## <a name="2610"></a>2.6.1.0
릴리스 날짜: 2020년 5월 19일

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - Unity 쪽에서 메시징 서버를 만들 수 없으면 경고합니다.

  - 경량 컴파일 중 분석기를 올바로 실행합니다.

  - Unity Hub 허브 설치와 함께 API 설명서가 수정되었습니다.
  
  - 디버거 시각화 도우미 크래시가 수정되었습니다.

## <a name="2600"></a>2.6.0.0
릴리스 날짜: 2020년 4월 14일

### <a name="new-features"></a>새로운 기능

- **통합:**

  - [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) 진단이 추가되었습니다. `StartCoroutine()`에서 코루틴 호출을 검색하고 래핑합니다.

  - [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) 진단이 추가되었습니다. 잘못되거나 중복된 `SerializeField` 특성을 검색하고 제거합니다.

  - [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) 진단이 추가되었습니다. 구성 요소가 아닌 형식 또는 인터페이스가 아닌 형식으로 호출된 `GetComponent()`를 검색합니다.

  - `IDE0051`에 대한 [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) 억제 장치가 추가되었습니다. `ContextMenu` 특성이 있는 메서드 또는 `ContextMenuItem` 특성이 있는 필드에 의해 참조된 메서드를 사용되지 않음으로 플래그 지정하지 않습니다.

  - `IDE0051`에 대한 [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) 억제 장치가 추가되었습니다. `ContextMenuItem` 특성이 있는 필드를 사용되지 않음으로 플래그 지정하지 않습니다.

  - `IDE0044`에 대한 [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) 억제 장치가 추가되었습니다. `ContextMenuItem` 특성이 있는 필드를 읽기 전용으로 설정하지 않습니다.

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) 및 [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md)이 이제 `SerializeReference` 및 `SerializeField` 특성 모두에서 작동합니다.

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 편집기에서 통신할 수 있는 경우에만 Unity에 시작/중지 명령을 보냅니다.

  - 상속된 메시지를 사용하여 QuickInfo 설명서가 수정되었습니다.

  - `CreateInspectorGUI` 메시지의 메시지 범위가 수정되었습니다.

  - 다형 한정자를 사용하는 메서드에 대해 [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md)을 보고하지 않습니다.

- **평가:**

  - 별칭이 지정된 using의 처리가 수정되었습니다.
  
  - Null 값의 처리가 수정되었습니다.  

## <a name="2520"></a>2.5.2.0

릴리스 날짜: 2020년 3월 23일

### <a name="bug-fixes"></a>버그 수정

- **디버거:**

  - 연결 후 스레드 등록이 수정되었습니다.

## <a name="2510"></a>2.5.1.0

릴리스 날짜: 2020년 3월 3일

### <a name="new-features"></a>새로운 기능

- **통합:**

  - `IDE0051`에 대한 [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) 억제 장치가 추가되었습니다. Invoke, InvokeRepeating, StartCoroutine 또는 StopCoroutine과 함께 사용되는 프라이빗 메서드는 사용되지 않음으로 표시될 수 없습니다.

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - OnDrawGizmos/OnDrawGizmosSelected 설명서가 수정되었습니다.

- **평가:**

  - 람다 인수 검사가 수정되었습니다.

## <a name="2501"></a>2.5.0.1

릴리스 날짜: 2020년 2월 19일

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 잘못된 메시지 시그니처에 대한 [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) 진단 검사가 수정되었습니다. 여러 수준의 상속을 갖는 형식을 검사할 때 이 진단이 실패하고 `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` 메시지가 표시되는 경우가 있었습니다.

## <a name="2500"></a>2.5.0.0

릴리스 날짜: 2020년 1월 22일

### <a name="new-features"></a>새로운 기능

- **통합:**

  - HLSL 파일에 대한 지원이 추가되었습니다.
  
  - 새로운 폴더 대화 상자 UI로 전환되었습니다.
  
  - 설정이 새로운 액세스 가능 속성 그리드로 전환되었습니다.

  - `IDE0051`에 대한 [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) 억제 장치가 추가되었습니다. `SerializeField` 특성이 있는 프라이빗 필드는 사용되지 않음으로 표시될 수 없습니다.

  - `CS0649`에 대한 [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) 억제 장치가 추가되었습니다. `SerializeField` 특성이 있는 필드는 할당되지 않음으로 표시될 수 없습니다.  

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 프로젝트 생성이 수정되었습니다(`GenerateTargetFrameworkMonikerAttribute` 대상이 잘못 찾아지는 경우가 있었습니다).

- **평가:**

  - 문자열 계산이 수정되었습니다(ToString() 호출이 사용되지 않았습니다).

## <a name="2420"></a>2.4.2.0

릴리스 날짜: 2019년 12월 3일

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 사용자 정의 인터페이스를 사용하여 진단을 수정했습니다.

  - 형식이 잘못된 식이 있는 빠른 도구 설명을 수정했습니다.
  
## <a name="2410"></a>2.4.1.0

릴리스 날짜: 2019년 11월 6일

### <a name="new-features"></a>새 기능

- **통합:**

  - Unity 백그라운드 프로세스에 대한 지원이 추가되었습니다. (디버거는 자식 프로세스가 아닌 기본 프로세스에 자동으로 연결할 수 있습니다.)

  - 관련 설명서를 표시하는 Unity 메시지에 대한 빠른 도구 설명을 추가했습니다.

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 고급 이진 및 호출 식을 사용하여 태그 비교 분석기 `UNT0002`를 수정했습니다.

### <a name="deprecated-features"></a>사용되지 않는 기능

- **통합:**

  - 앞으로 Visual Studio Tools for Unity에서는 Visual Studio 2017+만 지원합니다.

## <a name="2400"></a>2.4.0.0

릴리스 날짜: 2019년 10월 15일

### <a name="new-features"></a>새 기능

- **통합:**

  - 모든 Unity 메시지에 대해 `IDE0060`(사용되지 않는 매개 변수)에 대한 [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) 억제 장치가 추가되었습니다.

  - `TooltipAttribute` 태그가 지정된 필드에 대한 빠른 도구 설명을 추가했습니다. (이 내용은 이 필드를 사용하는 간단한 get 접근자에도 적용됩니다.)

## <a name="2330"></a>2.3.3.0

릴리스 날짜: 2019년 9월 23일

### <a name="new-features"></a>새 기능

- **통합:**

  - IDE에서 사용되지 않는 매개 변수를 제거하는 빠른 수정을 표시하지 않도록 하기 위해 IDE0060에 대한 새 억제 장치를 추가했습니다.
    - `IDE0060`의 `USP0005`: Unity 메시지는 Unity 런타임에서 호출됩니다.

## <a name="2320"></a>2.3.2.0

릴리스 날짜: 2019년 9월 16일

### <a name="new-features"></a>새 기능

- **통합:**

  - Unity와 관련된 새로운 진단 기능을 추가하여 Unity 프로젝트에 대한 Visual Studio의 지식을 심화했습니다. Unity 프로젝트에 적용되지 않는 일반적인 C# 진단을 억제하여 IDE를 보다 효율적으로 만들었습니다. 예를 들어 IDE에 검사기 변수를 `readonly`로 변경하는 빠른 수정이 표시되지 않습니다. 이렇게 하면 Unity 편집기에서 변수를 수정할 수 없습니다.
    - `UNT0001`: Unity 메시지는 비어 있는 경우에도 런타임에 의해 호출되며, Unity 런타임에 의한 불필요한 처리를 방지하려면 이 메시지를 선언하지 마십시오.
    - `UNT0002`: 문자열 같음을 사용한 태그 비교는 기본 제공 CompareTag 메서드보다 느립니다.
    - `UNT0003`: 형식 안전성을 위해 GetComponent의 일반 형식을 사용하는 것이 좋습니다.
    - `UNT0004`: Update 메시지는 프레임 속도에 따라 달라지며, Time.fixedDeltaTime 대신 Time.deltaTime을 사용해야 합니다.
    - `UNT0005`: FixedUpdate 메시지는 프레임 속도에 따라 달라지며, Time.deltaTime 대신 Time.fixedDeltaTime을 사용해야 합니다.
    - `UNT0006`: 이 Unity 메시지에 대해 잘못된 메서드 시그니처가 검색되었습니다.
    - `UNT0007`: Unity는 null 결합과 호환되지 않는 Unity 개체에 대해 null 비교 연산자를 재정의합니다.
    - `UNT0008`: Unity는 null 전파와 호환되지 않는 Unity 개체에 대해 null 비교 연산자를 재정의합니다.
    - `UNT0009`: 클래스에 InitializeOnLoad 특성을 적용할 때 정적 생성자를 제공해야 합니다. InitializeOnLoad 특성은 편집기가 시작될 때 호출되도록 합니다.
    - `UNT0010`: MonoBehaviours는 AddComponent()를 사용해서만 만들어야 합니다. MonoBehaviour는 구성 요소이며, GameObject에 연결되어야 합니다.
    - `UNT0011`: ScriptableObject는 CreateInstance()를 사용해서만 만들어야 합니다. Unity 메시지 메서드를 처리하려면 ScriptableObject는 Unity 엔진으로 만들어야 합니다.
    - `IDE0029`의 `USP0001`: Unity 개체는 null 결합을 사용하면 안 됩니다.
    - `IDE0031`의 `USP0002`: Unity 개체는 null 전파를 사용하면 안 됩니다.
    - `IDE0051`의 `USP0003`: Unity 메시지는 Unity 런타임에서 호출됩니다.
    - `IDE0044`의 `USP0004`: SerializeField 특성이 있는 필드는 readonly로 설정하면 안 됩니다.

## <a name="2310"></a>2.3.1.0

릴리스 날짜: 2019년 9월 4일

### <a name="new-features"></a>새 기능

- **평가:**

  - 보다 효율적인 형식 표시를 위한 지원을 추가했습니다(`List'1[[System.Object, <corlib...>]]` 대신 `List<object>` 사용).

  - 포인터 멤버 액세스 지원을 추가했습니다(`p->data->member`).

  - 배열 이니셜라이저의 암시적 변환 지원을 추가했습니다(`new byte [] {1,2,3,4}`).

  - 바이트 배열과 문자열을 검사할 때 16진수 편집기 지원을 추가했습니다.

## <a name="2300"></a>2.3.0.0

릴리스 날짜: 2019년 8월 13일

### <a name="bug-fixes"></a>버그 수정

- **평가:**

  - 예외를 사용하여 단계별 실행 문제를 해결했습니다.

  - 의사 식별자(예: $exception) 평가를 수정했습니다.

  - 잘못된 주소를 역참조하는 경우 크래시를 방지합니다.  

  - 언로드된 appdomain 관련 문제를 해결했습니다.

## <a name="2200"></a>2.2.0.0

릴리스 날짜: 2019년 7월 25일

### <a name="bug-fixes"></a>버그 수정

- **평가:**

  - IntPtr 형식의 검사 문제가 해결되었습니다.

- **디버거:**

  - catch 지점 및 함수 중단점의 처리 문제가 해결되었습니다.

## <a name="2130"></a>2.1.3.0

릴리스 날짜: 2019년 7월 9일

### <a name="new-features"></a>새로운 기능

- **디버거:**

  - 예외의 서브 클래스를 catch하기 위한 지원이 추가되었습니다.

  - MDS 프로토콜 2.51에 대한 지원이 추가되었습니다.

- **통합:**

  - asmdef 파일에 대한 지원이 추가되었습니다.

  - 템플릿에서 파일이 추가될 때 이름 바꾸기 모드로 전환하여 Unity 편집기 동작을 모방합니다.

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - Unity 플레이어와 통신하는 동안 형식이 잘못된 메시지 처리 문제가 해결되었습니다.

- **평가:**

  - 식에서 네임스페이스 처리 문제가 해결되었습니다.

## <a name="2120"></a>2.1.2.0

릴리스 날짜: 2019년 7월 2일

### <a name="bug-fixes"></a>버그 수정

- **평가:**

  - 구문 분석이 불가능한 식이 포함된 오류 보고 문제가 해결되었습니다.

## <a name="2110"></a>2.1.1.0

릴리스 날짜: 2019년 6월 27일

### <a name="new-features"></a>새 기능

- **통합:**

  - MonoBehaviour API가 2019.1로 업데이트되었습니다.

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - Unity 프로젝트 탐색기 성능 문제가 해결되었습니다.

  - 간단한 빌드가 사용되는 경우 출력에 대한 경고 및 오류 보고 문제가 해결되었습니다.

  - 간단한 빌드 성능 문제가 해결되었습니다.

## <a name="2100"></a>2.1.0.0

릴리스 날짜: 2019년 6월 20일

### <a name="new-features"></a>새 기능

- **통합:**

  - IntelliSense 오류 및 경고를 사용하기 위해 Unity 프로젝트에 대한 전체 빌드를 사용하지 않도록 설정했습니다. 실제로 Unity는 내부적으로 수행하는 작업을 나타내는 클래스 라이브러리 프로젝트를 사용하여 Visual Studio 솔루션을 만듭니다. 즉, Visual Studio에서 이루어진 빌드의 결과는 컴파일 파이프라인이 닫혀 있기 때문에 Unity에서 절대 사용하거나 선택하지 않습니다. Visual Studio에서 이루어지는 빌드는 아무런 결과 없이 리소스를 소비하기만 합니다. 도구 또는 종속된 설치 프로그램을 있어 전체 빌드가 필요한 경우에는 이 최적화를 사용하지 않도록 설정할 수 있습니다(설정/Unity 도구/프로젝트의 전체 빌드 사용 안 함).
  
  - UPE에 Unity 패키지에 대한 지원이 추가되었습니다. 참조 패키지(`Packages` 폴더에서 manifest.json 사용) 및 로컬 패키지(`Packages` 폴더에 포함)만 볼 수 있습니다.

## <a name="2021"></a>2.0.2.1

릴리스 날짜: 2019년 5월 30일

### <a name="new-features"></a>새 기능

- **통합:**

  - Unity 실행 대상에 대한 사용자 지정 아이콘이 추가되었습니다.

## <a name="2020"></a>2.0.2.0

릴리스 날짜: 2019년 4월 2일

### <a name="new-features"></a>새 기능

- **통합:**

  - 저장 시 Unity의 자산 데이터베이스를 자동으로 새로 고치는 지원이 추가되었습니다. 이 기능은 기본적으로 사용하도록 설정되고 Visual Studio에서 스크립트를 저장할 때 Unity 쪽에서 다시 컴파일을 트리거합니다. [도구]\[옵션]\[Unity용 도구]\[저장 시 Unity의 AssetDatabase 새로 고침]에서 이 기능을 사용하지 않도록 설정할 수 있습니다.

  - 오프라인 설명서의 기본 설정 Unity 설치를 설정하는 지원이 추가되었습니다.

  - 새 편집기의 상황에 맞는 메뉴가 추가되었습니다.

### <a name="bug-fixes"></a>버그 수정

- **디버거:**

  - 빈 프레임이 있는 어셈블리 필터링 및 프레임 검사가 수정되었습니다.

## <a name="2011"></a>2.0.1.1
 
 릴리스 날짜: 2019년 3월 26일

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 일시적으로 Mono를 매우 특별한 이 릴리스의 유일하게 사용할 수 있는 기본 디버거로 설정합니다.

## <a name="2006"></a>2.0.0.6

릴리스 날짜: 2019년 3월 26일

### <a name="new-features"></a>새 기능

- **통합:**

  - “Unity에 연결 및 재생” 지원이 추가되었습니다.

## <a name="2005"></a>2.0.0.5

릴리스 날짜: 2019년 3월 20일

### <a name="new-features"></a>새로운 기능

- **Project Generation:**

  - 솔루션 파일을 처리할 때 외부 속성을 보존합니다.
  
- **평가:**

  - 정규화된 별칭 이름에 대한 지원이 추가되었습니다(아직은 전역 네임스페이스만). 따라서 식 계산기는 이제 global::namespace.type 양식을 사용하는 형식을 허용합니다.

  - 포인터 역참조 `*(pointer+index)` 양식과 의미상 동일한 `pointer[index]` 양식에 대한 지원이 추가되었습니다.

## <a name="2004"></a>2.0.0.4

릴리스 날짜: 2019년 3월 5일

### <a name="new-features"></a>새 기능

- **통합:**

  - `ScriptableObject` API를 업데이트했습니다.

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 템플릿에서 네임스페이스가 제거되었습니다.

## <a name="2003"></a>2.0.0.3
 
 릴리스 날짜: 2019년 3월 5일

### <a name="new-features"></a>새로운 기능

- **Project Generation:**

  - 공용 및 직렬화된 필드에서 더 이상 경고가 발생하지 않습니다. 이 메시지를 만든 Unity 프로젝트의 `CS0649` 및 `IDE0051` 컴파일러 경고를 표시하지 않도록 자동으로 설정했습니다.

- **통합:**

  - 둘 이상의 Unity 프로세스가 실행 중인 경우 특정 인스턴스에 연결하라는 메시지를 표시합니다.

- **평가:**

  - 로컬 함수 지원이 추가되었습니다.

### <a name="bug-fixes"></a>버그 수정

- **디버거:**

  - 이전 프로토콜 버전을 사용하는 경우 명명된 인수의 사용자 지정 특성이 수정되었습니다.

## <a name="2002"></a>2.0.0.2

릴리스 날짜: 2019년 2월 4일

### <a name="new-features"></a>새로운 기능

- **통합:**

  - MonoBehaviour API가 업데이트되었습니다.

### <a name="bug-fixes"></a>버그 수정

- **디버거:**

  - 디버거에서 설정 기본값이 수정되었습니다.

## <a name="2001"></a>2.0.0.1

릴리스 날짜: 2018년 12월 4일

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 설치 패키지 자체 포함이 수정되었습니다.

## <a name="2000"></a>2.0.0.0
 릴리스 날짜: 2018년 12월 4일

### <a name="new-features"></a>새 기능

- **디버거:**

  - Mac용 Unity 디버거가 Windows의 동일한 핵심 Unity 디버거로 바뀌었습니다.

  - 식 계산을 위해 NRefactory가 Roslyn으로 바뀌었습니다.

  - 포인터에 대한 지원인 역참조, 캐스팅 및 포인터 산술이 추가되었습니다(이 경우 Unity 2018.2+ 및 새 런타임이 둘 다 필요함).

  - 배열 포인터 보기에 대한 지원이 추가되었습니다(C++와 유사). 포인터 식을 사용한 다음, 쉼표와 보려는 요소 수를 추가합니다.

  - 비동기 구문 지원이 추가되었습니다.

  - 의사 변수(예외 및 개체 식별자)에 대한 지원이 추가되었습니다.

### <a name="bug-fixes"></a>버그 수정

- **디버거:**

  - 잘못된 형식 또는 지원되지 않는 식이 포함된 식 계산이 수정되었습니다.

## <a name="1700"></a>1.7.0.0

릴리스 날짜: 2018년 11월 13일

### <a name="new-features"></a>새 기능

- **디버거:**

  - 연결 대화 상자에(IP, 머신 이름) 클라이언트 추가 정보가 추가되었습니다.

### <a name="bug-fixes"></a>버그 수정

- **디버거:**

  - 특히 ‘Unity에 연결’을 누르거나 게임을 다시 시작할 때, Unity의 디버거 엔진과 통신하는 데 사용되는 라이브러리에서 교착 상태가 발생하여 Visual Studio 또는 Unity를 동결시키는 문제가 해결되었습니다.

- **통합:**

  - 다른 기본 편집기가 선택되었을 때 고정 Unity 플러그 인 활성화.

  - 고정 Unity 파일 템플릿 생성.

## <a name="1602"></a>1.6.0.2

릴리스 날짜: 2018년 7월 24일

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - Unity에서 수정된 Unity 성능 버그에 대한 해결 방법이 롤백되었습니다.

## <a name="1601"></a>1.6.0.1

릴리스 날짜: 2018년 7월 10일

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 셰이더 코드 색 지정 지원이 수정되었습니다.

## <a name="1600"></a>1.6.0.0

릴리스 날짜: 2018년 6월 26일

### <a name="bug-fixes"></a>버그 수정

- **마법사:**

  - OnApplicationFocus 메시지에서 오타가 수정되었습니다.

- **Project Generation:**

  - Unity 성능 버그에 대한 일시적인 해결 방법: 프로젝트를 생성할 때 MonoIslands를 캐시합니다.

  - 새 Unity 런타임에서 사용하는 경우 더 이상 이식 가능한 pdb를 mdb로 변환하지 않습니다.

## <a name="1502"></a>1.5.0.2

릴리스 날짜: 2018년 4월 18일

### <a name="new-features"></a>새 기능

- **통합:**

  - 기본 셰이더 코드 완성에 대한 지원이 추가되었습니다.

  - 셰이더 파일에서 주석을 설정/해제하는 지원이 추가되었습니다.

## <a name="1501"></a>1.5.0.1

릴리스 날짜: 2018년 3월 28일

### <a name="new-features"></a>새 기능

- **통합:**

  - Unity 프로젝트 탐색기에서 추가 템플릿에 대한 지원이 추가되었습니다.

## <a name="1500"></a>1.5.0.0

릴리스 날짜: 2018년 3월 21일

### <a name="new-features"></a>새 기능

- **통합:**

  - USB로 연결된 Android 플레이어에 연결 및 검색에 대한 지원이 추가되었습니다.

## <a name="1403"></a>1.4.0.3

릴리스 날짜: 2018년 3월 5일

### <a name="new-features"></a>새 기능

- **Project Generation:**

  - Unity 2018.1에서 새 프로젝트 생성기에 대한 지원이 추가되었습니다.

- **통합:**

  - 전용 설정에 대한 옵션 패널이 추가되었습니다.

## <a name="1402"></a>1.4.0.2

릴리스 날짜: 2018년 1월 24일

### <a name="bug-fixes"></a>버그 수정

- **Project Generation:**

  - Mono 버전 검색이 수정되었습니다.

- **통합:**

  - 2018.1 및 플러그 인 활성화의 타이밍 문제가 수정되었습니다.

  - 새 플레이어를 검색하는 경우 알림이 수정되었습니다.

## <a name="1401"></a>1.4.0.1

릴리스 날짜: 2018년 1월 23일

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 두 번 클릭 시 확장/축소 폴더 수정함

## <a name="1400"></a>1.4.0.0

릴리스 날짜: 2017년 12월 13일

### <a name="new-features"></a>새 기능

- **Project Generation:**

  - .NET Standard에 대한 지원이 추가되었습니다.

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 자동 pdb에서 mdb로의 디버그 기호 변환을 수정했습니다.

## <a name="1301"></a>1.3.0.1

릴리스 날짜: 2017년 12월 12일

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 배열 크기를 변경하는 동안 검사기에 영향을 주는 EditorPrefs.GetBool에 대한 간접 호출이 수정되었습니다.

- **마법사:**

  - 메서드를 삽입하기 전에 roslyn 컨텍스트를 새로 고칩니다.

## <a name="1300"></a>1.3.0.0

릴리스 날짜: 2017년 11월 20일

### <a name="new-features"></a>새로운 기능

- **마법사:**

  - "Unity 메시지 구현" 마법사가 추가되었습니다.

  - Mac 7.4용 VS에서 새 완성 API에 대한 지원이 추가되었습니다.

## <a name="1200"></a>1.2.0.0

릴리스 날짜: 2017년 10월 23일

### <a name="new-features"></a>새로운 기능

- **디버거:**

  - 휴대용 디버그 기호 파일에 대한 지원을 추가했습니다.

### <a name="bug-fixes"></a>버그 수정

- **Project Generation:**

  - 어셈블리 파일 이름에 잘못 추가된 추가 .dll 확장명을 수정했습니다.

  - 이제 기본값이 'true'이므로 AllowAttachedDebuggingOfEditor Unity 플래그를 강제하지 않습니다.

## <a name="1103"></a>1.1.0.3

릴리스 날짜: 2017년 10월 23일

### <a name="new-features"></a>새로운 기능

- **Project Generation:**

  - .NET 4.6 프로필에 대한 지원이 추가되었습니다.

## <a name="1102"></a>1.1.0.2

릴리스 날짜: 2017년 8월 8일

### <a name="new-features"></a>새 기능

- **디버거:**

  - 어떤 Unity에 연결할지 확실하지 않은 경우 프로세스에 연결 대화 상자를 시작합니다.

- **Project Generation:**

  - Unity 5.6을 사용할 경우 안전하지 않은 컴파일 스위치를 항상 사용하도록 설정합니다.

## <a name="1101"></a>1.1.0.1

릴리스 날짜: 2017년 7월 20일

### <a name="new-features"></a>새 기능

- **통합:**

  - 지역화된 리소스에 대한 지원이 추가되었습니다.

## <a name="1100"></a>1.1.0.0

릴리스 날짜: 2017년 7월 12일

### <a name="new-features"></a>새로운 기능

- **통합:**

  - 프로세스에 연결 창을 통해 플레이어와 편집기에 연결에 대한 지원이 추가되었습니다.

- **Project Generation:**

  - mcs.rsp 파일을 사용한 어셈블리 이름 참조를 수정했습니다.

  - assembly.json 컴파일 단위 지원이 추가되었습니다.

  - API 수준을 사용한 정의를 수정했습니다.

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 컴파일할 때 셰이더 오류 메시지를 수정했습니다.

## <a name="1001"></a>1.0.0.1

릴리스 날짜: 2017년 5월 4일

### <a name="bug-fixes"></a>버그 수정

- **통합:**

  - 하이브리드 및 일반 프로젝트를 사용하여 활성 문서 추적을 수정했습니다.

## <a name="1000"></a>1.0.0.0

릴리스 날짜: 2017년 5월 3일
