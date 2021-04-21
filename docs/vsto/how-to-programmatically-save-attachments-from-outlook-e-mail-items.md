---
title: 프로그래밍 방식으로 Outlook 전자 메일 항목의 첨부 파일 저장
description: Visual Studio를 사용 하 여 Microsoft Outlook 전자 메일 항목의 첨부 파일을 프로그래밍 방식으로 저장 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ad64593f91e14bcfd993929420764869a8359e3e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826696"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>방법: 프로그래밍 방식으로 Outlook 전자 메일 항목의 첨부 파일 저장

이 예제는 받은 편지함에 전자 메일이 수신될 때 메일 첨부 파일을 지정된 폴더에 저장합니다.

> [!IMPORTANT]
> 이 예제는 C 디렉터리의 루트에 **Testfilesave** 라는 폴더를 추가 하는 경우에만 작동 합니다.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제

:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>참조

- [메일 항목 작업](../vsto/working-with-mail-items.md)
- [방법: 프로그래밍 방식으로 이름으로 폴더 검색](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [방법: 프로그래밍 방식으로 전자 메일 메시지를 받을 때 작업 수행](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [방법: 프로그래밍 방식으로 특정 폴더 내에서 검색](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
