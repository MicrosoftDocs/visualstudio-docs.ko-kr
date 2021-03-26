---
title: 기호 공급자 | Microsoft Docs
description: 식 계산기에서 변수와 식을 평가할 수 있도록 Visual Studio에서 제공 하는 기호 공급자에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 132e3c15eed86c9008e49b74b6da6e5da5a3ce33
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079386"
---
# <a name="symbol-provider"></a>기호 공급자
식 계산기 구현은 변수와 식을 계산 하기 위해 언어 컴파일러에 의해 생성 된 기호화 된 디버그 정보에 액세스 해야 합니다. 기호 처리기 라고도 하는 SP (기호 공급자)의 인터페이스를 사용 하 여이를 수행 합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] PDB (프로그램 데이터베이스) 기호 파일 형식을 사용 하 여 네이티브 코드 및 관리 코드에 대 한 SPs를 제공 합니다. 프로그램에서 사용자 지정 형식에 저장 된 기호를 사용 해야 하는 경우를 제외 하 고에서 제공 하는 SPs를 사용 하는 것이 좋습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>구현 참고 사항
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버그 엔진은 CLR (공용 언어 런타임) 인터페이스를 사용 하 여 SPs와 통신할 것으로 간주 합니다. 결과적으로, Visual Studio 디버그 엔진을 사용 하는 SP는 CLR을 지원 해야 합니다. 모든 CLR 디버깅 인터페이스의 전체 목록은의 일부인 debugref.doc에서 찾을 수 있습니다 [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 사용자 지정 디버그 엔진을 사용 하 여 SP를 사용 하는 경우 디버그 엔진의 필요에 따라 적합 한 것 처럼 SP를 구현할 수 있습니다.

## <a name="see-also"></a>참조
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
