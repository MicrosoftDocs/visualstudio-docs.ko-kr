---
description: 스크립트가 현재 페이지의 호스트가 아닌 다른 소스에서 데이터에 액세스하려고 했습니다.
title: 액세스가 거부 되었습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 6be3bce0643a5892973235871191766cac140962
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571937"
---
# <a name="access-is-denied"></a>액세스 거부됨
스크립트가 현재 페이지의 호스트가 아닌 다른 소스에서 데이터에 액세스하려고 했습니다. Internet Explorer 및 다른 브라우저가 따르는 동일 원본 정책에서는 스크립트가 현재 페이지 URL의 체계, 호스트 및 포트와 동일한 소스의 데이터만 액세스할 수 있습니다.  
  
 예를 들어 현재 페이지가 인 경우 `https://employees.mycompany.com` 다음 url에서 데이터에 액세스할 수 없습니다.  
  
- `http://data.contoso.com`HTTPS 대신 HTTP를 사용 하 고 있기 때문입니다.  
  
- `https://somedatasource.com`는 다른 도메인입니다.  
  
- `https://employees.mycompany.com:8888`다른 포트를 사용 하기 때문입니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 호출하려는 API가 원본 간 스크립팅을 안전하게 허용하는 두 가지 접근 방식인 JSONP 또는 CORS를 지원하는지 여부를 조사합니다.  
  
- REST API를 호출하려는 경우 이 호출을 서버 쪽 코드로 리팩터링한 다음 클라이언트 쪽 스크립트에 대해 새 REST 엔드포인트를 노출합니다.  
  
     자세한 내용은 동일 원본 정책, JSONP 및 CORS와 관련된 온라인 설명서를 참조하세요.
