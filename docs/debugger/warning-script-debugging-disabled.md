---
title: '경고: 스크립트 디버깅 사용 안 함 | Microsoft Docs'
description: “스크립트 디버깅 사용 안 함” 경고는 Internet Explorer에서 스크립트 디버깅을 사용할 수 없는 상태에서 스크립트를 디버그할 때 발생합니다. 해당 기능을 사용하도록 설정하는 단계를 확인합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 052445b1dbb69c433220caf5764413e04f0909fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884002"
---
# <a name="warning-script-debugging-disabled"></a>경고: 스크립트 디버깅 사용 안 함
Internet Explorer에서는 현재 스크립트 디버깅을 사용하지 않습니다.

 이 경고는 Internet Explorer에서 스크립트 디버깅을 사용할 수 없는 상태에서 스크립트를 디버깅할 때 발생합니다. 보안상의 이유로 Internet Explorer에서는 스크립트 디버깅을 기본적으로 사용하지 않습니다.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Internet Explorer에서 스크립트 디버깅을 사용하려면

1. Internet Explorer의 **도구** 메뉴에서 **인터넷 옵션** 을 선택합니다.

2. **인터넷 옵션** 대화 상자에서 **고급** 탭을 클릭합니다.

3. **고급** 탭의 **설정** 상자에서 **탐색** 범주를 찾습니다.

4. **스크립트 디버깅 사용 안 함(Internet Explorer)** 의 선택을 취소합니다.

5. **확인** 을 클릭합니다.

6. Internet Explorer를 종료하고 다시 시작합니다.

     그러면 새 설정이 적용됩니다.

## <a name="see-also"></a>참조
- [방법: 스크립트에 연결](attach-to-running-processes-with-the-visual-studio-debugger.md)