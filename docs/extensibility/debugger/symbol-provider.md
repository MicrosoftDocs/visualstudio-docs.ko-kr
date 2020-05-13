---
title: 기호 공급자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712815"
---
# <a name="symbol-provider"></a>기호 공급자
식 평가기 구현변수와 식을 평가하려면 언어 컴파일러에서 생성된 기호 디버그 정보에 액세스해야 합니다. 심볼 처리기라고도 하는 SP(심볼 공급자)의 인터페이스를 사용하여 사용합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]프로그램 데이터 베이스 (PDB) 기호 파일 형식을 사용 하 여 네이티브 코드 뿐만 아니라 관리 코드에 대 한 SP를 제공 합니다. 프로그램에서 사용자 지정 형식으로 저장된 기호를 사용해야 하는 경우가 많지 않은 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에서 제공하는 SP를 사용하는 것이 좋습니다.

## <a name="implementation-notes"></a>구현 참고 사항
 디버그 엔진은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 공통 언어 런타임(CLR) 인터페이스를 사용하여 SP와 대화할 것으로 예상합니다. 따라서 Visual Studio 디버그 엔진으로 작업하는 SP는 CLR을 지원해야 합니다. 모든 CLR 디버깅 인터페이스의 전체 목록은 [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]의 일부인 debugref.doc에서 찾을 수 있습니다.

 SP가 사용자 지정 디버그 엔진에서만 작동하는 경우 디버그 엔진의 요구에 따라 SP를 구현할 수 있습니다.

## <a name="see-also"></a>참조
- [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
