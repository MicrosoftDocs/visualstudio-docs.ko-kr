---
title: '방법: 스크립트 문서 보기 | Microsoft Docs'
ms.date: 11/05/2019
ms.topic: conceptual
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
ms.openlocfilehash: 5e362e0504c4ed2584bbbbea687fe3c58fc79edb
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714434"
---
# <a name="how-to-view-script-documents-javascript"></a>방법: 스크립트 문서 보기(JavaScript)

서버 쪽 스크립트 파일은 솔루션 탐색기에 표시됩니다. 클라이언트 쪽 스크립트 파일은 디버그 모드나 중단 모드에서만 표시되며 클라이언트 쪽 스크립트 파일은 **스크립트 문서** 노드에 표시됩니다.

페이지를 동적으로 생성하는 일부 애플리케이션 유형의 경우 브라우저에 로드되는 스크립트 문서에서 중단점을 설정할 때 중단 모드 및 디버그를 쉽게 시작할 수 있습니다. 마찬가지로 로드된 스크립트 문서에서 `debugger` 문을 추가하여 중단 모드를 시작할 수 있습니다. 이 문서에서는 문서를 보는 방법을 설명합니다.

> [!NOTE]
> [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 이전에서는 서버 쪽 스크립트에서 생성된 클라이언트 쪽 스크립트 파일이 스크립트 탐색기 창에 나타납니다.

### <a name="to-view-a-server-side-script-document"></a>서버 쪽 스크립트 문서를 보려면

1. **솔루션 탐색기**에서 **\<웹 사이트 경로 이름>** 노드를 엽니다.

2. 보려는 스크립트 파일을 두 번 클릭합니다.

     서버 쪽 스크립트 파일이 소스 창에 열립니다.

### <a name="to-view-a-client-side-script-document"></a>클라이언트 쪽 스크립트 문서를 보려면

1. **솔루션 탐색기**에서 **스크립트 문서** 노드를 엽니다.

2. 보려는 스크립트 파일을 두 번 클릭합니다.

     클라이언트 쪽 스크립트 파일이 소스 창에서 열립니다.

## <a name="see-also"></a>참조
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)