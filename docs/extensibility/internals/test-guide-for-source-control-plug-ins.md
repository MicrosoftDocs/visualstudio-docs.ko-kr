---
title: 소스 제어 플러그인테스트 가이드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6b3f8e76e977472a3459697a650b32dae657c22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704385"
---
# <a name="test-guide-for-source-control-plug-ins"></a>소스 제어 플러그 인에 대한 테스트 가이드
이 섹션에서는 소스 제어 플러그인을 으로 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]테스트하기 위한 지침을 제공합니다. 가장 일반적인 테스트 영역과 문제가 될 수 있는 보다 복잡한 영역중 일부에 대한 광범위한 개요가 제공됩니다. 이 개요는 테스트 사례의 전체 목록이 아닙니다.

> [!NOTE]
> 최신 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에 대한 몇 가지 버그 수정 및 개선 사항은 이전 버전의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. 이전 버전 의 플러그 인이후 플러그인을 변경하지 않은 경우에도 이 섹션에서 확장된 영역에 대해 기존 소스 제어 플러그인을 테스트하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]것이 좋습니다.

## <a name="common-preparation"></a>일반적인 준비
 설치된 대상 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어 플러그인이 있는 컴퓨터가 필요합니다. 유사하게 구성된 두 번째 컴퓨터는 소스 제어 테스트의 일부에 사용할 수 있습니다.

## <a name="definition-of-terms"></a>용어의 정의
 이 테스트 가이드에서는 다음 용어 정의를 사용합니다.

 클라이언트 프로젝트 소스 제어 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합(예: [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]또는)에서 사용할 수 있는 모든 프로젝트 유형입니다.

 웹 프로젝트 웹 프로젝트에는 파일 시스템, 로컬 IIS, 원격 사이트 및 FTP의 네 가지 유형이 있습니다.

- 파일 시스템 프로젝트는 로컬 경로에서 만들어지지만 UNC 경로를 통해 내부적으로 액세스하므로 IIS(인터넷 정보 서비스)를 설치할 필요가 없으며 클라이언트 프로젝트와 마찬가지로 IDE 내부에서 소스 제어하에 배치할 수 있습니다.

- 로컬 IIS 프로젝트는 동일한 컴퓨터에 설치되고 로컬 컴퓨터를 가리키는 URL로 액세스되는 IIS와 함께 작동합니다.

- 원격 사이트 프로젝트는 IIS 서비스 하에서도 생성되지만 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 내부가 아닌 IIS 서버 컴퓨터의 소스 제어 하에 배치됩니다.

- FTP 프로젝트는 원격 FTP 서버를 통해 액세스되지만 소스 제어하에 배치할 수 없습니다.

  참여 소스 제어하에 있는 솔루션 또는 프로젝트에 대한 또 다른 용어입니다.

  버전 저장소 소스 제어 플러그인 API를 통해 액세스중인 소스 제어 데이터베이스입니다.

## <a name="test-areas-covered-in-this-section"></a>이 섹션에서 다루는 테스트 영역

- [테스트 영역 1: 소스 제어에서 에/열기 추가](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - 사례 1a: 소스 제어에 솔루션 추가

  - 사례 1b: 소스 제어의 개방형 솔루션

  - 사례 1c: 소스 제어에서 솔루션 추가

- [테스트 영역 2: 소스 제어에서 가져오기](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [시험 영역 3: 체크 아웃/취소 체크아웃](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - 사례 3: 체크 아웃/취소 체크아웃

  - 케이스 3a: 체크 아웃

  - 케이스 3b: 연결이 끊긴 체크아웃

  - 사례 3c: 쿼리 편집/쿼리 저장(QEQS)

  - 케이스 3D: 무음 체크아웃

  - 사례 3e: 체크 아웃 취소

- [테스트 영역 4: 체크 인](../../extensibility/internals/test-area-4-check-in.md)

  - 케이스 4a: 수정된 항목

  - 사례 4b: 파일 추가

  - 사례 4c: 프로젝트 추가

- [테스트 영역 5: 소스 제어 변경](../../extensibility/internals/test-area-5-change-source-control.md)

  - 케이스 5a: 바인드

  - 케이스 5b: 언빈드

  - 케이스 5c: 리바인드

- [테스트 영역 6: 삭제](../../extensibility/internals/test-area-6-delete.md)

- [테스트 영역 7: 공유](../../extensibility/internals/test-area-7-share.md)

- [테스트 영역 8: 플러그 인 전환](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - 케이스 8a: 자동 변경

  - 사례 8b: 솔루션 기반 변경

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../../extensibility/source-control-plug-ins.md)
