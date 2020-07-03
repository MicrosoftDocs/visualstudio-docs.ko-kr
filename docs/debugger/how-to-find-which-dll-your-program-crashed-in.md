---
title: 방법 - 프로그램에서 충돌이 발생하는 DLL 찾기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 155fd74dc6e01f88bf04fe21b77ebdae6b04437f
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349538"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>방법: 프로그램에서 충돌이 발생하는 DLL 찾기(C#, C++, Visual Basic, F#)

 시스템 DLL 또는 다른 사람의 코드를 호출하는 동안 애플리케이션에 충돌이 발생하면 충돌 발생 시 활성 상태였던 DLL을 찾아야 합니다. 사용자 프로그램 외부에서 DLL에 충돌이 발생하는 경우 **모듈** 창을 사용하여 위치를 확인할 수 있습니다.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>모듈 창을 사용하여 충돌이 발생한 위치를 찾으려면

1. 충돌이 발생한 주소를 기록합니다.

    오류 메시지에 주소가 표시되지 않으면 다른 방법을 사용하여 DLL을 식별해야 할 수 있습니다. 시스템 DLL이 있다고 생각되면 디버깅할 때 Microsoft 기호 서버에서 [심볼을 로드](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)할 수 있습니다. 시스템 DLL이 없으면 대신에 힙 정보를 사용하여 [덤프 파일을 만들어야](../debugger/using-dump-files.md)할 수 있습니다. 다양한 [도구](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/)를 사용하여 덤프 파일을 만들 수 있습니다.

2. **디버그** 메뉴에서 **창**을 선택한 다음, **모듈**을 클릭합니다.

3. **모듈** 창에서 **주소** 열을 찾습니다. 이 열을 표시하려면 스크롤 막대를 사용해야 할 수도 있습니다.

4. 주소별로 DLL을 정렬하려면 열 맨 위에 있는 **주소** 단추를 클릭합니다.

5. 정렬된 목록을 조사하여 충돌 위치가 속하는 주소 범위를 가진 DLL을 찾습니다.

6. **이름** 및 **경로** 열에서 DLL 이름과 경로를 확인합니다.

## <a name="see-also"></a>참조
- [DLL 프로젝트 디버그](../debugger/debugging-dll-projects.md)
- [방법: 모듈 창 사용](../debugger/how-to-use-the-modules-window.md)