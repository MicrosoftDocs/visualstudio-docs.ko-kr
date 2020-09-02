---
title: 소스 제어 플러그 인 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5a99ebdf2366ce6a60a6a724afc7d742db7150f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705797"
---
# <a name="source-control-plug-ins"></a>소스 제어 플러그 인
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

소스 제어 플러그 인 SDK 참조 섹션에는 소스 제어 시스템을와 통합할 수 있도록 하는 전체 인터페이스 사양이 포함 되어 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 이 클래스는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE (통합 개발 환경)와의 상호 작용을 위해 소스 제어 플러그 인에서 구현 해야 하는 다양 한 함수 및 데이터 형식에 대 한 구문 및 의미 체계를 지정 합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)  
 소스 제어 플러그 인 API를 준수 하기 위해 소스 제어 플러그 인에서 구현 해야 하는 함수를 나열 합니다.  
  
 [IDE에서 구현된 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)  
 특정 명령이 실행 되는 동안 소스 제어 플러그 인이 정보를 다시 IDE에 전달 하는 데 사용 하는 함수에 대해 설명 합니다.  
  
 [Enumerators](../extensibility/enumerators.md)  
 소스 제어 플러그 인에서 알고 있어야 하는 소스 제어 플러그 인 API의 열거자 데이터 형식을 나열 합니다.  
  
 [기능 플래그](../extensibility/capability-flags.md)  
 `SCC_CAP_xxx`공급자의 기능을 나타내는 플래그를 설명 합니다.  
  
 [특정 명령에 사용되는 Bitflag](../extensibility/bitflags-used-by-specific-commands.md)  
 특정 명령의 컨텍스트에서 유용한 플래그를 나열 합니다.  
  
 [오류 코드](../extensibility/error-codes.md)  
 함수에서 반환 하는 일반적인 오류 값을로 나열 `SCCTRN` 합니다.  
  
 [소스 제어 플러그 인을 찾기 위한 키로 사용되는 문자열](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 소스 제어 플러그 인을 찾기 위해 레지스트리에 액세스 하는 데 사용할 수 있는 키에 대해 설명 합니다.  
  
 [MSSCCPRJ.SCC 파일](../extensibility/mssccprj-scc-file.md)  
 IDE에 대 한 정보를 불투명 하 게 포함 하는 클라이언트 쪽 파일에 대해 설명 하지만, 소스 제어 플러그 인에서 버전 제어에서 솔루션이 나 프로젝트를 찾는 데 사용 됩니다.  
  
 [소스 제어 플러그 인 구현 모범 사례](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 소스 제어 플러그 인 API를 구현 하는 동안 기억해 야 할 중요 한 기술 미리 알림 모음을 제공 합니다.  
  
 [문자열 길이에 대한 제한](../extensibility/restrictions-on-string-lengths.md)  
 다양 한 함수에 사용 되는 문자열의 길이에 대 한 소스 제어 플러그 인 API의 제한 사항을 설명 합니다.  
  
 [용어](../extensibility/source-control-plug-in-glossary.md)  
 소스 제어 플러그 인 SDK 설명서를 읽기 위한 유용한 용어와 해당 정의를 제공 합니다.  
  
 [방법: 소스 제어 플러그 인에 대한 호환성 경고 해제](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 경고를 사용 하지 않도록 설정 하는 방법을 설명 합니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [소스 제어 플러그 인 샘플](https://msdn.microsoft.com/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 소스 제어 플러그 인 기능의 샘플을 제공 합니다.  
  
 [소스 제어 플러그 인에 대한 테스트 가이드](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 소스 제어 플러그 인과 관련 된 테스트 절차에 대해 설명 합니다.  
  
 [소스 제어 플러그 인 만들기](../extensibility/internals/creating-a-source-control-plug-in.md)  
 소스 제어 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] UI (사용자 인터페이스)를 사용 하는 동안 소스 제어 기능을 제공 하는 소스 제어 플러그 인을 만드는 방법에 대해 설명 합니다.  
  
 [Visual Studio SDK 참조](../extensibility/visual-studio-sdk-reference.md)  
 참조 항목의 목록을 표시 합니다.
