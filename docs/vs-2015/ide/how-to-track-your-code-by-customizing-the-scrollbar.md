---
title: '방법: 스크롤 막대를 사용자 지정하여 코드 추적 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a852b0e5ac6c6a677caab97279a0b0cb0299d27f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670632"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>How to: Track Your Code by Customizing the Scrollbar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

긴 코드 파일을 사용하는 경우 모든 내용을 기억하기 어려울 수 있습니다. 코드에서 수행되는 작업을 간략하게 볼 수 있도록 코드 창의 스크롤 막대를 사용자 지정할 수 있습니다.

### <a name="to-show-annotations-on-the-scroll-bar"></a>스크롤 막대에 주석을 표시하려면

1. 코드 변경 내용, 중단점, 오류 및 책갈피를 표시하도록 스크롤 막대를 설정할 수 있습니다.

     **스크롤 막대** 옵션 페이지를 엽니다 (**도구, 옵션 텍스트 편집기). 모든 언어** 또는 특정 언어 또는 빠른 실행 창에서 **스크롤 막대** 를 입력 합니다.

2. **세로 스크롤 막대 위에 주석 표시**를 선택한 다음 표시할 주석을 선택합니다. **표시** 옵션에는 중단점 및 책갈피가 포함됩니다.

3. 이제 사용해 보세요. 많은 코드 파일을 열고 파일의 여러 위치에서 발생 하는 항목을 바꿉니다. 스크롤 막대에 바꾸기 결과가 표시되므로, 작업을 잘못 바꾼 경우 변경 내용을 취소할 수 있습니다.

     문자열을 검색한 후 스크롤 막대가 표시되는 모양은 다음과 같습니다. 문자열의 모든 인스턴스가 표시되는지 확인합니다.

     ![문자열을 찾은 후 스크롤 막대](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")

     문자열의 모든 인스턴스를 바꾼 후 스크롤 막대는 다음과 같습니다. 작업으로 인해 일부 문제가 발생했음을 즉시 확인할 수 있습니다.

     ![오류가 있는 문자열을 바꾼 후 스크롤 막대](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")

### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>스크롤 막대의 디스플레이 모드를 설정하려면

1. 스크롤 막대에는 막대 모드(기본값) 및 지도 모드의 두 가지 모드가 있습니다. 막대 모드에서는 스크롤 막대에 주석 표시기만 표시됩니다. 지도 모드에서는 코드 줄이 스크롤 막대에 표시됩니다. 줄에 포인터를 놓을 때 기본 코드를 표시할지 여부와 줄 너비를 선택할 수 있습니다. 스크롤 막대의 한 위치를 클릭하면 커서가 코드에서 해당 위치로 이동합니다. 축소된 영역은 다르게 회색으로 표시되며, 두 번 클릭하면 확장됩니다.

     **스크롤 막대** 옵션 페이지에서 **세로 스크롤 막대에 막대 모드 사용** 또는 **세로 스크롤 막대에 지도 모드 사용**을 선택합니다. **소스 개요** 드롭다운에서 너비를 선택할 수 있습니다.

     지도 모드가 설정되고 너비가 보통으로 설정된 경우 검색 예제가 표시되는 모양은 다음과 같습니다.

     ![맵 모드의 스크롤 막대](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")

2. 지도 모드에서 스크롤 막대 위/아래로 커서를 이동할 때 코드 미리 보기를 사용하도록 설정하려면 **미리 보기 도구 설명 표시** 옵션을 선택합니다. 다음과 같이 표시됩니다.

     ![도구 설명이 있는 스크롤 막대](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")

     지도 모드 스크롤 동작 및 미리 보기 도구 설명을 유지하지만 소스 코드 개요를 표시하지 않으려는 경우 **소스 개요**를 **해제**로 설정할 수 있습니다.
