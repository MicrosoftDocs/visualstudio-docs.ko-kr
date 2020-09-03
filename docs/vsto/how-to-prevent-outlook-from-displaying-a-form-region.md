---
title: '방법: Outlook에서 양식 영역 표시 하지 않기'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 90da255beb0a85a302158feb1f9d5cc4981437eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520136"
---
# <a name="how-to-prevent-outlook-from-displaying-a-form-region"></a>방법: Outlook에서 양식 영역 표시 하지 않기
  Outlook Microsoft Office 특정 항목에 대 한 양식 영역을 표시 하지 않으려는 경우가 있을 수 있습니다. 예를 들어 연락처 항목에 비즈니스 주소가 포함 되어 있지 않은 경우 지도에서 비즈니스의 위치를 표시 하는 양식 영역을 표시 하지 않을 수 있습니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="to-prevent-outlook-from-displaying-a-form-region"></a>Outlook에서 양식 영역을 표시 하지 않도록 하려면

1. 수정 하려는 양식 영역에 대 한 코드 파일을 엽니다.

2. **양식 영역 팩터리** 코드 영역을 확장 합니다.

3. `FormRegionInitializing` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 클래스의 속성을 <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> **true**로 설정 하는 코드를 이벤트 처리기에 추가 합니다.

   이 예제에서 연락처 항목에 주소가 포함 되어 있지 않으면 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 속성이 **true**로 설정 되 고 양식 영역이 표시 되지 않습니다.

## <a name="example"></a>예제
 [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]

## <a name="see-also"></a>참조
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [방법: Outlook 추가 기능 프로젝트에 양식 영역 추가](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [연습: Outlook에서 디자인 한 양식 영역 가져오기](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
