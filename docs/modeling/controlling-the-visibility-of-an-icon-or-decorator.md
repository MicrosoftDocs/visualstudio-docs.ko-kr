---
title: 아이콘 또는 데코레이터의 가시성 제어
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d2082f7e26d3e335ed88bbced0f59d6d6c4780c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546648"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>아이콘 또는 데코레이터의 가시성 제어
*데코레이터* 는 DSL (도메인별 언어)의 셰이프에 나타나는 아이콘이 나 텍스트 줄입니다. 모델의 속성 상태에 따라 데코레이터를 표시 하 고 사라지게 할 수 있습니다. 예를 들어 사람을 나타내는 도형에서 사용자의 성별, 자녀 수 등에 따라 다른 아이콘이 표시 될 수 있습니다.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>아이콘 또는 데코레이터의 표시 유형 제어
 다음 절차에서는 사용자가 셰이프 및 도메인 클래스에 대 한 매핑을 이미 정의 했다고 가정 합니다. 자세한 내용은 [도메인별 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)을 참조 하세요.

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>아이콘 또는 텍스트 데코레이터의 표시 유형을 제어 하려면

1. DSL 정의 다이어그램에서 표시 하려는 아이콘 또는 텍스트 데코레이터 셰이프 클래스에를 추가 합니다.

   1. Shape 클래스를 마우스 오른쪽 단추로 클릭 하 고 **추가**를 가리킨 다음 원하는 데코레이터 형식을 클릭 합니다.

   2. 데코레이터의 **Position** 속성을 설정 합니다. 둘 이상의 데코레이터 위치가 같을 수 있습니다. 예를 들어 동일한 위치를 공유 하는 남성 및 여성 아이콘이 있을 수 있습니다.

   3. 아이콘 데코레이터의 **기본 아이콘** 속성을 설정 합니다.

2. DSL 정의 다이어그램에서 모양 클래스와 도메인 클래스 사이의 회색 선 인 다이어그램 요소 맵을 선택 합니다.

3. DSL 정보 창의 **데코레이터 맵** 탭에서 데코레이터를 선택 합니다. 예를 들면 MaleDecorator입니다.

4. **표시 유형 필터** 상자를 선택 합니다.

5. 표시 여부를 제어 해야 하는 도메인 속성이 직계 도메인 클래스에 있는 경우 **필터 속성의 경로** 를 비워 둡니다.

    그렇지 않으면 드롭다운 메뉴를 클릭 하 고 속성이 있는 관계 또는 클래스로 이동 합니다.

   - 오류 보고서를 방지 하려면 탐색 도구에서 "*"로 표시 된 관계를 탐색 하면 안 됩니다.

6. **필터 속성** 을 도메인 속성으로 설정 합니다. 예: 성별.

7. **표시 유형 항목** 목록에서 데코레이터를 표시할이 도메인 속성의 값을 추가 합니다. 예: 남성.

8. 각 아이콘에 대해 단계를 반복 합니다.

9. **모든 템플릿을 변환**하 고, 빌드 및 실행 하 고, 테스트 다이어그램을 엽니다.

10. 제어 속성 값을 변경 하면 데코레이터 표시 되 고 사라집니다.

    간단한 값 집합 보다 더 복잡 한 수식으로 표시 여부를 제어 하는 경우가 많습니다. 예를 들어 특정 형식의 링크 수에 따라 아이콘을 사용 하거나 숫자가 특정 범위에 있는지 여부에 따라 달라 지도록 지정 합니다. 이 경우 다음 절차를 사용 합니다.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>수식을 기준으로 데코레이터의 표시 여부를 제어 하려면

1. 도메인 클래스에 계산 된 도메인 속성을 추가 합니다. **속성** 창에서 다음 값을 설정 합니다.

     **Isbrowsable 때 =** `False` **-사용자의 속성을 숨깁니다** .    

     **Kind =** `Calculated` **-값을 계산 하는 코드를 제공** 합니다.    

     **이름** 예: **DecoratorControl**

     **입력할** = `Boolean`

     자세한 내용은 [계산 된 저장소 속성 및 사용자 지정 저장소 속성](../modeling/calculated-and-custom-storage-properties.md)을 참조 하세요.

2. 새 속성이 데코레이터 표시 유형을 컨트롤로 만듭니다.

    1. 도메인 클래스에서 셰이프에 대 한 회색 선 인 다이어그램 요소 맵을 선택 합니다. **DSL 세부 정보** 창에서 **DecoratorMap** 탭을 엽니다.

    2. **표시 유형 필터** 상자를 선택 합니다.

    3. **필터 속성**에서 컨트롤 속성 **DecoratorControl**를 선택 합니다.

    4. **표시 유형 항목**아래에을 입력 `True` 합니다.

3. **솔루션 탐색기** 도구 모음에서 **모든 템플릿 변환** 을 클릭 합니다.

4. **빌드** 메뉴에서 **솔루션 빌드** 를 클릭 합니다.

5. "해당*클래스* 에 GetDecoratorControlValue에 대 한 정의가 포함 되어 있지 않습니다." 라는 오류 보고서를 두 번 클릭 합니다.

     텍스트 편집기가 Dsl\GeneratedCode\DomainClasses.cs.에서 열립니다. 강조 표시 된 오류는 메서드를 추가 하도록 요청 하는 주석입니다.

6. 누락 된 네임 스페이스, 클래스 및 메서드를 확인 합니다.  예를 들면 FamilyTree. GetDecoratorControlValue ()입니다.

7. 별도의 코드 파일에서 누락 된 메서드를 포함 하는 partial 클래스 정의를 작성 합니다. 예를 들면 다음과 같습니다.

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     프로그램 코드를 사용 하 여 모델을 사용자 지정 하는 방법에 대 한 자세한 내용은 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)를 참조 하세요.

8. 솔루션을 다시 빌드하고 실행 합니다.

## <a name="see-also"></a>추가 정보

- [모양 및 연결선 정의](../modeling/defining-shapes-and-connectors.md)
- [다이어그램에 배경 이미지 설정](../modeling/setting-a-background-image-on-a-diagram.md)
- [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [도메인별 언어를 사용자 지정하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)