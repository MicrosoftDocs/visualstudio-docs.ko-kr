---
title: 코딩된 UI 테스트가 특정 이벤트를 기다리도록 지정
ms.date: 11/04/2016
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea0bd0135ca90f96c2275248da7d116ecfd92e01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286780"
---
# <a name="make-coded-ui-tests-wait-for-specific-events-during-playback"></a>코딩된 UI 테스트가 재생 중 특정 이벤트를 기다리도록 지정

코딩된 UI 테스트 재생 시 창이 나타나거나 진행률 표시줄이 사라지는 등의 특정 이벤트가 발생할 때까지 기다리도록 테스트에 지시할 수 있습니다. 이렇게 하려면 다음 표에 설명된 대로 적절한 UITestControl.WaitForControlXXX() 메서드를 사용합니다. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> 메서드를 사용하여 컨트롤이 사용하도록 설정할 때까지 기다리는 코딩된 UI 테스트에 대한 예제는 [연습: 코딩된 UI 테스트 만들기, 편집 및 유지 관리](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)를 참조하세요.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**요구 사항**

Visual Studio Enterprise

> [!TIP]
> 또한 코딩된 UI 테스트 편집기를 사용해서 작업을 수행하기 전에 지연을 추가할 수도 있습니다. 자세한 내용은 [방법: 코딩된 UI 테스트 편집기를 사용하여 UI 작업 전에 지연 삽입](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)을 참조하세요.

**UITestControl.WaitForControlXXX() 메서드**

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>

컨트롤이 마우스 및 키보드 입력을 허용할 수 있을 때까지 기다립니다. 엔진은 모든 작업에 대해 이 API를 암시적으로 호출하여 컨트롤이 준비될 때까지 기다린 후 작업을 수행합니다. 그러나 일부 복잡한 시나리오에서는 명시적 호출을 수행해야 할 수 있습니다.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>

마법사가 서버를 호출하여 입력에 대해 몇 가지 비동기 유효성 검사를 수행하는 동안 컨트롤이 사용하도록 설정될 때까지 기다립니다. 예를 들어 메서드를 사용하여 마법사의 **다음** 단추를 사용하도록 설정할 때까지 기다릴 수 있습니다. 이 메서드에 대한 예제는 [연습: 코딩된 UI 테스트 만들기, 편집 및 유지 관리](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)를 참조하세요.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>

컨트롤이 UI에 나타날 때까지 기다립니다. 예를 들어 애플리케이션에서 매개 변수의 유효성 검사를 수행한 후 오류 대화 상자를 예상할 수 있습니다. 유효성 검사에 걸린 시간은 변수입니다. 이 메서드는 오류 대화 상자를 기다리는 데 사용할 수 있습니다.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>

컨트롤이 UI에서 사라질 때까지 기다립니다. 예를 들어 진행률 표시줄이 사라질 때까지 기다릴 수 있습니다.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>

컨트롤의 지정된 속성이 지정된 값을 갖게 될 때까지 기다립니다. 예를 들어 상태 텍스트가 **완료**로 변경될 때까지 기다립니다.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>

컨트롤의 지정된 속성이 지정된 값과 반대되는 값을 갖게 될 때까지 기다립니다. 예를 들어 편집 상자가 읽기 전용이 아니라 편집 가능이 될 때까지 기다립니다.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>

지정된 조건자가 `true`로 반환될 때까지 기다립니다. 이 메서드는 특정 컨트롤에서 복잡한 대기 작업(예: OR 조건)에 사용할 수 있습니다. 예를 들어 다음 코드에 표시된 대로 상태 텍스트가 **Succeeded** 또는 **Failed**가 될 때까지 기다릴 수 있습니다.

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDone(UITestControl control)
{
    WinText statusText = control as WinText;
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";
}

// In test method, wait till the method evaluates to true
statusText.WaitForControlCondition(IsStatusDone);
```

 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>

이전 메서드는 모두 UITestControl의 인스턴스 메서드입니다. 이 메서드는 정적 메서드입니다. 또한 이 메서드는 지정된 조건자가 `true`가 될 때까지 기다리지만 여러 컨트롤에서 복잡한 대기 작업(예: OR 조건)에 사용할 수 있습니다. 예를 들어 다음 코드에 표시된 대로 상태 텍스트가 **Succeeded**가 되거나 오류 메시지가 나타날 때까지 기다릴 수 있습니다.

```csharp

// Define the method to evaluate the condition
private static bool IsStatusDoneOrError(UITestControl[] controls)
{
    WinText statusText = controls[0] as WinText;
    WinWindow errorDialog = controls[1] as WinWindow;
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;
}

// In test method, wait till the method evaluates to true
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);
```

이러한 모든 메서드에는 다음과 같은 동작이 있습니다.

메서드는 대기에 성공하면 true를 반환하고 대기에 실패하면 false를 반환합니다.

대기 작업의 암시적 시간 제한은 <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> 속성으로 지정합니다. 이 속성의 기본값은 60000밀리초(1분)입니다.

메서드에 밀리초 단위의 명시적 시간 제한을 사용하는 오버로드가 있습니다. 그러나 대기 작업으로 인해 컨트롤을 암시적으로 검색하거나 애플리케이션이 사용 중인 경우 실제 대기 시간은 지정된 시간 제한보다 길어질 수 있습니다.

이전 함수는 강력하고 유연하지만 거의 모든 조건을 충족해야 합니다. 그러나 이러한 메서드가 요구를 충족하지 못하고 코드에서 <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A> 또는 <xref:System.Threading.Thread.Sleep%2A>을 코딩해야 하는 경우에는 Thread.Sleep() API 대신 Playback.Wait()를 사용하는 것이 좋습니다. 그 이유는 다음과 같습니다.

<xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A> 속성을 사용하여 절전 모드의 기간을 수정할 수 있습니다. 기본적으로 이 변수는 1이지만 늘리거나 줄여 코드 전체에서 대기 시간을 변경할 수 있습니다. 예를 들어 느린 네트워크 또는 일부 다른 성능 저하 사례를 특별히 테스트하는 경우 한 위치(또는 구성 파일에서도 가능)에서 이 변수를 1.5로 변경하여 모든 위치에서 대기를 50% 더 추가할 수 있습니다.

Playback.Wait()는 사용자 취소/분리 작업을 확인하는 동안 위의 계산 후 Thread.Sleep()을 for 루프의 더 작은 청크로 내부적으로 호출합니다. 즉, Playback.Wait()를 사용하면 대기가 끝나기 전에 재생을 취소할 수 있지만, 절전 모드에서는 취소할 수 없거나 예외를 throw합니다.

> [!TIP]
> 코딩된 UI 테스트 편집기에서는 코딩된 UI 테스트를 쉽게 수정할 수 있습니다. 코딩된 UI 테스트 편집기를 사용하면 테스트 메서드를 찾아서 보고 편집할 수 있습니다. 또한 UI 작업을 편집하고 UI 컨트롤 맵에서 관련 컨트롤을 편집할 수도 있습니다. 자세한 내용은 [코딩된 UI 테스트 편집기를 사용하여 코딩된 UI 테스트 편집](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
- [코딩된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md)
- [연습: 코딩된 UI 테스트 만들기, 편집 및 유지 관리](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [코딩된 UI 테스트 분석](../test/anatomy-of-a-coded-ui-test.md)
- [코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [방법: 코딩된 UI 테스트 편집기를 사용하여 UI 작업 전에 지연 삽입](editing-coded-ui-tests-using-the-coded-ui-test-editor.md#insert-a-delay-before-a-ui-action)
