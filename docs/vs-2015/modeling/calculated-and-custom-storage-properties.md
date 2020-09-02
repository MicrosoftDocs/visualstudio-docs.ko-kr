---
title: 계산 된 저장소 속성 및 사용자 지정 저장소 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 372159a7405eb7a350aa55c55cf0c7e582dc98e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668365"
---
# <a name="calculated-and-custom-storage-properties"></a>계산된 스토리지 속성 및 사용자 지정 스토리지 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL (도메인별 언어)의 모든 도메인 속성은 다이어그램과 언어 탐색기에서 사용자에 게 표시 될 수 있으며 프로그램 코드에서 액세스할 수 있습니다. 그러나 속성은 값이 저장 되는 방식에 따라 달라 집니다.

## <a name="kinds-of-domain-properties"></a>도메인 속성의 종류
 DSL 정의에서 다음 표에 나열 된 것 처럼 도메인 속성의 **종류** 를 설정할 수 있습니다.

|도메인 속성 종류|설명|
|--------------------------|-----------------|
|**Standard** (기본값)|*저장소* 에 저장 되 고 파일로 serialize 되는 도메인 속성입니다.|
|**계산**|저장소에 저장 되지 않지만 다른 값에서 계산 되는 읽기 전용 도메인 속성입니다.<br /><br /> 예를 들어는 `Person.Age` 에서 계산할 수 있습니다 `Person.BirthDate` .<br /><br /> 계산을 수행 하는 코드를 제공 해야 합니다. 일반적으로 다른 도메인 속성의 값을 계산 합니다. 그러나 외부 리소스를 사용할 수도 있습니다.|
|**사용자 지정 저장소**|저장소에 직접 저장 되지 않지만 get 및 set 일 수 있는 도메인 속성입니다.<br /><br /> 값을 가져오고 설정 하는 메서드를 제공 해야 합니다.<br /><br /> 예를 들어,, `Person.FullAddress` 및에를 저장할 수 있습니다 `Person.StreetAddress` `Person.City` `Person.PostalCode` .<br /><br /> 예를 들어 데이터베이스에서 값을 가져오고 설정 하기 위해 외부 리소스에 액세스할 수도 있습니다.<br /><br /> 가 true 일 때 코드에서 저장소에 값을 설정 하면 안 됩니다 `Store.InUndoRedoOrRollback` . [트랜잭션 및 사용자 지정 setter](#setters)를 참조 하세요.|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>계산 된 저장소 속성 또는 사용자 지정 저장소 속성에 대 한 코드 제공
 도메인 속성의 종류를 계산 또는 사용자 지정 저장소로 설정 하는 경우 액세스 방법을 제공 해야 합니다. 솔루션을 빌드하면 오류 보고서에서 필요한 항목을 알려 줍니다.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>계산 된 저장소 속성 또는 사용자 지정 저장소 속성을 정의 하려면

1. DslDefinition. dsl의 다이어그램 또는 **Dsl 탐색기**에서 도메인 속성을 선택 합니다.

2. **속성** 창에서 **Kind** 필드를 **계산** 또는 **사용자 지정 저장소**로 설정 합니다.

     또한 해당 **형식을** 원하는 대로 설정 했는지 확인 합니다.

3. **솔루션 탐색기**도구 모음에서 **모든 템플릿 변환** 을 클릭 합니다.

4. **빌드** 메뉴에서 **솔루션 빌드**를 클릭합니다.

     다음 오류 메시지가 표시 됩니다. "*클래스* 에 '*속성*가져오기에 대 한 정의가 포함 되어 있지 않습니다."

5. 오류 메시지를 두 번 클릭 합니다.

     Dsl\GeneratedCode\DomainClasses.cs 또는 DomainRelationships.cs가 열립니다. 강조 표시 된 메서드 호출 위에서 주석에는*속성*가져오기 ()에 대 한 구현을 제공 하 라는 메시지가 표시 됩니다.

    > [!NOTE]
    > 이 파일은 DslDefinition. dsl에서 생성 됩니다. 이 파일을 편집 하는 경우 다음 번에 **모든 템플릿 변환**을 클릭 하면 변경 내용이 손실 됩니다. 대신, 필요한 메서드를 별도의 파일에 추가 합니다.

6. 별도의 폴더 (예: CustomCode YourDomainClass)에서 클래스 파일을 만들거나 엽니다 \\ *YourDomainClass*.

     네임 스페이스는 생성 된 코드의 네임 스페이스와 동일 해야 합니다.

7. 클래스 파일에서 도메인 클래스의 부분 구현을 작성 합니다. 클래스에서 `Get` 다음 예제와 유사한 누락 된 메서드에 대 한 정의를 작성 합니다.

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. **Kind** 를 **사용자 지정 저장소**로 설정 하는 경우에도 메서드를 제공 해야 `Set` 합니다. 예를 들면 다음과 같습니다.

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     가 true 일 때 코드에서 저장소에 값을 설정 하면 안 됩니다 `Store.InUndoRedoOrRollback` . [트랜잭션 및 사용자 지정 setter](#setters)를 참조 하세요.

9. 솔루션을 빌드하고 실행합니다.

10. 속성을 테스트 합니다. **실행 취소** 및 **다시 실행**을 시도해 야 합니다.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> 트랜잭션 및 사용자 지정 Setter
 메서드가 일반적으로 활성 트랜잭션 내에서 호출 되기 때문에 사용자 지정 저장소 속성의 Set 메서드에서는 트랜잭션을 열 필요가 없습니다.

 그러나 사용자가 실행 취소 또는 다시 실행을 호출 하거나 트랜잭션을 롤백하는 경우에는 Set 메서드를 호출할 수도 있습니다. <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A>이 true 이면 Set 메서드가 다음과 같이 동작 해야 합니다.

- 다른 도메인 속성에 값을 할당 하는 것과 같이 저장소에서 변경 하지 않아야 합니다. 실행 취소 관리자가 해당 값을 설정 합니다.

- 그러나 데이터베이스 또는 파일 내용과 같은 외부 리소스 또는 저장소 외부의 개체를 업데이트 해야 합니다. 이렇게 하면 synchronism에 저장 된 값으로 유지 됩니다.

  예를 들면 다음과 같습니다.

```
void SetAgeValue(int value)
{
  // If we are in Undo, no changes to Store objects:
  if (!this.Store.InUndoRedoOrRollback)
  {
    this.BirthYear = System.DateTime.Today.Year - value;
  }
  // But always update external objects:
  System.IO.File.WriteAllText(AgeFile, value);
}
```

 트랜잭션에 대 한 자세한 내용은 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md) [도메인 속성의 속성](../modeling/properties-of-domain-properties.md) [도메인 특정 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)
