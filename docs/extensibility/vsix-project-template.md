---
title: VSIX 프로젝트 템플릿 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697930"
---
# <a name="vsix-project-template"></a>VSIX 프로젝트 템플릿

VSIX 프로젝트 템플릿을 사용 하 여 VSIX 프로젝트에서 하나 이상의 Visual Studio 확장을 래핑하고 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트에서 패키지를 게시할 수 있습니다.

 VSIX 배포에서는 Vspackage, 어셈블리, MEF 구성 요소, 프로젝트 템플릿, 항목 템플릿, 도구 상자 컨트롤 및 사용자 지정 확장 형식을 지원 합니다.

> [!NOTE]
> VSIX 프로젝트를 사용 하려면 Visual Studio SDK를 설치 해야 합니다. Visual Studio SDK에 대 한 자세한 내용은 [Visual STUDIO sdk](../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="where-to-find-the-vsix-project-template"></a>VSIX 프로젝트 템플릿을 찾을 수 있는 위치

VSIX 프로젝트 템플릿은 **새 프로젝트** 대화 상자에서 "vsix"를 검색 하 여 사용할 수 있습니다.  C # 및 Visual Basic 버전이 모두 있습니다.

> [!TIP]
> **새 프로젝트** 대화 상자의 맨 위에 있는 드롭다운 목록 상자에 .NET Framework 4.5 이상이 지정 되어 있는지 확인 해야 합니다.

## <a name="uses-of-the-vsix-project-template"></a>VSIX 프로젝트 템플릿 사용

VSIX 프로젝트 템플릿에는 두 가지 주요 사용이 있습니다.

- 프로젝트 템플릿, 항목 템플릿 및 확장을 배포 합니다.

- 여러 확장의 출력을 하나의 배포 패키지로 래핑합니다.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>빈 VSIX 프로젝트에서 확장 패키징

기존 확장 또는 VSIX를 아직 지원 하지 않는 확장을 빈 VSIX 프로젝트로 래핑하여 패키지할 수 있습니다. 래핑할 확장은 [VSIX 스키마](../extensibility/vsix-extension-schema-2-0-reference.md)에서 지원 되는 형식 이어야 합니다.

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>VSIX 프로젝트를 사용 하 여 확장을 패키지 하려면

1. 확장을 구성 하는 프로젝트를 빌드합니다.

2. **Vsix 프로젝트** 템플릿을 사용 하 여 vsix 프로젝트를 만듭니다.

    *Source.extension.vsixmanifest* 이 **매니페스트 디자이너**에서 열립니다.

3. **자산** 탭에서 **새로 만들기** 단추를 선택 합니다.

    **새 자산 추가** 대화 상자가 나타납니다.

4. **유형** 목록에서 추가할 확장 유형을 선택 합니다.

5. 현재 솔루션에 포함 된 extension 또는 content 요소 (예: 항목 템플릿 또는 컴파일된 어셈블리)를 추가 하려면 다음 단계를 수행 합니다.

   1. **원본** 목록에서 **현재 솔루션의 프로젝트**를 선택 합니다.

   2. **프로젝트** 목록에서 확장의 이름을 선택 합니다.

   3. **이 폴더에 포함** 상자에 자산을 포함할 폴더의 이름을 입력 하 고 **확인** 단추를 선택 합니다.

6. 현재 솔루션에 포함 되지 않은 확장 또는 콘텐츠 요소를 추가 하려면 다음 단계를 수행 합니다.

   1. **원본** 목록 상자에서 **파일 시스템의 파일**을 선택 합니다.

   2. **경로** 필드에 컴파일된 또는 압축 된 확장 파일의 전체 경로를 입력 하거나 **찾아보기** 단추를 사용 하 여 파일을 찾습니다.

   3. **이 폴더에 포함** 상자에 자산을 포함할 폴더의 이름을 입력 하 고 **확인** 단추를 선택 합니다.

7. 패키지에 추가 확장을 포함 하려는 경우 동일한 방식으로 추가 합니다.

8. 솔루션을 빌드합니다.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSIX 매니페스트 파일, [Content_Types]*.xml* 파일 및 프로젝트에 추가한 모든 확장 자산을 포함 하는 *.vsix* 파일을 빌드합니다.

## <a name="see-also"></a>추가 정보

- [VSIX 확장 스키마 2.0 참조](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Visual Studio 확장 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)
