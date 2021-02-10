---
title: '방법: 프로그래밍 방식으로 약속 삭제'
description: Microsoft Outlook에서 프로그래밍 방식으로 apppointments를 삭제 하는 방법에 대해 알아봅니다. 이 예제에서는 되풀이되는 약속의 인스턴스 하나를 삭제합니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- calendars [Office development in Visual Studio], deleting appointments
- deleting appointments
- appointments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0520014edc97f7517338652fa89e4c8269ba552c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963928"
---
# <a name="how-to-programmatically-delete-appointments"></a>방법: 프로그래밍 방식으로 약속 삭제
  이 예제에서는 되풀이되는 약속의 인스턴스 하나를 삭제합니다. 이 예제에서는 되풀이되는 약속의 인스턴스가 2006년 6월 28일 08시에 발생한다고 가정합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 [!code-vb[Trin_Outlook_RL_DeleteAppointment#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_DeleteAppointment/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_DeleteAppointment#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_DeleteAppointment/thisaddin.cs#1)]

## <a name="see-also"></a>참고 항목
- [일정 항목 작업](../vsto/working-with-calendar-items.md)
- [VSTO 추가 기능 프로그래밍 시작](../vsto/getting-started-programming-vsto-add-ins.md)
- [방법: 프로그래밍 방식으로 약속 만들기](../vsto/how-to-programmatically-create-appointments.md)
- [방법: 프로그래밍 방식으로 사용자 지정 달력 만들기](../vsto/how-to-programmatically-create-a-custom-calendar.md)
- [방법: 프로그래밍 방식으로 모임 요청 만들기](../vsto/how-to-programmatically-create-a-meeting-request.md)
