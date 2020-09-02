---
title: 소스 비 표시 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 63d405b0e62735c0c1e3d7bb716ea2db29bc19fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651570"
---
# <a name="in-source-suppression-overview"></a>ISS 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

소스 비 표시 제거는 위반을 발생 시키는 코드 세그먼트에 **SuppressMessage** 특성을 추가 하 여 관리 코드에서 코드 분석 위반을 억제 하거나 무시 하는 기능입니다. **SuppressMessage** 특성은 컴파일 시간에 CODE_ANALYSIS 컴파일 기호가 정의 된 경우에만 관리 코드 어셈블리의 IL 메타 데이터에 포함 되는 조건부 특성입니다.

 C++/CLI에서 CA_SUPPRESS_MESSAGE 또는 CA_GLOBAL_SUPPRESS_MESSAGE 매크로를 헤더 파일에 사용하여 특성을 추가합니다.

 소스 비 표시 제거 메타 데이터를 실수로 전달 하지 않도록 릴리스 빌드에서 소스 비 표시 오류를 사용 하면 안 됩니다. 원본 비 표시 제거의 처리 비용으로 인해 원본 비 표시 메타 데이터를 포함 하 여 응용 프로그램의 성능이 저하 될 수도 있습니다.

> [!NOTE]
> 이러한 특성을 직접 코딩할 필요가 없습니다. 자세한 내용은 [방법: 메뉴 항목을 사용 하 여 경고 표시 안 함](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)을 참조 하세요. 메뉴 항목은 c + + 코드에 사용할 수 없습니다.

## <a name="suppressmessage-attribute"></a>SuppressMessage 특성
 **오류 목록** 에서 코드 분석 경고를 마우스 오른쪽 단추로 클릭 한 다음 **메시지 표시 안 함**을 클릭 하면 코드 또는 프로젝트의 전역 비 표시 오류 (Suppression) 파일에 **SuppressMessage** 특성이 추가 됩니다.

 **SuppressMessage** 특성의 형식은 다음과 같습니다.

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]

```

 [C++]

```
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")

