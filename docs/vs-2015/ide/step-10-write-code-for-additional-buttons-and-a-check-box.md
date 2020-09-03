---
title: '10단계: 추가 단추 및 확인란의 코드 작성 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24152bf2e6acfcb1ed20b75a5c817e0336cdd4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851589"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>10단계: 추가 단추 및 확인란의 코드 작성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이제 다른 네 메서드를 완료할 준비가 되었습니다. 지금 이 코드를 복사하여 붙여넣을 수도 있지만 이 자습서의 내용을 최대한 학습하려면 이 코드를 입력하고 IntelliSense를 사용합니다.

 이 코드는 앞서 추가한 단추에 기능을 추가합니다. 이 코드가 없으면 단추로 어떤 작업도 수행되지 않습니다. 단추에서는 `Click` 이벤트의 코드를 사용하고 확인란에서는 `CheckChanged` 이벤트를 사용하여 컨트롤을 활성화했을 때 서로 다른 작업을 수행합니다. 예를 들어 **그림 지우기** 단추를 선택하면 활성화되는 `clearButton_Click` 이벤트는 해당 `Image` 속성을 `null` 또는 `nothing`으로 설정하여 현재 이미지를 지웁니다. 코드의 각 이벤트에는 코드의 기능에 대해 설명하는 주석이 포함되어 있습니다.

 ![비디오에 연결](../data-tools/media/playvideo.gif "링크 playvideo 보려면") 이 항목의 비디오 버전을 보려면 [자습서 1: Visual Basic에서 사진 뷰어 만들기-비디오 5](https://msdn.microsoft.com/vbasic/gg315356.aspx) 또는 [자습서 1: c #에서 사진 뷰어 만들기-비디오 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx)를 참조 하십시오. 이러한 비디오에서는 이전 버전의 Visual Studio를 사용하므로 일부 메뉴 명령과 기타 사용자 인터페이스 요소가 약간 다를 수 있습니다. 그러나 개념 및 절차는 Visual Studio의 현재 버전에서 비슷하게 작동합니다.

> [!NOTE]
> 가장 좋은 방법은 항상 코드를 주석 처리하는 것입니다. 주석은 코드를 읽는 사용자의 이해를 돕기 위한 것으로, 프로그램에서는 주석 줄에 있는 모든 내용을 무시합니다. Visual C#에서는 두 개의 슬래시(//)로 주석 줄을 시작하고, Visual Basic에서는 작은따옴표(')로 주석 줄을 시작합니다.

### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>추가 단추 및 확인란에 대한 코드를 작성하려면

- 다음 코드를 Form1 코드 파일(Form1.cs 또는 Form1.vb)에 추가합니다. Visual Basic 코드를 보려면 **VB** 탭을 선택합니다.

     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]

### <a name="to-continue-or-review"></a>계속하거나 검토하려면

- 다음 자습서 단계로 이동 하려면 [11 단계: 프로그램 실행 및 기타 기능 시도](../ide/step-11-run-your-program-and-try-other-features.md)를 참조 하세요.

- 이전 자습서 단계로 돌아가려면 [9 단계: 코드 검토, 주석 처리 및 테스트](../ide/step-9-review-comment-and-test-your-code.md)를 참조 하세요.
