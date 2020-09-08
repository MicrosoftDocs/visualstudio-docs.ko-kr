---
title: 소스 제어 플러그 인에 대한 테스트 가이드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: overview
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
ms.openlocfilehash: 321d61175068f135aae87bff73f13ac800f4793c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905160"
---
# <a name="test-guide-for-source-control-plug-ins"></a>소스 제어 플러그 인에 대한 테스트 가이드
이 섹션에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]를 사용하여 소스 제어 플러그 인을 테스트하기 위한 지침을 제공합니다. 가장 일반적인 테스트 영역에 대한 광범위한 개요와 문제를 일으킬 수 있는 복잡한 영역 중 일부에 대한 개요를 제공합니다. 이 개요는 테스트 사례의 전체 목록이 아닙니다.

> [!NOTE]
> 최신 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 버그 픽스 및 개선 사항에서 IDE는 이전 버전의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]를 사용하는 동안 이전에는 발생하지 않았던 기존 소스 제어 플러그 인과 관련된 문제가 발견될 수 있습니다. 이전 버전의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 이후 플러그 인이 변경되지 않은 경우에도 이 섹션에 열거된 영역에 대한 기존 소스 제어 플러그 인을 테스트하는 것이 좋습니다.

## <a name="common-preparation"></a>일반적인 준비
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]와 대상 소스 제어 플러그 인이 설치된 컴퓨터가 필요합니다. 비슷한 방식으로 구성된 두 번째 컴퓨터는 소스 제어에서 열기 테스트 중 일부에 사용할 수 있습니다.

## <a name="definition-of-terms"></a>용어 정의
 이 테스트 가이드의 목적에 따라 다음과 같은 용어 정의를 사용합니다.

 클라이언트 프로젝트 소스 제어 통합을 지원하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 사용 가능한 모든 프로젝트 형식(예: [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 또는 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 웹 프로젝트 웹 프로젝트 형식은 4가지입니다. 파일 시스템, 로컬 IIS, 원격 사이트 및 FTP입니다.

- 파일 시스템 프로젝트는 로컬 경로에 생성되지만, UNC 경로를 통해 내부적으로 액세스되므로 인터넷 정보 서비스(IIS)를 설치할 필요가 없으며, 클라이언트 프로젝트와 마찬가지로 IDE 내부에서 소스 제어에 배치할 수 있습니다.

- 로컬 IIS 프로젝트는 동일한 컴퓨터에 설치되고 로컬 컴퓨터를 가리키는 URL을 사용하여 액세스되는 IIS와 함께 사용됩니다.

- 원격 사이트 프로젝트는 IIS 서비스에도 생성되지만 IIS 서버 컴퓨터에서 소스 제어에 배치되고 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 내부에 배치되지 않습니다.

- FTP 프로젝트는 원격 FTP 서버를 통해 액세스할 수 있지만 소스 제어에 배치할 수 없습니다.

  인리스트먼트 소스 제어의 솔루션 또는 프로젝트에 대한 다른 용어입니다.

  버전 저장소 소스 제어 플러그 인 API를 통해 액세스하는 소스 제어 데이터베이스.

## <a name="test-areas-covered-in-this-section"></a>이 섹션에서 다루는 테스트 영역

- [테스트 영역 1: 소스 제어에 추가/소스 제어에서 열기](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - 사례 1a: 소스 제어에 솔루션 추가

  - 사례 1b: 소스 제어에서 솔루션 열기

  - 사례 1c: 소스 제어에서 솔루션 추가

- [테스트 영역 2: 소스 제어에서 가져오기](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [테스트 영역 3: 체크 아웃/체크 아웃 실행 취소](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - 사례 3: 체크 아웃/체크 아웃 실행 취소

  - 사례 3a: 체크 아웃

  - 사례 3b: 연결이 끊긴 체크 아웃

  - 사례 3c: 쿼리 편집/쿼리 저장(QEQS)

  - 사례 3d: 자동 체크 아웃

  - 사례 3e: 체크 아웃 취소

- [테스트 영역 4: 체크 인](../../extensibility/internals/test-area-4-check-in.md)

  - 사례 4a: 수정된 항목

  - 사례 4b: 파일 추가

  - 사례 4c: 프로젝트 추가

- [테스트 영역 5: 소스 제어 변경](../../extensibility/internals/test-area-5-change-source-control.md)

  - 사례 5a: 바인딩

  - 사례 5b: 바인딩 해제

  - 사례 5c: 다시 바인딩

- [테스트 영역 6: 삭제](../../extensibility/internals/test-area-6-delete.md)

- [테스트 영역 7: 공유](../../extensibility/internals/test-area-7-share.md)

- [테스트 영역 8: 플러그 인 전환](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - 사례 8a: 자동 변경

  - 사례 8b: 솔루션 기반 변경

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인](../../extensibility/source-control-plug-ins.md)
