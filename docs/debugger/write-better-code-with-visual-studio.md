---
title: 디버깅 기술 및 도구
description: Visual Studio를 사용 하 여 예외를 수정 하 고, 오류를 수정 하 고, 코드를 개선 하 여 버그를 줄이고 더 나은 코드 작성
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
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416414"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>더 나은 코드를 작성 하는 데 도움이 되는 디버깅 기술 및 도구

코드에서 버그 및 오류를 수정 하는 작업은 시간이 오래 걸리고 때로는 매우 어려울 수 있습니다. 효과적으로 디버그 하는 방법을 배우는 데 시간이 걸리므로 Visual Studio와 같은 강력한 IDE를 사용 하면 작업을 훨씬 더 쉽게 만들 수 있습니다. IDE를 사용 하면 오류를 수정 하 고 코드를 더 신속 하 게 디버그할 수 있을 뿐만 아니라 더 빠른 코드를 작성 하는 데 도움이 됩니다. 이 문서의 목표는 "버그 수정" 프로세스에 대 한 전체적인 뷰를 제공 하는 것입니다. 따라서 코드 분석기를 사용 하는 시기, 디버거를 사용 하는 시기, 예외를 해결 하는 방법 및 의도를 코딩 하는 방법을 알 수 있습니다. 디버거를 사용 해야 하는 경우 디버거를 [먼저 확인](../debugger/debugger-feature-tour.md)을 참조 하세요.

이 문서에서는 코딩 세션의 생산성을 높이기 위해 IDE를 활용 하는 방법에 대해 설명 합니다. 다음과 같은 몇 가지 작업을 수행 합니다.

* IDE의 코드 분석기를 활용 하 여 디버깅을 위해 코드 준비

* 예외 (런타임 오류)를 해결 하는 방법

* 버그를 최소화 하면서 의도한대로 코딩하는 방법(assert 사용)

* 디버거를 사용 하는 경우

이러한 작업을 설명 하기 위해 앱을 디버깅 하려고 할 때 발생 하는 몇 가지 일반적인 오류 및 버그 유형을 보여 줍니다. 샘플 코드는 C#이지만 개념적 정보는 일반적으로 Visual Studio에서 지원하는 C++, Visual Basic, JavaScript 및 기타 언어(명시된 경우 제외)에 적용됩니다. 스크린샷은 C#에 있습니다. 스크린샷은 C#에 있습니다.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>몇 가지 버그와 오류가 있는 샘플 앱 만들기

다음 코드에는 Visual Studio IDE를 사용하여 해결할 수 있는 몇 가지 버그가 있습니다. 여기에 있는 앱은 일부 작업에서 JSON 데이터 가져오기를 시뮬레이션하고, 데이터를 개체로 deserialize하고, 간단한 목록을 새 데이터로 업데이트하는 간단한 앱입니다.

앱을 만들려면 다음을 수행합니다.

1. 만들려는 앱 유형에 따라 Visual Studio를 설치 하 고 **.Net Core 플랫폼 간 개발** 또는 **.net 데스크톱 개발** 워크 로드를 설치 해야 합니다.

    아직 Visual Studio를 설치하지 않은 경우  [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/)  페이지로 이동하여 체험용으로 설치합니다.

    워크로드를 설치해야 하지만 이미 Visual Studio가 있는 경우 **도구** > **도구 및 기능 가져오기**를 클릭합니다. Visual Studio 설치 관리자가 시작됩니다. **.Net Core 플랫폼 간 개발** 또는 **.net 데스크톱 개발** 워크 로드를 선택한 다음 **수정**을 선택 합니다.

1. Visual Studio를 엽니다.

    ::: moniker range=">=vs-2019"
    시작 창에서 **새 프로젝트 만들기**를 선택합니다. 검색 상자에 **console** 을 입력 한 다음 **콘솔 앱 (.net Core)** 또는 **콘솔 앱 (.NET Framework)** 을 선택 합니다. **다음**을 선택합니다. **Console_Parse_JSON** 와 같은 프로젝트 이름을 입력 하 고 **만들기**를 클릭 합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에 있는 **Visual C#** 에서 **콘솔 앱**을 선택한 다음 가운데 창에서 **콘솔 앱 (.net Core)** 또는 **콘솔 앱 (.NET Framework)** 을 선택 합니다. **Console_Parse_JSON** 와 같은 이름을 입력 하 고 **확인**을 클릭 합니다.
    ::: moniker-end

    **콘솔 앱 (.Net Core)** 또는 **콘솔 앱 (.NET Framework)** 프로젝트 템플릿이 표시 되지 않으면 **도구** > 도구 **및 기능 가져오기**로 이동 하 여 Visual Studio 설치 관리자를 엽니다. **.Net Core 플랫폼 간 개발** 또는 **.net 데스크톱 개발** 워크 로드를 선택한 다음 **수정**을 선택 합니다.

    Visual Studio에서 콘솔 프로젝트를 만들고 오른쪽 창의 솔루션 탐색기에 나타납니다.

