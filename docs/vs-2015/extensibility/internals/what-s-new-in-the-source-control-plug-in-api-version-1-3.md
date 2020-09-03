---
title: 소스 제어 플러그 인 API 버전 1.3의 새로운 기능&#39;Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5333a5b44e9c990843e66da357578e4a90d210
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200923"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>소스 제어 플러그 인 API 버전 1.3의 새로운 기능&#39;
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스 제어 플러그 인 API 버전 1.3에는 보다 고급 제어를 제공 하는 다음과 같은 새로운 기능이 도입 되었습니다.  
  
## <a name="changes"></a>변경  
 다음 함수는 소스 제어 플러그 인 API 버전 1.3에 새로 있습니다.  
  
|함수|개요|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|추가 기능 비트를 보고할 수 있습니다.|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|로컬 디스크에 있는 버전 제어 데이터베이스에서 최신 버전을 포함 하는 파일을 검사할 수 있습니다.|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|지정 된 파일에 대 한 이름 변경 (이름 바꾸기, 추가 및 삭제)의 상태를 검사할 수 있습니다.|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|버전 제어 데이터베이스의 디렉터리 및 파일에 대 한 검사를 허용 합니다.|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|버전 제어 데이터베이스의 지정 된 파일 목록을 현재 프로젝트에 추가 합니다.|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|지정 된 파일의 자동 "Get"을 수행 합니다. 사용자 인터페이스가 표시 되지 않습니다.|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|사용자 관련 옵션에 대 한 액세스를 허용 합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [시작 하기](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
