---
title: DSL 정의에 확장 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fab56a7738ed7b52760cf20a5bfcc8542ee5a23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919053"
---
# <a name="adding-extensions-to-dsl-definitions"></a>DSL 정의에 확장 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 정의 확장을 사용 하면 DSL (도메인별 언어)에 대 한 확장 패키지를 만들 수 있습니다. VSIX (Visual Studio Integration Extension)에 포함 된 DSL 확장은 DSL과 동일한 방식으로 사용자의 컴퓨터에 설치할 수 있습니다. 추가 기능은 런타임에 동적으로 사용 하도록 설정 하 고 비활성화할 수 있습니다. Dsl은 확장을 위해 명시적으로 설계 하지 않아도 되며 확장 된 DSL을 변경 하지 않고 나중에 또는 제 3 자가 확장을 디자인할 수 있습니다.

 추가 기능에는 다음이 포함 될 수 있습니다.

- 모델 및 프레젠테이션 요소의 속성

- 데코레이터 셰이프 및 연결선

- 클래스, 관계, 모양 및 연결선

- 유효성 검사 제약 조건

- 도구 상자 항목 및 탭

  확장 된 DSL의 사용자는 추가 기능의 인스턴스를 포함 하는 모델을 만들고 저장할 수 있으며, 이러한 모델은 적절 한 확장을 설치한 다른 사용자가 읽을 수 있습니다. 확장을 설치 하지 않은 사용자는 추가 기능을 사용할 수 없지만 추가 기능을 잃지 않고도 모델을 업데이트 하 고 저장할 수 있습니다.

  예제 코드 및이 기능에 대 한 자세한 내용은 [Visual Studio 시각화 및 모델링 SDK](https://www.microsoft.com/en-us/download/details.aspx?id=48148) 웹 사이트를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [Visual Studio Visualization and Modeling SDK](https://www.microsoft.com/en-us/download/details.aspx?id=48148)
