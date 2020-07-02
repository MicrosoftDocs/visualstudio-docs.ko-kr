---
title: '방법: 프로그래밍 방식으로 Outlook 폴더에 웹 페이지 연결'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b8d44ffc46557243d2681b8f8b4a3b85d1cd9be6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546148"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>방법: 프로그래밍 방식으로 Outlook 폴더에 웹 페이지 연결
  이 예제에서는 Microsoft Office Outlook에서 이라는 폴더를 확인 `HtmlView` 합니다. 폴더가 없으면 코드에서 폴더를 만들고이 폴더에 웹 페이지를 할당 합니다. 폴더가 있으면 코드에서 폴더 내용을 표시 합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>예제
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>참고 항목
- [폴더 작업](../vsto/working-with-folders.md)
- [방법: 프로그래밍 방식으로 이름으로 폴더 검색](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [방법: 프로그래밍 방식으로 사용자 지정 폴더 항목 만들기](../vsto/how-to-programmatically-create-custom-folder-items.md)
