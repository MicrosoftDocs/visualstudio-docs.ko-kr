---
title: 전역 Windows Forms 및 Web Forms를 위한 문화권 관련 클래스 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c2d048387e4e81763a63b5bf010c36c87beeacf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665916"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>전역 Windows Forms 및 Web Forms을 위한 문화권 관련 클래스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

문화권마다 날짜, 시간, 숫자, 통화 및 기타 정보를 표시하는 규칙이 서로 다릅니다. <xref:System.Globalization> 네임스페이스는 <xref:System.Globalization.DateTimeFormatInfo>, **Calendar**, <xref:System.Globalization.NumberFormatInfo> 등 문화권 관련 값이 표시되는 방식을 수정하는 데 사용할 수 있는 클래스를 포함합니다.

## <a name="using-the-culture-setting"></a>문화권 설정 사용
 하지만 대부분은 애플리케이션 또는 **국가별 옵션** 제어판에 저장된 문화권 설정을 사용하여 런타임에 규칙을 자동으로 확인하고 그에 따라 정보의 서식을 지정합니다. 문화권 설정에 대한 자세한 내용은 [방법: Windows Forms 전역화를 위한 문화권 및 UI 문화권 설정](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) 또는 [방법: ASP.NET 웹 페이지 세계화를 위한 문화권 및 UI 문화권 설정](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)을 참조하세요. 문화권 설정에 따라 자동으로 정보의 서식을 지정하는 클래스를 문화권 관련 클래스라고 합니다. 일부 문화권 관련 메서드는 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName> 및 <xref:System.String.Format%2A?displayProperty=fullName>입니다. 몇 가지 문화권 관련 함수(Visual Basic 언어)로는 `MonthName` 및 `WeekDayName`이 있습니다.

 예를 들어 다음 코드는 <xref:System.IFormattable.ToString%2A> 메서드를 사용하여 현재 문화권에 대한 통화 서식을 지정하는 방법을 보여 줍니다.

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))

```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

 문화권이 "fr-FR"로 설정된 경우 출력 창에 다음과 같이 표시됩니다.

 `100,00`

 문화권이 "en-US"로 설정된 경우 출력 창에 다음과 같이 표시됩니다.

 `$100.00`

## <a name="see-also"></a>관련 항목
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName> <xref:System.Globalization.DateTimeFormatInfo>
 <xref:System.Globalization.NumberFormatInfo>
 <xref:System.Globalization.Calendar>
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>
 <xref:System.String.Format%2A?displayProperty=fullName>
 [응용 프로그램 전역화 및 지역화](../ide/globalizing-and-localizing-applications.md)
