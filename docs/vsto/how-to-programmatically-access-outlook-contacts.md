---
title: '방법: 프로그래밍 방식으로 Outlook 연락처 액세스'
description: 프로그래밍 방식으로 Outlook 연락처에 액세스할 수 있는 방법을 알아봅니다. 이 예에서는 마지막 이름에 지정 된 검색 문자열이 포함 된 모든 연락처를 찾습니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 08e9d9ea69985a26a9688152f5c3b028caf75300
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828906"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>방법: 프로그래밍 방식으로 Outlook 연락처 액세스
  이 예에서는 마지막 이름에 지정 된 검색 문자열이 포함 된 모든 연락처를 찾습니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb" id="Snippet1":::


## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 사항이 필요합니다.

- **연락처** 폴더에 "**Na"** 문자열 (예: Tzipi Butnaru)이 포함 된 성이 있는 연락처입니다.

## <a name="see-also"></a>참조
- [연락처 항목 작업](../vsto/working-with-contact-items.md)
- [방법: 프로그래밍 방식으로 Outlook 연락처에 항목 추가](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [방법: 프로그래밍 방식으로 특정 연락처 검색](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [방법: 프로그래밍 방식으로 연락처에서 전자 메일 주소 검색](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [방법: 프로그래밍 방식으로 Outlook 연락처 삭제](../vsto/how-to-programmatically-delete-outlook-contacts.md)
