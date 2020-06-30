---
title: 파일 스토리지 및 XML Serialization 사용자 지정
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07592247e0afb870f3c4774c6f2023a6e8141cd1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542742"
---
# <a name="customize-file-storage-and-xml-serialization"></a>파일 스토리지 및 XML Serialization 사용자 지정

사용자가 Visual Studio에서 DSL (도메인 특정 언어)의 인스턴스 또는 *모델*을 저장 하면 XML 파일이 만들어지거나 업데이트 됩니다. 파일을 다시 로드 하 여 저장소에서 모델을 다시 만들 수 있습니다.

DSL 탐색기의 **Xml Serialization 동작** 에서 설정을 조정 하 여 serialization 체계를 사용자 지정할 수 있습니다. 모든 도메인 클래스, 속성 및 관계에 대 한 **Xml Serialization 동작** 아래에 노드가 있습니다. 관계는 해당 소스 클래스 아래에 있습니다. 셰이프, 연결선 및 다이어그램 클래스에 해당 하는 노드도 있습니다.

더 고급 사용자 지정을 위해 프로그램 코드를 작성할 수도 있습니다.

> [!NOTE]
> 모델을 특정 형식으로 저장 하려는 경우에는 해당 형식에서 모델을 다시 로드할 필요가 없는 경우 사용자 지정 직렬화 스키마 대신 텍스트 템플릿을 사용 하 여 모델의 출력을 생성 하는 것이 좋습니다. 자세한 내용은 [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)을 참조 하세요.

## <a name="model-and-diagram-files"></a>모델 및 다이어그램 파일

각 모델은 일반적으로 다음 두 파일에 저장 됩니다.

- 모델 파일에는 **Model1**와 같은 이름이 있습니다. 모델 요소와 관계 및 해당 속성을 저장 합니다. **. Mydsl** 과 같은 파일 확장명은 DSL 정의에서 **편집기** 노드의 **fileextension** 속성에 의해 결정 됩니다.

- 다이어그램 파일에는 **Model1**와 같은 이름이 있습니다. 셰이프, 연결선 및 해당 위치, 색, 선 두께 및 다이어그램 모양의 기타 세부 정보를 저장 합니다. 사용자가 **다이어그램** 파일을 삭제 하면 모델의 필수 정보는 손실 되지 않습니다. 다이어그램의 레이아웃만 손실 됩니다. 모델 파일이 열리면 기본 모양 및 연결선 집합이 생성 됩니다.

### <a name="to-change-the-file-extension-of-a-dsl"></a>DSL의 파일 확장명을 변경 하려면

1. DSL 정의를 엽니다. DSL 탐색기에서 편집기 노드를 클릭 합니다.

2. 속성 창에서 **Fileextension** 속성을 편집 합니다. 파일 이름 확장명의 초기 "."를 포함 하지 마십시오.

3. 솔루션 탐색기에서 **DslPackage\ProjectItemTemplates**의 두 항목 템플릿 파일의 이름을 변경 합니다. 이러한 파일에는 다음 형식을 따르는 이름이 있습니다.

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>기본 직렬화 스키마

이 항목에 대 한 예제를 만들려면 다음 DSL 정의가 사용 되었습니다.

