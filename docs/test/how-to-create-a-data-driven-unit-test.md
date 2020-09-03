---
title: 데이터 기반 단위 테스트 만들기
ms.date: 05/08/2019
ms.topic: how-to
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 936c6b2ee9e05d059c09c2aa074829b35b6ca5fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287989"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>방법: 데이터 기반 단위 테스트 만들기

관리 코드용 Microsoft 단위 테스트 프레임워크를 사용하여 데이터 원본에서 값을 검색하도록 단위 테스트 메서드를 설정할 수 있습니다. 이 메서드는 데이터 소스의 각 행을 대상으로 연속 실행되므로 단일 메서드를 사용하여 다양한 입력을 쉽게 테스트할 수 있습니다.

데이터 기반 단위 테스트를 만드는 단계는 다음과 같습니다.

1. 테스트 메서드에서 사용할 값이 포함된 데이터 소스를 만듭니다. 테스트를 실행할 컴퓨터에 등록된 모든 형식을 데이터 소스로 사용할 수 있습니다.

2. private <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> 필드 및 public `TestContext` 속성을 테스트 클래스에 추가합니다.

3. 단위 테스트 메서드를 만들고 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> 특성을 메서드에 추가합니다.

4. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> 인덱서 속성을 사용하여 테스트에서 사용할 값을 검색합니다.

## <a name="the-method-under-test"></a>테스트 중인 메서드

예를 들어 다음이 있다고 가정해 보세요.

1. 다양한 형식의 계좌에 대한 트랜잭션을 수락하고 처리하는 `MyBank` 솔루션.

2. 계좌에 대한 트랜잭션을 관리하는 `MyBank`의 `BankDb` 프로젝트.

3. 모든 트랜잭션이 은행에 이로운지 확인하기 위해 수학적 함수를 실행하는 `BankDb` 프로젝트의 `Maths` 클래스.

4. `BankDb` 구성 요소의 동작을 테스트하기 위한 `BankDbTests` 단위 테스트 프로젝트.

5. `Maths` 클래스의 동작을 확인하기 위한 `MathsTests` 단위 테스트 클래스.

루프를 사용하여 두 개의 정수를 추가하는 `Maths`의 메서드를 테스트합니다.

```csharp
public int AddIntegers(int first, int second)
{
    int sum = first;
    for( int i = 0; i < second; i++)
    {
        sum += 1;
    }
    return sum;
}
```

## <a name="create-a-data-source"></a>데이터 원본 만들기

`AddIntegers` 메서드를 테스트하기 위해 반환되어야 하는 매개 변수 및 합계의 값 범위를 지정하는 데이터 소스를 만듭니다. 이 예제에서는 `MathsData`이라는 Sql Compact 데이터베이스 및 다음 열 이름과 값이 포함된 `AddIntegersData`라는 테이블을 만듬

|FirstNumber|SecondNumber|Sum|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>테스트 클래스에 TestContext 추가

단위 테스트 프레임워크는 데이터 기반 테스트를 위해 데이터 소스 정보를 저장할 `TestContext` 개체를 만듭니다. 그런 다음, 이 개체를 여기서 만든 `TestContext` 속성의 값으로 설정합니다.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

테스트 메서드에서 `TestContext`의 `DataRow` 인덱서 속성을 통해 데이터에 액세스합니다.

> [!NOTE]
> .NET Core는 [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute) 특성을 지원하지 않습니다. .NET Core 또는 UWP 단위 테스트 프로젝트에서 이 방식으로 테스트 데이터에 액세스하려고 하면 **"'TestContext'에는 'DataRow'에 대한 정의가 포함되어 있지 않으며, 'TestContext' 유형의 첫 번째 인수를 허용하는 액세스 가능한 확장 메서드 'DataRow'를 찾을 수 없음(using 지시문이나 어셈블리 참조가 누락되었나요?)"** 과 유사한 오류가 표시됩니다.

## <a name="write-the-test-method"></a>테스트 메서드 작성

