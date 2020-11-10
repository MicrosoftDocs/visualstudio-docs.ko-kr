---
title: 관리 코드에 대한 관리 최소 규칙 규칙 집합
ms.date: 11/04/2016
description: 보안, 견고성 및 기타 중요 한 문제에 초점을 맞춘 Visual Studio에서 관리 되는 최소 규칙 규칙 집합에 대해 알아봅니다. 규칙 설명을 참조 하세요.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5a0e5c59621f948cbb7465a6726fa8c3003480d4
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435393"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>관리 코드에 대한 관리 최소 규칙 규칙 집합

관리 되는 최소 규칙은 잠재적 보안 허점, 응용 프로그램 충돌 및 기타 중요 한 논리 및 디자인 오류를 포함 하 여 코드의 가장 중요 한 문제에 초점을 둡니다. 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에이 규칙 집합을 포함 합니다.

|규칙|설명|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|삭제 가능한 필드가 있는 형식은 삭제 가능해야 합니다.|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|빈 종료자를 제거하십시오.|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|삭제 가능한 필드는 삭제해야 합니다.|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|오버 로드 연산자는 재정의할 때 동일 합니다. `ValueType.Equals`|
