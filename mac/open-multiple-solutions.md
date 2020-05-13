---
title: '방법: 여러 솔루션 열기'
description: Mac용 Visual Studio에서 둘 이상의 솔루션을 여는 방법 및 둘 이상의 애플리케이션 인스턴스를 여는 방법을 알아봅니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/02/2019
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.openlocfilehash: 4d676f6109c97ae883473a35721f9207e72a6da4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "68872354"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Mac용 Visual Studio의 여러 솔루션 또는 인스턴스 열기

Mac에서 Mac용 Visual Studio를 포함한 모든 애플리케이션은 기본적으로 _단일 인스턴스_ 앱입니다. 즉, 사용하려는 애플리케이션이 이미 열려 있는 경우(도크의 아이콘 아래에 점으로 표시됨), 아이콘을 다시 선택하면 새 인스턴스가 아닌 실행 중인 인스턴스가 열립니다. [다음 섹션](#open-a-second-instance-of-visual-studio-for-mac)에 설명된 대로 애플리케이션의 추가 인스턴스가 필요한 경우 시스템에 열라는 메시지를 표시할 수 있습니다.

또한 솔루션을 열면 기본 동작은 새 작업 영역에서 솔루션을 열고 현재 작업 영역을 닫는 것입니다(필요한 경우). [두 번째 솔루션 열기](#open-a-second-solution-inside-a-single-instance) 섹션에 설명된 대로 현재 작업 영역이 열린 상태로 유지하여 이 기본 동작을 재정의할 수 있습니다.

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Mac용 Visual Studio의 두 번째 인스턴스 열기

IDE(통합 개발 환경)의 두 번째 인스턴스를 열려면 dock 또는 **애플리케이션** 폴더에서 Visual Studio 아이콘을 마우스 오른쪽 단추로 클릭하고 **새 인스턴스**를 선택합니다.

![마우스 오른쪽 단추로 클릭한 Visual Studio 아이콘의 새 인스턴스 메뉴 옵션 스크린샷](media/open-new-instance.png)

## <a name="open-a-second-solution-inside-a-single-instance"></a>단일 인스턴스 내에서 두 번째 솔루션 열기

첫 번째 솔루션과 함께 두 번째 솔루션을 열려면 다음 단계를 사용합니다.

1. 첫 번째 솔루션을 열고 **파일** > **열기**를 선택합니다.
2. 기존 솔루션을 찾으려면 파일 시스템을 검색합니다.
3. **.sln** 파일을 선택하고 **옵션**을 선택합니다.

    ![.sln 파일 및 옵션이 강조 표시된 Mac용 Visual Studio 스크린샷](media/open-multiple-solutions-image3.png)

4. **현재 작업 영역 닫기** 확인란의 선택을 취소합니다.

    ![현재 작업 영역 닫기 확인란이 선택 취소된 옵션 대화 상자 스크린샷](media/open-multiple-solutions-image1.png)

5. **열기**를 선택하여 Solution Pad에서 두 번째 솔루션을 엽니다.

또는 솔루션을 최근에 열었다면 다음 단계를 사용할 수 있습니다.

1. **파일** > **최근 솔루션**으로 이동합니다.

    ![최근 솔루션 메뉴 스크린샷](media/open-multiple-solutions-image2.png)

1. **Ctrl** 키를 누른 채로 솔루션을 선택합니다. 이 조합은 Solution Pad에서 두 번째 솔루션을 엽니다.

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
