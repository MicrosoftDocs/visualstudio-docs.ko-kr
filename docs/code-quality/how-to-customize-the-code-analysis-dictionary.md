---
title: '방법: 코드 분석 사전 사용자 지정'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1a50374a2603153cc7f4770a9aaf5ba72fbe007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87453646"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>방법: 코드 분석 사전 사용자 지정

코드 분석에서는 기본 제공 사전을 사용 하 여 코드에서 코드의 식별자를 검사 하 여 철자, 문법적 사례 및 .NET 디자인 지침의 다른 명명 규칙에서 오류를 확인 합니다. 사용자 지정 사전 Xml 파일을 만들어 용어, 약어 및 머리글자어를 기본 제공 사전에 추가, 제거 또는 수정할 수 있습니다.

예를 들어 코드에 **DoorKnokker**이라는 클래스가 포함 되어 있다고 가정 합니다. 코드 분석에서는 두 단어 ( **문** 및 **knokker**)의 복합형로 이름을 식별 합니다. 그러면 **knokker** 의 철자가 잘못 되었다는 경고가 발생 합니다. 코드 분석에서 철자를 인식할 수 있도록 하려면 **knokker** 이라는 용어를 사용자 지정 사전에 추가 합니다.

## <a name="to-create-a-custom-dictionary"></a>사용자 지정 사전을 만들려면

**CustomDictionary.xml**라는 파일을 만듭니다.

다음 XML 구조를 사용 하 여 사용자 지정 단어를 정의 합니다.

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>사용자 지정 사전 요소

사용자 지정 사전에서 다음 요소의 내부 텍스트로 용어를 추가 하 여 코드 분석 사전의 동작을 수정할 수 있습니다.

