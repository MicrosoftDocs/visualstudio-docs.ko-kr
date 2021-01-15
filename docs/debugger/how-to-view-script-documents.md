---
title: 스크립트 문서 보기 | Microsoft Docs
description: 솔루션 탐색기를 사용하여 Visual Studio에서 JavaScript 서버 쪽 스크립트 문서를 보는 방법을 이해합니다.
ms.custom: SEO-VS-2020
ms.date: 11/05/2019
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91c2e1c0438ebf8fad69f985f62a976ff6710a81
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150485"
---
# <a name="how-to-view-script-documents-javascript"></a>방법: 스크립트 문서 보기(JavaScript)

서버 쪽 스크립트 파일은 솔루션 탐색기에 표시됩니다. 클라이언트 쪽 스크립트 파일은 디버그 모드나 중단 모드에서만 표시되며 클라이언트 쪽 스크립트 파일은 **스크립트 문서** 노드에 표시됩니다.

페이지를 동적으로 생성하는 일부 애플리케이션 유형의 경우 브라우저에 로드되는 스크립트 문서에서 중단점을 설정할 때 중단 모드 및 디버그를 쉽게 시작할 수 있습니다. 마찬가지로 로드된 스크립트 문서에서 `debugger` 문을 추가하여 중단 모드를 시작할 수 있습니다. 이 문서에서는 문서를 보는 방법을 설명합니다.

> [!NOTE]
> [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 이전에서는 서버 쪽 스크립트에서 생성된 클라이언트 쪽 스크립트 파일이 스크립트 탐색기 창에 나타납니다.

### <a name="to-view-a-server-side-script-document"></a>서버 쪽 스크립트 문서를 보려면

1. **솔루션 탐색기** 에서 **\<Website Pathname>** 노드를 엽니다.

2. 보려는 스크립트 파일을 두 번 클릭합니다.

     서버 쪽 스크립트 파일이 소스 창에 열립니다.

### <a name="to-view-a-client-side-script-document"></a>클라이언트 쪽 스크립트 문서를 보려면

1. **솔루션 탐색기** 에서 **스크립트 문서** 노드를 엽니다.

2. 보려는 스크립트 파일을 두 번 클릭합니다.

     클라이언트 쪽 스크립트 파일이 소스 창에서 열립니다.

## <a name="see-also"></a>참조
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)