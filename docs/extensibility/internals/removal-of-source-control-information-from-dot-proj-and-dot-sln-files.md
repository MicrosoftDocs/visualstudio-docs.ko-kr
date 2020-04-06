---
title: .proj 및 .sln 파일에서 소스 제어 정보 제거
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705593"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>.Proj 및 .Sln 파일에서 소스 제어 정보 제거
소스 제어 플러그인 API의 버전 1.2에서 SCC 정보는 MSSCCPRJ에 저장됩니다. SCC 파일. MSSCCPRJ의 장점. SCC 파일은 .proj 및 .sln 파일과 같이 SCC 정보가 소스 제어되지 않는다는 것입니다.

## <a name="version-12-changes"></a>버전 1.2 변경 사항
 소스 제어 플러그인 API 버전 1.1을 기반으로 하는 소스 제어 플러그인에서는 소스 제어에 대한 정보가 프로젝트(.proj) 및 솔루션(.sln) 파일에 저장됩니다. 소스 제어 정보의 데이터베이스 위치는 AuxPath에 의해 지정되며 데이터베이스 내의 특정 위치는 ProjName에 의해 지정됩니다. 이 동작은 ProjName일반적으로 이러한 작업 후 유효하지 않습니다 때문에 분기, 분기 또는 복사 작업 후 문제가 발생할 수 있습니다.

 소스 제어 플러그인 API 버전 1.1에서 IDE는 ~ SAK 파일을 사용하여 플러그인이 MSSCCPRJ를 지원하는지 검색했습니다. 소스 제어 정보를 저장하는 SCC 방법입니다. 소스 제어 플러그인 API 버전 1.2는 MSSCCPRJ에 대한 지원을 검색하기 위한 새로운 기능을 제공합니다. ~ SAK 파일을 사용하지 않고 SCC 파일. 자세한 내용은 [~ SAK 파일 제거를](../../extensibility/internals/elimination-of-tilde-sak-files.md)참조하십시오.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
