---
title: 문제 해결
description: Mac용 Visual Studio 사용자를 위한 일반적인 문제 및 해결
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 6073e0bf2a601bf5183798a1df4fd835d0b93427
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985157"
---
# <a name="troubleshooting"></a>문제 해결

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 로그 보기

로그를 확인하려면 아래 그림과 같이 **도움말 > 로그 디렉터리 열기** 메뉴 항목으로 이동합니다.

![로그 디렉터리 열기 메뉴 항목](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>예외 사항 보기

예외가 catch되면 예외 풍선이 나타납니다. 자세한 내용을 보려면 **자세히 보기** 단추를 선택합니다.

![예외 자세히 보기](media/troubleshooting-image2.png)

그러면 예외에 대한 정보를 자세히 보여주는 **세부 정보 표시** 대화 상자가 나타납니다.

![세부 정보 대화 상자 표시](media/troubleshooting-image3.png)

위 대화 상자에서 번호가 매겨진 중요 섹션에 대한 자세한 설명은 아래와 같습니다.

1. 예외 형식으로서, 관찰된 예외 형식의 전체 이름을 표시합니다.
2. 예외 메시지로서, 예외 개체의 메시지 속성 값을 표시합니다.
3. 내부 예외 형식으로서, 내부 예외 트리 뷰에서 현재 선택한 예외에 대한 예외 형식의 전체 이름을 표시합니다.
4. 내부 예외 메시지로서, 내부 예외 트리 뷰에서 선택한 예외의 메시지 속성 값을 표시합니다.
5. 스택 추적 보기입니다. 노출 화살표로 축소할 수 있으며 스택 프레임 항목을 포함합니다.
6. 사용자 코드가 아닌 항목의 예입니다.
7. 사용자 코드 항목의 예입니다.
8. 속성 보기로서, 예외의 모든 속성과 필드를 표시합니다. 노출 화살표로 축소할 수 있습니다.
9. 내부 예외 트리 뷰입니다. 이 뷰에서 키보드의 위/아래 화살표 키, 마우스 또는 트랙패드로 내부 예외를 선택합니다.
10. 기본적으로 디버거 설정의 **프로젝트 코드만 디버깅합니다.** 옵션과 동일하게 설정됩니다. 이 확인란을 선택하면 사용자 코드가 아닌 모든 코드가 스택 추적에서 한 줄로 축소됩니다.
11. `exception.ToString()` 출력을 클립보드로 복사하는 복사 단추입니다.

이러한 섹션 중 일부는 예외에 내부 예외가 포함되는 경우에만 표시됩니다.

## <a name="see-also"></a>참고 항목

- [IDE 오류 문제 해결을 위한 리소스(Windows의 Visual Studio)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)