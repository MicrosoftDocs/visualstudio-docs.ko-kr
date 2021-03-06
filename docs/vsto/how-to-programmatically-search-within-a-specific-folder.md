---
title: '방법: 프로그래밍 방식으로 특정 폴더 내에서 검색'
description: Visual Studio를 사용 하 여 특정 Microsoft Outlook 폴더 내에서 프로그래밍 방식으로 검색 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b25880420e23b82f6f63ab28ef5f1f93429bdd8c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824759"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>방법: 프로그래밍 방식으로 특정 폴더 내에서 검색
  이 코드 예제에서는 및 메서드를 사용 하 여 `Find` `FindNext` **받은 편지함** 에 있는 전자 메일 메시지의 제목 필드에 있는 텍스트를 검색 합니다. 이 메서드는 문자열 필터를 사용 하 여 문자 T를 텍스트의 시작 문자로 확인 합니다 `Subject` .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>참조
- [폴더 작업](../vsto/working-with-folders.md)
- [Outlook 개체 모델 개요](../vsto/outlook-object-model-overview.md)
- [방법: 프로그래밍 방식으로 이름으로 폴더 검색](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
