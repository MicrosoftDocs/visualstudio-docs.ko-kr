---
title: Excel 솔루션 세계화 및 지역화
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f37ddcbbd3145fc96cd8081d7a1df524ef7ea8ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986050"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Excel 솔루션 세계화 및 지역화
  이 섹션에는 영어 이외의 Windows 언어 설정이 있는 컴퓨터에서 실행되는 Microsoft Office Excel 솔루션의 특수 고려 사항에 대한 정보를 포함합니다. Microsoft Office 솔루션을 전역화하고 지역화하는 대부분의 측면은 Visual Studio를 사용하여 다른 종류의 솔루션을 만들 때와 동일하게 발생합니다. 일반 정보는 [응용 프로그램 전역화 및 지역화](../ide/globalizing-and-localizing-applications.md)를 참조 하세요.

 기본적으로 Microsoft Office Excel의 호스트 컨트롤은 관리 코드를 사용하여 전달되거나 조작되는 모든 데이터의 서식이 영어(미국) 서식을 사용하여 지정되는 한 Windows 국가별 설정에서 올바르게 작동합니다. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]를 대상으로 하는 프로젝트에서는 이 동작이 CLR(공용 언어 런타임)에서 제어됩니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="format-data-in-excel-with-various-regional-settings"></a>다양 한 국가별 설정을 사용 하 여 Excel의 데이터 서식 지정
 날짜 및 통화와 같이 로캘 구분 서식을 가진 모든 데이터는 영어(미국) 데이터 서식(로캘 ID 1033)을 사용하여 서식을 지정한 다음 Microsoft Office Excel로 전달하거나 Office 프로젝트에서 코드의 데이터를 읽어야 합니다.

 기본적으로 Visual Studio에서 Office 솔루션을 개발할 때 Excel 개체 모델은 로캘 ID 1033 데이터 서식(이를 로캘 ID 1033으로 개체 모델 잠금이라고도 함)을 기대합니다. 이 동작은 Visual Basic for Applications가 작동하는 방식과 일치합니다. 그러나 이 동작은 Office 솔루션에서 수정할 수 있습니다.

### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Excel 개체 모델에서 항상 로캘 ID 1033을 예상 하는 방법 이해
 기본적으로 Visual Studio를 사용하여 만드는 Office 솔루션은 최종 사용자의 로캘 설정에 의해 영향을 받지 않고 항상 로캘이 영어(미국)인 것처럼 동작합니다. 예를 들어 Excel에서 <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> 속성을 가져오거나 설정하는 경우 데이터는 로캘 ID 1033이 예상하는 방식으로 서식이 지정되어야 합니다. 다른 데이터 서식을 사용하는 경우 예기치 않은 결과가 발생할 수 있습니다.

 관리 코드에서 전달되거나 조작된 데이터에 영어(미국) 서식을 사용해도, Excel은 최종 사용자의 로캘 설정에 따라 데이터를 올바르게 해석합니다. 관리 코드는 데이터와 함께 로캘 ID 1033을 전달하기 때문에 Excel은 데이터의 서식을 올바르게 지정할 수 있으며, 이는 데이터가 영어(미국) 서식이므로 사용자의 로캘 설정과 일치하도록 다시 서식이 지정되어야 한다는 것을 나타냅니다.

 예를 들어 최종 사용자의 국가별 옵션이 독일어(독일) 로캘로 설정되어 있는 경우 최종 사용자는 2005년 6월 29일이 29.06.2005로 서식화될 것을 기대합니다. 그러나 솔루션이 날짜를 문자열로 Excel에 전달하는 경우 영어(미국) 서식에 따라 6/29/2005로 날짜를 서식화해야 합니다. 셀의 서식이 날짜 셀로 지정된 경우 Excel은 독일어(독일) 서식으로 날짜를 표시합니다.

### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Excel 개체 모델에 다른 로캘 Id 전달
 CLR(공용 언어 런타임)은 로캘 구분 데이터를 허용하는 Excel 개체 모델의 모든 메서드 및 속성으로 로캘 ID 1033을 자동으로 전달합니다. 모든 호출에 대해 이 동작을 자동으로 개체 모델로 변경하는 방법은 없습니다. 그러나 메서드를 호출하는 <xref:System.Type.InvokeMember%2A> 를 사용하고 로캘 ID를 메서드의 *culture* 매개 변수에 전달하여 다른 로캘 ID를 특정 메서드에 전달할 수 있습니다.

