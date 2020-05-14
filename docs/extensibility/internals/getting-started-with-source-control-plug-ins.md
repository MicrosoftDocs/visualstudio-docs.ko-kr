---
title: 소스 제어 플러그인 시작하기 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708341"
---
# <a name="get-started-with-source-control-plug-ins"></a>소스 제어 플러그인 시작
소스 제어 플러그인을 만들려면 소스 제어 플러그인 API에 정의된 기능을 구현하는 DLL을 만든 다음 DLL을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 등록하여 소스 코드 버전 제어에서 사용할 수 있도록 해야 합니다.

 소스 제어 플러그인 API(버전 1.1, 1.2 및 1.3)의 세 가지 버전은 소스 제어 플러그인에 사용할 수 있습니다. 여기에 설명된 소스 제어 플러그인 API는 버전 1.3입니다. 1.1 및 1.2 버전을 지원하는 소스 제어 플러그인과 완벽하게 호환되도록 설계되었습니다. [소스 제어 플러그인 API 버전 1.3의 새로운](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) 기능에는 소스 제어 플러그인 API의 최신 버전에서 지원되는 새로운 기능에 대해 자세히 설명합니다.

## <a name="in-this-section"></a>섹션 내용
- [방법: 소스 제어 플러그인 설치](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

 소스 제어 DLL을 연결하는 데 필요한 레지스트리 항목을 만드는 방법에 대해 설명합니다.

- [소스 제어 플러그인 API 버전 1.3의 새로운 소식](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)

 버전 1.3에서 소스 제어 플러그인 API에 대한 변경 사항에 대한 간략한 개요를 제공합니다.

- [소스 제어 플러그인 API 버전 1.2의 새로운 소식](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

 버전 1.2에서 소스 제어 플러그인 API에 대한 변경 사항에 대한 간략한 개요를 제공합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 플러그인](../../extensibility/source-control-plug-ins.md)

 소스 제어 플러그인 API의 모든 요소에 대한 전체 목록을 제공합니다.

- [소스 제어 플러그인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)

 소스 제어 플러그인 SDK를 정의하고 포함된 리소스에 대해 설명합니다.
