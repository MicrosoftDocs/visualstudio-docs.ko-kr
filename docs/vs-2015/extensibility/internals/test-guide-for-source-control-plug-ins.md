---
title: 원본 제어 플러그 인에 대 한 테스트 가이드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6790e61eddc81045bb168028ee7aeef7a0492e3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825743"
---
# <a name="test-guide-for-source-control-plug-ins"></a>소스 제어 플러그 인에 대한 테스트 가이드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 섹션에서는를 사용 하 여 소스 제어 플러그 인을 테스트 하기 위한 지침을 제공 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 합니다. 가장 일반적인 테스트 영역에 대 한 광범위 한 개요와 문제를 일으킬 수 있는 복잡 한 영역 중 일부를 제공 합니다. 이 개요는 테스트 사례의 포괄적인 목록이 아닙니다.  
  
> [!NOTE]
> [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]이전 버전의를 사용 하는 동안 이전에는 발생 하지 않았던 기존 소스 제어 플러그 인에서 일부 버그 수정 및 향상 된 기능을 확인할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 이전 버전의에서 플러그 인이 변경 되지 않은 경우에도이 섹션에 열거 된 영역에 대 한 기존 소스 제어 플러그 인을 테스트 하는 것이 좋습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="common-preparation"></a>일반적인 준비  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]및 대상 소스 제어 플러그 인이 설치 된 컴퓨터가 필요 합니다. 비슷한 방식으로 구성 된 두 번째 컴퓨터는 소스 제어에서 열기 테스트 중 일부에 사용할 수 있습니다.  
  
## <a name="definition-of-terms"></a>용어 정의  
 이 테스트 가이드의 목적에 따라 다음과 같은 용어 정의를 사용 합니다.  
  
 클라이언트 프로젝트  
 에서 사용할 수 있는 모든 프로젝트 형식 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (예:, 또는)이 소스 제어 통합을 지원 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 합니다.  
  
 웹 프로젝트(Web project)  
 웹 프로젝트에는 파일 시스템, 로컬 IIS, 원격 사이트 및 FTP의 네 가지 유형이 있습니다.  
  
- 파일 시스템 프로젝트는 로컬 경로에 생성 되지만, UNC 경로를 통해 내부적으로 액세스 되므로 인터넷 정보 서비스 (IIS)를 설치할 필요가 없으며, 클라이언트 프로젝트와 마찬가지로 IDE 내부에서 소스 제어에 배치할 수 있습니다.  
  
- 로컬 IIS 프로젝트는 동일한 컴퓨터에 설치 되 고 로컬 컴퓨터를 가리키는 URL을 사용 하 여 액세스 되는 IIS와 작동 합니다.  
  
- 원격 사이트 프로젝트는 IIS 서비스 아래에도 만들어지지만, IDE 내부에서가 아니라 IIS 서버 컴퓨터의 소스 제어에 배치 됩니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- FTP 프로젝트는 원격 FTP 서버를 통해 액세스할 수 있지만 원본 제어에 배치할 수 없습니다.  
  
  트가  
  소스 제어에서 솔루션 또는 프로젝트에 대 한 또 다른 용어입니다.  
  
  버전 저장소  
  소스 제어 플러그 인 API를 통해 액세스 하는 소스 제어 데이터베이스입니다.  
  
## <a name="test-areas-covered-in-this-section"></a>이 섹션에서 다루는 테스트 영역  
  
- [테스트 영역 1: 소스 제어에서 추가/열기](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
  - Case 1a: 소스 제어에 솔루션 추가  

  - Case 1b: 소스 제어에서 솔루션 열기  

  - 사례 1c: 소스 제어에서 솔루션 추가  

- [테스트 영역 2: 소스 제어에서 가져오기](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
- [테스트 영역 3: 체크 아웃/체크 아웃 실행 취소](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
  - 사례 3: 체크 아웃/체크 아웃 취소  

  - 사례 3a: 체크 아웃  

  - 사례 3b: 오프 라인 체크 아웃  

  - 사례 3c: 쿼리 편집/쿼리 저장 (QEQS)  

  - 사례 3d: 자동 체크 아웃  

  - 사례 3e: 체크 아웃 취소  
  
- [테스트 영역 4: 체크 인](../../extensibility/internals/test-area-4-check-in.md)  
  
  - Case 4a: 수정 된 항목  

  - Case 4b: 파일 추가  

  - 사례 4c: 프로젝트 추가  
  
- [테스트 영역 5: 소스 제어 변경](../../extensibility/internals/test-area-5-change-source-control.md)  
  
  - Case 5a: 바인딩  

  - Case 5b: 바인딩 해제  

  - Case 5c: 리바인딩  

- [테스트 영역 6: 삭제](../../extensibility/internals/test-area-6-delete.md)  

- [테스트 영역 7: 공유](../../extensibility/internals/test-area-7-share.md)  

- [테스트 영역 8: 플러그 인 전환](../../extensibility/internals/test-area-8-plug-in-switching.md)  

  - Case 8a: 자동 변경  

  - Case 8b: 솔루션 기반 변경  

## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인](../../extensibility/source-control-plug-ins.md)
