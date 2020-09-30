---
title: '방법: 프로그래밍 방식으로 현재 Outlook 항목 확인'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 428dccf09235e2feea528bcdaef0a447e02ef58d
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585238"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>방법: 프로그래밍 방식으로 현재 Outlook 항목 확인
  이 예제에서는 이벤트를 사용 하 여 `Explorer.SelectionChange` 현재 폴더의 이름과 선택한 항목에 대 한 일부 정보를 표시 합니다. 그런 다음 코드에서 선택한 항목을 표시 합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 사항이 필요합니다.

- Microsoft Office Outlook의 약속, 연락처 및 전자 메일 항목입니다.

## <a name="see-also"></a>참고 항목
- [Outlook 개체 모델 개요](../vsto/outlook-object-model-overview.md)
- [방법: 프로그래밍 방식으로 이름으로 폴더 검색](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [방법: 프로그래밍 방식으로 특정 연락처 검색](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
