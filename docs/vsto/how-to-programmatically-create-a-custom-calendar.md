---
title: '방법: 프로그래밍 방식으로 사용자 지정 달력 만들기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom calendars [Office development in Visual Studio]
- calendars [Office development in Visual Studio], custom
- appointments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aab9e14c7fa4b4c70b2e61eca382af2ce787148c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546057"
---
# <a name="how-to-programmatically-create-a-custom-calendar"></a>방법: 프로그래밍 방식으로 사용자 지정 달력 만들기
  이 예에서는 **PersonalCalendar**이라는 새 일정 폴더를 만든 다음 새 약속 항목을 만들어 Calendar 폴더에 추가 합니다. 그런 다음 코드에서 Calendar 폴더를 표시 합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 [!code-csharp[Trin_OL_CustomCalendar#1](../vsto/codesnippet/CSharp/Trin_OL_CustomCalendar/thisaddin.cs#1)]

## <a name="see-also"></a>참고 항목
- [일정 항목 작업](../vsto/working-with-calendar-items.md)
- [방법: 프로그래밍 방식으로 약속 만들기](../vsto/how-to-programmatically-create-appointments.md)
- [방법: 프로그래밍 방식으로 모임 요청 만들기](../vsto/how-to-programmatically-create-a-meeting-request.md)
