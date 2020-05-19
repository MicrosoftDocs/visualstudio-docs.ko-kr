---
title: '오류: 프로세스의 ID를 검사할 수 있는 권한이 없음 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cad229f80676c3d1f7a7d23ad7a29729c834929b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736230"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>오류: 프로세스의 ID를 검사할 수 있는 권한이 없습니다.
프로세스의 ID를 검사할 수 있는 권한이 없습니다. 시스템의 구성에 문제가 있는 것 같습니다.

 디버깅에 필요한 정보인 프로세스 ID를 디버거에서 검사할 수 없습니다. 이는 터미널 서비스가 해제되었기 때문일 가능성이 높습니다. 터미널 서비스는 기본적으로 사용됩니다. 이 서비스를 다시 사용하려면 다음 단계에 따릅니다.

### <a name="to-enable-terminal-services"></a>터미널 서비스를 사용하려면

1. **시작**을 클릭한 다음, **제어판**을 선택합니다.

2. 제어판에서 필요한 경우 **클래식 보기로 전환**을 선택한 다음, **관리 도구**를 두 번 클릭합니다.

3. **관리 도구** 창에서 **컴퓨터 관리**를 두 번 클릭합니다.

4. 컴퓨터 관리 창에서 **서비스 및 애플리케이션** 노드를 확장합니다.

5. **서비스 및 애플리케이션**에서 **서비스**를 클릭합니다.

     오른쪽 창에 서비스 목록이 표시됩니다.

6. **서비스** 목록에서 **터미널 서비스**를 마우스 오른쪽 단추로 클릭한 다음, **속성**을 선택합니다.

7. **터미널 서비스 속성** 창의 **일반** 탭으로 이동하고 **시작 유형**을 **수동**으로 설정합니다.

8. **확인**을 클릭합니다.

9. 컴퓨터를 다시 시작합니다.

     이렇게 해도 원격 데스크톱은 자동으로 사용되지 않습니다. 컴퓨터에서 원격 데스크톱을 사용하려면 다음 절차를 추가로 수행합니다.

### <a name="to-enable-remote-desktop"></a>원격 데스크톱을 사용하려면

1. **시작**을 클릭한 다음, **내 컴퓨터**를 마우스 오른쪽 단추로 클릭합니다.

2. **속성**을 선택합니다.

     **시스템 속성** 창이 표시됩니다.

3. **원격**을 클릭합니다.

4. **원격 데스크톱** 아래에서 **사용자가 이 컴퓨터에 원격으로 연결할 수 있음**을 선택합니다.

5. **확인**을 클릭합니다.

## <a name="see-also"></a>참조
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)