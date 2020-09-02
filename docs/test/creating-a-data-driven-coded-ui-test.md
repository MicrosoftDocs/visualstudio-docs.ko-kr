---
title: 데이터 기반의 코딩된 UI 테스트 자습서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, data-driven
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ada1f297bbb30fbe636042c87aae42849c1b6b7d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595360"
---
# <a name="create-a-data-driven-coded-ui-test"></a>데이터 기반의 코딩된 UI 테스트 만들기

다른 조건을 테스트하려면 각기 다른 매개 변수 값을 사용하여 테스트를 여러 번 실행합니다. 이 경우 데이터 기반의 코딩된 UI 테스트를 사용하면 편리합니다. 데이터 소스에서 매개 변수 값을 정의하면 데이터 소스의 각 행에서 코딩된 UI 테스트가 반복됩니다. 테스트의 전체 결과는 모든 반복의 결과를 기반으로 합니다. 예를 들어 테스트 반복 하나가 실패하면 전체 테스트 결과가 실패로 됩니다.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**요구 사항**

- Visual Studio Enterprise
- 코딩된 UI 테스트 구성 요소

## <a name="create-a-test-project"></a>테스트 프로젝트 만들기

이 샘플은 Windows 계산기 애플리케이션에서 실행되는 코딩된 UI 테스트를 만듭니다. 이 테스트에서는 두 숫자를 더한 다음 어설션을 사용해 합이 올바른지 유효성을 검사합니다. 그런 다음, 두 숫자의 매개 변수 값과 어설션이 데이터 기반 방식으로 코딩되어 쉼표로 구분된 값(.*csv*) 파일에 저장됩니다.

### <a name="step-1---create-a-coded-ui-test"></a>1단계 - 코딩된 UI 테스트 만들기

1. 프로젝트를 만듭니다.

    ![코딩된 UI 테스트 프로젝트 만들기](../test/media/cuit_datadriven_.png)

   > [!NOTE]
   > **코딩된 UI 테스트 프로젝트** 템플릿이 표시되지 않으면, [코딩된 UI 테스트 구성 요소를 설치](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)해야 합니다.

2. **작업을 기록**하도록 선택합니다.

    ![작업을 기록하도록 선택](../test/media/cuit_datadriven_generatecodedialog.png)

3. 계산기 앱을 열고 테스트 기록을 시작합니다.

    ![작업 기록](../test/media/cuit_datadriven_cuitbuilder.png)

4. 1+2를 추가하고 레코더를 일시 중지한 다음 테스트 메서드를 생성합니다. 나중에 이 사용자 입력의 값을 데이터 파일의 값으로 바꿉니다.

    ![테스트 메서드 생성](../test/media/cuit_datadriven_cuitbuildergencode.png)

    테스트 빌더를 닫습니다. 메서드가 테스트에 추가됩니다.

   ```csharp
   [TestMethod]
   public void CodedUITestMethod1()
   {
       // To generate code for this test, select "Generate Code for Coded UI Test"
       // from the shortcut menu and select one of the menu items.
       this.UIMap.AddNumbers();
   }
   ```

5. `AddNumbers()` 메서드를 사용하여 테스트가 실행되는지 확인합니다. 위에 나와 있는 테스트 메서드에 커서를 놓고 오른쪽 클릭 메뉴를 열고 **테스트 실행**을 선택합니다. (바로 가기 키: **Ctrl**+**R**,**T**).

    테스트 성공 여부를 보여 주는 테스트 결과가 **테스트 탐색기** 창에 표시됩니다. 테스트 탐색기 창을 열려면 **테스트** 메뉴에서 **Windows**와 **테스트 탐색기**를 차례로 선택합니다.

6. 테스트에서 필요한 값을 확인하는 데 사용되는 어설션 매개 변수 값에는 데이터 소스도 사용할 수 있으므로, 어설션을 추가해 두 숫자의 합이 올바른지 유효성을 검사해 보겠습니다. 위에 나와 있는 테스트 메서드에 커서를 놓고 오른쪽 클릭 메뉴를 열고 **코딩된 UI 테스트에 대한 코드 생성**과 **코딩된 UI 테스트 빌더 사용**을 차례로 선택합니다.

    합을 표시하는 계산기의 텍스트 컨트롤을 매핑합니다.

    ![UI 텍스트 컨트롤 매핑](../test/media/cuit_datadriven_addassertion.png)

7. 합의 값이 올바른지 유효성을 검사하는 어설션을 추가합니다. 값이 **3**인 **DisplayText** 속성을 선택한 후 **어설션 추가**를 선택합니다. **AreEqual** 비교 연산자를 사용하여 비교 값이 **3**인지 확인합니다.

    ![어설션 구성](../test/media/cuit_datadriven_builderaddassertion2.png)

