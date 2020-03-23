---
title: 디버깅 기술 및 도구
description: Visual Studio를 사용하여 예외를 수정하고 오류를 수정하고 코드를 개선하여 버그가 적은 더 나은 코드를 작성합니다.
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
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301022"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>더 나은 코드를 작성하는 데 도움이 되는 디버깅 기술 및 도구

코드에서 버그와 오류를 수정하는 것은 시간이 오래 걸리고 때로는 실망스러울 수 있습니다. 효과적으로 디버깅하는 방법을 배우는 데는 시간이 걸리지만 Visual Studio와 같은 강력한 IDE를 사용하면 작업을 훨씬 쉽게 만들 수 있습니다. IDE를 사용하면 오류를 수정하고 코드를 더 빠르게 디버깅할 수 있으며 버그가 적은 경우 더 나은 코드를 작성할 수 있습니다. 이 문서의 목적은 "버그 수정" 프로세스에 대한 전체적인 보기를 제공하는 것이므로 코드 분석기를 사용할 시기, 디버거 사용 시기, 예외 수정 방법 및 의도를 위해 코딩하는 방법을 알 수 있습니다. 디버거를 사용해야 한다는 것을 이미 알고 있는 경우 [디버거 를 먼저 확인을](../debugger/debugger-feature-tour.md)참조하십시오.

이 문서에서는 코딩 세션의 생산성을 높이기 위해 IDE를 활용하는 것에 대해 설명합니다. 다음과 같은 몇 가지 작업을 다겠습니다.

* IDE의 코드 분석기를 활용하여 디버깅을 위한 코드 준비

* 예외를 수정하는 방법(런타임 오류)

* 의도를 위해 코딩하여 버그를 최소화하는 방법(어설션 사용)

* 디버거를 사용할 시기

이러한 작업을 설명하기 위해 앱을 디버깅할 때 발생하는 가장 일반적인 유형의 오류 및 버그를 보여 줍니다. 샘플 코드는 C#이지만 개념 정보는 일반적으로 C++, Visual Basic, JavaScript 및 Visual Studio에서 지원하는 기타 언어에 적용됩니다(명시된 경우 제외). 스크린샷은 C#에 있습니다.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>몇 가지 버그와 오류가있는 샘플 응용 프로그램을 만듭니다.

다음 코드에는 Visual Studio IDE를 사용하여 해결할 수 있는 몇 가지 버그가 있습니다. 여기에 응용 프로그램은 일부 작업에서 JSON 데이터를 받고, 개체에 데이터를 역직렬화하고, 새 데이터로 간단한 목록을 업데이트 시뮬레이션하는 간단한 응용 프로그램입니다.

앱을 만들려면 다음을 수행합니다.

