---
title: 프로그래밍 방식으로 워크시트 간에 데이터 및 서식 복사
description: FillAcrossSheets 메서드를 사용 하 여 한 시트의 범위에서 통합 문서의 다른 모든 시트에 데이터를 복사 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0696c99e78ee1b6a7acd174e5463bbdc514fe160
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828568"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>방법: 프로그래밍 방식으로 워크시트 간에 데이터 및 서식 복사
  메서드를 사용 하 여 한 시트의 범위에서 통합 문서의 다른 모든 시트에 데이터를 복사할 수 있습니다 <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> . 범위를 지정 하 고 데이터, 형식 또는 둘 다를 복사할지 여부를 지정 합니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>예제
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet44":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet44":::

## <a name="compile-the-code"></a>코드 컴파일
 이 예에서는 워크시트에 라는 범위가 필요 합니다 `rangeData` .

## <a name="see-also"></a>참조
- [워크시트 작업](../vsto/working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서에 새 워크시트 추가](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [방법: 프로그래밍 방식으로 선택한 셀이 포함 된 워크시트 행의 서식 변경](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