![DSL 정의 다이어그램 &#45; 패밀리 트리 모델](../modeling/media/familyt_person.png)

이 DSL은 화면에 다음과 같은 모양의 모델을 만드는 데 사용 되었습니다.

![패밀리 트리 다이어그램, 도구 상자 및 탐색기](../modeling/media/familyt_instance.png)

이 모델은 XML 텍스트 편집기에서 저장 된 후 다시 열립니다.

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

직렬화 된 모델에 대 한 다음 사항에 유의 하세요.

- 각 XML 노드에는 도메인 클래스 이름과 동일한 이름이 있습니다. 단, 첫 문자는 소문자입니다. 예를 들어 `familyTreeModel` 또는 `person`입니다.

- Name 및 BirthYear과 같은 도메인 속성은 XML 노드에 특성으로 직렬화 됩니다. 마찬가지로 속성 이름의 초기 문자는 소문자로 변환 됩니다.

- 각 관계는 관계의 원본 끝 안에 중첩 된 XML 노드로 serialize 됩니다. 노드에 원본 역할 속성과 이름이 같지만 대/소문자를 구분 합니다.

     예를 들어 DSL 정의에서 **사용자** 라는 역할은 **FamilyTree** 클래스를 기반으로 합니다.  XML에서이는 노드 내에 중첩 된 노드로 표시 됩니다 `people` `familyTreeModel` .

- 각 포함 관계의 대상 끝은 관계에서 중첩 된 노드로 serialize 됩니다. 예를 `people` 들어 노드는 여러 노드를 포함 `person` 합니다.

- 각 참조 관계의 대상 끝은 대상 요소에 대 한 참조를 인코딩하는 *모니커로*serialize 됩니다.

     예를 들어 노드 아래에 `person` 관계가 있을 수 있습니다 `children` . 이 노드에 포함 된 모니커는 다음과 같습니다.

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>모니커 이해

모니커는 모델 및 다이어그램 파일의 서로 다른 부분 간의 상호 참조를 나타내는 데 사용 됩니다. 또한 `.diagram` 파일에서 모델 파일의 노드를 참조 하는 데 사용 됩니다. 모니커에는 다음과 같은 두 가지 형태가 있습니다.

- *Id 모니커* 따옴표 대상 요소의 GUID입니다. 예를 들면 다음과 같습니다.

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- *정규화 된 키 모니커* 는 대상 요소를 모니커 키 라는 지정 된 도메인 속성 값으로 식별 합니다. 대상 요소의 모니커에는 포함 관계 트리에서 부모 요소의 모니커가 접두사로 붙습니다.

     다음 예제는 이름이 Song 인 도메인 클래스에 대 한 포함 관계를 포함 하는 이름이 앨범이 인 도메인 클래스가 있는 DSL에서 가져옵니다.

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     정규화 된 키 모니커는 대상 클래스에 **Moniker key** 옵션이 `true` **Xml Serialization 동작**에서로 설정 된 도메인 속성이 있는 경우 사용 됩니다. 이 예제에서이 옵션은 도메인 클래스 "앨범" 및 "곡"에서 이름이 "Title" 인 도메인 속성에 대해 설정 됩니다.

정규화 된 키 모니커는 ID 모니커 보다 읽기가 더 쉽습니다. 사용자가 모델 파일의 XML을 읽도록 하려면 정규화 된 키 모니커를 사용 하는 것이 좋습니다. 그러나 사용자가 두 개 이상의 요소를 설정 하 여 동일한 모니커 키를 가질 수 있습니다. 중복 키로 인해 파일이 올바르게 다시 로드 되지 않을 수 있습니다. 따라서 정규화 된 키 모니커를 사용 하 여 참조 되는 도메인 클래스를 정의 하는 경우 사용자가 중복 된 모니커가 있는 파일을 저장 하지 못하도록 방지 하는 방법을 고려해 야 합니다.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>ID 모니커에서 참조할 도메인 클래스를 설정 하려면

1. **Is Moniker Key** `false` 클래스 및 해당 기본 클래스의 모든 도메인 속성에 대해 모니커 키가 있는지 확인 합니다.

    1. DSL 탐색기에서 **Xml 직렬화 Behavior\Class data \\ \<the domain class> \element data**를 확장 합니다.

    2. 모든 도메인 속성에 대해 **모니커 키** 가 있는지 확인 `false` 합니다.

    3. 도메인 클래스에 기본 클래스가 있는 경우 해당 클래스에서 절차를 반복 합니다.

2. **Serialize Id**  =  `true` 도메인 클래스에 대 한 직렬화 Id를 설정 합니다.

     이 속성은 **Xml Serialization 동작**에서 찾을 수 있습니다.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>정규화 된 키 모니커에서 참조할 도메인 클래스를 설정 하려면

- 기존 도메인 클래스의 도메인 속성에 대 한 **모니커 키를** 설정 합니다. 속성의 형식은 이어야 합니다 `string` .

    1. DSL 탐색기에서 **Xml Serialization Behavior\Class data \\ \<the domain class> \element data**를 확장 한 다음 도메인 속성을 선택 합니다.

    2. 속성 창에서 **모니커 키** 를로 설정 `true` 합니다.

- \- 또는 -

     **명명 된 도메인 클래스** 도구를 사용 하 여 새 도메인 클래스를 만듭니다.

     이 도구는 Name 이라는 도메인 속성을 포함 하는 새 클래스를 만듭니다. 는 **요소 이름이** 고이 도메인 속성의 **모니커 키** 속성은로 초기화 됩니다 `true` .

- \- 또는 -

     도메인 클래스에서 모니커 키 속성이 있는 다른 클래스로의 상속 관계를 만듭니다.

### <a name="avoid-duplicate-monikers"></a>중복 된 모니커 방지

정규화 된 키 모니커를 사용 하는 경우 사용자의 모델에 있는 두 요소의 키 속성 값이 동일할 수 있습니다. 예를 들어 DSL에 속성 이름이 있는 클래스 사용자가 있는 경우 사용자는 두 요소의 이름을 동일 하 게 설정할 수 있습니다. 모델을 파일에 저장할 수는 있지만 제대로 다시 로드 되지 않습니다.

이러한 상황을 방지 하는 데 도움이 되는 몇 가지 방법이 있습니다.

- Set **은**  =  `true` 키 도메인 속성의 요소 이름입니다. DSL 정의 다이어그램에서 도메인 속성을 선택 하 고 속성 창 값을 설정 합니다.

     사용자가 클래스의 새 인스턴스를 만들 때이 값을 사용 하면 도메인 속성에 다른 값이 자동으로 할당 됩니다. 기본 동작은 클래스 이름 끝에 번호를 추가 합니다. 이렇게 해도 사용자가 이름을 중복으로 변경할 수 있지만 모델을 저장 하기 전에 사용자가 값을 설정 하지 않는 경우에 유용 합니다.

- DSL에 대해 유효성 검사를 사용 하도록 설정 합니다. DSL 탐색기에서 Editor\Validation을 선택 하 고 **사용 ...** 속성을로 설정 합니다. `true`

     모호성을 확인 하는 자동으로 생성 된 유효성 검사 메서드가 있습니다. 메서드가 `Load` 유효성 검사 범주에 있습니다. 이렇게 하면 사용자에 게 파일을 다시 열 수 없다는 경고가 표시 됩니다.

     자세한 내용은 [도메인별 언어의 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)를 참조 하세요.

### <a name="moniker-paths-and-qualifiers"></a>모니커 경로 및 한정자

정규화 된 키 모니커는 모니커 키로 끝나며 포함 트리에서 부모의 모니커가 접두사로 추가 됩니다. 예를 들어, 앨범의 모니커가 다음과 같은 경우:

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

그러면 해당 앨범의 곡 중 하나가 다음이 될 수 있습니다.

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

그러나 앨범이 ID로 참조 되는 경우 모니커는 다음과 같습니다.

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

GUID는 고유 하기 때문에 부모의 모니커가 접두사로 붙지 않습니다.

특정 도메인 속성에 항상 모델 내에서 고유한 값이 있는 경우 해당 속성에 대해 **모니커 한정자** 를로 설정할 수 있습니다 `true` . 이렇게 하면 부모의 모니커를 사용 하지 않고 한정자로 사용 됩니다. 예를 들어 **모니커 한정자** 로 설정 하 고 앨범 클래스의 제목 도메인 속성에 대해 **모니커 키** 를 설정 하는 경우에는 모델의 이름 또는 식별자가 앨범 및 포함 된 자식에 대 한 모니커에 사용 되지 않습니다.

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>XML의 구조 사용자 지정

다음 사용자 지정을 수행 하려면 DSL 탐색기에서 **Xml Serialization 동작** 노드를 확장 합니다. 도메인 클래스에서 요소 데이터 노드를 확장 하 여이 클래스에서 소스인 속성 및 관계의 목록을 표시 합니다. 관계를 선택 하 고 속성 창의 옵션을 조정 합니다.

- **생략 요소** 를 true로 설정 하 여 소스 역할 노드를 생략 하 고 대상 요소 목록만 남겨 둡니다. 원본 클래스와 대상 클래스 간에 관계가 둘 이상 있는 경우에는이 옵션을 설정 하면 안 됩니다.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- **전체 형식 사용** 을 설정 하 여 관계 인스턴스를 나타내는 노드에 대상 노드를 포함 합니다. 도메인 관계에 도메인 속성을 추가 하면이 옵션이 자동으로 설정 됩니다.

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

- **Representation**  =  도메인 속성을 특성 값 대신 요소로 저장 하도록 표시**요소** 를 설정 합니다.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- 특성 및 관계가 serialize 되는 순서를 변경 하려면 요소 데이터 아래의 항목을 마우스 오른쪽 단추로 클릭 하 고 **위로 이동** 또는 **아래로 이동** 메뉴 명령을 사용 합니다.

## <a name="major-customization-using-program-code"></a>프로그램 코드를 사용 하 여 주요 사용자 지정

Serialization 알고리즘의 일부 또는 전체를 바꿀 수 있습니다.

**Dsl\generated Code\Serializer.cs** 및 **SerializationHelper.cs**의 코드를 검토 하는 것이 좋습니다.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>특정 클래스의 serialization을 사용자 지정 하려면

1. **Xml Serialization 동작**에서 해당 클래스에 대 한 노드의 설정이 **사용자 지정입니다** .

2. 모든 템플릿을 변환 하 고, 솔루션을 빌드하고, 결과 컴파일 오류를 조사 합니다. 각 오류 근처의 주석에는 제공 해야 하는 코드가 설명 되어 있습니다.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>전체 모델에 대 한 사용자 고유의 serialization을 제공 하려면

1. Dsl\GeneratedCode\SerializationHelper.cs의 Override 메서드

## <a name="options-in-xml-serialization-behavior"></a>Xml Serialization 동작의 옵션

DSL 탐색기에서 Xml Serialization 동작 노드에는 각 도메인 클래스, 관계, 셰이프, 연결선 및 다이어그램 클래스에 대 한 자식 노드가 포함 되어 있습니다. 각 노드 아래에는 해당 요소에서 원본으로 적용 되는 속성과 관계가 나열 됩니다. 관계는 자체의 해당 소스 클래스의 오른쪽에 표시 됩니다.

다음 표에서는 DSL 정의의이 섹션에서 설정할 수 있는 옵션을 요약 하 여 보여 줍니다. 각각의 경우에는 DSL 탐색기에서 요소를 선택 하 고 속성 창의 옵션을 설정 합니다.

### <a name="xml-class-data"></a>Xml 클래스 데이터

이러한 요소는 DSL 탐색기의 **Xml Serialization Behavior\Class 데이터**아래에 있습니다.

|속성|설명|
|-|-|
|사용자 지정 요소 스키마 있음|True 이면 도메인 클래스에 사용자 지정 요소 스키마가 있음을 나타냅니다.|
|사용자 지정|이 도메인 클래스에 대 한 사용자 고유의 serialization 및 deserialization 코드를 작성 하려면이를 **True** 로 설정 합니다.<br /><br /> 솔루션을 빌드하고 오류를 조사 하 여 자세한 지침을 검색 합니다.|
|도메인 클래스|이 클래스 데이터 노드가 적용 되는 도메인 클래스입니다. 읽기 전용입니다.|
|요소 이름|이 클래스의 요소에 대 한 Xml 노드 이름입니다. 기본값은 도메인 클래스 이름의 소문자 버전입니다.|
|모니커 특성 이름|참조를 포함 하기 위해 모니커 요소에 사용 되는 특성의 이름입니다. 비어 있는 경우 키 속성 또는 id의 이름이 사용 됩니다.<br /><br /> 이 예제에서는 "name"입니다.`<personMoniker name="/Mike Nash"/>`|
|모니커 요소 이름|이 클래스의 요소를 참조 하는 모니커에 사용 되는 xml 요소의 이름입니다.<br /><br /> 기본값은 소문자 버전의 클래스 이름에 "모니커"가 붙은 소문자 버전입니다. 예들 들어 `personMoniker`입니다.|
|모니커 유형 이름|이 클래스의 요소에 대 한 모니커에 대해 생성 된 xsd 형식의 이름입니다. XSD는 **Dsl\generated 코드 \\ \* 스키마 .xsd에 있습니다.**|
|직렬화 Id|True 이면 요소 GUID가 파일에 포함 됩니다. 이는 **모니커 키** 로 표시 된 속성이 없고 DSL이이 클래스에 대 한 참조 관계를 정의 하는 경우에 true 여야 합니다.|
|유형 이름|지정 된 도메인 클래스에서 xsd에 생성 된 xml 형식의 이름입니다.|
|메모|이 요소와 연결 된 비공식 메모입니다.|

### <a name="xml-property-data"></a>Xml 속성 데이터

Xml 속성 노드는 클래스 노드 아래에 있습니다.

|속성|설명|
|-|-|
|도메인 속성|Xml 직렬화 구성 데이터가 적용 되는 속성입니다. 읽기 전용입니다.|
|모니커 키|True 이면 속성이이 도메인 클래스의 인스턴스를 참조 하는 모니커를 만들기 위한 키로 사용 됩니다.|
|모니커 한정자|True 이면 속성을 사용 하 여 모니커에 한정자를 만듭니다. False 이면이 도메인 클래스에 대해 SerializeId가 true가 아닌 경우 포함 트리의 부모 요소 모니커에 의해 모니커가 한정 됩니다.|
|표현|특성이 인 경우 속성은 xml 특성으로 serialize 됩니다. if 요소는 요소로 serialize 됩니다. 무시 하면 serialize 되지 않습니다.|
|Xml 이름|속성을 나타내는 xml 특성 또는 요소에 사용 되는 이름입니다. 기본적으로 도메인 속성 이름의 소문자 버전입니다.|
|메모|이 요소와 연결 된 비공식 메모입니다.|

### <a name="xml-role-data"></a>Xml 역할 데이터

역할 데이터 노드는 원본 클래스 노드 아래에 있습니다.

|속성|설명|
|-|-|
|사용자 지정 모니커 있음|이 관계를 트래버스하는 모니커를 생성 및 확인 하는 사용자 고유의 코드를 제공 하려면이를 true로 설정 합니다.<br /><br /> 자세한 지침을 보려면 솔루션을 빌드한 다음 오류 메시지를 두 번 클릭 합니다.|
|도메인 관계|이러한 옵션이 적용 되는 관계를 지정 합니다. 읽기 전용입니다.|
|생략 요소|True 이면 원본 역할에 해당 하는 XML 노드가 스키마에서 생략 됩니다.<br /><br /> 원본 클래스와 대상 클래스 간에 둘 이상의 관계가 있는 경우이 역할 노드는 두 관계에 속하는 링크를 구분 합니다. 따라서이 경우에는이 옵션을 설정 하지 않는 것이 좋습니다.|
|역할 요소 이름|원본 역할에서 파생 된 XML 요소의 이름을 지정 합니다. 기본값은 role 속성 이름입니다.|
|전체 양식 사용|True 이면 각 대상 요소 또는 모니커가 관계를 나타내는 XML 노드에 포함 됩니다. 관계에 고유한 도메인 속성이 있는 경우이 속성을 true로 설정 해야 합니다.|

## <a name="see-also"></a>참고 항목

- [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)
