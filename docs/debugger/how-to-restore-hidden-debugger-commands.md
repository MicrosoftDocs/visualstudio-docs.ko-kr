---
title: 숨겨진 디버거 명령 복원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, restoring commands
- debugging [Visual Studio], restoring commands
- commands, debugger
ms.assetid: 76ac9b77-f536-43b5-a9fc-984854b1c566
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 295d04aa33f7f6602d536a69baafae9105a51fe5
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852024"
---
# <a name="how-to-restore-hidden-debugger-commands"></a>방법: 숨겨진 디버거 명령 복원
Visual Studio를 설치할 때 주 프로그래밍 언어의 기본 IDE 설정 집합을 선택하는 단계가 있습니다. 일부 언어의 기본 IDE 설정에서는 특정 디버거 명령이 표시되지 않을 수 있습니다.

 기본 IDE 설정에 따라 숨겨진 디버거 기능을 사용하려면 다음 절차를 사용하여 명령을 메뉴에 다시 추가해야 합니다.

### <a name="to-restore-hidden-debugger-commands"></a>숨겨진 디버거 명령을 복원하려면

1. 프로젝트가 열려 있는 상태에서 **도구** 메뉴의 **사용자 지정**을 클릭합니다.

2. **사용자 지정** 대화 상자에서 **명령** 탭을 클릭합니다.

3. **메뉴 모음:** 드롭다운 목록에서 복원된 명령을 포함할 **디버그** 메뉴를 선택합니다.

4. **명령 추가...** 단추를 클릭합니다.

5. **명령 추가** 상자에서 추가할 명령을 선택하고 **확인**을 클릭합니다.

6. 다른 명령을 추가하려면 위 단계를 반복합니다.

7. 필요한 명령을 모두 메뉴에 추가하고 **닫기**를 클릭합니다.

    > [!WARNING]
    > 일부 메뉴 항목은 디버거가 실행 모드나 중단 모드 같은 특정 모드에 있을 때만 표시됩니다. 따라서 방금 추가한 항목이 이 단계를 완료한 직후에는 표시되지 않을 수도 있습니다.

## <a name="restoring-commands-not-available-from-the-customize-dialog-box"></a>사용자 지정 대화 상자에서 사용할 수 없는 명령 복원
 특히 계층 구조 메뉴에 있는 명령과 같은 일부 명령은 **사용자 지정** 대화 상자에서 복원할 수 없습니다. 이러한 명령을 복원하려면 IDE 설정의 새 컬렉션을 가져와야 합니다.

#### <a name="to-import-new-ide-settings"></a>새 IDE 설정을 가져오려면

1. **도구** 메뉴에서 **설정 가져오기 및 내보내기**를 선택합니다.

2. **설정 가져오기 및 내보내기 마법사 시작** 페이지에서 **선택한 환경 설정 가져오기**를 클릭하고 **다음**을 클릭합니다.

3. **현재 설정 저장** 페이지에서 기존의 설정을 저장할지 여부를 결정하고 **다음**을 클릭합니다.

4. **가져올 설정 모음 선택** 페이지의 **기본 설정** 폴더 아래에서 필요한 명령이 들어 있는 개발 설정 모음을 선택합니다. 어떤 모음을 선택해야 할지 알 수 없으면 대부분의 디버거 명령을 제공하는 **일반 개발 설정**이나 **Visual C++ 개발 설정**을 선택합니다.

5. **다음**을 클릭합니다.

6. **가져올 설정을 선택하세요.** 페이지의 **옵션** 아래에서 **디버깅**을 선택합니다. 함께 가져오려는 설정이 아닌 다른 모든 설정의 확인란은 선택을 해제합니다.

7. **마침**을 클릭합니다.

8. 설정을 다시 설정하는 데 관련된 오류가 있으면 **가져오기 완료** 페이지의 **자세히** 아래에서 해당 정보를 검토합니다.

9. **닫기**를 클릭합니다.

## <a name="see-also"></a>참조
- [디버거 보안](../debugger/debugger-security.md)
- [디버거 소개](../debugger/debugger-feature-tour.md)