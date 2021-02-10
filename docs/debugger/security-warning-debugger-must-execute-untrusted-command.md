---
title: '보안 경고: 디버거가 신뢰할 수 없는 명령을 실행해야 함 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d845719b758d3d64280337a1ab4138f2948ee97b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838992"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>보안 경고: 디버거가 신뢰할 수 없는 명령을 실행해야 함
이 경고 대화 상자는 소스 서버를 사용할 때 나타납니다. 이 경고는 소스 코드를 가져오기 위해 디버거에서 실행해야 하는 명령이 srcsvr.ini 파일에 포함된 소스 서버의 신뢰할 수 있는 명령 목록에 없음을 나타냅니다. 유효한 명령인 경우 srcsvr.ini 파일에 명령을 추가할 수 있으며, 그렇지 않은 경우에는 명령을 실행하지 않아야 합니다. 자세한 내용은 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

## <a name="message-text"></a>메시지 텍스트
 **소스 서버에서 소스 코드를 가져오기 위해 디버거가 신뢰할 수 없는 다음 명령을 실행해야 합니다.**

 **디버그 기호 파일(\*.pdb)의 출처를 알 수 없거나 신뢰할 수 없는 경우 이 명령을 실행하는 것은 잘못되거나 위험할 수 있습니다.**

 **이 명령을 실행하시겠습니까?**

## <a name="uielement-list"></a>UI 요소 목록
 텍스트 상자 - .pdb 파일에서 실행할 명령입니다.

 실행 - 명령을 실행할 수 있습니다.

 실행 안 함 - 명령 실행과 소스 서버에서의 파일 다운로드를 중지합니다.

## <a name="see-also"></a>참조
- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [디버거 보안](../debugger/debugger-security.md)
- [원본 서버](/windows/desktop/Debug/source-server-and-source-indexing)