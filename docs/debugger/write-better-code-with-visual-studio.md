---
title: 디버깅 기술 및 도구
description: Visual Studio를 사용하여 예외를 해결하고, 오류를 수정하고, 코드를 개선하여 버그를 줄이고 더 나은 코드를 작성합니다.
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301022"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>더 나은 코드를 작성하는 데 도움이 되는 디버깅 기술 및 도구

코드에서 버그 및 오류를 수정하는 작업은 시간이 오래 걸리고 때로는 매우 어려울 수 있습니다. 효과적으로 디버그하는 방법을 배우는 데는 시간이 걸리므로 Visual Studio와 같은 강력한 IDE를 사용하면 작업을 훨씬 쉽게 만들 수 있습니다. IDE를 사용하면 오류를 수정하고 코드를 더 빠르게 디버그할 수 있을 뿐만 아니라 버그를 줄이고 더 나은 코드를 작성하는 데 도움이 됩니다. 이 문서의 목표는 "버그 수정" 프로세스에 대한 종합적인 관점을 제공하는 것입니다. 따라서 코드 분석기를 사용하는 시기, 디버거를 사용하는 시기, 예외를 해결하는 방법, 의도를 코딩하는 방법을 알 수 있습니다. 디버거를 사용해야 함을 이미 알고 있는 경우 [디버거 소개](../debugger/debugger-feature-tour.md)를 참조하세요.

이 문서에서는 코딩 세션의 생산성을 높이기 위해 IDE를 활용하는 방법을 설명합니다. 여기서는 다음과 같은 몇 가지 작업을 다룹니다.

* IDE의 코드 분석기를 활용하여 디버깅을 위해 코드 준비

* 예외(런타임 오류)를 해결하는 방법

* 의도를 코딩하여 버그를 최소화하는 방법(어설션 사용)

* 디버거를 사용하는 시기

이러한 작업을 설명하기 위해 앱을 디버그할 때 발생하는 몇 가지 일반적인 오류 및 버그 유형을 보여 줍니다. 샘플 코드는 C#이지만 개념은 C++, Visual Basic, JavaScript 및 기타 Visual Studio에서 지원하는 언어(명시된 경우는 제외)에 일반적으로 적용됩니다. 스크린샷은 C#에 있습니다.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>몇 가지 버그와 오류가 있는 샘플 앱 만들기

다음 코드에는 Visual Studio IDE를 사용하여 해결할 수 있는 몇 가지 버그가 있습니다. 이 앱은 일부 작업에서 JSON 데이터 가져오기를 시뮬레이션하고 데이터를 개체로 deserialize하며 간단한 목록을 새 데이터로 업데이트하는 간단한 앱입니다.

앱을 만들려면:

1. Visual Studio가 설치되어 있어야 하며 만들려는 앱 형식에 따라 **.NET Core 플랫폼 간 개발** 워크로드 또는 **.NET 데스크톱 개발** 워크로드가 설치되어 있어야 합니다.

    아직 Visual Studio를 설치하지 않은 경우  [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/)  페이지로 이동하여 체험용으로 설치합니다.

    워크로드를 설치해야 하지만 이미 Visual Studio가 있는 경우 **도구** > **도구 및 기능 가져오기**를 클릭합니다. Visual Studio 설치 관리자가 시작됩니다. **.NET Core 플랫폼 간 개발**(또는 **.NET 데스크톱 개발**) 워크로드를 선택한 다음, **수정**을 선택합니다.

1. Visual Studio를 엽니다.

    ::: moniker range=">=vs-2019"
    시작 창에서 **새 프로젝트 만들기**를 선택합니다. 검색 창에 **콘솔**을 입력한 다음, **콘솔 앱(.NET Core)** 또는 **콘솔 앱(.NET Framework)** 을 선택합니다. **다음**을 선택합니다. **Console_Parse_JSON**과 같은 프로젝트 이름을 입력하고 **만들기**를 클릭합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C#** 아래에 **콘솔 앱**을 선택한 다음, 가운데 창에서 **콘솔 앱(.NET Core)** 또는 **콘솔 앱(.NET Framework)** 을 선택합니다. **Console_Parse_JSON**과 같은 이름을 입력하고 **확인**을 클릭합니다.
    ::: moniker-end

    **콘솔 앱(.NET Core)** 또는 **콘솔 앱(.NET Framework)** 프로젝트 템플릿이 표시되지 않는 경우 **도구** > **도구 및 기능 가져오기**로 이동하면 Visual Studio 설치 관리자가 열립니다. **.NET Core 플랫폼 간 개발** 또는 **.NET 데스크톱 개발** 워크로드를 선택한 다음, **수정**을 선택합니다.

    Visual Studio에서 콘솔 프로젝트를 만들고 오른쪽 창의 솔루션 탐색기에 나타납니다.

