---
title: 도메인 특정 언어 사용자 지정
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b67a50623eb1924c4a18b57524c409f7eba6ab20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546876"
---
# <a name="write-code-to-customize-a-domain-specific-language"></a>도메인 특정 언어를 사용자 지정하는 코드 작성

이 섹션에서는 사용자 지정 코드를 사용 하 여 도메인 특정 언어로 모델을 액세스, 수정 또는 만드는 방법을 보여 줍니다.

DSL을 사용 하는 코드를 작성할 수 있는 몇 가지 컨텍스트가 있습니다.

- **사용자 지정 명령** 사용자가 다이어그램을 마우스 오른쪽 단추로 클릭 하 여 사용자가 호출할 수 있는 명령을 만들어 모델을 수정할 수 있습니다. 자세한 내용은 [방법: 바로 가기 메뉴에 명령 추가](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)를 참조 하세요.

- **유효성 검사** 모델이 올바른 상태 인지 확인 하는 코드를 작성할 수 있습니다. 자세한 내용은 [도메인별 언어의 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)를 참조 하세요.

- **기본 동작을 재정의 합니다.** Node.js에서 생성 되는 코드의 많은 부분을 수정할 수 있습니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.

- **텍스트 변환입니다.** 모델에 액세스 하 고 텍스트 파일을 생성 하는 코드를 포함 하는 텍스트 템플릿을 작성할 수 있습니다. 예를 들어 프로그램 코드를 생성할 수 있습니다. 자세한 내용은 [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)을 참조 하세요.

- **다른 Visual Studio 확장.** 모델을 읽고 수정 하는 별도의 VSIX 확장을 작성할 수 있습니다. 자세한 내용은 [방법: 프로그램 코드에서 파일을 통해 모델 열기](../modeling/how-to-open-a-model-from-file-in-program-code.md) 를 참조 하세요.

사용자가 정의 하는 클래스의 인스턴스는 *메모리 내 저장소* (IMS) 또는 *저장소*라고 하는 데이터 구조에 유지 됩니다. DSL에서 정의 하는 클래스는 항상 저장소를 생성자에 대 한 인수로 사용 합니다. 예를 들어 DSL이 예제 라는 클래스를 정의 하는 경우

`Example element = new Example (theStore);`

개체를 일반 개체와는 다른 방식으로 저장소에 유지 하면 여러 가지 이점이 있습니다.

- **트랜잭션**. 일련의 관련 된 변경 내용을 트랜잭션으로 그룹화 할 수 있습니다.

     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`

     `{`

     `// make several changes to Store elements here`

     `t.Commit();`

     `}`

     변경 하는 동안 예외가 발생 하 여 최종 커밋 ()이 수행 되지 않도록 저장소가 이전 상태로 다시 설정 됩니다. 이를 통해 오류가 모델을 일관 되지 않은 상태로 유지 하지 않도록 할 수 있습니다. 자세한 내용은 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)를 참조 하세요.

- **이진 관계**. 두 클래스 간의 관계를 정의 하는 경우 양쪽 끝의 인스턴스에 다른 끝으로 이동 하는 속성이 있습니다. 두 end는 항상 동기화 됩니다. 예를 들어 부모 및 자식 역할의 역할을 사용 하 여 parenthood 관계를 정의 하는 경우 다음을 작성할 수 있습니다.

     `John.Children.Add(Mary)`

     이제 다음 식이 모두 true입니다.

     `John.Children.Contains(Mary)`

     `Mary.Parents.Contains(John)`

     또한 다음을 작성 하 여 동일한 결과를 달성할 수 있습니다.

     `Mary.Parents.Add(John)`

     자세한 내용은 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)를 참조 하세요.

- **규칙 및 이벤트**. 지정 된 변경이 이루어질 때마다 발생 하는 규칙을 정의할 수 있습니다. 예를 들어 규칙을 사용 하 여 다이어그램에 표시 된 모델 요소를 사용 하 여 다이어그램의 셰이프를 최신 상태로 유지할 수 있습니다. 자세한 내용은 [변경 내용에 대 한 응답 및 전파](../modeling/responding-to-and-propagating-changes.md)를 참조 하세요.

- **Serialization**. 저장소는 포함 된 개체를 파일에 serialize 하는 표준 방법을 제공 합니다. Serialize 및 deserialize에 대 한 규칙을 사용자 지정할 수 있습니다. 자세한 내용은 [File Storage 및 XML Serialization 사용자 지정](../modeling/customizing-file-storage-and-xml-serialization.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보

- [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)