1. 만들려는 앱 유형에 따라 Visual Studio가 설치되어 있고 **.NET Core 교차 플랫폼 개발** 또는 **.NET 데스크톱 개발** 워크로드가 설치되어 있어야 합니다.

    아직 Visual [Studio를](https://visualstudio.microsoft.com/downloads/) 설치하지 않은 경우 Visual Studio 다운로드 페이지로 이동하여 무료로 설치하십시오.

    워크로드를 설치해야 하지만 이미 Visual Studio가 있는 경우 **도구** > **받기 도구 및 기능**. Visual Studio 설치 관리자가 시작됩니다. **.NET Core 크로스 플랫폼 개발** 또는 **.NET 데스크톱 개발** 워크로드를 선택한 다음 **수정을**선택합니다.

1. Visual Studio를 엽니다.

    ::: moniker range=">=vs-2019"
    시작 창에서 **새 프로젝트 만들기를 선택합니다.** 검색 상자에 **콘솔을** 입력한 다음 **콘솔 앱(.NET 코어)** 또는 **콘솔 앱(.NET 프레임워크)을**선택합니다. **다음을 선택합니다.** **Console_Parse_JSON** 같은 프로젝트 이름을 입력하고 **만들기를**클릭합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    상단 메뉴 모음에서 **File** > **새** > **프로젝트**파일 선택. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C#** 아래에서 **콘솔 앱을**선택한 다음 중간 창에서 **콘솔 앱(.NET Core)** 또는 **콘솔 앱(.NET Framework)을**선택합니다. **Console_Parse_JSON** 같은 이름을 입력하고 **확인을**클릭합니다.
    ::: moniker-end

    **콘솔 앱(.NET Core)** 또는 콘솔 **앱(.NET Framework)** 프로젝트 템플릿이 **Tools** > 표시되지 않으면 도구**Get 도구 및 기능으로**이동하여 Visual Studio 설치 프로그램을 엽니다. **.NET Core 교차 플랫폼 개발** 또는 **.NET 데스크톱 개발** 워크로드 중 하나를 선택한 다음 **수정을 선택합니다.**

    Visual Studio에서 콘솔 프로젝트를 만들고 오른쪽 창의 솔루션 탐색기에 나타납니다.

1. 프로젝트의 *Program.cs* 파일의 기본 코드를 아래 의 샘플 코드로 바꿉니다.

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

## <a name="find-the-red-and-green-squiggles"></a>빨간색과 녹색 물결선 찾기!

샘플 앱을 시작하고 디버거를 실행하기 전에 코드 편집기에서 빨간색 및 녹색 물결선이 있는지 코드를 확인합니다. 이는 IDE의 코드 분석기에서 식별되는 오류 및 경고를 나타냅니다. 빨간색 물결선은 컴파일 타임 오류로 코드를 실행하기 전에 수정해야 합니다. 녹색 물결선은 경고입니다. 경고를 수정하지 않고 앱을 실행할 수 있지만 버그의 원인이 될 수 있으며 조사하여 시간과 문제를 줄일 수 있습니다. 목록 보기를 선호하는 경우 이러한 경고 및 오류도 **오류 목록** 창에 표시됩니다.

샘플 앱에서는 수정해야 하는 빨간색 물결선과 살펴볼 녹색 물결선이 하나 있습니다. 다음은 첫 번째 오류입니다.

![빨간색 물결선으로 표시되는 오류](../debugger/media/write-better-code-red-squiggle.png)

이 오류를 해결하려면 전구 아이콘으로 표시되는 IDE의 다른 기능을 살펴보겠습니다.

## <a name="check-the-light-bulb"></a>전구를 확인!

첫 번째 빨간색 물결선은 컴파일 타임 오류를 나타냅니다. 마우스로 가리키면 메시지가 ```The name `Encoding` does not exist in the current context```표시됩니다.

이 오류는 왼쪽 하단에 전구 아이콘을 표시합니다. 드라이버 ![아이콘 드라이버 아이콘과](../ide/media/screwdriver-icon.png)함께 전구 아이콘 ![전구](../ide/media/light-bulb-icon.png) 아이콘 아이콘은 코드를 인라인으로 수정하거나 리팩터링하는 데 도움이 되는 빠른 작업을 나타냅니다. 전구는 *해결해야* 할 문제를 나타냅니다. 드라이버는 문제를 해결하기 위해 선택할 수 있습니다. 왼쪽에 있는 **System.Text를 클릭하여** 이 오류를 해결하려면 첫 번째 제안된 수정 프로그램을 사용합니다.

![전구를 사용하여 코드 수정](../debugger/media/write-better-code-missing-include.png)

이 항목을 클릭하면 Visual Studio에서 `using System.Text` *Program.cs* 파일 맨 위에 문문을 추가하고 빨간색 물결선이 사라집니다. 제안된 수정 프로그램이 수행할 작업을 잘 모르는 경우 수정 프로그램을 적용하기 전에 오른쪽의 **변경 내용 미리 보기** 링크를 선택합니다.

앞의 오류는 일반적으로 코드에 새 `using` 문을 추가하여 수정하는 일반적인 오류입니다. 이러한 종류의 오류와 ```The type or namespace `Name` cannot be found.``` 같은 몇 가지 일반적이고 유사한 오류가 누락된 어셈블리 참조(프로젝트 마우스 오른쪽 단추 클릭,**참조** **추가** > 선택), 맞춤법이 틀린 이름 또는 추가해야 하는 누락된 라이브러리(C#의 경우 프로젝트를 마우스 오른쪽 단추로 클릭하고 NuGet 패키지 관리를 선택함)를 나타낼 수 **있습니다.**

## <a name="fix-the-remaining-errors-and-warnings"></a>나머지 오류 및 경고 수정

이 코드에는 몇 가지 물결선이 더 있습니다. 여기서 는 일반적인 형식 변환 오류가 표시됩니다. 물결선 위로 마우스를 가져가면 코드가 문자열을 int로 변환하려고 하는 것을 볼 수 있습니다.

![유형 변환 오류](../debugger/media/write-better-code-conversion-error.png)

코드 분석기는 의도를 추측할 수 없으므로 이번에는 도움이 되는 전구가 없습니다. 이 오류를 해결하려면 코드의 의도를 알아야 합니다. 이 예제에서는 `points` `points` `totalpoints`에 추가하려고 하므로 숫자(정수) 값이어야 한다는 것을 확인하는 것은 그리 어렵지 않습니다.

이 오류를 해결하려면 `points` 다음에서 `User` 클래스의 멤버를 변경합니다.

```csharp
[DataMember]
internal string points;
```

다음과 같이 변경합니다.

```csharp
[DataMember]
internal int points;
```

코드 편집기의 빨간색 구불구불한 줄은 사라지게 됩니다.

다음으로 `points` 데이터 멤버선언에서 녹색 물결선 위로 마우스를 가져갑니다. 코드 분석기는 변수가 값을 할당하지 않음을 알려줍니다.

![할당되지 않은 변수에 대한 경고 메시지](../debugger/media/write-better-code-warning-message.png)

일반적으로 이 문제는 수정해야 하는 문제를 나타냅니다. 그러나 샘플 앱에서는 실제로 역직화 프로세스 `points` 중에 변수에 데이터를 저장한 다음 해당 `totalpoints` 값을 데이터 멤버에 추가합니다. 이 예제에서는 코드의 의도를 알고 있으며 경고를 무시해도 됩니다. 그러나 경고를 제거하려는 경우 다음 코드를 바꿀 수 있습니다.

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

모든 빨간색 물결선과 해결되었거나 적어도 모든 녹색 물결선이 해결되면 디버거를 시작하고 앱을 실행할 준비가 된 것입니다.

**F5(디버그** **> 디버깅 시작)** 또는 디버그 도구 모음에서 **디버깅** ![시작](../debugger/media/dbg-tour-start-debugging.png "디버그") 단추를 누릅니다.

이 시점에서 샘플 앱은 `SerializationException` 예외(런타임 오류)를 throw합니다. 즉, 앱이 직렬화하려는 데이터에 질식합니다. 디버그 모드(디버거 가 연결됨)에서 앱을 시작했기 때문에 디버거의 예외 도우미는 예외를 throw한 코드로 바로 이동하여 유용한 오류 메시지를 제공합니다.

![직렬화예외 발생](../debugger/media/write-better-code-serialization-exception.png)

오류 메시지는 값을 `4o` 정수로 구문 분석할 수 없음을 지시합니다. 따라서 이 예제에서는 데이터가 나쁘다는 것을 `4o` 알고 `40`있습니다. 그러나 실제 시나리오에서 데이터를 제어하지 않는 경우(예: 웹 서비스에서 데이터를 가져오는 경우) 이에 대해 어떻게 해야 합니까? 이 문제를 어떻게 해결합니까?

예외를 누르면 몇 가지 질문을 (및 답변)해야 합니다.

* 이 예외는 해결할 수 있는 버그입니까? 또는

* 이 예외는 사용자가 발생할 수 있는 것입니까?

전자의 경우 버그를 수정합니다. (샘플 앱에서 잘못된 데이터를 수정하는 것을 의미합니다.) 후자의 경우 `try/catch` 블록을 사용하여 코드에서 예외를 처리해야 할 수 있습니다(다음 섹션에서 다른 가능한 전략을 살펴보겠습니다). 샘플 앱에서 다음 코드를 바꿉니다.

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

`try/catch` 블록에는 몇 가지 성능 비용이 있으므로 실제로 필요할 때만 사용하려고 합니다. 대부분의 경우 예외를 적절하게 처리할 수 있으므로 사용자는 예외에 대해 알 필요가 없습니다.

다음은 예외 처리를 위한 몇 가지 중요한 팁입니다.

* 오류를 노출하거나 처리하기 위해 `catch (Exception) {}`적절한 조치를 취하지 않는 빈 catch 블록을 사용하지 마십시오. 비어 있거나 정보를 알 수 없는 catch 블록은 예외를 숨길 수 있으며 코드를 쉽게 디버깅하기가 더 어려워질 수 있습니다.

* 예외를 `try/catch` throw 하는 특정 함수 주위의`ReadObject`블록을 사용 합니다 (샘플 앱에서). 더 큰 코드 덩어리 를 중심으로 사용하면 오류의 위치를 숨김하게됩니다. 예를 들어 여기에 표시된 `try/catch` 부모 함수에 `ReadToObject`대한 호출 주위에 블록을 사용하지 않거나 예외가 발생한 위치를 정확히 알 수 없습니다.

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

* 앱에 포함되는 익숙하지 않은 기능, 특히 웹 요청과 외부 데이터와 상호 작용하는 함수의 경우 설명서를 확인하여 함수가 발생할 가능성이 있는 예외를 확인합니다. 이는 적절한 오류 처리 및 앱 디버깅에 중요한 정보일 수 있습니다.

샘플 앱의 경우 `SerializationException` 메서드를 `GetJsonData` 로 `4o` 변경하여 수정합니다. `40`

## <a name="clarify-your-code-intent-by-using-assert"></a>어설션을 사용하여 코드 의도 명확히 하기

디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭합니다(**Ctrl** + **Shift** + **F5**). 이렇게 하면 더 적은 단계로 앱이 다시 시작됩니다. 콘솔 창에 다음 출력이 표시됩니다.

![출력의 Null 값](../debugger/media/write-better-code-using-assert-null-output.png)

당신은 아주 옳지 않은이 출력에서 뭔가를 볼 수 있습니다. 세 번째 레코드의 **이름과** **성은** 비어 있습니다!

이것은 함수에서 문을 사용하는 `assert` 유용한 코딩 연습에 대해 이야기하기에 좋은 시간입니다. 다음 코드를 추가하면 런타임 검사를 추가하여 해당 `firstname` 코드와 `lastname` `null`그렇지 않은지 확인합니다. 메서드에서 다음 코드를 `UpdateRecords` 바꿉니다.

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

개발 `assert` 프로세스 중에 이와 같은 문을 함수에 추가하면 코드의 의도를 지정할 수 있습니다. 앞의 예제에서는 다음을 지정합니다.

* 이름에 유효한 문자열이 필요합니다.
* 성에 유효한 문자열이 필요합니다.

이러한 방식으로 의도를 지정하면 요구 사항을 적용할 수 있습니다. 이 방법은 개발 중에 버그를 표시하는 데 사용할 수 있는 간단하고 편리한 방법입니다. (문은`assert` 단위 테스트의 주요 요소로도 사용됩니다.)

디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭합니다(**Ctrl** + **Shift** + **F5**).

> [!NOTE]
> 코드는 `assert` 디버그 빌드에서만 활성화됩니다.

`assert` 다시 시작하면 식이 `users[i].firstname != null` `false` `true`대신으로 평가되므로 디버거가 명령문에서 일시 중지됩니다.

![어설션이 false로 확인됨](../debugger/media/write-better-code-using-assert.png)

이 `assert` 오류는 조사해야 하는 문제가 있음을 알려줍니다. `assert`예외가 표시되지 않는 많은 시나리오를 다룰 수 있습니다. 이 예제에서는 사용자에게 예외가 표시되지 않으며 `null` 레코드 목록에서와 `firstname` 같이 값이 추가됩니다. 이로 인해 나중에 문제가 발생할 수 있으며(예: 콘솔 출력에 표시) 디버깅하기가 더 어려울 수 있습니다.

> [!NOTE]
> `null` 값에 메서드를 호출 하는 시나리오에서는 `NullReferenceException` 결과 입니다. 일반적으로 특정 라이브러리 함수에 `try/catch` 연결되지 않은 예외인 일반 예외에 대해 블록을 사용하지 않으려고 합니다. 모든 개체는 `NullReferenceException`을 throw할 수 있습니다. 확실하지 않은 경우 라이브러리 함수에 대한 설명서를 확인하십시오.

디버깅 프로세스 중에 실제 코드 수정으로 `assert` 교체해야 한다는 것을 알 때까지 특정 문을 유지하는 것이 좋습니다. 사용자가 앱의 릴리스 빌드에서 예외가 발생할 수 있다고 가정해 보겠습니다. 이 경우 앱에서 치명적인 예외를 throw하거나 다른 오류가 발생하지 않도록 코드를 리팩터링해야 합니다. 따라서 이 코드를 수정하려면 다음 코드를 바꿉니다.

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

이 코드를 사용하면 코드 요구 사항을 충족하고 또는 `firstname` `lastname` 값의 `null` 레코드가 데이터에 추가되지 않도록 해야 합니다.

이 예제에서는 루프 내부에 `assert` 두 문을 추가했습니다. 일반적으로 을 `assert`사용하는 경우 함수 또는 `assert` 메서드의 진입점(시작)에 문을 추가하는 것이 가장 좋습니다. 현재 샘플 앱에서 `UpdateRecords` 메서드를 보고 있습니다. 이 메서드에서는 메서드 인수 `null`중 하나가 있는 경우 문제가 있음을 알고 있으므로 `assert` 함수의 진입점에서 문으로 둘 다 확인합니다.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

앞의 명령문의 경우 아무것도 업데이트하기 전에`db`기존 데이터()를`users`로드하고 새 데이터()를 검색하는 것이 좋습니다.

또는 `false`에 `assert` 대해 해결하는 모든 종류의 `true` 식과 함께 사용할 수 있습니다. 예를 들어 다음과 같은 `assert` 문을 추가할 수 있습니다.

```csharp
Debug.Assert(users[0].points > 0);
```

위의 코드는 사용자의 레코드를 업데이트하는 데 0(0)보다 큰 새 포인트 값을 지정하려는 경우에 유용합니다.

## <a name="inspect-your-code-in-the-debugger"></a>디버거에서 코드 검사

좋아, 이제 샘플 앱에 문제가있는 중요한 모든 것을 수정했기 때문에 다른 중요한 것들로 이동할 수 있습니다!

디버거의 예외 도우미를 보여 주었지만 디버거는 코드를 단계별로 수행하여 변수를 검사할 수 있는 훨씬 더 강력한 도구입니다. 이러한 보다 강력한 기능은 많은 시나리오, 특히 다음과 같은 경우에 유용합니다.

* 코드에서 런타임 버그를 분리하려고 하지만 이전에 설명한 메서드 및 도구를 사용하여 버그를 분리할 수 없습니다.

* 코드의 유효성을 검사하려고 합니다.

    코드가 실행되는 동안 코드를 보는 것은 유익합니다. 이러한 방식으로 코드에 대해 자세히 알아볼 수 있으며 버그가 명백한 증상을 나타내기 전에 종종 버그를 식별할 수 있습니다.

디버거의 필수 기능을 사용하는 방법에 대해 알아보려면 [절대 초보자를 위한 디버깅을](../debugger/debugging-absolute-beginners.md)참조하십시오.

## <a name="fix-performance-issues"></a>성능 문제 해결

다른 종류의 버그에는 앱이 느리게 실행하거나 너무 많은 메모리를 사용하는 비효율적인 코드가 포함됩니다. 일반적으로 성능 최적화는 앱 개발의 후반부에서 수행하는 기능입니다. 그러나 성능 문제가 조기에 발생할 수 있으며(예: 앱의 일부가 느리게 실행되는 경우) 프로파일링 도구를 사용하여 앱을 조기에 테스트해야 할 수 있습니다. CPU 사용 도구 및 메모리 분석기와 같은 프로파일링 도구에 대한 자세한 내용은 [프로파일링 도구를 먼저 참조하십시오.](../profiling/profiling-feature-tour.md)

## <a name="next-steps"></a>다음 단계

이 문서에서는 코드에서 많은 일반적인 버그를 방지하고 수정하는 방법과 디버거를 사용하는 시기에 대해 배웠습니다. 다음으로 Visual Studio 디버거를 사용하여 버그를 수정하는 방법에 대해 자세히 알아봅니다.

> [!div class="nextstepaction"]
> [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)
