---
title: '방법: 프로그래밍 방식으로 텍스트 파일을 통합 문서로 열기'
description: Visual Studio를 사용 하 여 프로그래밍 방식으로 텍스트 파일을 Microsoft Excel 통합 문서로 여는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14a73d7a06c3d79c15df5b823b38efc9ddceb846
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824174"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>방법: 프로그래밍 방식으로 텍스트 파일을 통합 문서로 열기
  텍스트 파일을 통합 문서로 열 수 있습니다. 열려는 텍스트 파일의 이름을 전달 해야 합니다. 구문 분석을 시작할 행 번호와 파일의 데이터 열 형식 등 여러 가지 선택적 매개 변수를 지정할 수 있습니다.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>예제
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet80":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet80":::

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 구성 요소가 필요 합니다.

- `Test.txt`텍스트를 세 줄 이상 포함 하는 라는 쉼표로 구분 된 텍스트 파일입니다.

- `Test.txt`C 드라이브에 저장 되는 텍스트 파일입니다.

## <a name="see-also"></a>참조
- [통합 문서 작업](../vsto/working-with-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서 열기](../vsto/how-to-programmatically-open-workbooks.md)
- [방법: 프로그래밍 방식으로 새 통합 문서 만들기](../vsto/how-to-programmatically-create-new-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서 저장](../vsto/how-to-programmatically-save-workbooks.md)
- [방법: 프로그래밍 방식으로 통합 문서 닫기](../vsto/how-to-programmatically-close-workbooks.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
