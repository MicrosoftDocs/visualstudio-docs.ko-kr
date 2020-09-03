---
title: '9단계: 기타 기능 사용 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 379fc9c28b8d36f7bd606719a443b16108f0095d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299971"
---
# <a name="step-9-try-other-features"></a>9단계: 기타 기능 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

아이콘과 색을 변경하고 게임 타이머와 소리를 추가하는 등 다른 작업을 더 시도해 볼 수 있습니다. 보드를 크게 하거나 타이머를 조정해 보면 게임을 더 흥미롭게 즐길 수 있습니다.

### <a name="to-try-other-features"></a>다른 기능을 테스트하려면

- 다른 옵션을 선택하여 아이콘 및 색을 바꿉니다.

    > [!TIP]
    > 레이블의 [Forecolor](https://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) 속성을 확인합니다.

- 플레이어가 승리하는 데 걸리는 시간을 추적하는 게임 타이머를 추가합니다.

    > [!TIP]
    > 이렇게 하려면 TableLayoutPanel 위의 폼에 경과된 시간을 표시하는 레이블을 추가하고, 시간을 추적하는 다른 하나의 타이머를 폼에 추가합니다. 코드를 사용하여 플레이어가 게임을 시작할 때 타이머가 시작되고 마지막 두 개의 아이콘을 일치시킨 후 타이머가 중지되도록 합니다.

- 플레이어가 일치 항목을 찾을 때 재생되는 소리, 일치하지 않는 두 아이콘을 발견할 때 재생되는 소리, 프로그램에서 다시 아이콘을 숨길 때 재생되는 소리를 각각 다르게 추가합니다.

    > [!TIP]
    > 소리를 재생하려면 System.media 네임스페이스를 사용하면 됩니다. 자세한 내용은 [Play Sounds in Windows Forms App (C# .NET)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be)(Windows Forms 앱에서 소리 재생(C# .NET)) 또는 [How To Play Audio In Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be)(Visual Basic에서 오디오를 재생하는 방법)을 참조하세요.

- 보드 크기를 늘려 게임 수준을 더 어렵게 만듭니다.

    > [!TIP]
    > TableLayoutPanel에 단순히 행과 열을 추가하는 것 이외의 작업을 수행해야 할 수 있으며, 생성한 아이콘 번호를 고려해야 할 수도 있습니다.

- 플레이어의 응답 속도가 너무 느리고 특정 시간 내에 두 번째 아이콘을 선택하지 않으면 첫 번째 아이콘을 숨겨 게임을 더 재미있게 만듭니다.

### <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 어려운 점이 있거나 프로그래밍 관련 질문이 있는 경우 MSDN 포럼에 질문을 게시해 보십시오. [Visual Basic 포럼](https://social.msdn.microsoft.com/Forums/en-US/home) 및 [Visual C# 포럼](https://social.msdn.microsoft.com/Forums/en-US/home)을 참조하세요.

- 훌륭한 비디오 학습 자료가 무료로 제공됩니다. Visual Basic 프로그래밍에 대 한 자세한 내용은 [Visual Basic 기본 사항: 절대 초보자를 위한 개발](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)을 참조 하세요. Visual C#의 프로그래밍에 대한 자세한 내용은 [C# Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)(C# 기초: 완전 초보자를 위한 개발)를 참조하세요.

- 이전 자습서 단계로 돌아가려면 [8 단계: 플레이어의 추가를 확인 하는 메서드 추가](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)를 참조 하세요.
