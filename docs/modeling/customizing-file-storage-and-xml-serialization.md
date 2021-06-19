---
title: 파일 스토리지 및 XML Serialization 사용자 지정
description: Visual Studio DSL(도메인 특정 언어)의 인스턴스 또는 모델을 저장할 때 생성되거나 업데이트된 XML 파일에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be19b3026010e37108ca1b19096d48a3c8d88ab6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389373"
---
# <a name="customize-file-storage-and-xml-serialization"></a>파일 스토리지 및 XML Serialization 사용자 지정

사용자가 DSL(도메인 특정 언어)의 인스턴스 또는 *모델을* Visual Studio 저장하면 XML 파일이 생성되거나 업데이트됩니다. 파일을 다시 로드하여 Store에서 모델을 다시 만들 수 있습니다.

DSL 탐색기의 **Xml Serialization 동작에서** 설정을 조정하여 serialization 체계를 사용자 지정할 수 있습니다. 모든 도메인 클래스, 속성 및 관계에 대한 **Xml Serialization 동작** 아래에 노드가 있습니다. 관계는 해당 소스 클래스 아래에 있습니다. 도형, 커넥터 및 다이어그램 클래스에 해당하는 노드도 있습니다.

고급 사용자 지정을 위해 프로그램 코드를 작성할 수도 있습니다.

> [!NOTE]
> 모델을 특정 형식으로 저장하지만 해당 양식에서 다시 로드할 필요가 없는 경우 사용자 지정 serialization 스키마 대신 텍스트 템플릿을 사용하여 모델에서 출력을 생성하는 것이 좋습니다. 자세한 내용은 [Domain-Specific 언어에서 코드 생성을 참조하세요.](../modeling/generating-code-from-a-domain-specific-language.md)

## <a name="model-and-diagram-files"></a>모델 및 다이어그램 파일

각 모델은 일반적으로 두 개의 파일에 저장됩니다.

- 모델 파일에는 **Model1.mydsl** 과 같은 이름이 있습니다. 모델 요소와 관계 및 해당 속성을 저장합니다. **.mydsl과** 같은 파일 확장 프로그램은 DSL 정의에 있는 **편집기** 노드의 **FileExtension** 속성에 의해 결정됩니다.

- 다이어그램 파일에는 **Model1.mydsl.diagram** 와 같은 이름이 있습니다. 도형, 커넥터 및 해당 위치, 색, 선 두께 및 다이어그램 모양에 대한 기타 세부 정보를 저장합니다. 사용자가 **.diagram** 파일을 삭제하면 모델의 필수 정보가 손실되지 않습니다. 다이어그램의 레이아웃만 손실됩니다. 모델 파일이 열리면 기본 도형 및 커넥터 집합이 만들어집니다.

### <a name="to-change-the-file-extension-of-a-dsl"></a>DSL의 파일 확장자를 변경하려면

1. DSL 정의를 엽니다. DSL 탐색기에서 편집기 노드를 클릭합니다.

2. 속성 창 **FileExtension 속성을 편집합니다.** 파일 이름 확장명에 대한 초기 "."를 포함하지 않습니다.

3. 솔루션 탐색기 **DslPackage\ProjectItemTemplates** 에서 두 항목 템플릿 파일의 이름을 변경합니다. 이러한 파일에는 다음 형식을 따르는 이름이 있습니다.

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>기본 직렬화 구성표

이 항목에 대한 예제를 만들기 위해 다음 DSL 정의가 사용되었습니다.

