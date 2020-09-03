---
title: 소스 제어 플러그 인 시작 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efc21e07830614d9d3041b2d2d231fd82c652114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708341"
---
# <a name="get-started-with-source-control-plug-ins"></a>원본 제어 플러그 인 시작
소스 제어 플러그 인을 만들려면 소스 제어 플러그 인 API에 정의 된 함수를 구현 하는 DLL을 만든 다음에 DLL을 등록 하 여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 코드 버전 제어에 사용할 수 있도록 해야 합니다.

 원본 제어 플러그 인에는 세 가지 버전의 소스 제어 플러그 인 API (버전 1.1, 1.2 및 1.3)를 사용할 수 있습니다. 여기에 설명 된 소스 제어 플러그 인 API는 버전 1.3입니다. 버전 1.1 및 1.2을 지 원하는 소스 제어 플러그 인과 완전히 호환 되도록 설계 되었습니다. [소스 제어 플러그 인 Api 버전 1.3 섹션의 새로운](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) 기능에서 최신 버전의 소스 제어 플러그 인 api에서 지원 되는 새로운 기능에 대해 자세히 설명 합니다.

## <a name="in-this-section"></a>섹션 내용
- [방법: 소스 제어 플러그 인 설치](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 소스 제어 DLL에 연결 하는 데 필요한 레지스트리 항목을 만드는 방법을 설명 합니다.

- [소스 제어 플러그 인 API 버전 1.3의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 버전 1.3에서 소스 제어 플러그 인 API에 적용 된 변경 내용에 대 한 간략 한 개요를 제공 합니다.

- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 버전 1.2에서 소스 제어 플러그 인 API에 적용 된 변경 내용에 대 한 간략 한 개요를 제공 합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 플러그 인](../../extensibility/source-control-plug-ins.md)

 소스 제어 플러그 인 API의 모든 요소에 대 한 전체 목록을 제공 합니다.

- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)

 소스 제어 플러그 인 SDK를 정의 하 고 포함 된 리소스를 설명 합니다.
