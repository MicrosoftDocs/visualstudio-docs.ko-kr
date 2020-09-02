---
title: 코드 분석 체크 인 정책 만들기 및 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8e31ff799edc93d250eeeab57b349873a63ecf14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667708"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>코드 분석 체크 인 정책 만들기 및 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TFVC (Team Foundation 버전 제어)를 사용 하는 경우 팀 프로젝트의 .NET Framework 및 네이티브 (C/c + +) 코드 프로젝트에 대해 코드 분석 체크 인 정책을 만들 수 있습니다. 코드 분석 체크 인 정책을 사용 하 여 코드 베이스에 체크 인 한 코드의 품질을 제어 하 고 향상 시킬 수 있습니다.

 로컬 빌드가 최신 상태이 고 코드 분석이 최신 원본 파일에서 실행 된 경우 정책이 통과 합니다. 코드 프로젝트에서 사용 되는 코드 분석 규칙은 팀 프로젝트 체크 인 정책에 정의 된 규칙과 동일한 규칙을 포함 해야 합니다. 팀 프로젝트 설정에서 오류로 지정 된 규칙도 코드 프로젝트에서 오류로 지정 해야 합니다.

> [!IMPORTANT]
> 코드 분석 체크 인 정책은 웹 사이트 프로젝트에 적용할 수 없습니다. 웹 응용 프로그램 프로젝트에 적용할 수 있습니다.

 의 팀 프로젝트 설정을 사용 하 여 코드 분석 체크 인 정책을 만듭니다 [!INCLUDE[esprscc](../includes/esprscc-md.md)] . 팀 프로젝트에 대 한 체크 인 정책을 지정 하 고 적용 하지만 로컬 개발 컴퓨터의 개별 코드 프로젝트에 대해 코드 분석 실행을 구성 하 고 실행 합니다. 이 섹션에서는 팀 프로젝트에 대 한 코드 분석 체크 인 정책을 지정 하는 방법과 관리 코드에 대 한 사용자 지정 코드 분석 정책을 구현 하는 방법을 설명 합니다.

## <a name="in-this-section"></a>섹션 내용
 [방법: 표준 코드 분석 체크 인 정책 만들기 또는 업데이트](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md) 팀 프로젝트에 대 한 코드 분석 정책을 설정 하 고 수정 하는 데 사용 하는 단계를 설명 합니다.

 [관리 코드에 대 한 사용자 지정 체크 인 정책 구현](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md) 팀 프로젝트의 체크 인 정책에 대 한 사용자 지정 규칙 집합을 만들고 체크 인 정책을 사용 하 여 팀 프로젝트의 코드 프로젝트를 동기화 하는 데 사용 하는 단계를 설명 합니다.

 [코드 분석 체크 인 정책에 대 한 버전 호환성](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md) 버전 간의 코드 분석 체크 인 호환성 문제에 대해 설명 [!INCLUDE[vstsLong](../includes/vstslong-md.md)] 합니다.

 [방법: 코드 분석 사전 사용자 지정](../code-quality/how-to-customize-the-code-analysis-dictionary.md) 코드 분석 명명 규칙에서 참조 되는 사전에 단어와 토큰을 추가 하는 방법에 대해 설명 합니다.

## <a name="related-sections"></a>관련 섹션
 [품질 게이트 설정 및 적용](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)

 [팀 프로젝트 체크 인 정책을 사용하여 코드 품질 향상](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
