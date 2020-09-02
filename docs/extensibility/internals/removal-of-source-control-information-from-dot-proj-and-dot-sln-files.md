---
title: Proj 및 .sln 파일에서 소스 제어 정보를 제거 합니다.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705593"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>.Proj 및 .Sln 파일에서 소스 제어 정보 제거
원본 제어 플러그 인 API 버전 1.2에서 SCC 정보는 MSSCCPRJ.SCC에 저장 됩니다. SCC 파일. MSSCCPRJ.SCC의 이점입니다. SCC 파일은 proj 및 .sln 파일에 있는 것 처럼 SCC 정보를 원본 제어 하지 않습니다.

## <a name="version-12-changes"></a>버전 1.2 변경 내용
 소스 제어 플러그 인 API 버전 1.1을 기반으로 하는 소스 제어 플러그 인에서 원본 제어에 대 한 정보는 프로젝트 (proj) 및 솔루션 (.sln) 파일에 저장 됩니다. 원본 제어 정보의 데이터베이스 위치는 지정 된 Xpath로 지정 되며 데이터베이스 내의 특정 위치는 ProjName으로 지정 됩니다. 이 동작은 일반적으로 이러한 작업을 수행한 후에는 ProjName이 유효 하지 않기 때문에 분기, 포크 또는 복사 작업 후에 문제를 일으킬 수 있습니다.

 소스 제어 플러그 인 API 버전 1.1에서 IDE는 SAK 파일을 사용 하 여 플러그 인에서 MSSCCPRJ.SCC을 지원 하는지 여부를 검색 합니다. 소스 제어 정보를 저장 하는 SCC 메서드입니다. 소스 제어 플러그 인 API 버전 1.2에서는 MSSCCPRJ.SCC에 대 한 지원을 검색 하는 새로운 기능을 제공 합니다. ~ SAK 파일을 사용 하지 않는 SCC 파일. 자세한 내용은 [~ SAK Files 제거](../../extensibility/internals/elimination-of-tilde-sak-files.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