```

 위치:

- **규칙 범주** -규칙이 정의 된 범주입니다. 코드 분석 규칙 범주에 대 한 자세한 내용은 [관리 코드 경고에 대 한 코드 분석](../code-quality/code-analysis-for-managed-code-warnings.md)을 참조 하세요.

- **규칙 Id** -규칙의 식별자입니다. 지원에는 규칙 식별자에 대 한 짧은 이름과 긴 이름이 모두 포함 됩니다. 약식 이름은 CAXXXX입니다. 긴 이름은 CAXXXX: FriendlyTypeName입니다.

- **근거** -메시지를 표시 하지 않는 이유를 문서화 하는 데 사용 되는 텍스트입니다.

- **메시지 Id** -각 메시지의 문제에 대 한 고유 식별자입니다.

- **범위** -경고가 표시 되지 않는 대상입니다. 대상이 지정 되지 않은 경우 특성의 대상으로 설정 됩니다. 지원 되는 범위는 다음과 같습니다.

  - 모듈

  - 네임스페이스

  - 리소스

  - 형식

  - 멤버

- **대상** -경고를 표시 하지 않을 대상을 지정 하는 데 사용 되는 식별자입니다. 정규화 된 항목 이름을 포함 해야 합니다.

## <a name="suppressmessage-usage"></a>SuppressMessage 사용
 **SuppressMessage** 특성의 인스턴스가 적용 되는 수준에서 코드 분석 경고가 표시 되지 않습니다. 이는 위반이 발생 하는 코드에 비 표시 정보를 긴밀 하 게 두는 것입니다.

 일반 표시 형식에는 규칙 범주와 규칙 이름에 대 한 사람이 읽을 수 있는 선택적 표현이 포함 된 규칙 식별자가 포함 되어 있습니다. 예를 들면 다음과 같습니다.

 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

 원본 비 표시 메타 데이터를 최소화 하는 엄격한 성능상의 이유가 있는 경우 규칙 이름 자체를 남겨둘 수 있습니다. 규칙 범주와 해당 규칙 ID는 모두 충분히 고유한 규칙 식별자를 구성 합니다. 예를 들면 다음과 같습니다.

 `[SuppressMessage("Microsoft.Design", "CA1039")]`

 유지 관리 문제 때문에이 형식을 권장 하지 않습니다.

## <a name="suppressing-multiple-violations-within-a-method-body"></a>메서드 본문 내에서 여러 위반 표시 안 함
 특성은 메서드에만 적용 될 수 있으며 메서드 본문에 포함할 수 없습니다. 그러나 메서드 내에서 여러 위반 발생을 구분 하기 위해 식별자를 메시지 ID로 지정할 수 있습니다.

 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]

## <a name="generated-code"></a>생성된 코드
 관리 코드 컴파일러와 일부 타사 도구는 코드를 신속 하 게 개발 하는 코드를 생성 합니다. 소스 파일에 표시 되는 컴파일러 생성 코드는 일반적으로 **Generatedcodeattribute** 특성으로 표시 됩니다.

 생성 된 코드에 대 한 코드 분석 경고 및 오류를 표시 하지 않을 지 여부를 선택할 수 있습니다. 이러한 경고 및 오류를 표시 하지 않는 방법에 대 한 자세한 내용은 [방법: 생성 된 코드에 대 한 경고 표시 안 함](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)을 참조 하세요.

 코드 분석은 전체 어셈블리나 단일 매개 변수에 적용 될 때 **Generatedcodeattribute** 를 무시 합니다. 이러한 상황은 거의 발생 하지 않습니다.

## <a name="global-level-suppressions"></a>전역 수준 비 표시 오류
 관리 코드 분석 도구는 어셈블리, 모듈, 형식, 멤버 또는 매개 변수 수준에서 적용 되는 **SuppressMessage** 특성을 검사 합니다. 리소스와 네임 스페이스에 대 한 위반도 발생 시킵니다. 이러한 위반은 전역 수준에서 적용 해야 하며 범위 지정 및 대상 지정이 가능 합니다. 예를 들어 다음 메시지는 네임 스페이스 위반을 억제 합니다.

 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> 네임 스페이스 범위를 사용 하 여 경고를 표시 하지 않으면 네임 스페이스 자체에 대해 경고를 표시 하지 않습니다. 네임 스페이스 내의 형식에 대해 경고를 표시 하지 않습니다.

 명시적 범위를 지정 하 여 모든 억제를 표현할 수 있습니다. 이러한 비 표시 오류는 전역 수준에서 지속 되어야 합니다. 형식을 데코레이팅하 면 멤버 수준 제거를 지정할 수 없습니다.

 전역 수준 비 표시 오류는 명시적으로 제공 된 사용자 소스에 매핑되지 않는 컴파일러 생성 코드를 참조 하는 메시지를 표시 하지 않는 유일한 방법입니다. 예를 들어 다음 코드는 컴파일러에서 내보낸 생성자에 대 한 위반을 억제 합니다.

 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> 대상에는 항상 정규화 된 항목 이름이 포함 됩니다.

## <a name="global-suppression-file"></a>전역 비 표시 파일
 전역 비 표시 오류 (suppression) 파일은 대상을 지정 하지 않는 전역 수준 비 표시 오류 (suppression) 또는 비 표시 오류 (suppression)를 유지 합니다. 예를 들어 어셈블리 수준 위반에 대 한 비 표시 오류는이 파일에 저장 됩니다. 또한 일부 ASP.NET 비 표시 오류는이 파일에 저장 됩니다 .이는 프로젝트 수준 설정을 폼의 코드에 사용할 수 없기 때문입니다. 오류 목록 창에서 **메시지 표시 안 함** 명령의 **Project 비 표시 오류 (suppression) 파일** 옵션을 처음으로 선택 하면 전역 비 표시 제거가 만들어지고 프로젝트에 추가 됩니다. 자세한 내용은 [방법: 메뉴 항목을 사용 하 여 경고 표시 안 함](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 <xref:System.Diagnostics.CodeAnalysis>
