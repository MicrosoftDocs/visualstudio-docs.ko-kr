---
title: 소스 제어 플러그인 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc5f092e0ae93109d071af0b1a67999947e73e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699899"
---
# <a name="source-control-plug-ins"></a>소스 제어 플러그 인
소스 제어 플러그인 SDK 참조 섹션에는 소스 제어 시스템을 와 통합할 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]수 있는 전체 인터페이스 사양이 포함되어 있습니다. 소스 제어 플러그인이 통합 개발 환경(IDE)과 인터페이스하기 위해 구현해야 하는 다양한 함수 및 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 데이터 형식의 구문 및 의미 체계를 지정합니다.

## <a name="in-this-section"></a>섹션 내용
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md) 소스 제어 플러그인 API를 준수하기 위해 소스 제어 플러그인에서 구현해야 하는 함수를 나열합니다.

- [IDE에서 구현한 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md) 특정 명령이 실행되는 동안 소스 제어 플러그인이 정보를 IDE로 다시 전달하는 데 사용하는 함수에 대해 설명합니다.

- [열거자](../extensibility/enumerators.md) 소스 제어 플러그인 API에 열거자 데이터 형식을 나열합니다.

- [기능 플래그](../extensibility/capability-flags.md) 공급자의 `SCC_CAP_xxx` 기능을 나타내는 플래그에 대해 설명합니다.

- [특정 명령에서 사용되는 비트 플래그](../extensibility/bitflags-used-by-specific-commands.md) 특정 명령의 컨텍스트에서 유용한 플래그를 나열합니다.

- [오류 코드](../extensibility/error-codes.md) 함수에서 반환되는 공통 오류 `SCCTRN`값을 으로 나열합니다.

- [소스 제어 플러그인을 찾기 위한 키로 사용되는 문자열](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) 소스 제어 플러그인을 찾기 위해 레지스트리에 액세스하기 위한 키에 대해 설명합니다.

- [MSSCCPRJ. SCC 파일은](../extensibility/mssccprj-scc-file.md) IDE에 대한 정보가 불천한 정보를 포함하지만 소스 제어 플러그인에서 버전 제어에서 솔루션 또는 프로젝트를 찾는 데 사용되는 클라이언트 측 파일을 설명합니다.

- [소스 제어 플러그인 구현을 위한 모범 사례](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) 소스 제어 플러그인 API를 구현하는 동안 기억해야 할 중요한 기술 미리 알림 모음을 제공합니다.

- [문자열 길이 제한](../extensibility/restrictions-on-string-lengths.md) 소스 제어 플러그인 API의 다양한 함수에 사용되는 문자열의 길이에 대한 제한 사항에 대해 설명합니다.

- [용어집](../extensibility/source-control-plug-in-glossary.md) 소스 제어 플러그인 SDK 설명서를 읽기 위한 유용한 용어와 정의를 제공합니다.

- [방법: 소스 제어 플러그인에 대한 호환성 경고 끄기](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) 경고를 사용하지 않도록 설정하는 방법에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 플러그인 샘플](https://www.microsoft.com/download/details.aspx?id=55984) 소스 제어 플러그인 기능의 샘플을 제공합니다.

- [소스 제어 플러그인테스트 가이드](../extensibility/internals/test-guide-for-source-control-plug-ins.md) 소스 제어 플러그인과 관련된 테스트 절차에 대해 설명합니다.

- [소스 제어 플러그인 만들기](../extensibility/internals/creating-a-source-control-plug-in.md) 소스 제어 사용자 인터페이스(UI)를 사용하는 동안 소스 제어 기능을 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 제공하는 소스 제어 플러그인을 만드는 방법에 대해 설명합니다.

- [비주얼 스튜디오 SDK 참조](../extensibility/visual-studio-sdk-reference.md) 참조 항목 목록을 제공합니다.
