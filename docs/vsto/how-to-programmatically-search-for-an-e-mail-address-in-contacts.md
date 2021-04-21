---
title: 프로그래밍 방식으로 연락처에서 전자 메일 주소 찾기
description: Visual Studio를 사용 하 여 Microsoft Outlook 연락처에서 프로그래밍 방식으로 전자 메일 주소를 찾는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd977840cd75081d87011540ca00675fb84cee36
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828945"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>방법: 프로그래밍 방식으로 연락처에서 전자 메일 주소 검색
  이 예제에서는 메일 주소에 도메인 이름 **example.com** 이 있는 연락처에 대한 연락처 폴더를 검색합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 사항이 필요합니다.

- 메일 주소에 도메인 이름 **example.com** (예: `somebody@example.com`) 및 이름과 성이 있는 연락처입니다.

## <a name="see-also"></a>참조
- [연락처 항목 작업](../vsto/working-with-contact-items.md)
- [방법: 프로그래밍 방식으로 전자 메일 보내기](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [방법: 프로그래밍 방식으로 Outlook 연락처 액세스](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [방법: 프로그래밍 방식으로 Outlook 연락처에 항목 추가](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