## <a name="localize-document-text"></a>문서 텍스트 지역화
 프로젝트의 문서, 템플릿 또는 통합 문서는 정적 텍스트를 포함하고 있을 가능성이 있으며 이는 어셈블리 및 다른 관리되는 리소스에서 별도로 지역화되어야 합니다. 이 작업을 수행하는 간단한 방법은 Microsoft Office Word 또는 Microsoft Office Excel을 사용하여 문서의 복사본을 만들고 텍스트를 번역하는 것입니다. 이 프로세스는 몇몇 문서가 동일한 어셈블리에 연결될 수 있기 때문에 코드를 변경하지 않는 경우에도 작동합니다.

 문서 텍스트와 상호 작용하는 일부 코드가 텍스트의 언어와 계속 일치하는지 그리고 책갈피, 명명된 범위, 기타 표시 필드가 다른 문법 및 텍스트 길이에 맞도록 조정하는 데 필요한 Office 문서의 서식을 다시 지정하는 것을 수용하는지는 여전히 확인해야 합니다. 비교적 적은 양의 텍스트가 포함된 문서 템플릿의 경우 리소스 파일에 텍스트를 저장한 다음 런타임에 텍스트를 로드하는 것이 좋습니다.

### <a name="text-direction"></a>텍스트 방향
 Excel에서는 텍스트를 오른쪽에서 왼쪽으로 렌더링하도록 워크시트의 속성을 설정할 수 있습니다. 호스트 컨트롤 또는 속성을 가진 모든 컨트롤 `RightToLeft` 은 런타임에 자동으로 이러한 설정과 일치 합니다. Word에는 양방향 텍스트에 대 한 문서 설정이 없으므로 컨트롤을이 설정에 매핑할 수 없습니다. 대신 각 컨트롤에 대한 텍스트 맞춤을 설정해야 합니다. 모든 컨트롤을 안내하는 코드를 작성하고 텍스트를 오른쪽에서 왼쪽으로 렌더링하도록 할 수 있습니다.

### <a name="change-culture"></a>문화권 변경
 문서 수준 사용자 지정 코드는 일반적으로 Excel의 주 UI 스레드를 공유하므로 스레드 문화권을 변경하면 해당 스레드에서 실행되는 그 밖의 모든 부분에 영향을 미칩니다. 즉, 변경 내용이 사용자 지정에 제한되는 것이 아닙니다.

 Windows Forms 컨트롤은 애플리케이션 수준 VSTO 추가 기능을 호스트 애플리케이션에서 시작하기 전에 초기화됩니다. 이러한 상황에서 문화권은 UI 컨트롤을 설정하기 전에 변경되어야 합니다.

