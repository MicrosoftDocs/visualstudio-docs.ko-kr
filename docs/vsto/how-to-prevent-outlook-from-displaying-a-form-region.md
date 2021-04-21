---
title: '방법: Outlook에서 양식 영역 표시 하지 않기'
description: Microsoft Office Outlook에서 특정 항목에 대 한 양식 영역을 표시 하지 않도록 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], canceling display
- canceling form region display
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1dc9322dd2ad3c3a2111222d7491f9e1a82cd6c4
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825851"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>방법: Outlook에서 양식 영역 표시 하지 않기
  Outlook Microsoft Office 특정 항목에 대 한 양식 영역을 표시 하지 않으려는 경우가 있을 수 있습니다. 예를 들어 연락처 항목에 비즈니스 주소가 포함 되어 있지 않은 경우 지도에서 비즈니스의 위치를 표시 하는 양식 영역을 표시 하지 않을 수 있습니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Outlook에서 양식 영역을 표시 하지 않도록 하려면

1. 수정 하려는 양식 영역에 대 한 코드 파일을 엽니다.

2. **양식 영역 팩터리** 코드 영역을 확장 합니다.

3. `FormRegionInitializing` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 클래스의 속성을 <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> **true** 로 설정 하는 코드를 이벤트 처리기에 추가 합니다.

   이 예제에서 연락처 항목에 주소가 포함 되어 있지 않으면 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 속성이 **true** 로 설정 되 고 양식 영역이 표시 되지 않습니다.

## <a name="example"></a>예제
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb" id="Snippet1":::


## <a name="see-also"></a>참조
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [방법: Outlook 추가 기능 프로젝트에 양식 영역 추가](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [연습: Outlook에서 디자인 한 양식 영역 가져오기](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
