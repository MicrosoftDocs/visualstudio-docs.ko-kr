---
title: Unity에서 .NET 4.x 사용
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: how-to
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 9a53db2d7cb73fbbb8ea694386dbada3186957ee
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508979"
---
# <a name="using-net-4x-in-unity"></a>Unity에서 .NET 4.x 사용

Unity 스크립팅을 기반으로 하는 기술인 C# 및 .NET는 Microsoft가 2002년에 처음 출시한 이래 계속 업데이트를 받아왔습니다. 하지만 Unity 개발자는 C# 언어 및 .NET Framework에 추가된 새로운 기능의 일관된 흐름을 인식하지 못할 수 있습니다. Unity 2017.1 이전에는 Unity가 .NET 3.5 해당 스크립팅 런타임을 사용하여 수년간 업데이트를 받지 못했기 때문입니다.

Unity 2017.1의 릴리스부터 Unity는 NET 4.6 C# 6 호환 버전으로 업그레이드된 실험적 버전을 도입했습니다. Unity 2018.1에서는 .NET 4.x 해당 런타임이 더 이상 실험적인 것으로 간주되지 않지만, 이전 .NET 3.5 해당 런타임은 이제 레거시 버전으로 간주됩니다. 또한 Unity 2018.3의 릴리스부터 Unity는 업그레이드된 스크립팅 런타임을 기본 선택으로 설정하고 C# 7로 업데이트할 계획입니다. 이 로드맵에 대한 자세한 정보와 최신 업데이트는 Unity의 [블로그 게시물](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)을 읽거나 [실험적 스크립팅 미리 보기 포럼](https://forum.unity.com/forums/experimental-scripting-previews.107/)을 방문하세요. 그 동안 .NET 4.x 스크립팅 런타임에서 현재 사용할 수 있는 새 기능에 대해 자세히 알아보려면 아래 섹션을 확인하세요.

## <a name="prerequisites"></a>사전 요구 사항

