---
title: 종속성 다이어그램에 사용자 지정 아키텍처 유효성 검사 추가
description: 종속성 다이어그램에 사용자 지정 아키텍처 유효성 검사를 추가 하는 방법에 대 한 정보를 제공 합니다.
ms.date: 11/04/2016
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: ea168744427469d1d08dd78bc1a23d79d577604f
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100528"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>종속성 다이어그램에 사용자 지정 아키텍처 유효성 검사 추가

Visual Studio에서 사용자는 소스 코드가 종속성 다이어그램의 종속성을 따르는지 확인할 수 있도록 레이어 모델에 대해 프로젝트의 소스 코드에 대 한 유효성을 검사할 수 있습니다. 표준 유효성 검사 알고리즘이 있지만 고유한 유효성 검사 확장을 정의할 수 있습니다.

사용자가 종속성 다이어그램에서 **아키텍처 유효성** 검사 명령을 선택 하면 표준 유효성 검사 메서드가 호출 되 고 그 다음에 설치 된 유효성 검사 확장이 발생 합니다.

> [!NOTE]
> 종속성 다이어그램에서 유효성 검사의 주요 목적은 다이어그램을 솔루션의 다른 파트에 있는 프로그램 코드와 비교 하는 것입니다.

다른 Visual Studio 사용자에게 배포할 수 있는 VSIX(Visual Studio Integration Extension)로 레이어 유효성 검사 확장을 패키지할 수 있습니다. 한 VSIX에 단독으로 유효성 검사기를 배치하거나 다른 확장과 같은 VSIX에서 유효성 검사기를 결합할 수 있습니다. 다른 확장과 같은 프로젝트가 아니라 고유한 Visual Studio 프로젝트에서 유효성 검사기 코드를 작성해야 합니다.