![패밀리 트리 모델을 &#45; DSL 정의 다이어그램](../modeling/media/familyt_person.png)

이 DSL은 화면에 다음과 같은 모양의 모델을 만드는 데 사용되었습니다.

![패밀리 트리 다이어그램, 도구 상자 및 탐색기](../modeling/media/familyt_instance.png)

이 모델을 저장한 다음 XML 텍스트 편집기에서 다시 엽니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>
```

직렬화된 모델에 대한 다음 사항을 알아 두세요.

- 각 XML 노드에는 초기 문자가 소문자라는 점을 제외하고 도메인 클래스 이름과 동일한 이름이 있습니다. 예를 들어 `familyTreeModel` 및 `person`를 지정합니다.

- Name 및 BirthYear와 같은 도메인 속성은 XML 노드에서 특성으로 직렬화됩니다. 다시 말하지만 속성 이름의 초기 문자는 소문자로 변환됩니다.

- 각 관계는 관계의 원본 끝 내에 중첩된 XML 노드로 serialized됩니다. 노드는 원본 역할 속성과 이름이 같지만 소문자 초기 문자가 있습니다.

     예를 들어 DSL 정의에서 **People이라는** 역할은 **FamilyTree** 클래스에서 원본이 지정됩니다.  XML에서 이 노드는 노드 내부에 `people` 중첩된 노드로 `familyTreeModel` 표시됩니다.

- 각 포함 관계의 대상 끝은 관계 아래에 중첩된 노드로 직렬화됩니다. 예를 들어 `people` 노드에는 여러 `person` 노드가 포함됩니다.

- 각 참조 관계의 대상 끝은 대상 요소에 대한 참조를 인코딩하는 *모니커* 로 직렬화됩니다.

     예를 들어 노드 아래에 `person` 관계가 있을 수 `children` 있습니다. 이 노드에는 다음과 같은 모니커가 포함되어 있습니다.

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>모니커 이해

모니커를 사용하여 모델의 여러 부분과 다이어그램 파일 간의 상호 참조를 나타냅니다. 또한 `.diagram` 모델 파일의 노드를 참조하기 위해 파일에서 사용됩니다. 모니커에는 두 가지 형태가 있습니다.

- *ID 모니커가* 대상 요소의 GUID를 따옴표로 지정합니다. 예를 들면 다음과 같습니다.

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- *정규화된 키 모니커는 모니커* 키라는 지정된 도메인 속성의 값으로 대상 요소를 식별합니다. 대상 요소의 모니커 앞에는 포함 관계 트리에 있는 부모 요소의 모니커가 있습니다.

     다음 예제는 Song이라는 도메인 클래스와 포함 관계가 있는 Album이라는 도메인 클래스가 있는 DSL에서 가져온 것입니다.

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     정규화된 키 모니커는 대상 클래스에 Xml Serialization 동작에서 **모니커 키** 옵션 이 로 설정된 도메인 속성이 있는 경우에 `true` 사용됩니다. 예제에서 이 옵션은 도메인 클래스 "Album" 및 "Song"에서 "Title"이라는 도메인 속성에 대해 설정됩니다.

정규화된 키 모니커는 ID 모니커보다 읽기 쉽습니다. 사용자가 모델 파일의 XML을 읽으려는 경우 정규화된 키 모니커를 사용하는 것이 좋습니다. 그러나 사용자가 두 개 이상의 요소에 동일한 모니커 키를 갖도록 설정할 수 있습니다. 키가 중복되면 파일이 올바르게 다시 로드되지 않을 수 있습니다. 따라서 정규화된 키 모니커를 사용하여 참조되는 도메인 클래스를 정의하는 경우 사용자가 중복 모니커가 있는 파일을 저장하지 못하게 하는 방법을 고려해야 합니다.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>ID 모니커에서 참조할 도메인 클래스를 설정하려면

1. **모니커 키는** 클래스 `false` 및 해당 기본 클래스의 모든 도메인 속성에 대한 키인지 확인합니다.

    1. DSL 탐색기에서 **Xml Serialization Behavior\Class Data \Element Data 를 \\ \<the domain class> 확장합니다.**

    2. **모니커 키가** 모든 도메인 속성에 대한 키인지 `false` 확인합니다.

    3. 도메인 클래스에 기본 클래스가 있는 경우 해당 클래스에서 프로시저를 반복합니다.

2. 도메인 클래스에 대한 **직렬화**  =  `true` ID를 설정합니다.

     이 속성은 **Xml Serialization 동작** 에서 찾을 수 있습니다.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>정규화된 키 모니커에서 참조할 도메인 클래스를 설정하려면

- 기존 도메인 클래스의 도메인 속성에 대해 **모니커 키로** 설정합니다. 속성의 형식은 이어야 `string` 합니다.

    1. DSL 탐색기에서 **Xml Serialization Behavior\Class Data \\ \<the domain class> \Element Data** 를 확장한 다음 도메인 속성을 선택합니다.

    2. 속성 창 **모니커 키로** 를 `true` 설정합니다.

- \- 또는-

     명명된 도메인 클래스 도구를 사용하여 새 **도메인 클래스를** 만듭니다.

     이 도구는 Name이라는 도메인 속성이 있는 새 클래스를 만듭니다. 이 도메인 속성의 **Is 요소 이름** 및 Is **모니커 키** 속성은 로 초기화됩니다. `true`

- \- 또는-

     도메인 클래스에서 모니커 키 속성이 있는 다른 클래스로 상속 관계를 만듭니다.

### <a name="avoid-duplicate-monikers"></a>중복 모니커 방지

정규화된 키 모니커를 사용하는 경우 사용자 모델의 두 요소가 키 속성에서 동일한 값을 가질 수 있습니다. 예를 들어 DSL에 Name 속성이 있는 Person 클래스가 있는 경우 사용자는 두 요소의 Names를 동일하게 설정할 수 있습니다. 모델을 파일에 저장할 수 있지만 올바르게 다시 로드되지는 않습니다.

이 상황을 방지하는 데 도움이 되는 몇 가지 방법이 있습니다.

- 키 도메인 속성에 대한 **요소 이름**  =  `true` 을 설정합니다. DSL 정의 다이어그램에서 도메인 속성을 선택한 다음 속성 창 값을 설정합니다.

     사용자가 클래스의 새 인스턴스를 만들 때 이 값을 지정하면 도메인 속성에 다른 값이 자동으로 할당됩니다. 기본 동작은 클래스 이름의 끝에 숫자를 추가합니다. 이렇게 하면 사용자가 이름을 중복으로 변경할 수 없지만 사용자가 모델을 저장하기 전에 값을 설정하지 않은 경우에 도움이 됩니다.

- DSL에 대한 유효성 검사를 사용하도록 설정합니다. DSL 탐색기에서 Editor\Validation을 선택하고 **Uses...** 속성을 `true` 로 설정합니다.

     모호성을 확인하는 자동으로 생성된 유효성 검사 메서드가 있습니다. 메서드는 유효성 `Load` 검사 범주에 있습니다. 이렇게 하면 사용자가 파일을 다시 열 수 없다는 경고가 표시됩니다.

     자세한 내용은 [Domain-Specific 언어의 유효성 검사를 참조하세요.](../modeling/validation-in-a-domain-specific-language.md)

### <a name="moniker-paths-and-qualifiers"></a>모니커 경로 및 한정자

정규화된 키 모니커는 모니커 키로 끝나며 포함 트리에 부모의 모니커가 접두사로 수록됩니다. 예를 들어, 앨범의 모니커가 다음과 같은 경우입니다.

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

그런 다음, 해당 앨범의 노래 중 하나는 다음과 같습니다.

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

그러나 앨범이 ID로 참조되는 경우 모니커가 다음과 같습니다.

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

GUID는 고유하기 때문에 부모의 모니커가 접두사로 해서는 안 됩니다.

특정 도메인 속성에 항상 모델 내에서 고유한 값이 있다는 것을 알고 있는 경우 해당 속성에 대해 **모니커 한정자 를** 로 설정할 수 `true` 있습니다. 이렇게 하면 부모의 모니커를 사용하지 않고 한정자로 사용됩니다. 예를 들어, Album 클래스의 Title 도메인 속성에 **대해 Is Moniker Qualifier** 및 Is **Moniker Key를** 둘 다 설정하는 경우 모델 이름 또는 식별자는 Album 및 포함된 자식의 모니커에서 사용되지 않습니다.

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>XML의 구조 사용자 지정

다음 사용자 지정을 수행하려면 DSL 탐색기에서 **Xml Serialization 동작** 노드를 확장합니다. 도메인 클래스에서 요소 데이터 노드를 확장하여 이 클래스에서 원본으로 사용되는 속성 및 관계 목록을 확인합니다. 관계를 선택하고 속성 창 해당 옵션을 조정합니다.

- **Omit 요소를** true로 설정하여 원본 역할 노드를 생략하고 대상 요소 목록만 남깁니다. 소스 클래스와 대상 클래스 간에 관계가 두 개 이상 있는 경우 이 옵션을 설정하면 안 됩니다.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- **전체 양식 사용을** 설정하여 관계 인스턴스를 나타내는 노드에 대상 노드를 포함합니다. 이 옵션은 도메인 관계에 도메인 속성을 추가할 때 자동으로 설정됩니다.

    ```xml
    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>
    ```

- **Representation**  =  **요소를** 설정하여 도메인 속성을 특성 값이 아닌 요소로 저장합니다.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- 특성 및 관계가 serialized되는 순서를 변경하려면 요소 데이터에서 항목을 마우스 오른쪽 단추로 클릭하고 **위로 이동** 또는 아래로 **이동** 메뉴 명령을 사용합니다.

## <a name="major-customization-using-program-code"></a>프로그램 코드를 사용한 주요 사용자 지정

부분 또는 모든 serialization 알고리즘을 바꿀 수 있습니다.

**Dsl\Generated Code\Serializer.cs** 및 **SerializationHelper.cs** 의 코드를 연구하는 것이 좋습니다.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>특정 클래스의 serialization을 사용자 지정하려면

1. **Xml Serialization 동작** 아래의 해당 클래스에 대한 노드에서 **사용자 지정으로** 설정합니다.

2. 모든 템플릿을 변환하고, 솔루션을 빌드하고, 결과 컴파일 오류를 조사합니다. 각 오류 근처의 주석은 제공해야 하는 코드를 설명합니다.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>전체 모델에 고유한 직렬화를 제공하려면

1. Dsl\GeneratedCode\SerializationHelper.cs의 메서드 재정의

## <a name="options-in-xml-serialization-behavior"></a>Xml Serialization 동작의 옵션

DSL 탐색기에서 Xml Serialization 동작 노드에는 각 도메인 클래스, 관계, 셰이프, 커넥터 및 다이어그램 클래스에 대한 자식 노드가 포함됩니다. 이러한 각 노드 아래에는 해당 요소에서 소스가 되는 속성 및 관계 목록이 있습니다. 관계는 고유한 오른쪽 및 소스 클래스에서 모두 표시됩니다.

다음 표에서는 DSL 정의의 이 섹션에서 설정할 수 있는 옵션을 요약합니다. 각 경우에 DSL 탐색기에서 요소를 선택하고 속성 창 옵션을 설정합니다.

### <a name="xml-class-data"></a>Xml 클래스 데이터

이러한 요소는 DSL 탐색기의 **Xml Serialization Behavior\Class Data** 아래에 있습니다.

|속성|설명|
|-|-|
|사용자 지정 요소 스키마가 있습니다.|True이면 도메인 클래스에 사용자 지정 요소 스키마가 있음을 나타냅니다.|
|사용자 지정|이 도메인 **클래스에** 대한 직렬화 및 역직렬화 코드를 직접 작성하려면 True로 설정합니다.<br /><br /> 솔루션을 빌드하고 오류를 조사하여 자세한 지침을 검색합니다.|
|도메인 클래스|이 클래스 데이터 노드가 적용되는 도메인 클래스입니다. 읽기 전용입니다.|
|요소 이름|이 클래스의 요소에 대한 Xml 노드 이름입니다. 기본값은 도메인 클래스 이름의 소문자 버전입니다.|
|모니커 특성 이름|참조를 포함하기 위해 모니커 요소에 사용되는 특성의 이름입니다. 비어 있으면 키 속성 또는 ID의 이름이 사용됩니다.<br /><br /> 이 예제에서는 "name"입니다.  `<personMoniker name="/Mike Nash"/>`|
|모니커 요소 이름|이 클래스의 요소를 참조하는 모니커에 사용되는 xml 요소의 이름입니다.<br /><br /> 기본값은 "모니커" 접미사가 붙는 클래스 이름의 소문자 버전입니다. 예들 들어 `personMoniker`입니다.|
|모니커 형식 이름|이 클래스의 요소에 대한 모니커에 대해 생성된 xsd 형식의 이름입니다. XSD는 **Dsl\Generated Code \\ \* Schema.xsd에 있습니다.**|
|직렬화 ID|True이면 요소 GUID가 파일에 포함됩니다. **모니커 키로** 표시된 속성이 없고 DSL이 이 클래스에 대한 참조 관계를 정의하는 경우에는 true여야 합니다.|
|유형 이름|지정된 도메인 클래스에서 xsd에 생성된 xml 형식의 이름입니다.|
|참고|이 요소와 관련된 비공식 메모|

### <a name="xml-property-data"></a>Xml 속성 데이터

Xml 속성 노드는 클래스 노드 아래에 있습니다.

|속성|설명|
|-|-|
|도메인 속성|xml serialization 구성 데이터가 적용되는 속성입니다. 읽기 전용입니다.|
|모니커 키임|True이면 속성이 이 도메인 클래스의 인스턴스를 참조하는 모니커를 만들기 위한 키로 사용됩니다.|
|모니커 한정자|True이면 속성이 모니커에서 한정자를 만드는 데 사용됩니다. false이고 이 도메인 클래스에 대해 SerializeId가 true가 아닌 경우 모니커는 포함 트리에 있는 부모 요소의 모니커로 한정됩니다.|
|표현|Attribute이면 속성이 xml 특성으로 serialized됩니다. 요소이면 요소로 serialized됩니다. Ignore이면 직렬화되지 않습니다.|
|Xml 이름|속성을 나타내는 xml 특성 또는 요소에 사용되는 이름입니다. 기본적으로 도메인 속성 이름의 소문자 버전입니다.|
|참고|이 요소와 관련된 비공식 메모|

### <a name="xml-role-data"></a>Xml 역할 데이터

역할 데이터 노드는 원본 클래스 노드 아래에 있습니다.

|속성|설명|
|-|-|
|사용자 지정 모니커가 있습니다.|이 관계를 트래버스하는 모니커를 생성하고 확인하기 위한 사용자 고유의 코드를 제공하려면 이 설정을 true로 설정합니다.<br /><br /> 자세한 지침을 보려면 솔루션을 빌드한 다음 오류 메시지를 두 번 클릭합니다.|
|도메인 관계|이러한 옵션이 적용되는 관계를 지정합니다. 읽기 전용입니다.|
|Omit 요소|true이면 원본 역할에 해당하는 XML 노드가 스키마에서 생략됩니다.<br /><br /> 원본 및 대상 클래스 간에 둘 이상의 관계가 있는 경우 이 역할 노드는 두 관계에 속하는 링크를 구분합니다. 따라서 이 경우에는 이 옵션을 설정하지 않는 것이 좋습니다.|
|Role 요소 이름|원본 역할에서 파생된 XML 요소의 이름을 지정합니다. 기본값은 역할 속성 이름입니다.|
|전체 양식 사용|true이면 각 대상 요소 또는 모니커가 관계를 나타내는 XML 노드로 묶입니다. 관계에 고유한 도메인 속성이 있는 경우 true로 설정해야 합니다.|

## <a name="see-also"></a>참조

- [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)
