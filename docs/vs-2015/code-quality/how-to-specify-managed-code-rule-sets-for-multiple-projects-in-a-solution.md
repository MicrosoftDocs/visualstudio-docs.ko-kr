---
title: '방법: 솔루션의 여러 프로젝트에 대 한 관리 코드 규칙 집합 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656418"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>방법: 솔루션의 여러 프로젝트에 대한 관리 코드 규칙 집합 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

기본적으로 솔루션의 모든 관리 되는 프로젝트에는 Microsoft 최소 권장 규칙 코드 분석 *규칙 집합이*할당 됩니다. 솔루션에 대 한 속성 대화 상자에서 솔루션의 프로젝트에 할당 된 규칙 집합을 변경할 수 있습니다.

> [!NOTE]
> 기본적으로 프로젝트 코드 분석은 빌드 단계로 실행 되지 않습니다. 빌드 단계로 코드 분석을 사용 하도록 설정 하려면 [방법: 관리 코드 프로젝트에 대 한 코드 분석 구성](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)을 참조 하세요.

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>관리 코드 솔루션의 여러 프로젝트에 대 한 규칙 집합을 지정 하려면

1. [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 문서 내 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]또는 [!INCLUDE[vsPro](../includes/vspro-md.md)] 솔루션을 엽니다.

2. **분석** 메뉴에서 **솔루션에 대 한 코드 분석 구성**을 클릭 합니다.

3. 필요한 경우 **공용 속성**을 확장 한 다음 **코드 분석 설정**을 클릭 합니다.

4. 하나 이상의 프로젝트에 대 한 규칙 집합을 지정할 수 있습니다.

    - 개별 프로젝트에 대 한 규칙 집합을 지정 하려면 프로젝트 이름을 클릭 합니다.

    - 여러 프로젝트에 대 한 규칙 집합을 지정 하려면 CTRL 키를 누른 채 프로젝트 이름을 클릭 합니다.

    - 솔루션의 모든 프로젝트를 지정 하려면 SHIFT 키를 누른 채 프로젝트 목록을 클릭 합니다.

5. 프로젝트의 **규칙 집합** 필드를 클릭 한 다음 적용 하려는 규칙 집합의 이름을 클릭 합니다.