> [!WARNING]
> 유효성 검사 프로젝트를 만들고 나서 [예제 코드](#example) 를 이 항목의 끝에 복사하고 필요에 따라 편집합니다.

## <a name="requirements"></a>요구 사항

[요구 사항](../modeling/extend-layer-diagrams.md#requirements)을 참조 하세요.

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>새 VSIX에서 레이어 유효성 검사기 정의

유효성 검사기를 만드는 가장 빠른 방법은 프로젝트 템플릿을 사용하는 것입니다. 이 방법에서는 코드 및 VSIX 매니페스트를 동일한 프로젝트에 배치합니다.

### <a name="to-define-an-extension-by-using-a-project-template"></a>프로젝트 템플릿을 사용하여 확장을 정의하려면

1. 새 **레이어 디자이너 유효성 검사 확장** 프로젝트를 만듭니다.

    템플릿에서 작은 예제가 포함된 프로젝트를 만듭니다.

   > [!WARNING]
   > 템플릿이 제대로 작동하도록 설정하려면
   >
   > - `LogValidationError` 에 대한 호출을 편집하여 선택적 인수 `errorSourceNodes` 및 `errorTargetNodes`를 제거합니다.
   > - 사용자 지정 속성을 사용 하는 경우 [종속성 다이어그램에 사용자 지정 속성 추가](../modeling/add-custom-properties-to-layer-diagrams.md)에 설명 된 업데이트를 적용 합니다.

2. 코드를 편집하여 유효성 검사를 정의합니다. 자세한 내용은 [프로그래밍 유효성 검사](#programming)를 참조하세요.

3. 확장을 테스트하려면 [레이어 유효성 검사 디버그](#debugging)를 참조하세요.

   > [!NOTE]
   > 메서드는 특정 상황에서만 호출되고 중단점은 자동으로 작동하지 않습니다. 자세한 내용은 [레이어 유효성 검사 디버그](#debugging)를 참조하세요.

::: moniker range="vs-2017"

4. Visual Studio의 주 인스턴스 또는 다른 컴퓨터에 확장을 설치 하려면 *bin* 디렉터리에서 *.vsix* 파일을 찾습니다. 설치할 컴퓨터로 파일을 복사하고 파일을 두 번 클릭합니다. 제거 하려면 **도구** 메뉴에서 **확장 및 업데이트** 를 선택 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

4. Visual Studio의 주 인스턴스 또는 다른 컴퓨터에 확장을 설치 하려면 *bin* 디렉터리에서 *.vsix* 파일을 찾습니다. 설치할 컴퓨터로 파일을 복사하고 파일을 두 번 클릭합니다. 제거 하려면 **확장** 메뉴에서 **확장 관리** 를 선택 합니다.

::: moniker-end

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>개별 VSIX에 레이어 유효성 검사기 추가

레이어 유효성 검사기, 명령 및 기타 확장이 포함된 하나의 VSIX를 만들려면 VSIX를 정의하는 프로젝트 하나와 처리기에 대한 개별 프로젝트를 만드는 것이 좋습니다.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>개별 VSIX에 레이어 유효성 검사를 추가하려면

1. 새 **클래스 라이브러리** 프로젝트를 만듭니다. 이 프로젝트에는 레이어 유효성 검사 클래스가 포함됩니다.

2. 솔루션에서 **VSIX 프로젝트** 를 찾거나 만듭니다. VSIX 프로젝트에는 이름이 **source.extension.vsixmanifest**인 파일이 포함됩니다.

3. **솔루션 탐색기**의 VSIX 프로젝트 오른쪽 클릭 메뉴에서 **시작 프로젝트로 설정**을 선택 합니다.

4. **source.extension.vsixmanifest**의 **자산**에서 레이어 유효성 검사 프로젝트를 MEF 구성 요소로 추가합니다.

    1. **새로 만들기**를 선택합니다.

    2. **새 자산 추가** 대화 상자에서 다음을 설정합니다.

         **유형**  =  **VisualStudio 구성 요소**

         **원본**  =  **현재 솔루션의 프로젝트**

         **프로젝트**  =  *유효성 검사기 프로젝트*

5. 또한 레이어 유효성 검사로 추가해야 합니다.

    1. **새로 만들기**를 선택합니다.

    2. **새 자산 추가** 대화 상자에서 다음을 설정합니다.

         **유형**  =  **VisualStudio. microsoft.visualstudio.architecturetools.layer.validator**. 이는 드롭다운 목록의 옵션 중 하나가 아닙니다. 키보드에서 입력해야 합니다.

         **원본**  =  **현재 솔루션의 프로젝트**

         **프로젝트**  =  *유효성 검사기 프로젝트*

6. 레이어 유효성 검사 프로젝트로 돌아가서 다음 프로젝트 참조를 추가합니다.

    |**참조**|**수행할 수 있는 기능**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|아키텍처 그래프 읽기|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|레이어와 연결된 코드 DOM 읽기|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|레이어 모델 읽기|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|모양 및 다이어그램을 읽고 업데이트합니다.|
    |System.ComponentModel.Composition|MEF(Managed Extensibility Framework)를 사용하여 유효성 검사 구성 요소를 정의합니다.|
    |Microsoft.VisualStudio.Modeling.Sdk.[version]|모델링 확장 정의|

7. 이 항목의 끝에 있는 예제 코드를 유효성 검사기 라이브러리 프로젝트의 클래스 파일에 복사하여 유효성 검사에 대한 코드를 포함합니다. 자세한 내용은 [프로그래밍 유효성 검사](#programming)를 참조하세요.

8. 확장을 테스트하려면 [레이어 유효성 검사 디버그](#debugging)를 참조하세요.

    > [!NOTE]
    > 메서드는 특정 상황에서만 호출되고 중단점은 자동으로 작동하지 않습니다. 자세한 내용은 [레이어 유효성 검사 디버그](#debugging)를 참조하세요.

9. Visual Studio의 주 인스턴스 또는 다른 컴퓨터에 VSIX를 설치 하려면 VSIX 프로젝트의 **bin** 디렉터리에서 **.vsix** 파일을 찾습니다. VSIX를 설치할 컴퓨터에 파일을 복사합니다. Windows 탐색기에서 VSIX 파일을 두 번 클릭합니다.

## <a name="programming-validation"></a><a name="programming"></a> 프로그래밍 유효성 검사

레이어 유효성 검사 확장을 정의하려면 다음 특징을 가진 클래스를 정의합니다.

- 전체 선언 형식은 다음과 같습니다.

  ```csharp
  using System.ComponentModel.Composition;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
  using Microsoft.VisualStudio.GraphModel;
  ...
   [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator1Extension :
                    IValidateArchitectureExtension
    {
      public void ValidateArchitecture(Graph graph)
      {
         GraphSchema schema = graph.DocumentSchema;
        ...
    } }
  ```

- 오류를 검색할 때 `LogValidationError()`를 사용하여 오류를 보고할 수 있습니다.

  > [!WARNING]
  > `LogValidationError`의 선택적 매개 변수를 사용하지 마세요.

사용자가 **아키텍처 유효성 검사** 메뉴 명령을 호출하면 레이어 런타임 시스템에서는 레이어 및 해당 아티팩트를 분석하여 그래프를 생성합니다. 그래프는 다음 네 파트로 구성됩니다.

- 그래프에서 노드 및 링크로 표시 되는 Visual Studio 솔루션의 레이어 모델입니다.

- 솔루션에 정의되고 노드로 표시되는 코드, 프로젝트 항목 및 기타 아티팩트와 분석 프로세스에서 검색되는 종속성을 나타내는 링크.

- 레이어 노드에서 코드 아티팩트 노드로 연결된 링크.

- 유효성 검사기에서 검색된 오류를 나타내는 노드.

그래프가 생성되면 표준 유효성 검사 메서드가 호출됩니다. 호출이 완료되면 모든 설치된 확장 유효성 검사 메서드가 지정되지 않은 순서로 호출됩니다. 그래프는 그래프를 검사하고 발견한 오류를 보고할 수 있는 각 `ValidateArchitecture` 메서드에 전달됩니다.

> [!NOTE]
> 도메인 특정 언어에서 사용할 수 있는 유효성 검사 프로세스와는 다릅니다.

유효성 검사 메서드가 유효성 검사 중인 레이어 모델 또는 코드를 변경하면 안 됩니다.

그래프 모델은 <xref:Microsoft.VisualStudio.GraphModel>에 정의됩니다. 주체 클래스는 <xref:Microsoft.VisualStudio.GraphModel.GraphNode> 및 <xref:Microsoft.VisualStudio.GraphModel.GraphLink>입니다.

각 노드와 각 링크에는 각 노드 및 링크가 나타내는 요소 또는 관계의 형식을 지정하는 범주가 하나 이상 있습니다. 일반적인 그래프의 노드에는 다음 범주가 있습니다.

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

코드에서 레이어에서 요소로 연결된 링크에는 “Represents” 범주가 있습니다.

## <a name="debugging-validation"></a><a name="debugging"></a> 디버깅 유효성 검사

레이어 유효성 검사 확장을 디버그하려면 Ctrl+F5를 누릅니다. Visual Studio의 실험적 인스턴스가 열립니다. 이 인스턴스에서 레이어 모델을 열거나 만듭니다. 이 모델은 코드와 연결되어야 하고 종속성을 하나 이상 포함해야 합니다.

### <a name="test-with-a-solution-that-contains-dependencies"></a>종속성이 포함된 솔루션으로 테스트

다음 특징이 있어야 유효성 검사가 실행됩니다.

- 종속성 다이어그램에 종속성 링크가 하나 이상 있습니다.

- 모델에 코드 요소와 연결된 레이어가 있습니다.

Visual Studio의 실험적 인스턴스를 처음으로 시작 하 여 유효성 검사 확장을 테스트 하는 경우 이러한 특성이 포함 된 솔루션을 열거나 만듭니다.

### <a name="run-clean-solution-before-validate-architecture"></a>아키텍처 유효성 검사 전에 솔루션 정리 실행

유효성 검사 코드를 업데이트할 때마다 유효성 검사 명령을 테스트하기 전에 실험적 솔루션에서 **빌드** 메뉴의 **솔루션 정리** 를 사용합니다. 유효성 검사의 결과가 캐시되므로 이 작업이 필요합니다. 테스트 종속성 다이어그램이 나 해당 코드를 업데이트 하지 않은 경우 유효성 검사 메서드가 실행 되지 않습니다.

### <a name="launch-the-debugger-explicitly"></a>명시적으로 디버거 시작

유효성 검사는 개별 프로세스로 실행됩니다. 따라서 유효성 검사 메서드의 중단점이 트리거되지 않습니다. 유효성 검사가 시작되었을 때 디버거를 프로세스에 명시적으로 연결해야 합니다.

유효성 검사 프로세스에 디버거를 연결하려면 유효성 검사 메서드의 시작 부분에 `System.Diagnostics.Debugger.Launch()` 에 대한 호출을 삽입합니다. 디버깅 대화 상자가 나타나면 Visual Studio의 기본 인스턴스를 선택 합니다.

또는 `System.Windows.Forms.MessageBox.Show()`에 대한 호출을 삽입할 수 있습니다. 메시지 상자가 나타나면 Visual Studio의 주 인스턴스로 이동 하 고 **디버그** 메뉴에서 **프로세스에 연결을**클릭 합니다. 이름이 **Graphcmd.exe**인 프로세스를 선택합니다.

항상 Crtl+F5(**디버깅하지 않고 시작**)를 눌러서 실험적 인스턴스를 시작합니다.

### <a name="deploying-a-validation-extension"></a>유효성 검사 확장 배포

적합한 Visual Studio 버전이 설치된 컴퓨터에 유효성 검사 확장을 설치하려면 대상 컴퓨터에서 VSIX 파일을 엽니다.

## <a name="example-code"></a><a name="example"></a> 예제 코드

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>참고 항목

- [종속성 다이어그램 확장](../modeling/extend-layer-diagrams.md)
