---
title: 비주얼 스튜디오 2017 SDK에서&#39;새로운 것 | 마이크로 소프트 문서
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697204"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>비주얼 스튜디오 2017 SDK에서&#39;새로운 것

비주얼 스튜디오 SDK에는 Visual Studio 2017에 대한 다음과 같은 새롭고 업데이트된 기능이 있습니다.

## <a name="vsix-v3-format"></a>VSIX v3 형식

Visual Studio 2017의 새로운 경량 설치를 지원하기 위해 VSIX 확장 매니페스트 형식이 버전 3(VSIX v3)으로 업데이트되었습니다.

새 형식에는 다음을 지원합니다.

* VSIXInstaller에서 검색하고 설치할 필수 구성 조건을 명시적으로 선언합니다.
* 확장 설치시 Ngen 어셈블리.
* 일반적인 확장 루트 외부에 에셋을 설치합니다.

이러한 변경 사항에 대해 알아보려면 다음 항목을 참조하십시오.

* [비주얼 스튜디오 2017의 확장성 변경](breaking-changes-2017.md)
* [VSIX v3의 Ngen 지원](ngen-support.md)
* [확장 폴더 외부에 설치](set-install-root.md)
* [Visual Studio 2017 확장성에 대한 자주 묻는 질문](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>확장성 프로젝트를 Visual Studio 2017로 마이그레이션

확장성 프로젝트및 해당 VSIX 매니페스트를 Visual Studio 2017로 업데이트하는 방법에 대해 알아보려면 [확장성 프로젝트를 Visual Studio 2017로 마이그레이션하는 방법을 참조하세요.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

## <a name="custom-project-and-item-templates"></a>사용자 지정 프로젝트 및 항목 템플릿

Visual Studio 2017부터 는 사용자 지정 프로젝트 및 항목 템플릿에 대한 검색이 더 이상 수행되지 않습니다. 대신 확장은 이러한 템플릿의 설치 위치를 설명하는 템플릿 매니페스트 파일을 제공해야 합니다. Visual Studio 2017을 사용하여 VSIX 확장을 업데이트할 수 있습니다. If you deploy your extension using an MSI, you must generate the template manifest files by hand. 자세한 내용은 [Visual Studio 2017의 사용자 지정 프로젝트 및 항목 템플릿 업그레이드를](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md)참조하십시오. 템플릿 매니페스트 스키마는 [Visual Studio 템플릿 매니페스트 스키마 참조에](../extensibility/visual-studio-template-manifest-schema-reference.md)설명되어 있습니다.

## <a name="updated-extension-performance-guidelines"></a>업데이트된 확장 성능 지침

새로운 방법: [VSPackage 관리에서](managing-vspackages.md) 확장 성능 문서를 [진단하여](how-to-diagnose-extension-performance.md) Visual Studio 시작 및 솔루션 로드 시간에 대한 확장 영향을 감지하고 분석하는 방법을 보여 준다.
