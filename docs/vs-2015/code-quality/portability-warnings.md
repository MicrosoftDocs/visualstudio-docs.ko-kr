---
title: 이식성 경고 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 932474143b4770e81d8bfca14ab05a6538ae84a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671162"
---
# <a name="portability-warnings"></a>이식성 경고
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이식성 경고는 다양 한 운영 체제 간의 이식성을 지원 합니다.

## <a name="in-this-section"></a>섹션 내용

|규칙|설명|
|----------|-----------------|
|[CA1900: 값 형식 필드는 이식 가능해야 합니다.](../code-quality/ca1900-value-type-fields-should-be-portable.md)|이 규칙은 명시적 레이아웃 특성을 사용 하 여 선언 된 구조체가 64 비트 운영 체제에서 비관리 코드로 마샬링될 때 올바르게 정렬 되는지 확인 합니다.|
|[CA1901: P/Invoke 선언은 이식 가능 해야 합니다.](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|이 규칙은 각 매개 변수의 크기와 P/Invoke의 반환 값을 평가 하 고 32 비트 및 64 비트 운영 체제에서 비관리 코드로 마샬링될 때 크기가 올바른지 확인 합니다.|
|[CA1903: 대상 프레임워크의 API만 사용하세요.](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|멤버 또는 형식이 프로젝트의 대상 프레임워크에 함께 포함되지 않은 서비스 팩에 도입된 멤버 또는 형식을 사용합니다.|