1. 프로젝트의 *Program.cs* 파일에서 기본 코드를 아래의 샘플 코드로 바꿉니다.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>빨간색 및 녹색 오류 표시선을 찾으세요!

샘플 앱을 시작하고 디버거를 실행하기 전에 코드 편집기에서 코드에 빨간색 및 녹색 오류 표시선이 표시되는지 확인합니다. 이러한 표시선은 IDE의 코드 분석기가 식별하는 오류 및 경고를 나타냅니다. 빨간색 오류 표시선은 컴파일 시간 오류로, 코드를 실행하기 전에 수정해야 합니다. 녹색 오류 표시선은 경고입니다. 경고를 수정하지 않아도 애플리케이션을 실행할 수 있지만 버그의 원인이 될 수 있으며, 이를 조사하면 시간과 문제를 줄일 수 있는 경우가 많습니다. 목록 보기를 선호하는 경우 이러한 경고 및 오류는 **오류 목록** 창에도 표시됩니다.

샘플 앱에는 수정해야 하는 몇 가지 빨간색 오류 표시선과 조사해야 하는 하나의 녹색 오류 표시선이 있습니다. 첫 번째 오류는 다음과 같습니다.

![빨간색 오류 표시선으로 표시되는 오류](../debugger/media/write-better-code-red-squiggle.png)

이 오류를 해결하려면 전구 아이콘으로 표시되는 IDE의 다른 기능을 살펴보아야 합니다.

## <a name="check-the-light-bulb"></a>전구를 확인하세요!

첫 번째 빨간색 오류 표시선은 컴파일 시간 오류를 나타냅니다. 이 오류 표시선을 마우스로 가리키면 ```The name `Encoding` does not exist in the current context``` 메시지가 표시됩니다.

이 오류가 발생하면 왼쪽 아래에 전구 아이콘이 표시됩니다. 전구 아이콘 ![전구 아이콘](../ide/media/light-bulb-icon.png)은 스크루드라이버 아이콘 ![드라이버 아이콘](../ide/media/screwdriver-icon.png)과 함께 인라인으로 코드를 수정 또는 리팩터링하는 데 도움이 되는 빠른 작업을 나타냅니다. 전구는  반드시 수정해야 하는 문제를 나타냅니다. 스크루드라이버는 해결을 선택할 수 있는 문제에 대한 것입니다. 왼쪽에 있는 **using System.Text 사용**을 클릭하여 이 오류를 해결하기 위한 첫 번째 권장 픽스를 사용합니다.

![전구를 사용하여 코드 수정](../debugger/media/write-better-code-missing-include.png)

이 항목을 클릭하면 Visual Studio가 *Program.cs* 파일의 맨 위에 `using System.Text` 문을 추가하고 빨간색 오류 표시선이 사라집니다. (제안된 픽스가 어떤 작업을 수행하는지 잘 모르는 경우 픽스를 적용하기 전에 오른쪽에 있는 **변경 내용 미리 보기** 링크를 선택합니다.)