* [Unity 2017.1 이상](https://unity3d.com/)(2018.2 권장)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Unity에서.NET 4.x 스크립팅 런타임 사용

.NET 4.x 스크립팅 런타임을 사용하려면 다음 단계를 수행합니다.

1. **편집 > 프로젝트 설정 > 플레이어**를 선택하여 Unity Inspector에서 PlayerSettings를 엽니다.

1. **구성** 제목에서 **스크립팅 런타임 버전** 드롭다운을 클릭하고 **.NET 4.x 동등**을 선택합니다. Unity를 다시 시작하라는 메시지가 표시됩니다.

![.NET 4.x 해당 선택](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>.NET 4.x 및 NET Standard 2.0 프로필 중에서 선택

.NET 4.x 해당 스크립팅 런타임으로 전환한 후 PlayerSettings(**편집 > 프로젝트 설정 > 플레이어**)의 드롭다운 메뉴를 사용하여 **Api 호환성 수준**을 지정할 수 있습니다. 옵션에는

* **.NET Standard 2.0**. 이 프로필은 .NET Foundation에서 게시한 [.NET Standard 2.0 프로필](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md)과 일치합니다. Unity는 새 프로젝트에 .NET Standard 2.0을 권장합니다. 크기가 제한된 플랫폼에 적합한 .NET 4.x보다 작습니다. 또한 Unity는 Unity가 지원하는 모든 플랫폼에서 이 프로필을 지원하기 위해 커밋되었습니다.

* **.NET 4.x**. 이 프로필은 최신.NET 4 API에 대한 액세스를 제공합니다. 또한 .NET Framework 클래스 라이브러리에 사용할 수 있는 모든 코드를 포함하며 .NET Standard 2.0 프로필도 지원합니다. 프로젝트에 .NET Standard 2.0 프로필에 포함되지 않은 API의 일부가 필요한 경우 .NET 4.x 프로필을 사용합니다. 그러나 이 API의 일부는 Unity의 일부 플랫폼에서 지원되지 않을 수 있습니다.

Unity의 [블로그 게시물](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)에서 이러한 옵션에 대해 자세히 읽을 수 있습니다.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>.NET 4.x Api 호환성 수준 사용 시 어셈블리 참조 추가

**Api 호환성 수준** 드롭다운에서 .NET Standard 2.0 설정을 사용하면 API 프로필의 모든 어셈블리를 참조하고 사용할 수 있습니다. 그러나 대규모 .NET 4.x 프로필을 사용하는 경우 Unity와 함께 제공되는 일부 어셈블리는 기본적으로 참조되지 않습니다. 이러한 API를 사용하려면 어셈블리 참조를 수동으로 추가해야 합니다. Unity 편집기 설치의 **MonoBleedingEdge/lib/mono** 디렉터리에서 Unity와 함께 제공되는 어셈블리를 볼 수 있습니다.

![MonoBleedingEdge 디렉터리](media/vstu_monobleedingedge.png)

예를 들어 .NET 4.x 프로필을 사용 중이고 `HttpClient`를 사용하려면 System.Net.Http.dll에 대한 어셈블리 참조를 추가해야 합니다. 그렇지 않으면 컴파일러에서 어셈블리 참조가 누락되었다는 메시지가 표시될 수 있습니다.

![어셈블리 참조 추가 누락](media/vstu_missing-reference.png)

Visual Studio는 Unity 프로젝트가 열릴 때마다 .csproj 및.sln 파일을 다시 생성합니다. 따라서 프로젝트를 다시 열면 어셈블리 참조가 손실되므로 Visual Studio에서 직접 어셈블리 참조를 추가할 수 없습니다. 대신 **mcs.rsp**라는 특수 텍스트 파일을 사용해야 합니다.

1. Unity 프로젝트의 루트 **자산** 디렉터리에 **mcs.rsp**라는 새 텍스트 파일을 만듭니다.

1. 빈 텍스트 파일의 첫 번째 줄에 `-r:System.Net.Http.dll`을 입력한 다음, 파일을 저장합니다. "System.Net.Http.dll"을 누락되었을 수 있는 참조가 포함된 어셈블리로 바꿀 수 있습니다.

1. Unity 편집기를 다시 시작합니다.

## <a name="taking-advantage-of-net-compatibility"></a>.NET 호환성 활용

새 C# 구문과 언어 기능 외에도 .NET 4.x 스크립팅 런타임은 Unity 사용자에게 레거시 .NET 3.5 스크립팅 런타임과 호환되지 않는 대규모 .NET 패키지 라이브러리에 대한 액세스를 제공합니다.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>NuGet에서 Unity 프로젝트에 패키지 추가

[NuGet](https://www.nuget.org/)은 .NET의 패키지 관리자입니다. NuGet은 Visual Studio에 통합됩니다. 그러나 Unity 프로젝트에는 NuGet 패키지를 추가하는 특별한 프로세스가 필요합니다. 이는 Unity에서 프로젝트를 열면 Visual Studio 프로젝트 파일이 다시 생성되어 필요한 구성이 실행 취소되기 때문입니다. NuGet에서 Unity 프로젝트에 패키지를 추가하려면 다음을 수행합니다.

1. NuGet을 검색하여 추가할 호환 패키지(.NET Standard 2.0 또는.NET 4.x)를 찾습니다. 이 예제에서는 JSON을 사용하기 위한 인기 있는 패키지인 [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/)을 .NET Standard 2.0 프로젝트에 추가하는 방법을 보여 줍니다.

1. **다운로드** 단추를 클릭합니다.

    ![다운로드 단추](media/vstu_nuget-download.png)

1. 다운로드한 파일을 찾아서 확장자를 **.nupkg**에서 **.zip**으로 변경합니다.

1. zip 파일 내에서 **lib/netstandard2.0** 디렉터리로 이동하여 **Newtonsoft.Json.dll** 파일을 복사합니다.

1. Unity 프로젝트의 루트 **Assets** 폴더에서 **Plugins**라는 새 폴더를 만듭니다. 플러그 인은 Unity의 특수 폴더 이름입니다. 자세한 내용은 [Unity 설명서](https://docs.unity3d.com/Manual/Plugins.html)를 참조하세요.

1. **Newtonsoft.Json.dll** 파일을 Unity 프로젝트의 **플러그 인** 디렉터리에 붙여 넣습니다.

1. Unity 프로젝트의 **자산** 디렉터리에 **link.xml**이라는 파일을 만들고 다음 XML을 추가합니다.  이렇게 하면 IL2CPP 플랫폼으로 내보낼 때 Unity의 바이트코드 제거 프로세스가 필요한 데이터를 제거하지 않습니다.  이 단계는 이 라이브러리에 한정되지만, 비슷한 방식으로 리플렉션을 사용하는 다른 라이브러리에서는 문제가 발생할 수 있습니다.  자세한 내용은 이 항목의 [Unity 문서](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html)를 참조하세요.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

모든 것이 갖추어 졌으니, 이제 Json.NET 패키지를 사용할 수 있습니다.

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

이는 종속성이 없는 라이브러리를 사용하는 간단한 예입니다. NuGet 패키지가 다른 NuGet 패키지를 사용하는 경우 이러한 종속성을 수동으로 다운로드하여 동일한 방식으로 프로젝트에 추가해야 합니다.

## <a name="new-syntax-and-language-features"></a>새 구문 및 언어 기능

업데이트된 스크립팅 런타임을 사용하면 Unity 개발자는 C# 6에 액세스하고 새로운 언어 기능과 구문을 호스트할 수 있습니다.

### <a name="auto-property-initializers"></a>Auto 속성 이니셜라이저

Unity의 .NET 3.5 스크립팅 런타임에서 자동 속성 구문을 사용하면 초기화되지 않은 속성을 신속히 정의할 수 있지만, 초기화는 스크립트의 다른 위치에서 수행해야 합니다. 이제 .NET 4.x 런타임에서는 같은 줄에서 자동 속성을 초기화할 수 있습니다.

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>문자열 보간

이전 .NET 3.5 런타임에서는 문자열 연결에 복잡한 구문이 필요했습니다. 이제 .NET 4.x 런타임에서 [`$` 문자열 보간](/dotnet/csharp/language-reference/tokens/interpolated) 기능을 사용하면 식을 보다 직접적이고 읽기 쉬운 구문으로 문자열에 삽입할 수 있습니다.

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>식 본문 멤버

.NET 4.x 런타임에서 사용할 수 있는 최신 C# 구문을 사용하면 [람다 식](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)이 함수 본문을 더 간결하게 바꿀수 있습니다.

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

읽기 전용 속성에서 식 본문 멤버를 사용할 수도 있습니다.

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>TAP(작업 기반 비동기 패턴)

[비동기 프로그래밍](/dotnet/csharp/async)을 사용하면 애플리케이션이 응답하지 않는 시간이 오래 걸리는 작업을 수행할 수 있습니다. 또한 이 기능을 사용하면 시간이 많이 소요되는 작업이 완료될 때까지 코드를 기다렸다가 이러한 작업의 결과에 따라 코드를 계속 사용할 수 있습니다. 예를 들어 파일이 로드되거나 네트워크 작업이 완료될 때까지 기다릴 수 있습니다.

Unity에서 비동기 프로그래밍은 일반적으로 [코루틴](https://docs.unity3d.com/Manual/Coroutines.html)을 사용하여 수행됩니다. 그러나 C# 5 이후부터 .NET 개발에서 비동기 프로그래밍의 기본 방법은 [ System.Threading.Task](/dotnet/api/system.threading.tasks.task)와 함께 `async` 및 `await` 키워드를 사용하는 [TAP(작업 기반 비동기 패턴)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)입니다. 요약하면 `async` 함수에서 나머지 애플리케이션의 업데이트를 차단하지 않고 `await` 작업의 완료가 가능합니다.

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

TAP는 Unity별 뉘앙스를 고려해야 하는 복잡한 주제입니다. 결과적으로 TAP는 Unity의 코루틴에 대한 유니버설 대체물은 아니지만, 활용할 수 있는 또 다른 도구입니다. 이 기능의 범위는 이 문서에서 다루지 않지만 몇 가지 모범 사례 및 팁은 아래에 나와 있습니다.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Unity를 사용하여 TAP에 대한 시작 참조

이러한 팁은 Unity에서 TAP를 시작하는 데 도움이 될 수 있습니다.

* 대기할 비동기 함수는 반환 형식이 [`Task`](/dotnet/api/system.threading.tasks.task) 또는 [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1)이어야 합니다.
* 작업을 반환하는 비동기 함수에는 **"Async"** 접미사가 해당 이름에 추가되어야 합니다. "Async" 접미사는 함수가 항상 대기해야 함을 나타냅니다.
* 기존 동기식 코드에서 비동기 함수를 실행하는 함수에 대해서만 `async void` 반환 형식을 사용합니다. 이러한 함수는 자체적으로 대기할 수 없으며 이름에 "Async" 접미사가 없어야 합니다.
* Unity는 UnitySynchronizationContext를 사용하여 기본적으로 주 스레드에서 비동기 함수가 실행되도록 합니다. Unity API는 주 스레드의 외부에서 액세스할 수 없습니다.
* [`Task.Run`](/dotnet/api/system.threading.tasks.task.run) 및 [`Task.ConfigureAwait(false)`](/dotnet/api/system.threading.tasks.task.configureawait)와 같은 메서드를 사용하여 백그라운드 스레드에서 작업을 실행할 수 있습니다. 이 기술은 성능 향상을 위해 주 스레드에서 비용이 많이 드는 작업을 오프로딩하는 데 유용합니다. 그러나 백그라운드 스레드를 사용하면 [경합 조건](https://wikipedia.org/wiki/Race_condition)과 같이 디버그하기 어려운 문제가 발생할 수 있습니다.
* Unity API는 주 스레드 외부에서 액세스할 수 없습니다.
* 스레드를 사용하는 작업은 Unity WebGL 빌드에서 지원되지 않습니다.

#### <a name="differences-between-coroutines-and-tap"></a>코루틴과 TAP 사이의 차이점

코루틴과 TAP / async-await 사이에는 몇 가지 중요한 차이점이 있습니다.

* 코루틴은 값을 반환할 수 없지만 `Task<TResult>`는 반환할 수 있습니다.
* try-catch 문에 `yield`를 배치할 수 없으므로 코루틴에서 오류 처리를 어렵게 만듭니다. 그러나 try-catch는 TAP와 작동합니다.
* Unity의 코루틴 기능은 MonoBehaviour에서 파생되지 않은 클래스에서는 사용할 수 없습니다. TAP는 이러한 클래스의 비동기 프로그래밍에 적합합니다.
* 이 시점에서 Unity는 TAP를 코루틴의 도매 대체품으로 권장하지 않습니다. 프로파일링은 지정된 프로젝트에 대해 한 방식과 다른 방식의 특정 결과를 알 수 있는 유일한 방법입니다.

> [!NOTE]
> Unity 2018.2부터 중단점이 있는 디버깅 비동기 메서드가 충분히 지원되지 않지만 [이 기능은 Unity 2018.3에 필요합니다](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof 연산자

`nameof` 연산자는 변수, 형식 또는 멤버의 문자열 이름을 가져옵니다. `nameof`가 유용하게 사용되는 몇 가지 경우는 오류 로깅 및 열거형의 문자열 이름 가져오기 등이 있습니다.

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>호출자 정보 특성

[호출자 정보 특성](/dotnet/csharp/programming-guide/concepts/caller-information)은 메서드의 호출자에 대한 정보를 제공합니다. 호출자 정보 특성과 함께 사용할 각 매개 변수에 대한 기본값을 제공해야 합니다.

```csharp
private void Start ()
{
    ShowCallerInfo("Something happened.");
}
public void ShowCallerInfo(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    Debug.Log($"message: {message}");
    Debug.Log($"member name: {memberName}");
    Debug.Log($"source file path: {sourceFilePath}");
    Debug.Log($"source line number: {sourceLineNumber}");
}
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>Using static

[Using static](/dotnet/csharp/language-reference/keywords/using-static)은 해당 클래스 이름을 입력하지 않고 정적 함수를 사용할 수 있도록 합니다. using static을 사용하면, 동일한 클래스의 여러 정적 함수를 사용해야 하는 경우 공간과 시간을 절약할 수 있습니다

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>IL2CPP 고려 사항

iOS와 같은 플랫폼에 게임을 내보낼 때 Unity는 IL2CPP 엔진을 사용하여 IL을 C++ 코드로 "트랜스 파일"한 다음, 대상 플랫폼의 네이티브 컴파일러를 사용하여 컴파일합니다. 이 시나리오에서는 리플렉션 부분과 같이 지원되지 않는 몇 가지 .NET 기능 및 `dynamic` 키워드 사용법이 있습니다. 사용자 코드에서 이러한 기능을 사용하여 제어할 수 있지만, Unity 및 IL2CPP로 작성되지 않은 타사 DLL 및 SDK를 사용하면 문제가 발생할 수 있습니다. 이 항목에 대한 자세한 내용은 Unity 사이트의 [스크립팅 제한](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) 문서를 참조하세요.

또한 위의 Json.NET 예제에서 설명된 바와 같이 Unity는 IL2CPP 내보내기 프로세스 중에 사용되지 않는 코드를 제거하려고 시도합니다.  이 동작은 일반적으로 문제가 되지 않지만 리플렉션을 사용하는 라이브러리에서 내보내기 시 확인할 수 없는, 런타임에 호출되는 속성이나 메서드를 실수로 제거할 수 있습니다.  이러한 문제를 해결하려면 제거 프로세스를 실행하지 않는 어셈블리 및 네임스페이스 목록이 포함된 **link.xml** 파일을 프로젝트에 추가합니다.  자세한 세부 정보는 [바이트코드 제거에 대한 Unity의 문서](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html)를 참조하세요.

## <a name="net-4x-sample-unity-project"></a>.NET 4.x 샘플 Unity 프로젝트

샘플에는 여러 .NET 4.x 기능의 예가 포함되어 있습니다. [GitHub](https://github.com/Microsoft/unity-scripting-upgrade)에서 프로젝트를 다운로드하거나 소스 코드를 볼 수 있습니다.

## <a name="additional-resources"></a>추가 리소스

* [Unity 블로그 - Unity 2018.2에서 스크립팅 런타임 개선](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [C#의 기록](/dotnet/csharp/whats-new/csharp-version-history)
* [C# 6의 새로운 기능](/dotnet/csharp/whats-new/csharp-6)
* [코루틴 및 TAP를 사용한 Unity의 비동기 프로그래밍](/archive/blogs/appconsult/unity-coroutine-tap-en-us)
* [Unity 2017의 코루틴 대신 Async-Await](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Unity 포럼 - 실험적 스크립팅 미리 보기](https://forum.unity.com/forums/experimental-scripting-previews.107/)