8. 어설션을 구성한 후 빌더에서 코드를 다시 생성합니다. 그러면 이 유효성 검사를 위한 새 메서드가 작성됩니다.

    ![어설션 메서드 생성](../test/media/cuit_datadriven_assertiongencode.png)

    `ValidateSum` 메서드는 `AddNumbers` 메서드의 결과 유효성을 검사하므로 코드 블록 아래쪽으로 이동합니다.

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSum();
   }
   ```

9. `ValidateSum()` 메서드를 사용하여 테스트가 실행되는지 확인합니다. 위에 나와 있는 테스트 메서드에 커서를 놓고 오른쪽 클릭 메뉴를 열고 **테스트 실행**을 선택합니다. (바로 가기 키: **Ctrl**+**R**,**T**).

     이 시점에서는 모든 매개 변수 값이 해당 메서드에서 상수로 정의되어 있습니다. 다음으로는 데이터 집합을 만들어 테스트를 데이터 기반으로 설정합니다.

### <a name="step-2---create-a-data-set"></a>2단계 - 데이터 집합 만들기

1. dataDrivenSample 프로젝트 *data.csv*에 텍스트 파일을 추가합니다.

     ![프로젝트에 쉼표로 구분된 값 파일 추가](../test/media/cuit_datadriven_addcsvfile.png)

2. 다음 데이터를 사용하여 *.csv* 파일을 채웁니다.

    |Num1|Num2|Sum|
    |-|-|-|
    |3|4|7|
    |5|6|11|
    |6|8|14|

     데이터를 추가하고 나면 파일은 다음과 같이 표시됩니다.

     ![데이터로 .csv 파일 채우기](../test/media/cuit_datadriven_adddatatocsvfile.png)

3. *.csv* 파일은 올바른 인코딩을 사용하여 저장되어야 합니다. **파일** 메뉴에서 **고급 저장 옵션**을 선택하고 인코딩으로 **유니코드(시그니처 없는 UTF-8) - 코드 페이지 65001**을 선택합니다.

4. *.csv* 파일은 출력 디렉터리에 복사해야 하며 그렇지 않으면 테스트를 실행할 수 없습니다. **속성** 창에서 해당 파일을 복사합니다.

     ![.csv 파일 배포](../test/media/cuit_datadriven_deploycsvfile.png)

     이제 데이터 집합을 만들었으므로 데이터를 테스트에 바인딩하겠습니다.

### <a name="step-3---add-data-source-binding"></a>3단계 - 데이터 소스 바인딩 추가

1. 데이터 소스를 바인딩하려면 테스트 메서드 바로 위에 있는 기존 `DataSource` 특성 내에 `[TestMethod]` 특성을 추가합니다.

    ```csharp
    [DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddNumbers();
        this.UIMap.ValidateSum();
    }
    ```

     이제 이 테스트 메서드에서 데이터 소스를 사용할 수 있습니다.

    > [!TIP]
    > XML, SQL Express, Excel 등의 다른 데이터 소스 형식을 사용하는 샘플은 Q & A 섹션의 [데이터 소스 특성 샘플](#CreateDataDrivenCUIT_QA_DataSourceAttributes)을 참조하세요.

2. 테스트를 실행합니다.

     테스트는 3회 반복 실행됩니다. 바인딩된 데이터 소스에 데이터 행 3개가 포함되어 있기 때문입니다. 그러나 테스트는 상수 매개 변수 값을 여전히 사용하고 있어 매번 1+2와 해당 합인 3을 추가하는 것도 확인할 수 있습니다.

     다음으로는 데이터 소스 파일의 값을 사용하는 테스트를 구성합니다.

### <a name="step-4---use-the-data-in-the-coded-ui-test"></a>4단계 - 코딩된 UI 테스트에서 데이터 사용

1. *CodedUITest.cs* 파일의 맨 위에 `using Microsoft.VisualStudio.TestTools.UITesting.WinControls`를 추가합니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text.RegularExpressions;
    using System.Windows.Input;
    using System.Windows.Forms;
    using System.Drawing;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UnitTesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    ```

