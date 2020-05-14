---
title: '9단계: 기타 기능 사용'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32ac2f1977bb0b8b391651ed7ed459b9dc560330
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579739"
---
# <a name="step-9-try-other-features"></a>9단계: 기타 기능 사용
아이콘과 색을 변경하고 게임 타이머와 소리를 추가하는 등 다른 작업을 더 시도해 볼 수 있습니다. 보드를 크게 하거나 타이머를 조정해 보면 게임을 더 흥미롭게 즐길 수 있습니다.

샘플의 전체 버전을 다운로드하려면 [Complete matching game tutorial sample](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba)(전체 일치 게임 자습서 샘플)을 참조하세요.

## <a name="to-try-other-features"></a>다른 기능을 테스트하려면

- 다른 옵션을 선택하여 아이콘 및 색을 바꿉니다.

    > [!TIP]
    > 레이블의 [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) 속성을 확인합니다.

- 플레이어가 승리하는 데 걸리는 시간을 추적하는 게임 타이머를 추가합니다.

    > [!TIP]
    > 이렇게 하려면 <xref:System.Windows.Forms.TableLayoutPanel> 위의 폼에 경과된 시간을 표시하는 레이블을 추가하고, 시간을 추적하는 다른 하나의 타이머를 폼에 추가합니다. 코드를 사용하여 플레이어가 게임을 시작할 때 타이머가 시작되고 마지막 두 개의 아이콘을 일치시킨 후 타이머가 중지되도록 합니다.

- 플레이어가 일치 항목을 찾을 때 재생되는 소리, 일치하지 않는 두 아이콘을 발견할 때 재생되는 소리, 프로그램에서 다시 아이콘을 숨길 때 재생되는 소리를 각각 다르게 추가합니다.

    > [!TIP]
    > 소리를 재생하려면 <xref:System.Media> 네임스페이스를 사용할 수 있습니다. 자세한 내용은 [Play sounds in Windows Forms app (C#)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be)(Windows Forms 앱에서 소리 재생(C#)) 또는 [How to play audio in Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be)(Visual Basic에서 오디오를 재생하는 방법)을 참조하세요.

- 보드 크기를 늘려 게임 수준을 더 어렵게 만듭니다.

    > [!TIP]
    > TableLayoutPanel에 단순히 행과 열을 추가하는 것 이외의 작업을 수행해야 할 수 있으며, 생성한 아이콘 번호를 고려해야 할 수도 있습니다.

- 플레이어의 응답 속도가 너무 느리고 특정 시간 내에 두 번째 아이콘을 선택하지 않으면 첫 번째 아이콘을 숨겨 게임을 더 재미있게 만듭니다.

## <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 훌륭한 비디오 학습 자료가 무료로 제공됩니다. Visual Basic의 프로그래밍에 대한 자세한 내용은 [Visual Basic 기초: 완전 초보자를 위한 개발](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners)을 참조하세요. C# 프로그래밍에 대한 자세한 내용은 [C# 기초: 완전 초보자를 위한 개발](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)을 참조하세요.

- 이전 자습서 단계로 돌아가려면 [8단계: 게임 플레이어가 이겼는지 여부를 확인하는 메서드 추가](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)를 참조하세요.
