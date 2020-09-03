---
title: '&apos;Visual Studio 2017 SDK의 새로운 기능 | Microsoft Docs'
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fb5b81341f8184d713755b3b934fbae4c8031b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88711601"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Visual Studio 2017 SDK의 새로운 기능&#39;

Visual studio SDK에는 Visual Studio 2017에 대 한 다음과 같은 새롭고 업데이트 된 기능이 있습니다.

## <a name="vsix-v3-format"></a>VSIX v3 형식

Visual Studio 2017의 새로운 경량 설치를 지원 하기 위해 VSIX 확장 매니페스트 형식이 버전 3 (VSIX v3)으로 업데이트 되었습니다.

새 형식은 다음을 지원 합니다.

* VSIXInstaller에서 검색 하 고 설치할 필수 구성 요소를 명시적으로 선언 합니다.
* 확장 설치의 Ngen 어셈블리
* 일반적인 확장 루트 외부에 자산을 설치 합니다.

이러한 변경 내용에 대 한 자세한 내용은 다음 항목을 참조 하십시오.

* [Visual Studio 2017에 대 한 확장성 변경 내용](breaking-changes-2017.md)
* [VSIX v3의 Ngen 지원](ngen-support.md)
* [확장 폴더 외부에 설치](set-install-root.md)
* [Visual Studio 2017 확장성에 대 한 질문과 대답](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Visual Studio 2017로 확장성 프로젝트 마이그레이션

확장성 프로젝트 및 VSIX 매니페스트를 Visual Studio 2017로 업데이트 하는 방법을 알아보려면 [방법: 확장성 프로젝트를 Visual studio 2017로 마이그레이션](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)을 참조 하세요.

## <a name="custom-project-and-item-templates"></a>사용자 지정 프로젝트 및 항목 템플릿

Visual Studio 2017부터 사용자 지정 프로젝트 및 항목 템플릿 검색을 더 이상 수행하지 않습니다. 대신 확장에서는 해당 템플릿의 설치 위치를 설명하는 템플릿 매니페스트 파일을 제공해야 합니다. Visual Studio 2017을 사용하여 VSIX 확장을 업데이트할 수 있습니다. MSI를 사용하여 확장을 배포하는 경우 템플릿 매니페스트 파일을 직접 생성해야 합니다. 자세한 내용은 [Visual Studio 2017에 대 한 사용자 지정 프로젝트 및 항목 템플릿 업그레이드](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)를 참조 하세요. 템플릿 매니페스트 스키마는 [Visual Studio 템플릿 매니페스트 스키마 참조](../extensibility/visual-studio-template-manifest-schema-reference.md)에 설명되어 있습니다.

## <a name="updated-extension-performance-guidelines"></a>확장 성능 지침 업데이트

Visual Studio 시작 및 솔루션 로드 시간에 대 한 확장 영향을 검색 하 고 분석 하는 방법을 보여 주기 위해 [Vspackage 관리](managing-vspackages.md) 에서 새로운 [방법: 확장 성능 진단](how-to-diagnose-extension-performance.md) 문서를 참조 하세요.
