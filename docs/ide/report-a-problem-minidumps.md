---
title: 모든 호출 스택을 사용하여 미니덤프 만들기
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 7b3be91e5d0d2e1f14724dd647670fc4885bcd4d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271191"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>모든 호출 스택을 사용하여 Visual Studio 프로세스에 대한 미니덤프 만들기

일부 경우 Microsoft는 모든 호출 스택에 대한 정보를 사용하여 실행 중인 Visual Studio 프로세스의 미니덤프를 요청할 수 있습니다. 이 정보를 수집하려면 다음 단계를 수행합니다.

## <a name="create-the-minidump-file"></a>미니덤프 파일 만들기

1. Visual Studio의 새 인스턴스를 시작합니다.
1. 주 메뉴에서 **디버그** > **프로세스에 연결**을 선택합니다.
1. 관련된 **관리** 확인란 및 **원시** 확인란을 선택하고 **첨부**를 누릅니다.

   ![프로세스에 연결](../ide/media/attach-to-process.png)

1. 실행 중인 프로세스 목록에서 연결할 다른 Visual Studio 인스턴스를 선택합니다.
1. 주 메뉴에서 **디버그** > **모두 중단**을 선택합니다.
1. 주 메뉴에서 **디버그** > **다른 이름으로 덤프 저장**을 선택합니다.

## <a name="get-the-call-stacks-from-the-minidump"></a>미니덤프에서 호출 스택 가져오기

1. Visual Studio에서 덤프 파일을 엽니다.
1. **도구** > **옵션** > **디버깅** > **기호**로 이동하여 **Microsoft 기호 서버**가 **기호 파일(.pdb) 위치**에서 선택되었는지 확인합니다.
1. **명령** 창(**보기** > **다른 창** > **명령 창**) 열기
1. ‘~*k’를 입력합니다. 모든 스레드의 호출 스택이 창에 표시됩니다.
1. 명령 창에서 모든 텍스트를 복사하고 텍스트 파일에 저장합니다.
1. txt 파일을 버그에 첨부합니다.