2. 데이터 소스의 값을 적용하는 `TestContext.DataRow[]`를 `CodedUITestMethod1()` 메서드에 추가합니다. 데이터 소스 값은 `SearchProperties` 컨트롤을 사용하여 UIMap 컨트롤에 할당된 상수를 재정의합니다.

   ```csharp
   public void CodedUITestMethod1()
   {
       this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();
       this.UIMap.UICalculatorWindow.UIItemWindow2.UIItem2Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num2"].ToString();
       this.UIMap.AddNumbers();
       this.UIMap.ValidateSumExpectedValues.UIItem3TextDisplayText = TestContext.DataRow["Sum"].ToString();
       this.UIMap.ValidateSum();
    }
    ```

     데이터를 코딩할 검색 속성을 확인하려면 코딩된 UI 테스트 편집기를 사용합니다.

    - *UIMap.uitest* 파일을 엽니다.

         ![코딩된 UI 테스트 편집기 열기](../test/media/cuit_datadriven_opentesteditor.png)

    - UI 작업을 선택하고 해당 UI 컨트롤 매핑을 관찰하여 매핑과 그에 해당하는 `this.UIMap.UICalculatorWindow.UIItemWindow.UIItem1Button` 등의 코드를 살펴봅니다.

         ![코딩에 도움을 받으려면 코딩된 UI 테스트 편집기 사용](../test/media/cuit_datadriven_testeditor.png)

    - **속성** 창에서 **검색 속성**을 엽니다. 검색 속성 **Name** 값은 코드에서 데이터 소스를 사용하여 조작하는 항목입니다. 예를 들어 `SearchProperties`에는 다음과 같이 각 데이터 행의 첫 번째 열 값이 할당됩니다. `UIItem1Button.SearchProperties[WinButton.PropertyNames.Name] = TestContext.DataRow["Num1"].ToString();`. 이 테스트는 3회 반복하는 동안 검색 속성의 **Name** 값을 3, 5, 6의 순서로 변경합니다.

         ![코딩에 도움을 받으려면 검색 속성 사용](../test/media/cuit_datadriven_searchproperties.png)

3. 솔루션을 저장합니다.

### <a name="step-5---run-the-data-driven-test"></a>5단계 – 데이터 기반 테스트 실행

테스트를 다시 실행하여 이제 테스트가 데이터 기반인지를 확인합니다.

*.csv* 파일의 값을 사용하여 3회 반복 실행되는 테스트를 확인할 수 있습니다. 유효성 검사도 작동해야 하며, 테스트 탐색기에서 테스트가 통과로 표시되어야 합니다.

## <a name="q--a"></a>Q&A

### <a name="what-are-the-data-source-attributes-for-other-data-source-types-such-as-sql-express-or-xml"></a><a name="CreateDataDrivenCUIT_QA_DataSourceAttributes"></a> SQL Express 또는 XML과 같은 기타 데이터 소스 형식에는 어떤 데이터 소스 특성이 있나요?

**A:** 아래 테이블의 샘플 데이터 소스 문자열을 코드에 복사하고 필요한 항목을 사용자 지정하여 사용할 수 있습니다.

**데이터 소스 형식 및 특성**

- CSV

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.CSV", "|DataDirectory|\\data.csv", "data#csv", DataAccessMethod.Sequential), DeploymentItem("data.csv"), TestMethod]`

- Excel

     `DataSource("System.Data.Odbc", "Dsn=ExcelFiles;Driver={Microsoft Excel Driver (*.xls)};dbq=|DataDirectory|\\Data.xls;defaultdir=.;driverid=790;maxbuffersize=2048;pagetimeout=5;readonly=true", "Sheet1$", DataAccessMethod.Sequential), DeploymentItem("Sheet1.xls"), TestMethod]`

- Team Foundation Server의 테스트 사례

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.TestCase", "http://vlm13261329:8080/tfs/DefaultCollection;Agile", "30", DataAccessMethod.Sequential), TestMethod]`

- XML

     `[DataSource("Microsoft.VisualStudio.TestTools.DataSource.XML", "|DataDirectory|\\data.xml", "Iterations", DataAccessMethod.Sequential), DeploymentItem("data.xml"), TestMethod]`

- SQL Express

     `[DataSource("System.Data.SqlClient", "Data Source=.\\sqlexpress;Initial Catalog=tempdb;Integrated Security=True", "Data", DataAccessMethod.Sequential), TestMethod]`

### <a name="q-why-cant-i-modify-the-code-in-the-uimapdesigner-file"></a>Q: UIMap.Designer 파일에서 코드를 수정할 수 없는 이유는 무엇인가요?

**A:** UIMap - 코딩된 UI 테스트 빌더를 사용하여 코드를 생성할 때마다 *UIMapDesigner.cs* 파일에서 수정된 코드 변경 내용을 덮어씁니다. 이 샘플에서 그리고 대부분의 경우에는 테스트가 데이터 소스를 사용하도록 설정하는 데 필요한 코드 변경을 테스트의 소스 코드 파일(즉, *CodedUITest1.cs*)에서 수행할 수 있습니다.

기록된 메서드를 수정해야 하는 경우에는 해당 메서드를 *UIMap.cs* 파일에 복사한 후 이름을 바꾸어야 합니다. *UIMap.cs* 파일을 사용하여 *UIMapDesigner.cs* 파일의 메서드와 속성을 재정의할 수 있습니다. 코딩된 *UITest.cs* 파일에서 원래 메서드에 대한 참조를 제거하고 이름을 바꾼 메서드 이름으로 바꾸어야 합니다.

## <a name="see-also"></a>참조

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
- [코딩된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md)
- [코딩된 UI 테스트에 대한 모범 사례](../test/best-practices-for-coded-ui-tests.md)
- [코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
