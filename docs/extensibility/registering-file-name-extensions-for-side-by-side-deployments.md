---
title: 나란히 배포할 파일 이름 확장자 등록 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701550"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>나란히 배포할 파일 이름 확장명 등록
나란히 배치된 VSPackage의 경우 파일 이름 확장명을 등록하여 파일을 올바른 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]와 연결해야 합니다. 버전별 파일 이름 확장명을 사용하지 않는 한 등록을 통해 사용자는 프로젝트 및 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]프로젝트 항목 파일을 적절한 버전의 에서 열 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [파일 이름 확장명 에 대해](../extensibility/about-file-name-extensions.md) 파일 이름 확장명을 등록하는 방법에 대해 설명합니다.

- [파일 이름 확장명에 대한 파일 처리기 지정](../extensibility/specifying-file-handlers-for-file-name-extensions.md) 특정 파일 이름 확장자를 열고 편집할 수 있는 응용 프로그램을 등록하는 방법에 대한 정보를 제공합니다.

- [파일 이름 확장명에 대한 동사 등록](../extensibility/registering-verbs-for-file-name-extensions.md) 동사를 등록하는 방법에 대해 설명합니다.

- [나란히 파일 연결 관리](../extensibility/managing-side-by-side-file-associations.md) 파일을 열려면 특정 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 특정 버전을 호출해야 하는 병렬 설치를 처리하는 방법에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원
- [여러 버전의 Visual Studio 지원](../extensibility/supporting-multiple-versions-of-visual-studio.md) 최종 사용자에게 개발 및 배포하는 동안 VSPackage의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 여러 버전 및 VSPackage와 관련된 문제를 설명합니다.