1. 프로젝트의 *Program.cs* 파일에 있는 기본 코드를 아래의 샘플 코드로 바꿉니다.

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

## <a name="find-the-red-and-green-squiggles"></a>Red 및 green 물결선을 찾습니다.

샘플 앱을 시작하고 디버거를 실행하기 전에 코드 편집기에서 red 및 green 물결선 코드를 확인합니다. 이는 IDE의 코드 분석기에서 식별하는 오류 및 경고를 나타냅니다. Red 물결선은 컴파일 시간 오류로, 코드를 실행하기 전에 수정해야 합니다. 녹색 물결선은 경고입니다. 경고를 수정하지 않고 응용 프로그램을 실행할 수 있지만, 버그의 원인이 될 수 있으며, 종종 이를 조사하여 시간과 문제를 줄일 수 있습니다. 이러한 경고 및 오류는 목록 보기를 선호 하는 경우에도 **오류 목록** 창에 표시 됩니다.

샘플 앱에는 수정해야 하는 몇 개의 빨간 물결선과 조사해야 하는 녹색 물결선 하나가 표시됩니다. 첫 번째 오류는 다음과 같습니다.

![빨간색 물결선으로 표시 되는 오류](../debugger/media/write-better-code-red-squiggle.png)

이 오류를 해결 하려면 전구 아이콘으로 표시 되는 IDE의 다른 기능을 살펴봅니다.

## <a name="check-the-light-bulb"></a>전구를 확인합니다.

첫 번째 빨강 물결선은 컴파일 시간 오류를 나타냅니다. 위로 마우스를 가져가면 ```The name `Encoding` does not exist in the current context```메시지가 표시 됩니다.

이 오류가 발생하면 왼쪽 아래에 전구 아이콘이 표시됩니다. 드라이버 아이콘 ![드라이버 아이콘](../ide/media/screwdriver-icon.png), 전구 아이콘 ![전구 아이콘](../ide/media/light-bulb-icon.png) 코드 인라인을 수정 하거나 리팩터링 하는 데 도움이 되는 빠른 작업을 나타냅니다. 전구는 해결 *해야* 하는 문제를 나타냅니다. 드라이버는 해결하기 위해 선택할 수 있는 문제에 대한 것입니다. 왼쪽에 있는 **system.web 사용** 을 클릭 하 여이 오류를 해결 하려면 첫 번째 권장 픽스를 사용 합니다.

![전구를 사용 하 여 코드 수정](../debugger/media/write-better-code-missing-include.png)

이 항목을 클릭 하면 Visual Studio에서 *Program.cs* 파일의 맨 위에 `using System.Text` 문을 추가 하 고 빨간색 물결선은 사라집니다. (제안 된 수정 작업을 수행 하는 것이 확실 하지 않은 경우 수정 내용을 적용 하기 전에 오른쪽의 **변경 내용 미리 보기** 링크를 선택 합니다.)

