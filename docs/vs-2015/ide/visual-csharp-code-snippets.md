---
title: Visual C# 코드 조각 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fb84854bd871277f680a753b28c17e3429283928
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646716"
---
# <a name="visual-c-code-snippets"></a>Visual C# 코드 조각
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 조각은 신속하게 코드에 삽입할 수 있는 준비된 코드 조각입니다. 예를 들어 `for` 코드 조각에서는 비어 있는 `for` 루프를 만듭니다. 일부 코드 조각은 코드 감싸기 코드 조각으로, 코드 줄을 선택한 다음 선택한 코드 줄을 통합하는 코드 조각을 선택할 수 있습니다. 예를 들어 코드 줄을 선택한 다음 `for` 코드 조각을 활성화하는 경우 루프 블록 안에 해당 코드 줄을 포함하여 `for` 루프를 만듭니다. 코드 조각을 사용하면 빠르고 쉽게, 안정적으로 프로그램 코드를 작성할 수 있습니다.

 커서 위치에 코드 조각을 삽입하거나, 현재 선택한 코드 주위에 코드 감싸기 코드 조각을 삽입할 수 있습니다. 코드 조각 삽입기는 **IntelliSense** 메뉴의 **코드 조각 삽입** 또는 **코드 감싸기** 명령을 통해 또는 바로 가기 키 Ctrl+K, X 또는 Ctrl+K, S를 차례로 각각 사용하여 호출됩니다.

 코드 조각 삽입기에 사용 가능한 모든 코드 조각에 대한 코드 조각 이름이 표시됩니다. 또한 코드 조각 삽입기에는 코드 조각의 이름이나 코드 조각 이름의 일부를 입력할 수 있는 입력 대화 상자가 포함되어 있습니다. 코드 조각 삽입기에서 코드 조각 이름과 가장 일치하는 항목이 강조 표시됩니다. 언제든지 Tab 키를 누르면 코드 조각 삽입기가 해제되고 현재 선택한 코드 조각이 삽입됩니다. Esc 키를 입력하거나 코드 편집기에서 마우스를 클릭하면 코드 조각을 삽입하지 않고 코드 조각 삽입기가 해제됩니다.

## <a name="default-code-snippets"></a>기본 코드 조각
 기본적으로 다음 코드 조각이 Visual Studio에 포함되어 있습니다.

|이름(또는 바로 가기)|Description|코드 조각을 삽입할 수 있는 유효 위치|
|--------------------------|-----------------|---------------------------------------|
|#if|[#if](https://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) 지시문과 [#endif](https://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05) 지시문을 만듭니다.|원하는 위치|
|#region|[#region](https://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) 지시문과 [#endregion](https://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526) 지시문을 만듭니다.|원하는 위치|
|~|포함하는 클래스에 대한 소멸자를 만듭니다.|클래스 내부|
|attribute|<xref:System.Attribute>에서 파생되는 클래스에 대한 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|선택|[checked](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|class|class 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|ctor|포함하는 클래스에 대한 생성자를 만듭니다.|클래스 내부|
|cw|<xref:System.Console.WriteLine%2A> 호출을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|do|[Do](https://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb) `while` 루프를 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|else|[else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|enum|[enum](https://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c) 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|equals|<xref:System.Object> 클래스에 정의된 <xref:System.Object.Equals%2A> 메서드를 재정의하는 메서드 선언을 만듭니다.|클래스 또는 구조체 내부|
|exception|예외(기본적으로 <xref:System.Exception>)에서 파생되는 클래스에 대한 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|for|[for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) 루프를 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|foreach|[foreach](https://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec) 루프를 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|forr|각 반복 후에 루프 변수가 감소하는 [for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) 루프를 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|if|[if](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|인덱서|indexer 선언을 만듭니다.|클래스 또는 구조체 내부|
|인터페이스|[interface](https://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|호출|안전하게 이벤트를 호출하는 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|iterator|반복기를 만듭니다.|클래스 또는 구조체 내부|
|iterindex|중첩된 클래스를 사용하여 "명명된" 반복기 및 인덱서 쌍을 만듭니다.|클래스 또는 구조체 내부|
|lock|[lock](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|mbox|<xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> 호출을 만듭니다. System.Windows.Forms.dll에 대한 참조를 추가해야 할 수도 있습니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|네임스페이스|[namespace](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함) 내부|
|prop|[자동 구현 속성](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) 선언을 만듭니다.|클래스 또는 구조체 내부|
|propfull|get 및 set 접근자를 사용하여 속성 선언을 만듭니다.|클래스 또는 구조체 내부|
|propg|전용 "set" 접근자를 사용하여 읽기 전용 [자동 구현 속성](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7)을 만듭니다.|클래스 또는 구조체 내부|
|sim|[static](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[int](https://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52) Main 메서드 선언을 만듭니다.|클래스 또는 구조체 내부|
|struct|[struct](https://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c) 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|svm|[static](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[void](https://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4) Main 메서드 선언을 만듭니다.|클래스 또는 구조체 내부|
|스위치|[switch](https://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|다음을 시도해 보세요.|[try-catch](https://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|tryf|[try-finally](https://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|선택 취소|[unchecked](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|unsafe|[unsafe](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|사용|[using](https://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8) 지시문을 만듭니다.|네임스페이스(전역 네임스페이스 포함) 내부|
|while|[while](https://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59) 루프를 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|

## <a name="see-also"></a>관련 항목
 [코드 조각 함수](../ide/code-snippet-functions.md) [코드 조각](../ide/code-snippets.md) 방법: 대체 [템플릿 매개 변수](../ide/template-parameters.md) 를 사용 하 [여 새 코드 조각 만들기](https://msdn.microsoft.com/8d56d43c-097a-475b-aa85-cae1554b6338) [방법: 코드 감싸기 코드 조각 사용](../ide/how-to-use-surround-with-code-snippets.md) [방법: c # 리팩터링](../ide/how-to-restore-csharp-refactoring-snippets.md) 코드 조각 복원
