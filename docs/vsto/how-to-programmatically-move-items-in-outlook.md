---
title: '방법: 프로그래밍 방식으로 Outlook에서 항목 이동'
description: Microsoft Outlook에서 프로그래밍 방식으로 항목을 이동 하는 방법을 알아봅니다. 이 예제에서는 받은 편지함의 읽지 않은 전자 메일 메시지를 Test 라는 폴더로 이동 합니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b8e951ab393d09506ad4f2d593962ea1826eff09
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826735"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>방법: 프로그래밍 방식으로 Outlook에서 항목 이동
  이 예제에서는 **받은 편지함** 의 읽지 않은 전자 메일 메시지를 **Test** 라는 폴더로 이동 합니다. 이 예에서는 필드에 **Test** 라는 단어가 있는 메시지만 이동 합니다 `Subject` .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 사항이 필요합니다.

- **Test** 라는 Outlook 메일 폴더입니다.

- 필드의 단어 **테스트** 와 함께 도착 하는 전자 메일 메시지입니다 `Subject` .

## <a name="see-also"></a>참조
- [폴더 작업](../vsto/working-with-folders.md)
- [방법: 프로그래밍 방식으로 이름으로 폴더 검색](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [방법: 프로그래밍 방식으로 특정 폴더 내에서 검색](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [방법: 프로그래밍 방식으로 전자 메일 메시지를 받을 때 작업 수행](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
