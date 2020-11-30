---
title: 사용자 지정 도구 | Microsoft Docs
description: Visual Studio에서 도구를 프로젝트의 항목과 연결 하 고 파일이 저장 될 때마다 해당 도구를 실행 하는 사용자 지정 도구를 만드는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ba8760ce53f222ebbe4626bde0d897d4d12c8a6
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329967"
---
# <a name="custom-tools"></a>사용자 지정 도구
*사용자 지정 도구* 를 사용 하면 프로젝트의 항목과 도구를 연결 하 고 파일이 저장 될 때마다 해당 도구를 실행할 수 있습니다. *단일 파일 생성기* 라고도 하는 특정 사용자 지정 도구는 데이터에서 코드를 생성 하는 번역기를 구현 하는 데 자주 사용 되며 그 반대의 경우도 마찬가지입니다. 예를 들어 단일 파일 생성기는 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] *설정* 및 *.resx* 파일에서 코드를 만들고 소스 코드를 만듭니다. 생성 된 소스 코드는 *. settings* 및 *.resx* 파일의 데이터에 대해 강력한 형식의 액세스를 제공 합니다. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]및 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트 형식은 사용자 지정 도구를 지원 합니다. 프로젝트 형식은 사용자 지정 도구를 지원 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 하지 않습니다. 사용자 고유의 프로젝트 형식이 사용자 지정 도구를 지원할 수도 있습니다.

 사용자 지정 도구는 인터페이스를 구현 하는 등록 된 구성 요소 `IVsSingleFileGenerator` 입니다.

 사용자 지정 도구는 인터페이스 개체와 연결 되며 `ProjectItem` 디자이너 및 편집기와 비슷합니다. 사용자 지정 도구는로 표시 되는 파일을 `ProjectItem` 입력으로 사용 하 고 해당 파일 이름이 메서드에서 제공 하는 새 파일을 씁니다 `DefaultExtension` .

## <a name="in-this-section"></a>섹션 내용
- [단일 파일 생성기 구현](../../extensibility/internals/implementing-single-file-generators.md)

 인터페이스를 사용 하 여 사용자 지정 도구를 구현 하는 방법을 설명 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .

- [단일 파일 생성기 등록](../../extensibility/internals/registering-single-file-generators.md)

 사용자 지정 도구의 모든 레지스트리 항목에 대 한 설명을 제공 합니다.

- [비주얼 디자이너에 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)

 프로젝트 시스템에서 임시 PE (이식 가능한 실행) 파일을 통해 생성 된 클래스와 형식에 액세스 하기 위해 비주얼 디자이너를 지 원하는 방법을 설명 합니다.

- [프로젝트 항목의 속성 유지](../../extensibility/persisting-the-property-of-a-project-item.md)

 프로젝트 파일에서 소스 파일의 작성자와 같은 프로젝트 항목 속성을 유지 하는 방법을 보여 줍니다.

## <a name="reference"></a>참조
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator><xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>단일 입력 파일을 프로젝트에 컴파일하거나 추가할 수 있는 단일 출력 파일로 변환 하는에 대 한 세부 정보를 제공 합니다.

 <xref:EnvDTE.ProjectItem>`ProjectItem`프로젝트의 항목을 나타내는 인터페이스에 대해 설명 합니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>`DefaultExtension`출력 파일 이름에 지정 된 파일 이름 확장명을 검색 하는 메서드에 대 한 세부 정보를 제공 합니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 확장](../../extensibility/extending-projects.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 및 솔루션을 사용하여 코드 파일 및 리소스 파일을 구성하는 방법 및 소스 제어를 구현하는 방법을 설명합니다.
