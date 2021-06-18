---
title: Visual Studio 2022 미리 보기의 API 변경 내용 중단
description: 확장을 Visual Studio 2022 Preview로 마이그레이션할 때 기존 VS 확장이 컴파일되지 않는 API 변경에 대해 알아봅니다.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 9427b7a75ad53fc9a0795b249d96431113aba36d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308587"
---
# <a name="breaking-api-changes-in-visual-studio-2022"></a>Visual Studio 2022의 API 변경 내용 중단

[!INCLUDE [preview-note](../includes/preview-note.md)]

확장을 Visual Studio 2022로 마이그레이션하는 경우 여기에 나열 된 주요 변경 내용이 영향을 받을 수 있습니다.

## <a name="reference-assemblies-no-longer-installed"></a>참조 어셈블리가 더 이상 설치 되지 않습니다.

Visual Studio 설치 디렉터리에서 확인 된 MSBuild를 참조 했을 수 있는 어셈블리 중 상당수가 더 이상 설치 되지 않습니다. 필요한 Visual Studio SDK 참조 어셈블리를 얻으려면 NuGet을 사용 해야 합니다. 이 작업을 수행 하는 자세한 단계는 [현대화 projects](update-visual-studio-extension.md#modernize-your-vsix-project) 를 참조 하세요.

## <a name="removed-apis"></a>제거 Api

Visual Studio 2022에서 Visual Studio를 앞으로 이동 하는 과정에서 많은 Api가 제거 되었습니다. 제거 된 api 목록은 [제거 된 Api 목록](removed-api-list.md) 페이지에서 찾을 수 있습니다.

## <a name="interop-breaking-changes"></a>Interop 관련 호환성이 손상되는 변경

대부분의 Api는 Visual Studio 2022에서 변경 되었으며, 일반적으로 코드에 쉽게 적용할 수 있는 간단한 변경 내용이 있습니다.

주요 변경 사항을 관리 하기 위해 interop 어셈블리 배포에 대 한 새로운 메커니즘을 제공할 계획입니다. 특히 Visual Studio 2022 이상에서는 일반적인 여러 공용 Visual Studio 인터페이스에 대 한 정의가 포함 된 단일 interop 어셈블리를 제공 합니다. 이 어셈블리에는 여러 interop 어셈블리에서 벗어나 이동 하는 많은 Visual Studio 인터페이스에 대 한 관리 정의가 포함 되어 있습니다. 새 interop 어셈블리는 NuGet 패키지를 통해 배포 됩니다 `Microsoft.VisualStudio.Interop` .

그러나 기본 컨텍스트에서 주로 사용 되 고 주요 변경 내용 수가 적은 Visual Studio 구성 요소는 해당 하는 interop 어셈블리를 계속 포함 합니다. 예를 들어 디버거 어셈블리는 현재와 마찬가지로 계속 VisualStudio.Debugger.Interop.dll 됩니다. 어떤 경우 든 어셈블리는 현재와 마찬가지로 응용 프로그램에서 참조 될 수 있습니다.

이는 중요 한 변경 사항 이며,이 새로운 방법으로 작성 된 및 어셈블리의 Api를 사용 하는 확장이 이전 interop 어셈블리를 사용 하는 이전 버전의 Visual Studio와 호환 되지 않는다는 것을 의미 합니다.

여기에는 Visual Studio 2022에 대 한 확장 업데이트를 용이 하 게 하는 몇 가지 중요 한 이점이 있습니다.

- 모든 손상 된 Api는 빌드 시간 오류가 발생 하 여 쉽게 찾고 수정할 수 있습니다.
- Visual Studio 2022에서 중단 된 API를 사용 하는 코드를 업데이트 하기만 하면 됩니다.
- 현재 중단 된 이전 API는 실수로 사용할 수 없습니다.

전체적으로 이러한 변경으로 인해 모든 사용자에 게 더 안정적인 버전의 Visual Studio가 적용 됩니다. 이 방법의 주요 단점은 각 대상 Visual Studio 버전에 대해 코드를 한 번도 컴파일하지 않고도 관리 되는 어셈블리를 Visual Studio 2019 및 Visual Studio 2022에서 실행할 수 없다는 것입니다.

Visual Studio 2019와 Visual Studio 2022의 API 차이로 인해 컴파일 오류가 발생할 때이를 해결 하는 방법에 대 한 지침을 사용 하 여 아래 나열 된 API 또는 패턴을 찾을 수 있습니다.

### <a name="int-or-uint-where-intptr-is-expected"></a>`int` 또는 `uint` `IntPtr` 이 필요 합니다.

이것은 매우 일반적인 오류입니다. Visual Studio 2022을 64 비트 프로세스로 만들기 위해 일부 interop Api는 포인터 크기 값을 실제로 사용 하기 위해 포인터가 32 비트 정수에 맞을 수 있다고 가정 하는 일부 interop Api를 수정 해야 했습니다.

샘플 오류:

> 인수 3: ' out uint '에서 ' out System.object '로 변환할 수 없습니다.

코드를 원하는 대로 업데이트 하거나 중단을 `IntPtr` `UIntPtr` 해결 하는 데 사용할 위치 또는 위치를 지정 합니다 `int` `uint` .

샘플 수정:

```diff
-shell.LoadLibrary(myGuid, myFlags, out uint ptrLib);
+shell.LoadLibrary(myGuid, myFlags, out IntPtr ptrLib);
```

### <a name="an-interop-type-defined-in-two-assemblies"></a>두 어셈블리에 정의 된 interop 형식

C # 컴파일러에서 사용 중인 형식이 두 어셈블리에 정의 되어 있는 것과 같은 오류를 보고 하는 경우 더 이상 참조 하지 않아야 하는 SDK의 Visual Studio 2019 버전에서 어셈블리를 참조 하는 것일 수 있습니다.

샘플 오류:

> 오류 CS0433: ' IVsDpiAware ' 형식이 ' VisualStudio, Version = 17.0.0.0, Culture = 중립, PublicKeyToken = b03f5f7f11d50a3a ' 및 ' ' 및 ' e x p. VisualStudio, Version = 16.0, Culture = 중립, PublicKeyToken = 16.0.0.0 ' 모두에 있습니다.

Visual Studio 2022에서 기본 이름인 어셈블리 이름을 확인 하려면 [참조 어셈블리 다시 매핑 표](migrated-assemblies.md) 를 참조 하세요.
위의 샘플 오류에 명명 된 두 어셈블리를 고려 하 고이 테이블을 보면 `Microsoft.VisualStudio.Interop` 가 새 어셈블리 이름 임을 알 수 있습니다. 그런 다음 프로젝트에서에 대 한 참조를 제거 합니다 `Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` .

일부 경우에는 형식 전달 자가 포함 된 사용 되지 않는 어셈블리에 대 한 Visual Studio 2022 버전의 패키지를 제공 합니다. 이 옵션을 사용할 수 있는 경우 패키지 참조를 제거 하는 대신 Visual Studio 2022 버전으로 *업그레이드할* 수 있습니다. 형식 전달자는 컴파일러에서 오류를 해결 합니다.

때로는 이러한 참조가 전이적 패키지 참조로 제공 될 수 있으므로 프로젝트 파일에서 직접 참조 하는 것 보다 제거 하기가 어려울 수 있습니다. 이러한 경우 모든 직접 패키지 참조는 Visual Studio 2022 SDK 패키지 자체를 사용 하 고 있는지 확인 합니다. *에서project.assets.js* 를 참조 하 여 사용 되지 않는 어셈블리를 가져오는 패키지 체인을 식별할 수 있습니다. 전이적 패키지 참조를 Visual Studio 2022 버전으로 업데이트 하는 것은 직접 참조로 설치 하는 것 만큼 쉽습니다.

종속성 트리를 변경할 수 없는 경우 (예: 타사 종속성을 포함 하는 경우) Visual Studio 2022 이전 패키지에 직접 패키지 참조를 추가 하 고 `ExcludeAssets="compile"` 해당 항목에 메타 데이터를 추가 하 여 `PackageReference` 컴파일러 오류를 해결할 수 있습니다. 그러나이 기법을 사용 하는 경우 확장은 Visual Studio 2022 이전 어셈블리에 대 한 종속성을 유지 하 고 확장이 런타임에 제대로 작동 하지 않을 수 있습니다.

### <a name="missing-reference-to-an-interop-assembly"></a>Interop 어셈블리에 대 한 참조가 없습니다.

이전 Visual Studio 2022 SDK에 대해 컴파일된 어셈블리를 참조 하는 경우 어셈블리 참조가 누락 되었다는 오류가 발생할 수 있습니다.

샘플 오류:

> ' IVsTextViewFilter ' 형식이 참조 되지 않은 어셈블리에 정의 되어 CS0012 오류가 발생 했습니다. ' VisualStudio, Version = 7.1.40304.0, Culture = 중립, PublicKeyToken = b03f5f7f11d50a3a ' 어셈블리에 대 한 참조를 추가 해야 합니다.

[참조 어셈블리 다시 매핑 테이블](migrated-assemblies.md)을 사용 하 여 요청 된 어셈블리가 실제로 참조 해야 하는 어셈블리가 아닌지 확인할 수 있습니다.

가장 좋은 해결 방법은 제거 된 interop 어셈블리를 컴파일러에서 더 이상 요청 하지 않도록 Visual Studio 2022 SDK에 대해 컴파일된 버전으로 종속성을 업데이트 하는 것입니다.

일부 경우에는 형식 전달 자가 포함 된 사용 되지 않는 어셈블리에 대 한 Visual Studio 2022 버전의 패키지를 제공 합니다. 이 옵션을 사용할 수 있는 경우 형식 전달 자가 컴파일러에서 오류를 해결 하도록 사용 되지 않는 패키지의 Visual Studio 2022 버전에 패키지 참조를 추가할 수 있습니다.

### <a name="iasyncserviceprovider-is-missing"></a>`IAsyncServiceProvider` 누락 됨

이 인터페이스에는 두 가지 네임 스페이스의 정의가 있습니다. 이러한 중 하나만 관리 되는 용도로 사용 됩니다.

Visual Studio 2019 네임 스페이스 | Visual Studio 2022 네임 스페이스 | 올바른 사용법
--|--|--
VisualStudio. IAsyncServiceProvider | VisualStudio. IAsyncServiceProvider | 관리 코드 사용
VisualStudio. IAsyncServiceProvider | VisualStudio. COMAsyncServiceProvider. IAsyncServiceProvider | 하위 수준 interop만

에 대 한 오류가 표시 되는 경우 `IAsyncServiceProvider` 네이티브 코드 (두 번째 행) 용으로 사용 하는 것이 원인일 수 *있습니다* .
이 경우 새 네임 스페이스로 업데이트 하거나 관리 하기 쉬운 인터페이스로 전환할 수 있습니다.

### <a name="dte-and-_dte-type-cast-failures"></a>`DTE` 및 `_DTE` 형식 캐스팅 실패

`DTE` 와 `_DTE` 는 모두 인터페이스입니다. 하나는 다른에서 파생 됩니다. 그러나 Visual Studio 2022에서는 기본 및 파생 형식이 교환 됩니다.
이렇게 하면 특정 유형 할당 또는 캐스팅이 실패 합니다.

또한를 사용 하는 경우를 사용 하 여 `new DTE()` 를 사용 해야 `new _DTE()` 합니다.

### <a name="missing-argument-on-a-method-invocation"></a>메서드 호출에 인수가 없습니다.

일부 메서드는 더 이상 interop API에서 선택적 매개 변수 였던 기본 인수를 선언 하지 않습니다.
COM interop 호출에 대 한 누락 된 인수에 대 한 오류가 발생 하 고 매개 변수가 형식에 대해를 호출 하는 경우 `object` Visual Studio 2019 INTEROP API에 정의 된 이전 기본값을 인수로 지정 하는 것 `""` 이 좋습니다 `""` . 따라서 컴파일 오류를 해결 하기 위해 인수로를 추가 하는 것이 좋습니다.

기본 인수를 사용 하는 것이 확실 하지 않은 경우 Visual Studio 2022에서 Visual studio 2019로 언어 서비스 컨텍스트를 전환 하 여 기본 인수가 무엇 인지 확인 하 고 코드에 명시적으로 추가 합니다. Visual Studio 2019 용으로 컴파일될 때 계속 해 서 정상적으로 작동 하지만 이제 Visual Studio 2022 용으로 컴파일됩니다.

샘플 수정:

```diff
-process4.Attach2();
+process4.Attach2("");
```
