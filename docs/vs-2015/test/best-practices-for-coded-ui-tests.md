---
title: 코딩된 UI 테스트에 대한 모범 사례 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 41
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2dffebeaa0349c149e319d20794f8b065baa5647
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660682"
---
# <a name="best-practices-for-coded-ui-tests"></a>최선의 코딩된 UI 테스트 방법
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 코딩된 UI 테스트를 개발할 때 따라야 할 모범 사례를 설명합니다.

 **요구 사항**

- Visual Studio Enterprise

## <a name="best-practices"></a>모범 사례
 유연한 코딩된 UI 테스트를 만들려면 다음 지침을 따르세요.

- 가능한 한 **코딩된 UI 테스트 빌더**를 사용합니다.

- `UIMap.designer.cs` 파일을 직접 수정하지 마세요. 수정하면 파일에 대한 변경 내용을 덮어씁니다.

- 기록된 메서드의 시퀀스로 테스트를 만듭니다. 메서드를 기록하는 방법에 대한 자세한 내용은 [코딩된 UI 테스트](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)를 참조하세요.

- 기록된 각 메서드는 단일 페이지, 폼 또는 대화 상자에서 작동해야 합니다. 각각의 새 페이지, 폼 또는 대화 상자에 대해 새 테스트 메서드를 만듭니다.

- 메서드를 만들 때 기본 이름 대신 의미 있는 메서드 이름을 사용합니다. 의미 있는 이름은 메서드의 용도를 식별하는 데 도움이 됩니다.

- 가능하면 기록된 각 메서드를 10개 미만의 작업으로 제한합니다. 이 모듈식 방법을 사용하면 UI가 변경될 경우 메서드를 쉽게 바꿀 수 있습니다.

- `UIMap.Designer.cs` 파일에 어설션 메서드를 자동으로 추가하는 **코딩된 UI 테스트 빌더**를 사용하여 각 어설션을 만듭니다.

- UI(사용자 인터페이스)가 변경되면 테스트 메서드 또는 어설션 메서드를 다시 기록하거나 기존 테스트 메서드의 영향을 받는 섹션을 다시 기록합니다.

- 테스트 대상 애플리케이션의 각 모듈에 대해 별도 [UIMap](/previous-versions/dd580454(v=vs.140)) 파일을 만듭니다. 자세한 내용은 [여러 UI 맵이 포함된 대형 애플리케이션 테스트](../test/testing-a-large-application-with-multiple-ui-maps.md)를 참조하세요.

- 테스트 대상 애플리케이션에서 UI 컨트롤을 만들 때 의미 있는 이름을 사용합니다. 이렇게 하면 자동으로 생성된 컨트롤 이름에 더 많은 의미와 유용성이 제공됩니다.

- API로 코딩 하 여 어설션을 만드는 경우 파일에 있는 [UIMap](/previous-versions/dd580454(v=vs.140)) 클래스 부분에 각 어설션에 대 한 메서드를 만듭니다 `UIMap.cs` . 어설션을 실행하려면 테스트 메서드에서 이 메서드를 호출합니다.

- API로 직접 코딩하는 경우 `UIMap.Designer.cs` 파일에 생성된 클래스의 속성 및 메서드를 코드에서 가능한 한 많이 사용합니다. 이러한 클래스는 작업을 더 쉽고 안정적으로 만들며 생산성 향상에 도움이 됩니다.

  코딩된 UI 테스트는 사용자 인터페이스의 여러 변경 내용에 맞게 자동으로 조정됩니다. 예를 들어 UI 요소의 위치 또는 색이 변경된 경우에도 대체로 코딩된 UI 테스트에서 올바른 요소를 찾습니다.

  테스트 실행 중에 테스트 프레임워크가 **코딩된 UI 테스트 빌더**에 의해 `UIMap.Designer.cs`파일에 생성된 정의의 각 컨트롤 클래스에 적용되는 검색 속성 집합을 사용하여 UI 컨트롤을 찾습니다. 검색 속성에는 컨트롤의 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A> 및 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> 속성과 같이 컨트롤을 식별하는 데 사용할 수 있는 속성 이름과 속성 값의 이름-값 쌍이 포함됩니다. 검색 속성이 변경되지 않은 경우 코딩된 UI 테스트가 UI에서 컨트롤을 성공적으로 찾습니다. 검색 속성이 변경된 경우 코딩된 UI 테스트에 추론을 적용하여 UI에서 컨트롤과 창을 찾는 스마트 일치 알고리즘이 있습니다. UI가 변경된 경우 이전에 식별된 요소의 검색 속성을 수정하여 찾을 수 있습니다.

## <a name="what-to-do-if-your-user-interface-changes"></a>사용자 인터페이스가 변경된 경우 수행할 작업
 개발 중에는 사용자 인터페이스가 자주 변경됩니다. 이러한 변경의 영향을 줄이는 몇 가지 방법은 다음과 같습니다.

- 이 컨트롤을 참조하는 기록된 메서드를 찾고 **코딩된 UI 테스트 빌더**를 사용하여 이 메서드에 대한 작업을 다시 기록합니다. 메서드에 동일한 이름을 사용하여 기존 작업을 덮어쓸 수 있습니다.

- 컨트롤에 더 이상 유효하지 않은 어설션이 있는 경우

  - 어설션이 포함된 메서드를 삭제합니다.

  - 테스트 메서드에서 이 메서드 호출을 제거합니다.

  - 십자선 단추를 UI 컨트롤로 끌어와 새 어설션을 추가하고 UI 맵을 연 다음 새 어설션을 추가합니다.

  코딩된 UI 테스트를 기록하는 방법에 대한 자세한 내용은 [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)를 참조하세요.

## <a name="what-to-do-if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>백그라운드 프로세스가 완료되어야 테스트를 계속할 수 있는 경우 수행할 작업
 다음 UI 작업을 계속하기 전에 프로세스가 완료될 때까지 기다려야 할 수도 있습니다. 이렇게 하려면 다음 샘플과 같이 <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A>을 사용하여 테스트를 계속하기 전에 기다릴 수 있습니다.

```
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>추가 정보

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [UI 자동화를 사용 하 여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
- [코딩 된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [여러 UI 맵을 사용 하 여 규모가 많은 응용 프로그램 테스트](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [코딩 된 UI 테스트 및 작업 기록에 지원 되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
