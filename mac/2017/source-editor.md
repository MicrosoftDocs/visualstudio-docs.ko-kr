---
title: 소스 편집기
description: Mac용 Visual Studio에서 소스 편집기 사용
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: 187805767e9f67851975dccf8513c708c4233ccc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985211"
---
# <a name="source-editor"></a>소스 편집기

코드를 간결하고 효율적으로 작성하려면 신뢰할 수 있는 소스 편집기가 꼭 필요합니다. Mac용 Visual Studio에서 제공하는 정교한 소스 편집기는 IDE 상호 작용의 핵심을 이룹니다. 소스 편집기는 구문 강조 표시, 코드 조각, 코드 접기 등의 기초적인 기능부터 Roslyn 컴파일러 통합에 따르는 완벽한 기능의 IntelliSense 코드 완성과 같은 이점에 이르기까지 작업의 편의성을 높여 주는 기능을 다양하게 제공합니다.

Mac용 Visual Studio의 소스 편집기에서는 디버깅, 리팩터링, 버전 제어 통합 등 IDE의 다른 모든 기능을 원활하게 사용할 수 있습니다.

이 문서에서는 소스 편집기의 주요 기능 중 일부를 소개하고 Mac용 Visual Studio의 생산성을 극대화하는 방법을 살펴봅니다.

## <a name="the-source-editor-experience"></a>소스 편집기 환경

코드 전체를 효율적으로 보면서 탐색하는 작업은 개발 워크플로에서 필수적인 부분입니다. 코드를 살펴보고 유지 관리하는 방법은 개발자 개인마다 다르며, 프로젝트마다 다르기도 합니다.

Mac용 Visual Studio는 플랫폼 간 개발을 최대한 편리하고 실용적으로 진행할 수 있도록 하는 효과적인 기능을 다양하게 제공합니다. 다음 섹션에서는 몇 가지 주요 사항에 대해 설명합니다.

## <a name="code-folding"></a>코드 접기

개발자는 코드 접기를 사용하여 using 지시문, 상용구 코드 및 주석, #region 명령문 등의 전체 코드 섹션을 표시하거나 숨김으로써 대규모 소스 코드 파일을 더욱 쉽게 ​​관리할 수 ​​있습니다. 코드 접기는 Mac용 Visual Studio에서 기본적으로 해제되어 있습니다.

코드 접기를 설정하려면 **Visual Studio > 기본 설정 > 텍스트 편집기 > 일반 > 코드 접기**로 이동합니다.

![코드 접기 옵션](media/source-editor-image1.png)

이 메뉴에는 기본적으로 #regions 및 주석을 접고 코드 대신 명명된 힌트를 표시하는 옵션도 포함되어 있습니다.

섹션을 표시하거나 숨기려면 줄 번호 옆의 노출 위젯을 사용합니다.

![코드의 섹션 표시 또는 숨기기](media/source-editor-image2.png)

**보기 > 접기 > 접기 토글/모든 접기 토글** 메뉴 항목을 사용하면 접기 표시 및 숨기기를 서로 전환할 수도 있습니다.

![접기 메뉴 항목](media/source-editor-image19.png)

이 메뉴 항목으로 코드 접기를 사용하거나 사용하지 않도록 설정할 수도 있습니다.

## <a name="white-space"></a>공백

소스 코드에서 보이지 않는 문자를 표시해야 하는 경우도 있습니다. 이는 코딩 표준을 준수하고 불필요한 공간 낭비를 방지하는 수단이 됩니다. 또한 정확한 줄 들여쓰기가 품질을 좌우하는 F# 코드를 작성할 때 유용합니다.

**Visual Studio > 기본 설정 > 텍스트 편집기 > 표식 및 눈금자**로 이동하여 공백을 표시하는 옵션을 설정합니다. 이 옵션을 선택하면 보이지 않는 문자를 표시할 _경우_ 를 안 함(Never), 선택 시(On Selection), 항상(Always) 중 하나로 설정할 수 있습니다.

![보이지 않는 문자 표시 옵션](media/source-editor-image3.png)

탭, 공백 및 줄 끝을 표시하는 옵션도 사용할 수 있습니다.

![탭 및 공백 표시](media/source-editor-image4.png)

보이지 않는 문자는 다음 이미지와 같이 회색 점으로 표시됩니다.

![공백 표시](media/source-editor-image22.png)

## <a name="ruler"></a>눈금자

열 눈금자는 줄의 길이를 확인할 때, 특히 줄 길이를 규정해 놓은 팀에서 작업할 때 특히 유용합니다. 다음 이미지에 설명된 대로 **Visual Studio > 기본 설정 > 텍스트 편집기 > 표식 및 눈금자**로 이동한 다음, **열 눈금자 표시**를 선택하거나 선택 취소하여 열 눈금자를 켜거나 끌 수 있습니다.

!["열 눈금자 표시"가 강조 표시된 기본 설정 대화 상자](media/source-editor-image5.png)

 눈금자는 소스 편집기에서 연한 회색 선으로 표시됩니다.

## <a name="highlight-identifier-references"></a>식별자 참조 강조 표시

“식별자 참조 강조 표시” 옵션을 사용하면 소스 코드에서 기호를 선택할 때 소스 편집기에서 해당 파일의 다른 모든 참조를 시각적으로 알려줍니다. 이 옵션을 켜려면 다음 이미지에 설명된 대로 **Visual Studio > 기본 설정 > 텍스트 편집기 > 표식 및 눈금자**로 이동한 다음, _식별자 참조 강조 표시_를 선택합니다.

!["식별자 참조 강조 표시"가 강조 표시된 기본 설정 대화 상자](media/source-editor-image6.png)

강조 표시의 색으로 할당 또는 참조 여부를 구분할 수도 있습니다. 할당은 빨간색으로, 참조는 파란색으로 강조 표시됩니다.

![강조 표시 색을 보여주는 예제](media/source-editor-image7.png)

## <a name="see-also"></a>참고 항목

- [코드 편집기의 기능(Windows의 Visual Studio)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [개요(Windows의 Visual Studio)](/visualstudio/ide/outlining)