앞의 오류는 일반적으로 코드에 새 `using` 문을 추가하여 수정하는 일반적인 오류입니다. 이와 비슷한 여러 가지 일반적 오류가 있습니다(예: ```The type or namespace `Name` cannot be found.```). 이러한 종류의 오류는 어셈블리 참조 누락(프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **레퍼런스**를 선택), 철자가 잘못된 이름 또는 추가해야 하는 라이브러리 누락(C# 경우 프로젝트를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리**를 선택)을 나타낼 수 있습니다.

## <a name="fix-the-remaining-errors-and-warnings"></a>나머지 오류 및 경고 수정

이 코드에는 살펴볼 몇 가지 추가 오류 표시선이 있습니다. 여기서는 일반적인 형식 변환 오류가 표시됩니다. 오류 표시선을 마우스로 가리키면 코드에서 문자열을 int로 변환하려고 시도하는 것을 확인할 수 있습니다. 이 변환은 명시적 변환 코드를 추가하지 않으면 지원되지 않습니다.

![형식 변환 오류](../debugger/media/write-better-code-conversion-error.png)

코드 분석기는 개발자의 의도를 추측할 수 없기 때문에 이번에는 디버깅에 도움이 되는 전구가 표시되지 않습니다. 이 오류를 해결하려면 코드의 의도를 알고 있어야 합니다. 이 예제에서는 `totalpoints`에 `points`를 추가하려는 것이므로 `points`가 숫자(정수) 값이어야 한다는 것을 어렵지 않게 알 수 있습니다.

이 오류를 해결하려면 `User` 클래스의 `points` 멤버를

```csharp
[DataMember]
internal string points;
```

아래와 같이 변환합니다.

```csharp
[DataMember]
internal int points;
```

코드 편집기에서 빨간색 오류 표시선이 사라집니다.

다음으로 `points` 데이터 멤버의 선언에서 녹색 오류 표시선을 마우스로 가리킵니다. 코드 분석기는 변수에 값이 할당되지 않았음을 보여 줍니다.

![할당되지 않은 변수에 대한 경고 메시지](../debugger/media/write-better-code-warning-message.png)

일반적으로 이는 해결해야 하는 문제를 나타냅니다. 그러나 실제로는 샘플 앱에서 deserialization 프로세스 중에 `points` 변수에 데이터를 저장한 다음 `totalpoints` 데이터 멤버에 해당 값을 추가합니다. 이 예제에서는 코드의 의도를 알고 있으므로 경고를 안전하게 무시할 수 있습니다. 그러나 경고를 제거하려면 다음 코드를

```csharp
item.totalpoints = users[i].points;
```

다음 코드로 바꿉니다.

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

녹색 오류 표시선이 사라집니다.

## <a name="fix-an-exception"></a>예외 수정

모든 빨간색 오류 표시선을 수정하고 모든 녹색 오류 표시선을 해결(또는 최소한 조사)했으면 디버거를 시작하고 앱을 실행할 준비가 된 것입니다.

디버그 도구 모음에서 **F5**(**디버그 > 디버깅 시작**) 또는 **디버깅 시작** 단추 ![디버깅 시작](../debugger/media/dbg-tour-start-debugging.png "디버깅 시작")를 누릅니다.

이 시점에서 샘플 앱은 `SerializationException` 예외(런타임 오류)를 throw합니다. 즉, 앱이 serialize하려고 하는 데이터에서 중단됩니다. 디버그 모드에서 앱을 시작했으므로(디버거가 연결됨), 디버거의 예외 도우미가 예외를 throw한 코드로 바로 이동하고 유용한 오류 메시지를 제공합니다.

![SerializationException 발생](../debugger/media/write-better-code-serialization-exception.png)

`4o` 값을 정수로 구문 분석할 수 없다는 오류 메시지가 표시됩니다. 따라서 이 예제에서는 데이터가 잘못된 것을 알 수 있습니다. `4o`는 `40`이어야 합니다. 그러나 실제 시나리오에서 데이터를 제어하지 않는 경우(웹 서비스에서 데이터를 가져오는 경우) 어떻게 해야 할까요? 어떻게 이 문제를 해결할 수 있을까요?

예외가 발생하면 몇 가지 질문을 하고 대답해야 합니다.

* 이 예외는 해결할 수 있는 버그인가? 또는,

* 이 예외가 사용자에게 발생할 수 있는가?

전자인 경우 버그를 수정합니다. (샘플 앱에서는 잘못된 데이터를 수정하는 것을 의미합니다.) 후자인 경우 `try/catch` 블록을 사용하여 코드에서 예외를 처리해야 할 수 있습니다. (다음 섹션에서 가능한 다른 전략을 알아봅니다.) 샘플 앱에서 다음 코드를

```csharp
users = ser.ReadObject(ms) as User[];
```

이 코드로 바꿉니다.

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

`try/catch` 블록에는 일부 성능 비용이 있으므로 정말로 필요한 경우에만, 즉 (a) 애플리케이션의 릴리스 버전에서 발생할 수 있는 경우와 (b) 메서드 설명서에서 예외를 확인해야 한다고 표시된 경우(설명서가 완벽하다고 가정)에 사용해야 합니다. 대부분의 경우 예외를 적절하게 처리할 수 있으며 사용자는 예외를 알 필요가 없습니다.

예외 처리에 대한 몇 가지 중요한 팁은 다음과 같습니다.

* 오류를 노출 또는 처리하기 위해 적절한 조치를 취하지 않는 `catch (Exception) {}`와 같은 빈 catch 블록을 사용하지 마세요. 비어 있거나 정보를 제공하지 않는 catch 블록은 예외를 숨길 수 있으며 오히려 코드를 디버그하기 어려워질 수 있습니다.

* 예외를 throw하는 특정 함수(샘플 앱의 `ReadObject`) 주위에 `try/catch` 블록을 사용하세요. 더 큰 코드 청크 주위에 사용하는 경우 오류 위치를 찾을 수 없게 됩니다. 예를 들어 여기에 표시된 `ReadToObject` 부모 함수 호출 주위에 `try/catch` 블록을 사용하지 마세요. 그러면 예외가 발생한 위치를 정확하게 알 수 없습니다.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* 애플리케이션에 포함하는 익숙하지 않은 함수, 특히 외부 데이터(예: 웹 요청)와 상호 작용하는 함수는 설명서를 확인하여 함수가 throw할 가능성이 높은 예외를 확인하세요. 이는 적절한 오류 처리 및 앱 디버깅에 대한 중요한 정보일 수 있습니다.

샘플 앱의 경우 `4o`를 `40`으로 변경하여 `GetJsonData` 메서드에서 `SerializationException`을 수정합니다.

## <a name="clarify-your-code-intent-by-using-assert"></a>어설션을 사용하여 코드 의도 명시

디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭합니다(**Ctrl** + **Shift** + **F5**). 그러면 앱이 더 적은 단계로 다시 시작합니다. 콘솔 창에서 다음과 같은 출력이 표시됩니다.

![출력의 Null 값](../debugger/media/write-better-code-using-assert-null-output.png)

이 출력에서 잘못된 항목을 볼 수 있습니다. 세 번째 레코드의 **name** 및 **lastname**이 비어 있습니다.

이는 함수에서 `assert` 문을 사용하는 데 도움이 되는 유용하지만 종종 잘 사용하지 않는 코딩 습관에 대해 설명하기 좋은 기회입니다. 다음 코드를 추가하여 `firstname` 및 `lastname`이 `null`이 아닌지 확인하는 런타임 검사를 포함합니다. `UpdateRecords` 메서드에서 다음 코드를

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

다음 코드로 바꿉니다.

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

개발 프로세스 중에 다음과 같은 `assert` 문을 함수에 추가하면 코드의 의도를 지정할 수 있습니다. 앞의 예제에서는 다음이 지정되어 있습니다.

* 이름에 유효한 문자열이 필요
* 성에 유효한 문자열이 필요

이러한 방식으로 의도를 지정하여 요구 사항을 적용합니다. 이는 개발 중에 버그를 표시하는 데 사용할 수 있는 간단하고 편리한 방법입니다. (`assert` 문은 단위 테스트의 기본 요소로도 사용됩니다.)

디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭합니다(**Ctrl** + **Shift** + **F5**).

> [!NOTE]
> `assert` 코드는 디버그 빌드에서만 활성화됩니다.

다시 시작하면 `users[i].firstname != null` 식이 `true`가 아니라 `false`로 계산되기 때문에 디버거가 `assert` 문에서 일시 중지됩니다.

![어설션이 false로 확인됨](../debugger/media/write-better-code-using-assert.png)

`assert` 오류는 조사해야 할 문제가 있음을 나타냅니다. `assert`는 반드시 예외가 표시되지는 않는 여러 시나리오를 처리할 수 있습니다. 이 예제에서는 사용자에게 예외가 표시되지 않으며 레코드 목록에서 `firstname`으로 `null` 값이 추가됩니다. 이로 인해 나중에 문제가 발생할 수 있으며(예를 들어 콘솔 출력에 표시됨) 디버그하기 어려워질 수 있습니다.

> [!NOTE]
> `null` 값에 대해 메서드를 호출하는 시나리오에서는 `NullReferenceException`이 발생합니다. 일반적으로 일반 예외, 즉 특정 라이브러리 함수에 연결되지 않은 예외에는 `try/catch` 블록을 사용하지 않는 것이 좋습니다. 모든 개체는 `NullReferenceException`을 throw할 수 있습니다. 확실하지 않은 경우 라이브러리 함수에 대한 설명서를 확인합니다.

디버깅 프로세스 중에는 실제 코드 픽스로 바꾸어야 할 때까지 특정 `assert` 문을 유지하는 것이 좋습니다. 앱의 릴리스 빌드에서 사용자에게 예외가 발생할 수 있다고 판단하는 경우를 가정해 보겠습니다. 이 경우 앱이 심각한 예외를 throw하지 않는지, 다른 오류가 발생하지 않는지 확인하기 위해 코드를 리팩터링해야 합니다. 따라서 이 코드를 수정하려면 다음 코드를

```csharp
if (existingUser == false)
{
    User user = new User();
```

이 코드로 바꿉니다.

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

이 코드를 사용하여 코드 요구 사항을 충족하고 `null`의 `firstname` 또는 `lastname` 값이 포함된 레코드가 데이터에 추가되지 않는지 확인합니다.

이 예제에서는 루프 내에 두 개의 `assert` 문을 추가했습니다. 일반적으로 `assert`를 사용하는 경우 함수 또는 메서드의 진입점(시작 부분)에 `assert` 문을 추가하는 것이 가장 좋습니다. 샘플 앱에서는 `UpdateRecords` 메서드가 보입니다. 이 메서드에서는 메서드 인수 중 하나라도 `null`일 경우 문제라는 것을 알고 있으므로 함수 진입점에서 `assert` 문을 사용하여 모두 확인합니다.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

위의 문에서는 모든 항목을 업데이트하기 전에 기존 데이터(`db`)를 로드하고 새 데이터(`users`)를 검색합니다.

`true` 또는 `false`로 확인되는 모든 종류의 식에 `assert`를 사용할 수 있습니다. 따라서 예를 들어 다음과 같이 `assert` 문을 추가할 수 있습니다.

```csharp
Debug.Assert(users[0].points > 0);
```

앞의 코드는 사용자 레코드를 업데이트하려면 0보다 큰 새 포인트 값이 필요하다는 의도를 지정하는 데 유용합니다.

## <a name="inspect-your-code-in-the-debugger"></a>디버거에서 코드 검사

이제 샘플 앱에 문제가 있는 모든 것을 수정했으므로 다른 중요한 항목으로 이동할 수 있습니다.

디버거의 예외 도우미를 살펴보았지만, 디버거는 코드를 단계별로 실행하고 변수를 검사하는 등의 다른 작업을 수행할 수 있는 훨씬 더 강력한 도구입니다. 보다 강력한 이러한 기능은 다양한 시나리오에서, 특히 다음과 같은 경우에 유용합니다.

* 코드에서 런타임 버그를 격리하려고 하지만 앞에서 설명한 메서드 및 도구를 사용하여 이 작업을 수행할 수 없는 경우

* 코드의 유효성을 검사, 즉 코드 실행을 감시하며 코드가 예상대로 동작하고 원하는 작업을 수행하는지 확인하려는 경우

    코드를 실행하는 동안 코드를 감시하는 것이 좋습니다. 이러한 방식으로 코드에 대한 자세한 정보를 확인할 수 있으며, 확실한 증상이 발생하기 전에 버그를 식별할 수 있는 경우가 자주 있습니다.

디버거의 주요 기능을 사용하는 방법을 자세히 알아보려면 [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)을 참조하세요.

## <a name="fix-performance-issues"></a>성능 문제 해결

다른 종류의 버그에는 앱이 느리게 실행되거나 너무 많은 메모리를 사용하는 비효율적인 코드가 포함됩니다. 일반적으로 성능 최적화는 앱 개발에서 나중에 수행하는 작업입니다. 그러나 초기에 성능 문제가 발생할 수 있으며(예를 들어 앱의 일부가 느리게 실행되는 것이 확인됨) 프로파일링 도구를 사용하여 조기에 애플리케이션을 테스트해야 할 수도 있습니다. CPU 사용량 도구 및 메모리 분석기와 같은 프로파일링 도구에 대한 자세한 내용은 [프로파일링 도구 살펴보기](../profiling/profiling-feature-tour.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

이 문서에서는 코드에서 일반적으로 발생하는 많은 버그를 방지하고 수정하는 방법과 디버거를 사용하는 시기에 대해 배웠습니다. 다음으로, Visual Studio 디버거를 사용하여 버그를 수정하는 방법을 자세히 알아봅니다.

> [!div class="nextstepaction"]
> [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)
