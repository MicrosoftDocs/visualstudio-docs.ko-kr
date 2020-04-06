---
title: VSIX 프로젝트 템플릿 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697930"
---
# <a name="vsix-project-template"></a>VSIX 프로젝트 템플릿

VSIX 프로젝트 템플릿을 사용하여 VSIX 프로젝트에서 하나 이상의 Visual Studio 확장을 래핑한 다음 [Visual Studio 마켓플레이스](https://marketplace.visualstudio.com/) 웹 사이트에 패키지를 게시할 수 있습니다.

 VSIX 배포는 VSPackage, 어셈블리, MEF 구성 요소, 프로젝트 템플릿, 항목 템플릿, 도구 상자 컨트롤 및 사용자 지정 확장 유형을 지원합니다.

> [!NOTE]
> VSIX 프로젝트를 사용하려면 Visual Studio SDK를 설치해야 합니다. 비주얼 스튜디오 SDK에 대한 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

## <a name="where-to-find-the-vsix-project-template"></a>VSIX 프로젝트 템플릿을 찾을 수 있는 위치

VSIX 프로젝트 템플릿은 "vsix"를 검색하여 **새 프로젝트** 대화 상자에서 사용할 수 있습니다.  C# 및 시각적 기본 버전이 모두 있습니다.

> [!TIP]
> .NET Framework 4.5 이상은 **새 프로젝트** 대화 상자 상단의 드롭다운 목록 상자에 지정되어 있는지 확인해야 합니다.

## <a name="uses-of-the-vsix-project-template"></a>VSIX 프로젝트 템플릿 사용

VSIX 프로젝트 템플릿에는 두 가지 주요 용도가 있습니다.

- 프로젝트 템플릿, 항목 템플릿 및 확장을 배포합니다.

- 여러 확장의 출력을 하나의 배포 패키지로 래핑합니다.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>빈 VSIX 프로젝트에서 확장 패키징

빈 VSIX 프로젝트에 래핑하여 기존 확장 또는 VSIX 지원이 없는 확장을 패키징할 수 있습니다. 래핑할 확장은 [VSIX 스키마에서](../extensibility/vsix-extension-schema-2-0-reference.md)지원하는 형식이어야 합니다.

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>VSIX 프로젝트를 사용하여 확장을 패키징하려면

1. 확장을 구성하는 프로젝트를 빌드합니다.

2. VSIX 프로젝트 템플릿을 사용하여 **VSIX 프로젝트를** 만듭니다.

    *Source.extension.vsixmanifest* **매니페스트 디자이너에서**열립니다.

3. **자산** 탭에서 **새** 단추를 선택합니다.

    **새 자산 추가** 대화 상자가 나타납니다.

4. **유형** 목록에서 추가할 확장 유형을 선택합니다.

5. 현재 솔루션에 포함된 확장 또는 콘텐츠 요소(예: 항목 템플릿 또는 컴파일된 어셈블리)를 추가하려면 다음 단계를 수행합니다.

   1. **소스** 목록에서 현재 **솔루션의 A 프로젝트를 선택합니다.**

   2. **프로젝트** 목록에서 확장의 이름을 선택합니다.

   3. 이 폴더 상자에 **포함하려면** 에셋을 포함할 폴더의 이름을 입력한 다음 **확인** 단추를 선택합니다.

6. 현재 솔루션에 포함되지 않은 확장 또는 콘텐츠 요소를 추가하려면 다음 단계를 수행합니다.

   1. **소스** 목록 상자에서 **파일 시스템에서 파일을**선택합니다.

   2. **경로** 필드에서 컴파일되거나 압축된 확장자 파일에 대한 전체 경로를 입력하거나 **찾아보기** 단추를 사용하여 파일을 찾아봅봅합니다.

   3. 이 폴더 상자에 **포함하려면** 에셋을 포함할 폴더의 이름을 입력한 다음 **확인** 단추를 선택합니다.

7. 패키지에 추가 확장을 포함하려면 동일한 방식으로 추가합니다.

8. 솔루션을 빌드합니다.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서는 VSIX 매니페스트 파일, [Content_Types]*.xml* 파일 및 프로젝트에 추가한 모든 확장 자 자산이 포함된 *.vsix* 파일을 빌드합니다.

## <a name="see-also"></a>참조

- [VSIX 확장 스키마 2.0 참조](../extensibility/vsix-extension-schema-2-0-reference.md)
- [비주얼 스튜디오 확장 프로그램 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)