- [사전/단어/인식/단어](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [사전/단어/인식할 수 없음/단어](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [사전/단어/사용 되지 않음/용어 [ @PreferredAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [사전/단어/복합/단어 [ @CompoundAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dictionary/Words/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [사전/머리글자어/CasingExceptions/머리글자어](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="dictionarywordsrecognizedword"></a><a name="BKMK_DictionaryWordsRecognizedWord"></a> 사전/단어/인식/단어

코드 분석이 올바른 철자를 식별 하는 용어 목록에 용어를 포함 하려면 용어를 사전/단어/인식/단어 요소의 내부 텍스트로 추가 합니다. Dictionary/Words/인식할 수 있는/Word 요소의 용어는 대/소문자를 구분 하지 않습니다.

**예제**

```xml
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>
```

사전/단어/인식할 수 있는 노드의 용어는 다음 코드 분석 규칙에 적용 됩니다.

- [CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1701.md)

- [CA1702: 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1702.md)

- [CA1703: 리소스 문자열에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1703.md)

- [CA1704: 식별자에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1704.md)

- [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709.md)

- [CA1726: 기본 설정 용어를 사용하세요.](../code-quality/ca1726.md)

- [CA2204: 리터럴의 맞춤법이 정확해야 합니다.](../code-quality/ca2204.md)

### <a name="dictionarywordsunrecognizedword"></a><a name="BKMK_DictionaryWordsUnrecognizedWord"></a> 사전/단어/인식할 수 없음/단어

코드 분석이 올바른 철자를 식별 하는 용어 목록에서 용어를 제외 하려면 a s o/Words/인식할 수 없는/Word 요소의 내부 텍스트로 제외할 용어를 추가 합니다. 사전/단어/인식할 수 없는/Word 요소의 용어는 대/소문자를 구분 하지 않습니다.

**예제**

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>
```

사전/단어/인식할 수 없는 노드의 용어는 다음 코드 분석 규칙에 적용 됩니다.

- [CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1701.md)

- [CA1702: 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1702.md)

- [CA1703: 리소스 문자열에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1703.md)

- [CA1704: 식별자에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1704.md)

- [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709.md)

- [CA1726: 기본 설정 용어를 사용하세요.](../code-quality/ca1726.md)

- [CA2204: 리터럴의 맞춤법이 정확해야 합니다.](../code-quality/ca2204.md)

### <a name="dictionarywordsdeprecatedtermpreferredalternate"></a><a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> 사전/단어/사용 되지 않음/용어 [ @PreferredAlternate ]

코드 분석이 더 이상 사용 되지 않는 것으로 식별 하는 용어 목록에 용어를 포함 하려면 용어를 사전/단어/사용 되지 않음/기간 요소의 내부 텍스트로 추가 합니다. 사용 되지 않는 용어는 철자가 올바르지만 사용 하면 안 되는 단어입니다.

경고에 제안 된 대체 단어를 포함 하려면 Term 요소의 PreferredAlternate 특성에 대체를 지정 합니다. 대체를 제안 하지 않으려는 경우 특성 값을 비워 둘 수 있습니다.

- 사전/단어/사용 되지 않음/조건 요소에서 사용 되지 않는 용어는 대/소문자를 구분 하지 않습니다.

- PreferredAlternate 특성 값은 대/소문자를 구분 합니다. 복합 대체 (파스칼식)의 경우를 사용 합니다.

**예제**

```xml
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>
```

사전/단어/사용 되지 않는 노드의 용어는 다음 코드 분석 규칙에 적용 됩니다.

- [CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1701.md)

- [CA1702: 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1702.md)

- [CA1703: 리소스 문자열에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1703.md)

- [CA1704: 식별자에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1704.md)

- [CA1726: 기본 설정 용어를 사용하세요.](../code-quality/ca1726.md)

### <a name="dictionarywordscompoundtermcompoundalternate"></a><a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> 사전/단어/복합/단어 [ @CompoundAlternate ]

기본 제공 사전은 일부 용어를 복합 용어가 아닌 단일 불연속 용어로 식별 합니다. 코드 분석이 복합 단어로 식별 하는 용어 목록에 용어를 포함 하 고 용어의 정확한 대/소문자를 지정 하려면 용어를 사전/단어/복합/용어 요소의 내부 텍스트로 추가 합니다. Term 요소의 CompoundAlternate 특성에서 개별 단어의 첫 글자를 대문자로 하 여 복합 용어를 구성 하는 개별 단어를 지정 합니다 (파스칼식 대/소문자). 내부 텍스트에 지정 된 용어는 Dictionary/Words/DiscreteExceptions 목록에 자동으로 추가 됩니다.

- Dictionary/Words/복합/용어 요소의 복합 용어는 대/소문자를 구분 하지 않습니다.

- CompoundAlternate 특성 값은 대/소문자를 구분 합니다. 복합 대체 (파스칼식)의 경우를 사용 합니다.

**예제**

```xml
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>
```

사전/단어/복합 노드의 용어는 다음 코드 분석 규칙에 적용 됩니다.

- [CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1701.md)

- [CA1702: 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1702.md)

- [CA1703: 리소스 문자열에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1703.md)

- [CA1704: 식별자에는 정확한 철자를 사용해야 합니다.](../code-quality/ca1704.md)

### <a name="dictionarywordsdiscreteexceptionsterm"></a><a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionary/Words/DiscreteExceptions/Term

복합 단어에 대 한 대/소문자 규칙에 따라 용어를 확인할 때 코드 분석이 단일의 불연속 단어로 식별 하는 용어 목록에서 용어를 제외 하려면 용어를 Dictionary/Words/DiscreteExceptions/Term 요소의 내부 텍스트로 추가 합니다. Dictionary/Words/DiscreteExceptions/Term 요소의 용어는 대/소문자를 구분 하지 않습니다.

**예제**

```xml
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>
```

Dictionary/Words/DiscreteExceptions 노드의 용어는 다음 코드 분석 규칙에 적용 됩니다.

- [CA1701: 리소스 문자열 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1701.md)

- [CA1702: 복합 단어는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1702.md)

### <a name="dictionaryacronymscasingexceptionsacronym"></a><a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> 사전/머리글자어/CasingExceptions/머리글자어

코드 분석이 올바른 철자를 확인 하는 용어 목록에 머리글자어를 포함 하 고 복합 단어에 대 한 대/소문자 규칙에 따라 용어를 선택 하는 방법을 표시 하려면 용어를 Dictionary/머리글자어/CasingExceptions/머리글자어 요소의 내부 텍스트로 추가 합니다. Dictionary/머리글자어/CasingExceptions/머리글자어 요소의 머리글자어는 대/소문자를 구분 합니다.

**예제**

```xml
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>
```

Dictionary/머리글자어/CasingExceptions 노드의 용어는 다음 코드 분석 규칙에 적용 됩니다.

- [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709.md)

## <a name="to-apply-a-custom-dictionary-to-a-project"></a><a name="BKMK_ToApplyACustomDictionaryToAProject"></a> 프로젝트에 사용자 지정 사전을 적용 하려면

1. **솔루션 탐색기**에서 다음 절차 중 하나를 사용 합니다.

    - 단일 프로젝트에 사전을 추가 하려면 프로젝트 이름을 마우스 오른쪽 단추로 클릭 한 다음 **기존 항목 추가**를 클릭 합니다. **기존 항목 추가** 대화 상자에서 파일을 지정 합니다.
  
    - 둘 이상의 프로젝트 간에 공유 되는 사전을 추가 하려면 **기존 항목 추가** 대화 상자에서 공유할 파일을 찾고 **추가** 단추에서 아래쪽 화살표를 클릭 한 다음 **링크로 추가**를 클릭 합니다.

2. **솔루션 탐색기**에서 **CustomDictionary.xml** 파일 이름을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 클릭 합니다.

3. **빌드 작업** 목록에서 **CodeAnalysisDictionary**를 선택 합니다.

4. **출력 디렉터리에 복사** 목록에서 **복사 안 함**을 선택 합니다.
