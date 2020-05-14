---
title: 디버거의 형식 지정자(C#) | Microsoft Docs
ms.date: 11/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: caaf36e286f1bdc664ebdbb10e3baf7ed28183e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849830"
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Visual Studio 디버거의 C# 형식 지정자
형식 지정자를 사용하여 **조사식** 창에 값이 표시되는 형식을 변경할 수 있습니다. 또한 **직접 실행** 창, **명령** 창, [추적점](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) 및 소스 창에서도 형식 지정자를 사용할 수 있습니다. 이러한 창에서 식을 일시 중지하면 결과가 [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)에 지정된 형식 표시로 나타납니다.

형식 지정자를 사용하려면 변수 식을 입력한 다음 쉼표와 적절한 지정자를 입력합니다.

## <a name="set-format-specifiers"></a>형식 지정자 설정
다음 예제 코드를 사용합니다.

```csharp
{
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

디버그 중에 `my_var1` 변수를 **조사식** 창에 추가합니다(**디버그** > **창** > **조사식** > **조사식 1**). 그런 다음, 변수를 마우스 오른쪽 단추로 클릭하고 **16진수 표시**를 선택합니다. 이제 **조사식** 창에 0x0065 값이 표시됩니다. 이 값을 16진수 정수 대신 10진수 정수로 표시하려면 **이름** 열에서 변수 이름 뒤에 10진수 형식 지정자 **, d**를 추가합니다. 이제 **값** 열에 **101**이 표시됩니다.

![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")

::: moniker range=">= vs-2019" 

**조사식** 창에서 값에 쉼표(,)를 추가하여 사용 가능한 형식 지정자 목록을 보고 형식 지정자를 선택할 수 있습니다. 

![FormatSpecCSharp](../debugger/media/vs-2019/format-specs-csharp.png "FormatSpecCSharp")

::: moniker-end

## <a name="format-specifiers"></a>형식 지정자
다음 표에서는 Visual Studio 디버거의 C# 형식 지정자에 대해 설명합니다.

|지정자|서식|원래 조사식 값|표시|
|---------------|------------|--------------------------|--------------|
|ac|식 계산을 강제 수행합니다. 암시적 속성 확인과 암시적 함수 호출이 해제된 경우에 유용할 수 있습니다.|메시지 “사용자가 암시적 함수 실행을 해제했습니다.”|\<value>|
|일|10진수 정수|0x0065|101|
|dynamic|동적 뷰를 사용하여 지정된 개체를 표시합니다.|동적 뷰를 포함하여 개체의 모든 멤버를 표시합니다.|동적 뷰만 표시합니다.|
|h|16진수 정수|61541|0x0000F065|
|nq|따옴표 없는 문자열|"My String"|My String|
|nse|형식이 아니라 동작을 지정합니다. “의도하지 않은 결과가 없는” 식을 평가합니다. 식을 해석할 수 없고 평가로만 확인할 수 있는 경우(예: 함수 호출) 대신 오류가 표시됩니다.|N/A|N/A|
|hidden|모든 public 멤버 및 public이 아닌 멤버를 표시합니다.|공용 멤버를 표시합니다.|모든 멤버를 표시합니다.|
|raw|항목을 원시 항목 노드에 나타나는 대로 표시합니다. 프록시 개체에만 사용할 수 있습니다.|Dictionary\<T>|Dictionary\<T>의 Raw 뷰|
|results|IEnumerable 또는 IEnumerable\<T>를 구현하는 형식의 변수와 함께 사용되며, 일반적으로 쿼리 식의 결과입니다. 쿼리 결과가 포함된 멤버만 표시합니다.|모든 멤버 표시|쿼리 조건에 맞는 멤버 표시|

## <a name="see-also"></a>참조
- [조사식 및 간략한 조사식 창](../debugger/watch-and-quickwatch-windows.md)
- [자동 및 지역 창](../debugger/autos-and-locals-windows.md)
