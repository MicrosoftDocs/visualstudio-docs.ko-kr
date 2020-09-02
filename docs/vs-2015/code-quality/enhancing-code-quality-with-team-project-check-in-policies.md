---
title: 팀 프로젝트 체크 인 정책을 사용 하 여 코드 품질 향상 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eaf95bdba84d116198bf332e3cf2725f5e95e614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75848224"
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>팀 프로젝트 체크 인 정책을 사용하여 코드 품질 향상
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TFVC(Team Foundation Version Control)를 사용할 때는 팀 프로젝트에 대한 체크 인 정책을 만들어 코드 품질을 향상시키고 그룹 개발을 보다 효율적으로 수행할 수 있게 해주는 방법을 적용할 수 있습니다. 체크 인 정책은 팀 프로젝트 수준에서 설정되어 코드 체크 인이 허용되기 전에 개발자 컴퓨터에서 적용되는 규칙입니다.

 다음과 같은 팀 프로젝트 체크 인 정책을 지정할 수 있습니다.

- **빌드**: 새로 체크 인하기 전에 빌드 중 생성된 빌드 중단을 수정해야 합니다.

- **변경 집합 주석**: 변경 내용을 체크 인할 때 사용자가 주석을 제공해야 합니다.

- **코드 분석**: 체크 인하기 전에 코드 분석을 실행해야 합니다.

- **작업 항목**: 체크 인에 하나 이상의 작업 항목을 연결해야 합니다.

> [!IMPORTANT]
> 체크 인 정책을 사용하려면 [!INCLUDE[vststfsLong](../includes/vststfslong-md.md)]에 연결해야 합니다.

## <a name="common-tasks"></a>일반 태스크

|Task|지원 콘텐츠|
|----------|------------------------|
|**체크 인 정책 만들기 및 사용:**[!INCLUDE[esprscc](../includes/esprscc-md.md)]의 팀 프로젝트 설정을 사용하여 체크 인 정책을 만듭니다.|[품질 게이트 설정 및 적용](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**코드 분석 체크 인 정책 만들기 및 사용:** 표준 코드 분석 규칙 집합에서 선택하거나 사용자 지정 집합을 만들 수 있습니다.|[코드 분석 체크 인 정책 만들기 및 사용](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>관련 작업

|Task|지원 콘텐츠|
|----------|------------------------|
|**개발 환경 설정:** 코드를 만들거나 수정하려면 먼저 적절한 소스 코드를 사용하여 개발 및 테스트 환경을 설정해야 합니다. 데이터베이스로 작업하는 경우 해당 오프라인 표현에도 액세스할 수 있어야 합니다.|[개발 환경 설정](https://msdn.microsoft.com/7b686610-d379-4ca0-9608-73ef0e576e3a)|
|**개발 프로세스에서 코드 분석 사용:** 팀 멤버는 해당 개발 컴퓨터에서 코드 분석을 실행합니다. Visual Studio에서 개발자는 개별 코드 프로젝트에 대해 코드 분석 실행을 구성 및 실행하고, 해당 실행을 통해 발견된 문제를 확인 및 분석하며, 경고에 대한 작업 항목을 만듭니다.|[애플리케이션 품질 분석](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**단위 테스트 만들기 및 실행:** 단위 테스트를 통해 개발자와 테스터는 C#, Visual Basic .NET 및 C++ 프로젝트의 클래스 메서드에서 논리 오류를 신속하게 찾을 수 있습니다. 단위 테스트를 한 번 만든 후 해당 소스 코드가 변경될 때마다 실행하여 버그가 없는지 확인할 수 있습니다.|[코드 단위 테스트](../test/unit-test-your-code.md)|
|**작업 항목 및 결함 추적:** 작업 항목을 사용하여 팀 프로젝트에 대한 작업 및 정보 둘 다를 추적 및 관리할 수 있습니다. 작업 항목은 [!INCLUDE[esprfound](../includes/esprfound-md.md)] 에서 작업의 할당 및 진행률을 추적하는 데 사용하는 데이터베이스 레코드입니다. 다양한 유형의 작업 항목을 사용하여 고객 요구 사항, 제품 버그 및 개발 작업과 같은 여러 유형의 작업을 추적할 수 있습니다.|[작업 추적 및 워크플로 관리 &#91;리디렉션&#93;](https://msdn.microsoft.com/d2d8637d-0ef8-4ca3-874e-a04713344032)|

## <a name="external-resources"></a>외부 리소스

### <a name="guidance"></a>지침
 [Visual Studio 2012를 사용한 연속 배달 테스트 - 2장: 단위 테스트: 내부 테스트](https://msdn.microsoft.com/library/jj159340.aspx)