`AddIntegers`에 대한 테스트 메서드는 매우 간단합니다. 데이터 소스의 각 행을 대상으로 **FirstNumber** 및 **SecondNumber** 열 값을 매개 변수로 사용하여 `AddIntegers`를 호출하고 **Sum** 열 값에 대한 반환 값을 확인합니다.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]
[TestMethod()]
public void AddIntegers_FromDataSourceTest()
{
    var target = new Maths();

    // Access the data
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.IntegerMethod(x, y);
    Assert.AreEqual(expected, actual,
        "x:<{0}> y:<{1}>",
        new object[] {x, y});
}
```

`Assert` 메서드에는 실패한 반복의 `x` 및 `y` 값을 표시하는 메시지가 포함됩니다. 기본적으로 어설션된 값 `expected` 및 `actual`은 실패한 테스트 세부 정보에 이미 포함되어 있습니다.

### <a name="specify-the-datasourceattribute"></a>DataSourceAttribute 지정

`DataSource` 특성은 테스트 메서드에 사용할 테이블의 이름 및 데이터 소스의 연결 문자열을 지정합니다. 연결 문자열의 정확한 정보는 어떤 종류의 데이터 소스를 사용하는지에 따라 달라집니다. 이 예제에서는 SqlServerCe 데이터베이스를 사용했습니다.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

DataSource 특성에는 세 개의 생성자가 있습니다.

```csharp
[DataSource(dataSourceSettingName)]
```

하나의 매개 변수가 있는 생성자는 솔루션에 대한 *app.config* 파일에 저장된 연결 정보를 사용합니다. *dataSourceSettingsName*은 연결 정보를 지정하는 구성 파일의 Xml 요소 이름입니다.

*app.config* 파일을 사용하면 단위 테스트 자체를 변경하지 않고 데이터 원본의 위치를 변경할 수 있습니다. *app.config* 파일을 만들고 사용하는 방법에 대한 자세한 내용은 [연습: 구성 파일을 사용하여 데이터 원본 정의](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)를 참조하세요.

```csharp
[DataSource(connectionString, tableName)]
```

두 개의 매개 변수가 있는 `DataSource` 생성자는 테스트 메서드에 대한 데이터가 포함된 테이블의 이름 및 데이터 소스의 연결 문자열을 지정합니다.

연결 문자열은 데이터 소스의 형식에 따라 달라지지만 데이터 공급자의 고정 이름을 지정하는 Provider 요소를 포함해야 합니다.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>TestContext.DataRow를 사용하여 데이터 액세스

`AddIntegersData` 테이블의 데이터에 액세스하려면 `TestContext.DataRow` 인덱서를 사용합니다. `DataRow`는 <xref:System.Data.DataRow> 개체이므로 인덱스 또는 열 이름별로 열 값을 검색합니다. 값은 개체로 반환되므로 값을 적절한 형식으로 변환합니다.

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>테스트 실행 및 결과 보기

테스트 메서드 작업을 완료했으면 테스트 프로젝트를 빌드합니다. 테스트 메서드는 **테스트 실행 안 함** 그룹의 **테스트 탐색기**에 표시됩니다. 테스트를 실행하고, 작성하고, 재실행할 때 **테스트 탐색기**에는 **실패한 테스트**, **통과한 테스트** 및 **테스트 실행 안 함** 그룹에 결과가 표시됩니다. 사용자는 **모두 실행** 을 선택해서 모든 테스트를 실행하거나 **실행** 을 선택해서 실행할 테스트 하위 집합을 선택할 수 있습니다.

테스트가 실행되면 **테스트 탐색기** 위쪽에 있는 테스트 결과 표시줄에 애니메이션 효과가 적용됩니다. 테스트 실행이 끝날 때 모든 테스트가 통과했으면 표시줄이 녹색이 되고 테스트가 실패하면 빨간색이 됩니다. **테스트 탐색기** 창 아래쪽의 세부 정보 창에 테스트 실행의 요약이 표시됩니다. 테스트를 선택하면 아래쪽 창에 해당 테스트의 세부 정보가 표시됩니다.

> [!NOTE]
> 각 데이터 행의 결과와 하나의 요약 결과도 있습니다. 각 데이터 행에서 테스트가 통과되면 요약 실행이 **통과**로 표시됩니다. 데이터 행에서 테스트가 실패하면 요약 실행이 **실패**로 표시됩니다.

예제에서 `AddIntegers_FromDataSourceTest` 메서드를 실행한 경우 결과 표시줄이 빨간색으로 바뀌고 테스트 메서드가 **실패한 테스트**로 전환됩니다. 데이터 원본에서 반복된 메서드 중 하나라도 실패하면 데이터 기반 테스트에 실패합니다. **테스트 탐색기** 창에서 실패한 테스트 기반 테스트를 선택하면 세부 정보 창에 데이터 행 인덱스별로 식별된 각 반복의 결과가 표시됩니다. 예제에서는 `AddIntegers` 알고리즘이 음수 값을 제대로 처리하지 않는 것 같습니다.

테스트 중인 메서드가 수정되고 테스트가 다시 실행되면 결과 표시줄이 녹색으로 바뀌고 테스트 메서드가 **통과한 테스트** 그룹으로 이동합니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [코드 단위 테스트](../test/unit-test-your-code.md)
- [테스트 탐색기를 사용하여 단위 테스트 실행](../test/run-unit-tests-with-test-explorer.md)
- [Microsoft 단위 테스트 프레임워크를 사용하여 .NET에 대한 단위 테스트 작성](../test/unit-test-your-code.md)