## <a name="install-the-language-packs"></a>언어 팩 설치
 Windows에 대해 영어가 아닌 설정이 있는 경우 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 언어 팩을 설치하여 Windows와 동일한 언어로 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 메시지를 볼 수 있습니다. 최종 사용자가 Windows에 대해 영어가 아닌 설정으로 솔루션을 실행하는 경우 Windows와 동일한 언어로 런타임 메시지를 보려면 올바른 언어 팩이 있어야 합니다. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]언어 팩은 [Microsoft 다운로드 센터](https://www.microsoft.com/download)에서 다운로드할 수 있습니다.

 또한 ClickOnce 메시지를 위해 재배포 가능한 .NET Framework 언어 팩이 필요합니다. .NET Framework 언어 팩은 [Microsoft 다운로드 센터](https://www.microsoft.com/download)에서 다운로드할 수 있습니다.

## <a name="regional-settings-and-excel-com-calls"></a>국가별 설정 및 Excel COM 호출
 관리되는 클라이언트가 COM 개체에서 메서드를 호출하고 문화권별 정보를 전달할 때마다 현재 스레드 로캘과 일치하는 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (로캘)을 사용해서 수행해야 합니다. 현재 스레드 로캘은 기본적으로 사용자의 국가별 설정에서 상속됩니다. 그러나 Visual Studio에서 Office 개발 도구를 사용하여 만든 Excel 솔루션에서 Excel 개체 모델로 호출하는 경우에는 영어(미국) 데이터 서식(로캘 ID 1033)이 Excel 개체 모델에 자동으로 전달됩니다. 날짜 및 통화와 같이 로캘 구분 서식을 가진 모든 데이터는 영어(미국) 데이터 서식을 사용하여 서식을 지정한 다음에 Microsoft Office Excel로 전달하거나 프로젝트 코드에서 데이터를 읽어야 합니다.

## <a name="considerations-for-storing-data"></a>데이터 저장 시 고려 사항
 데이터가 올바르게 해석되고 표시되게 하려면 강력한 형식의 개체 대신 하드 코드된 문자열 리터럴로 Excel 워크시트 수식 같이 애플리케이션이 데이터를 저장할 때 문제가 발생할 수 있다는 것도 고려해야 합니다. 고정 문화권 또는 영어(미국)(LCID 값 1033) 스타일을 가정하여 서식이 지정된 데이터를 사용해야 합니다.

### <a name="applications-that-use-string-literals"></a>문자열 리터럴을 사용 하는 응용 프로그램
 하드 코드되었을 수 있는 값에는 영어(미국) 서식으로 기록된 날짜 리터럴과 지역화된 함수 이름이 있는 Excel 워크시트 수식이 포함됩니다. 다른 가능한 값으로는 "1,000"과 같은 숫자가 포함된 하드 코드된 문자열이 있을 수 있습니다. 즉, 일부 문화권에서 이 값은 천(1,000)으로 해석되지만 다른 문화권에서는 1.0을 나타냅니다. 잘못된 서식으로 수행된 계산 및 비교는 잘못된 데이터를 유발할 수 있습니다.

 Excel은 문자열로 전달된 LCID에 따라 모든 문자열을 해석합니다. 이는 문자열의 서식이 전달된 LCID에 해당하지 않는 경우 문제가 될 수 있습니다. Visual Studio에서 Office 개발 도구를 사용하여 만든 Excel 솔루션은 모든 데이터를 전달할 때 LCID 1033(en-US)을 사용합니다. Excel은 국가별 설정 및 Excel 사용자 인터페이스 언어에 따라 데이터를 표시합니다. 또한 VBA(Visual Basic for Applications)도 이 방식으로 작동합니다. 즉, 문자열이 en-US 서식으로 지정되고 VBA는 거의 항상 LCID로 0(언어 중립)을 전달합니다. 예를 들어 다음 VBA 코드는 현재 사용자 로캘 설정에 따라 2004 년 5 월 12 일에 대 한 올바른 형식의 값을 표시 합니다.

```vb
'VBA
Application.ActiveCell.Value2 = "05/12/04"
```

 Visual Studio의 Office 개발 도구를 사용하여 만든 솔루션에서 사용되고 COM interop를 통해 Excel로 전달되는 경우 날짜 서식이 en-US 스타일로 지정될 때 동일한 코드는 동일한 결과를 생성합니다.

 예를 들면 다음과 같습니다.

 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]

 가능하다면 문자열 리터럴 대신 강력한 형식의 데이터를 사용하여 작업해야 합니다. 예를 들어 데이터를 문자열 리터럴로 저장하는 대신 <xref:System.Double>로 저장한 다음 조작을 위해 <xref:System.DateTime> 개체로 변환합니다.

 다음 코드 예제는 사용자가 A5 셀에 입력하는 날짜를 <xref:System.Double>로 저장한 다음 A7 셀에 표시하기 위해 <xref:System.DateTime> 개체로 변환합니다. A7 셀은 날짜를 표시하도록 서식이 지정되어야 합니다.

 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]

### <a name="excel-worksheet-functions"></a>Excel 워크시트 함수
 대부분의 언어 버전의 Excel의 경우 워크시트 함수 이름은 내부적으로 변환됩니다. 그러나 잠재적인 언어 및 COM interop 문제로 인해 코드에서 영어 함수 이름만 사용 하는 것이 좋습니다.

### <a name="applications-that-use-external-data"></a>외부 데이터를 사용 하는 응용 프로그램
 레거시 시스템에서 내보낸 쉼표로 구분된 값이 포함된 파일(CSV 파일)과 같이 외부 데이터를 사용하거나 열려 있는 모든 코드는 en-US 이외의 서식을 사용하여 이러한 파일을 내보내는 경우에도 영향을 받을 수 있습니다. 데이터베이스가 날짜를 문자열로 저장하지 않거나 이진 형식을 사용하는 작업만 수행하면 모든 값이 이진 형식이 되기 때문에 데이터베이스 액세스가 영향을 받지 않을 수 있습니다. 또한 Excel의 데이터를 사용하여 SQL 쿼리를 구성하는 경우 사용하는 함수에 따라 해당 쿼리가 en-US 형식인지 확인해야 합니다.

## <a name="see-also"></a>추가 정보

- [방법: Office 다국어 사용자 인터페이스 대상](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)