앞의 오류는 일반적으로 코드에 새 `using` 문을 추가 하 여 수정 하는 일반적인 오류입니다. 이러한 종류의 오류는 어셈블리 참조가 누락 된 경우 (프로젝트를 마우스 오른쪽 단추로 클릭 하 고 > **참조** C# **추가** 선택), 철자가 잘못 된 이름 또는 추가 해야 하는 누락 된 라이브러리 (의 경우 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리**선택)를 나타낼 수 ```The type or namespace `Name` cannot be found.```와 같은 일반적인 유사한 오류가 있습니다.

## <a name="fix-the-remaining-errors-and-warnings"></a>나머지 오류 및 경고 수정

이 코드에서 살펴볼 몇 가지 추가 물결선 있습니다. 여기에서 일반적인 형식 변환 오류가 표시 됩니다. 물결선을 마우스로 가리키면 코드에서 문자열을 int로 변환 하려고 시도 하는 것을 확인할 수 있습니다 .이는 변환을 수행 하기 위해 명시적 코드를 추가 하지 않으면 지원 되지 않습니다.

![형식 변환 오류](../debugger/media/write-better-code-conversion-error.png)

코드 분석기는 의도를 추측할 수 없기 때문에이 시간을 지 원하는 데 도움이 되는 가벼운 전구 없습니다. 이 오류를 해결 하려면 코드의 의도를 알고 있어야 합니다. 이 예제에서는 `totalpoints`에 `points`를 추가 하려고 하기 때문에 `points` 숫자 (정수) 값 이어야 한다는 것을 확인 하기가 너무 어렵습니다.

이 오류를 해결 하려면 `User` 클래스의 `points` 멤버를 다음과 같이 변경 합니다.

```csharp
[DataMember]
internal string points;
```

다음과 같이 변경합니다.

```csharp
[DataMember]
internal int points;
```

코드 편집기에서 빨간 물결 모양의 선이 사라집니다.

그런 다음 `points` 데이터 멤버의 선언에서 녹색 물결선을 마우스로 가리킵니다. 코드 분석기는 변수에 값이 할당 되지 않음을 나타냅니다.

![할당 되지 않은 변수에 대 한 경고 메시지](../debugger/media/write-better-code-warning-message.png)

일반적으로이 문제는 해결 해야 하는 문제를 나타냅니다. 그러나 샘플 앱에서는 deserialization 프로세스 중에 `points` 변수에 데이터를 저장 한 다음 `totalpoints` 데이터 멤버에 해당 값을 추가 합니다. 이 예제에서는 코드의 의도를 알고 있으므로 경고를 안전 하 게 무시할 수 있습니다. 그러나 경고를 제거 하려는 경우 다음 코드를 바꿀 수 있습니다.

```csharp
item.totalpoints = users[i].points;
```

다음 코드로 바꿉니다.

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

녹색 물결선이 사라집니다.

## <a name="fix-an-exception"></a>예외 수정

모든 red 물결선을 수정 하 고 해결 한 경우 또는 최소한 조사--모든 녹색 물결선 하면 디버거를 시작 하 고 앱을 실행할 준비가 된 것입니다.

디버그 도구 ![모음에서](../debugger/media/dbg-tour-start-debugging.png "디버그") **F5** 키 (**디버그 > 디버깅 시작**) **또는 디버깅 시작 단추를** 누릅니다.

이 시점에서 샘플 앱은 `SerializationException` 예외 (런타임 오류)를 throw 합니다. 즉, 응용 프로그램은 serialize 하려고 하는 데이터에서 좁게 합니다. 디버그 모드에서 응용 프로그램을 시작 했으므로 (디버거 연결), 디버거의 예외 도우미가 예외를 throw 한 코드를 바로 사용 하 고 유용한 오류 메시지를 제공 합니다.

![SerializationException 발생](../debugger/media/write-better-code-serialization-exception.png)

`4o` 값을 정수로 구문 분석할 수 없다는 오류 메시지가 표시 됩니다. 따라서이 예에서는 데이터가 잘못 된 것을 알 수 있습니다. `4o` `40`해야 합니다. 그러나 실제 시나리오에서 데이터를 제어 하지 않는 경우 (웹 서비스에서 데이터를 가져오는 경우) 어떻게 해야 하나요? 이 문제를 해결 하려면 어떻게 해야 하나요?

예외가 발생 하면 몇 가지 질문을 하 고 대답 해야 합니다.

* 이 예외는 해결할 수 있는 버그 인가요? 또는

* 이 예외는 사용자에 게 발생할 수 있는 것입니다.

이전 인 경우 버그를 수정 합니다. 샘플 앱에서 잘못 된 데이터를 수정 하는 것을 의미 합니다. 후자 인 경우 `try/catch` 블록을 사용 하 여 코드에서 예외를 처리 해야 할 수 있습니다 (다음 섹션에서 가능한 다른 전략을 참조). 샘플 앱에서 다음 코드를 바꿉니다.

```csharp
users = ser.ReadObject(ms) as User[];
```

바꿉니다.

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

`try/catch` 블록에는 성능 비용이 있습니다. 즉,이 경우에는 (a) 응용 프로그램의 릴리스 버전에서 발생할 수 있는 위치, 즉 (b) 메서드에 대 한 설명서에서 예외를 확인 해야 한다고 표시 됩니다 (설명서 완료 라고 가정). 대부분의 경우 예외를 적절 하 게 처리할 수 있으며 사용자는 해당 예외를 몰라도 됩니다.

예외 처리에 대 한 몇 가지 중요 한 팁은 다음과 같습니다.

* 오류를 노출 하거나 처리 하기 위해 적절 한 조치를 취하지 않는 `catch (Exception) {}`와 같은 빈 catch 블록을 사용 하지 마십시오. 비어 있거나 정보를 사용 하지 않는 catch 블록은 예외를 숨길 수 있으며 더 쉽게 코드를 디버그 하기가 더 어려워질 수 있습니다.

* 예외를 throw 하는 특정 함수 (샘플 응용 프로그램의`ReadObject`) 주위에 `try/catch` 블록을 사용 합니다. 더 큰 코드 청크 주위에서 사용 하는 경우 오류 위치를 숨깁니다. 예를 들어 여기에 표시 된 `ReadToObject`부모 함수 호출 주위에 `try/catch` 블록을 사용 하지 않거나 예외가 발생 한 위치를 정확 하 게 알 수 없습니다.

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

* 응용 프로그램에 포함 하는 익숙하지 않은 함수, 특히 외부 데이터 (예: 웹 요청)와 상호 작용 하는 함수에 대해 설명서를 확인 하 여 함수가 throw 할 가능성이 높은 예외를 확인 합니다. 이는 적절 한 오류 처리 및 앱 디버깅에 대 한 중요 한 정보 일 수 있습니다.

샘플 앱의 경우 `4o`를 `40`로 변경 하 여 `GetJsonData` 메서드에서 `SerializationException`을 수정 합니다.

## <a name="clarify-your-code-intent-by-using-assert"></a>Assert를 사용 하 여 코드 의도 명시

디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭합니다(**Ctrl** + **Shift** + **F5**). 그러면 앱이 보다 낮은 단계로 다시 시작 됩니다. 콘솔 창에 다음 출력이 표시 됩니다.

![출력의 Null 값](../debugger/media/write-better-code-using-assert-null-output.png)

이 출력에서 잘못 된 항목을 볼 수 있습니다. 세 번째 레코드의 **이름** 및 **lastname** 은 비어 있습니다.

이는 함수에서 `assert` 문을 사용 하는 데 도움이 되는 유용한 코딩 습관 (종종 미달 사용)에 대해 설명 하는 데 유용 합니다. 다음 코드를 추가 하 여 `firstname` 및 `lastname` `null`되지 않도록 런타임 검사를 포함 합니다. `UpdateRecords` 메서드에서 다음 코드를 바꿉니다.

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

개발 프로세스 중에 함수와 같은 `assert` 문을 함수에 추가 하면 코드의 의도를 지정할 수 있습니다. 앞의 예제에서는 다음을 지정 합니다.

* 이름에 올바른 문자열이 필요 합니다.
* 마지막 이름에는 유효한 문자열이 필요 합니다.

이러한 방식으로 의도를 지정 하 여 요구 사항을 적용 합니다. 개발 중에 버그를 표시 하는 데 사용할 수 있는 간단 하 고 편리한 메서드입니다. (`assert` 문은 단위 테스트의 기본 요소로도 사용 됩니다.)

디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭합니다(**Ctrl** + **Shift** + **F5**).

> [!NOTE]
> `assert` 코드는 디버그 빌드에서만 활성화 됩니다.

를 다시 시작할 때 `users[i].firstname != null` 식이 `true`대신 `false`으로 계산 되기 때문에 디버거는 `assert` 문에서 일시 중지 합니다.

![어설션이 false로 확인 됩니다.](../debugger/media/write-better-code-using-assert.png)

`assert` 오류는 조사 해야 할 문제가 있음을 나타냅니다. `assert`는 예외를 반드시 표시 하지 않는 여러 시나리오를 처리할 수 있습니다. 이 예에서는 사용자에 게 예외가 표시 되지 않으며 `null` 값이 레코드 목록에 `firstname`로 추가 됩니다. 이로 인해 나중에 문제가 발생할 수 있습니다 (예: 콘솔 출력에 표시 됨). 디버깅 하기 어려울 수 있습니다.

> [!NOTE]
> `null` 값에 대해 메서드를 호출 하는 시나리오에서는 `NullReferenceException` 결과가 발생 합니다. 일반적으로 일반 예외에는 `try/catch` 블록을 사용 하지 않도록 하는 것이 좋습니다. 즉, 특정 라이브러리 함수에 연결 되지 않은 예외입니다. 모든 개체는 `NullReferenceException`을 throw 할 수 있습니다. 확실 하지 않은 경우 라이브러리 함수에 대 한 설명서를 확인 합니다.

디버깅 프로세스 중에는 실제 코드 수정으로 바꾸어야 할 때까지 특정 `assert` 문을 유지 하는 것이 좋습니다. 사용자가 앱의 릴리스 빌드에서 예외를 발생 시킬 수 있다고 판단 하는 경우를 가정해 보겠습니다. 이 경우 앱이 심각한 예외를 throw 하지 않거나 다른 오류가 발생 하지 않는지 확인 하기 위해 코드를 리팩터링 해야 합니다. 따라서이 코드를 수정 하려면 다음 코드를 바꿉니다.

```csharp
if (existingUser == false)
{
    User user = new User();
```

바꿉니다.

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

이 코드를 사용 하 여 코드 요구 사항을 충족 하 고 `null`의 `firstname` 또는 `lastname` 값이 포함 된 레코드가 데이터에 추가 되지 않았는지 확인 합니다.

이 예제에서는 루프 내에 두 개의 `assert` 문을 추가 했습니다. 일반적으로 `assert`를 사용 하는 경우 함수 또는 메서드의 진입점 (시작)에 `assert` 문을 추가 하는 것이 가장 좋습니다. 현재 샘플 앱에서 `UpdateRecords` 메서드를 보고 있습니다. 이 메서드에서는 메서드 인수 중 하나가 `null`되는 경우 문제가 있음을 알 수 있으므로 함수 진입점에서 `assert` 문을 사용 하 여 모두 확인 합니다.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

위의 문에서는 모든 항목을 업데이트 하기 전에 기존 데이터 (`db`)를 로드 하 고 새 데이터 (`users`)를 검색 합니다.

`true` 또는 `false`으로 확인 되는 모든 종류의 식에 `assert`를 사용할 수 있습니다. 따라서 예를 들어 다음과 같이 `assert` 문을 추가할 수 있습니다.

```csharp
Debug.Assert(users[0].points > 0);
```

앞의 코드는 사용자의 레코드를 업데이트 하는 데 필요 합니다. 0 보다 큰 새 점 값을 지정 하려는 경우에 유용 합니다.

## <a name="inspect-your-code-in-the-debugger"></a>디버거에서 코드 검사

이제 샘플 앱에 문제가 있는 모든 것을 수정 했으므로 다른 중요 한 항목으로 이동할 수 있습니다.

디버거의 예외 도우미를 살펴보았습니다. 디버거는 코드를 단계별로 실행 하 고 변수를 검사 하는 등의 다른 작업을 수행할 수 있는 훨씬 더 강력한 도구입니다. 이러한 보다 강력한 기능은 대부분의 시나리오에서 유용 합니다. 특히 다음과 같은 작업을 수행 합니다.

* 코드에서 런타임 버그를 격리 하려고 하지만 앞에서 설명한 메서드와 도구를 사용 하 여이 버그를 수행할 수 없습니다.

* 코드의 유효성을 검사 하려고 합니다. 즉, 실행 되는 동안 코드의 유효성을 검사 하 여 원하는 대로 작동 하는지 확인 하는 것이 좋습니다.

    코드를 실행 하는 동안 코드를 시청 하는 것이 좋습니다. 이러한 방식으로 코드에 대 한 자세한 정보를 확인할 수 있으며, 버그를 식별 하는 것이 확실 한 증상이 발생 하기 전에 종종 있습니다.

디버거의 주요 기능을 사용 하는 방법에 대 한 자세한 내용은 [절대 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)을 참조 하십시오.

## <a name="fix-performance-issues"></a>성능 문제 해결

다른 종류의 버그에는 앱이 느리게 실행 되거나 너무 많은 메모리를 사용 하는 비효율적인 코드가 포함 됩니다. 일반적으로 성능 최적화는 나중에 앱 개발에서 수행 하는 작업입니다. 그러나 초기에 성능 문제를 발생 시킬 수 있습니다 (예를 들어 앱의 일부는 느리게 실행 되는 것을 확인할 수 있음). 프로 파일링 도구를 사용 하 여 응용 프로그램을 조기에 테스트 해야 할 수도 있습니다. CPU 사용량 도구 및 메모리 분석기와 같은 프로 파일링 도구에 대 한 자세한 내용은 [프로 파일링 도구를 먼저 확인](../profiling/profiling-feature-tour.md)을 참조 하세요.

## <a name="next-steps"></a>다음 단계

이 문서에서는 코드에서 많은 일반적인 버그를 방지 하 고 수정 하는 방법 및 디버거를 사용 하는 경우를 배웠습니다. 다음으로, Visual Studio 디버거를 사용 하 여 버그를 수정 하는 방법에 대해 자세히 알아보세요.

> [!div class="nextstepaction"]
> [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)
