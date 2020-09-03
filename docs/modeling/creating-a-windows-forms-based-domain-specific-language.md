---
title: Windows Forms 기반 도메인별 언어 만들기
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c52b3bd352c2ecb2272ad8e229a0fe52a9ee5b41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238363"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Windows Forms 기반 도메인별 언어 만들기

DSL 다이어그램을 사용 하는 대신 Windows Forms를 사용 하 여 DSL (도메인별 언어) 모델의 상태를 표시할 수 있습니다. 이 항목에서는 Visual Studio 시각화 및 모델링 SDK를 사용 하 여 Windows Form을 DSL에 바인딩하는 과정을 안내 합니다.

다음 이미지는 DSL 인스턴스의 Windows Form UI 및 모델 탐색기를 보여 줍니다.

![Visual Studio의 DSL 인스턴스](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Windows Forms DSL 만들기

**최소 WinForm 디자이너** dsl 템플릿은 사용자 고유의 요구 사항에 맞게 수정할 수 있는 최소 DSL을 만듭니다.

1. **최소 WinForm Designer** 템플릿에서 DSL을 만듭니다.

    이 연습에서는 다음 이름이 가정 됩니다.

    - 솔루션 및 DSL 이름: `FarmApp`
    - 네임스페이스: `Company.FarmApp`

2. 템플릿이 제공 하는 초기 예제를 실험 합니다.

   1. 모든 템플릿을 변환 합니다.

   2. 샘플을 빌드하고 실행 합니다 (**Ctrl** + **F5**).

   3. Visual Studio의 실험적 인스턴스에서 `Sample` 디버깅 프로젝트의 파일을 엽니다.

        Windows Forms 컨트롤에 표시 되는지 확인 합니다.

        탐색기에 표시 되는 모델의 요소를 볼 수도 있습니다.

        폼 이나 탐색기에서 일부 요소를 추가 하 고 다른 요소에 표시 되는지 확인 합니다.

   Visual Studio의 기본 인스턴스에서 DSL 솔루션에 대 한 다음 사항에 유의 하세요.

- `DslDefinition.dsl` 에는 다이어그램 요소가 없습니다. 이는 DSL 다이어그램을 사용 하 여이 DSL의 인스턴스 모델을 보는 것이 아니기 때문입니다. 대신 Windows Form을 모델에 바인딩하면 폼의 요소에 모델이 표시 됩니다.

- 및 프로젝트 외에 `Dsl` 도 `DslPackage` 솔루션에는 `UI.` **UI** 프로젝트에 Windows Forms 컨트롤의 정의가 포함 된 세 번째 프로젝트가 포함 되어 있습니다. `DslPackage` 에 따라 다르며 `UI` `UI` 에 따라 결정 `Dsl` 됩니다.

- 프로젝트에는 `DslPackage` `UI\DocView.cs` 프로젝트에 정의 된 Windows Forms 컨트롤을 표시 하는 코드가 포함 되어 있습니다 `UI` .

- 프로젝트에는 `UI` DSL에 바인딩된 양식 컨트롤의 작업 샘플이 포함 되어 있습니다. 그러나 DSL 정의를 변경한 경우에는 작동 하지 않습니다. 프로젝트에는 `UI` 다음이 포함 됩니다.

  - 이라는 Windows Forms 클래스 `ModelViewControl` 입니다.

  - `DataBinding.cs`의 추가 부분 정의를 포함 하는 라는 파일입니다 `ModelViewControl` . 해당 콘텐츠를 보려면 **솔루션 탐색기**에서 파일의 바로 가기 메뉴를 열고 **코드 보기**를 선택 합니다.

### <a name="about-the-ui-project"></a>UI 프로젝트 정보

Dsl 정의 파일을 업데이트 하 여 dsl을 정의 하는 경우에는 `UI` dsl을 표시 하도록 프로젝트의 컨트롤을 업데이트 해야 합니다. `Dsl`및 프로젝트와 달리 `DslPackage` 샘플 프로젝트는 `UI` 에서 생성 되지 않습니다 `DslDefinitionl.dsl` . 이 연습에서 다루지 않지만 원하는 경우 코드를 생성 하는 .tt 파일을 추가할 수 있습니다.

## <a name="update-the-dsl-definition"></a>DSL 정의 업데이트

이 연습에서는 다음 DSL 정의가 사용 됩니다.

![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png)

1. DSL 디자이너에서 DslDefinition를 엽니다.

2. **ExampleElement** 삭제

3. **Examplemodel.store.customer** 도메인 클래스의 이름을로 바꿉니다 `Farm` .

     Int32 형식 이라는 추가 도메인 속성을 지정 `Size` 하 **Int32**고 `IsOrganic` **부울**형식으로 지정 합니다.

    > [!NOTE]
    > 루트 도메인 클래스를 삭제 하 고 새 루트를 만든 경우 편집기 루트 클래스 속성을 다시 설정 해야 합니다. **DSL 탐색기**에서 **편집기**를 선택 합니다. 그런 다음 속성 창에서 **루트 클래스** 를로 설정 `Farm` 합니다.

4. **명명 된 도메인 클래스** 도구를 사용 하 여 다음 도메인 클래스를 만듭니다.

    - `Field` -이 추가 도메인 속성을 지정 `Size` 합니다.

    - `Animal` -속성 창에서 **상속 한정자** 를 **Abstract**로 설정 합니다.

5. **도메인 클래스** 도구를 사용 하 여 다음 클래스를 만듭니다.

    - `Sheep`

    - `Goat`

6. **상속** 도구를 사용 하 여 `Goat` `Sheep` 에서 만들고 상속 `Animal` 합니다.

7. **포함** 도구를 사용 하 여 `Field` 및을 포함 `Animal` `Farm` 합니다.

8. 다이어그램을 정리 하는 것이 좋습니다. 중복 요소 수를 줄이려면 리프 요소의 바로 가기 메뉴에서 **하위 트리 가져오기** 명령을 사용 합니다.

9. 솔루션 탐색기 도구 모음에서 **모든 템플릿을 변환** 합니다.

10. **Dsl** 프로젝트를 빌드합니다.

    > [!NOTE]
    > 이 단계에서는 다른 프로젝트가 오류 없이 빌드되지 않습니다. 그러나 Dsl 프로젝트를 빌드하여 데이터 원본 마법사에서 해당 어셈블리를 사용할 수 있도록 하려고 합니다.

## <a name="update-the-ui-project"></a>UI 프로젝트 업데이트

이제 DSL 모델에 저장 된 정보를 표시 하는 새 사용자 정의 컨트롤을 만들 수 있습니다. 사용자 정의 컨트롤을 모델에 연결 하는 가장 쉬운 방법은 데이터 바인딩을 사용 하는 것입니다. **Modelingbindingsource** 라는 데이터 바인딩 어댑터 형식은 dsl을 비 VMSDK 인터페이스에 연결 하기 위해 특별히 설계 되었습니다.

### <a name="define-your-dsl-model-as-a-data-source"></a>DSL 모델을 데이터 원본으로 정의

1. **데이터** 메뉴에서 **데이터 소스 표시**를 선택 합니다.

     **데이터 원본** 창이 열립니다.

     **새 데이터 원본 추가**를 선택 합니다. **데이터 원본 구성** 마법사가 열립니다.

2. **개체**를 선택 하 고 **다음**을 선택 합니다.

     **Dsl**, **FarmApp**을 확장 하 고 모델의 루트 클래스인 **팜**을 선택 합니다. **마침**을 선택합니다.

     솔루션 탐색기 **UI** 프로젝트에는 이제 **Properties\DataSources\Farm.datasource** 이 포함 되어 있습니다.

     모델 클래스의 속성 및 관계가 데이터 소스 창에 표시 됩니다.

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>모델을 폼에 연결

1. **UI** 프로젝트에서 기존 .cs 파일을 모두 삭제 합니다.

2. 이라는 새 **사용자 정의 컨트롤** 파일을 `FarmControl` **UI** 프로젝트에 추가 합니다.

3. **데이터 소스** 창의 **팜**드롭다운 메뉴에서 **자세히**를 선택 합니다.

    다른 속성에 대 한 기본 설정은 그대로 둡니다.

4. 디자인 뷰에서 FarmControl.cs를 엽니다.

    데이터 소스 창에서 FarmControl로 **팜을** 끌어 옵니다.

    각 속성에 대해 하나씩, 컨트롤 집합이 표시 됩니다. 관계 속성은 컨트롤을 생성 하지 않습니다.

5. **FarmBindingNavigator**를 삭제 합니다. 이는 디자이너에도 자동으로 생성 `FarmControl` 되지만이 응용 프로그램에는 유용 하지 않습니다.

6. 도구 상자를 사용 하 여 **DataGridView**의 두 인스턴스를 만들고 이름을 및로 이름을로 `AnimalGridView` `FieldGridView` 합니다.

   > [!NOTE]
   > 다른 단계는 데이터 소스 창에서 컨트롤로 동물 및 필드 항목을 끌어 놓는 것입니다. 이 작업을 수행 하면 표 뷰와 데이터 원본 간에 데이터 표 및 바인딩이 자동으로 만들어집니다. 그러나이 바인딩은 Dsl에 대해 올바르게 작동 하지 않습니다. 따라서 데이터 표 및 바인딩을 수동으로 만드는 것이 좋습니다.

7. 도구 상자에 **Modelingbindingsource** 도구가 없는 경우 추가 합니다. **데이터** 탭의 바로 가기 메뉴에서 **항목 선택**을 선택 합니다. **도구 상자 항목 선택** 대화 상자의 **.NET Framework** 탭에서 **modelingbindingsource** 를 선택 합니다.

8. 도구 상자를 사용 하 여 **Modelingbindingsource**의 두 인스턴스를 만들고 이름을 `AnimalBinding` 및로 `FieldBinding` 합니다.

9. 각 **Modelingbindingsource** 의 **DataSource** 속성을 **farmBindingSource**로 설정 합니다.

     **DataMember** 속성을 **동물** 또는 **필드로**설정 합니다.

10. 의 **DataSource** 속성을으로 설정 하 고을로 설정 합니다 `AnimalGridView` `AnimalBinding`  `FieldGridView` `FieldBinding` .

11. 팜 컨트롤의 레이아웃을 원하는 대로 조정 합니다.

    **Modelingbindingsource** 는 dsl과 관련 된 몇 가지 기능을 수행 하는 어댑터입니다.

- VMSDK 저장소 트랜잭션에서 업데이트를 래핑합니다.

   예를 들어 사용자가 데이터 뷰 표에서 행을 삭제 하면 일반 바인딩에서 트랜잭션 예외가 발생 합니다.

- 이를 통해 사용자가 행을 선택 하면 데이터 표 행 대신 해당 모델 요소의 속성이 속성 창 표시 됩니다.

  ![](../modeling/media/dslwpf4.png)데이터 원본 및 뷰 간의 링크 스키마를 DslWpf4 합니다.

### <a name="complete-the-bindings-to-the-dsl"></a>DSL에 바인딩 완료

1. **UI** 프로젝트에서 별도의 코드 파일에 다음 코드를 추가 합니다.

    ```csharp
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace Company.FarmApp
    {
      partial class FarmControl
      {
        public IContainer Components { get { return components; } }

        /// <summary>Binds the WinForms data source to the DSL model.
        /// </summary>
        /// <param name="nodelRoot">The root element of the model.</param>
        public void DataBind(ModelElement modelRoot)
        {
          WinFormsDataBindingHelper.PreInitializeDataSources(this);
          this.farmBindingSource.DataSource = modelRoot;
          WinFormsDataBindingHelper.InitializeDataSources(this);
        }
      }
    }
    ```

2. **Dslpackage** 프로젝트에서 **Dslpackage\docview.tt** 를 편집 하 여 다음 변수 정의를 업데이트 합니다.

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>DSL 테스트

이제 나중에 향상 된 기능을 더 추가할 수 있지만 DSL 솔루션을 빌드하고 실행할 수 있습니다.

1. 솔루션을 빌드하고 실행합니다.

2. Visual Studio의 실험적 인스턴스에서 **샘플** 파일을 엽니다.

3. **FarmApp 탐색기**에서 **팜** 루트 노드의 바로 가기 메뉴를 열고 **추가 새 goat**를 선택 합니다.

     `Goat1`**동물** 보기에 표시 됩니다.

    > [!WARNING]
    > **동물** 노드가 아닌 **팜** 노드에서 바로 가기 메뉴를 사용 해야 합니다.

4. **팜** 루트 노드를 선택 하 고 해당 속성을 봅니다.

     폼 보기에서 팜의 **이름** 또는 **크기** 를 변경 합니다.

     폼의 각 필드에서 다른 위치로 이동 하면 속성 창의 해당 속성이 변경 됩니다.

## <a name="enhance-the-dsl"></a>DSL 향상

### <a name="make-the-properties-update-immediately"></a>속성을 즉시 업데이트 하도록 설정

1. FarmControl.cs의 디자인 뷰에서 Name, Size 또는 IsOrganic와 같은 간단한 필드를 선택 합니다.

2. 속성 창에서 **데이터 바인딩** 을 확장 하 고 **(고급)** 을 엽니다.

     **서식 지정 및 고급 바인딩** 대화 상자의 **데이터 원본 업데이트 모드**에서 **OnPropertyChanged**를 선택 합니다.

3. 솔루션을 빌드하고 실행합니다.

     필드의 내용을 변경할 때 팜 모델의 해당 속성이 즉시 변경 되는지 확인 합니다.

### <a name="provide-add-buttons"></a>추가 단추 제공

1. FarmControl.cs의 디자인 뷰에서 도구 상자를 사용 하 여 폼에 단추를 만듭니다.

    단추의 이름과 텍스트 (예:)를 편집 `New Sheep` 합니다.

2. 단추를 두 번 클릭 하는 등의 방법으로 코드를 엽니다.

    다음과 같이 편집 합니다.

   ```csharp
   private void NewSheepButton_Click(object sender, EventArgs e)
   {
     using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
     {
       elementOperations.MergeElementGroup(farm,
         new ElementGroup(new Sheep(farm.Partition)));
       t.Commit();
     }
   }

   // The following code is shared with other add buttons:
   private ElementOperations operationsCache = null;
   private ElementOperations elementOperations
   {
     get
     {
       if (operationsCache == null)
       {
         operationsCache = new ElementOperations(farm.Store, farm.Partition);
       }
       return operationsCache;
     }
   }
   private Farm farm
   {
     get { return this.farmBindingSource.DataSource as Farm; }
   }
   ```

    또한 다음 지시문을 삽입 해야 합니다.

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Goats 및 필드에 대해 비슷한 단추를 추가 합니다.

4. 솔루션을 빌드하고 실행합니다.

5. 새 단추가 항목을 추가 하는지 확인 합니다. FarmApp 탐색기와 적절 한 데이터 그리드 뷰에 새 항목이 표시 됩니다.

    데이터 표 뷰에서 요소의 이름을 편집할 수 있어야 합니다. 또한 여기에서 삭제할 수 있습니다.

   ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>요소를 추가 하는 코드 정보

새 요소 단추에 대해 다음과 같은 대체 코드는 약간 더 간단 합니다.

```csharp
private void NewSheepButton_Click(object sender, EventArgs e)
{
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
  {
    farm.Animals.Add(new Sheep(farm.Partition)); ;
    t.Commit();
  }
}
```

그러나이 코드는 새 항목의 기본 이름을 설정 하지 않습니다. DSL의 **요소 병합 지시문** 에서 정의 했을 수 있는 사용자 지정 된 병합은 실행 되지 않으며, 정의 되었을 수 있는 사용자 지정 병합 코드는 실행 되지 않습니다.

따라서를 사용 하 여 새 요소를 만드는 것이 좋습니다 <xref:Microsoft.VisualStudio.Modeling.ElementOperations> . 자세한 내용은 [요소 만들기 및 이동 사용자 지정](../modeling/customizing-element-creation-and-movement.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보

- [도메인 특정 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)
- [도메인 특정 언어를 사용자 지정 하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Visual Studio용 모델링 SDK - 도메인별 언어](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
