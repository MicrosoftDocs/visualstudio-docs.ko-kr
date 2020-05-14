---
title: 사용자 지정 도구 | 마이크로 소프트 문서
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
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708953"
---
# <a name="custom-tools"></a>사용자 지정 도구
*사용자 지정 도구를* 사용하면 도구를 프로젝트의 항목과 연결하고 파일이 저장될 때마다 해당 도구를 실행할 수 있습니다. *단일 파일 생성기라고도*하는 특정 사용자 지정 도구는 데이터에서 코드를 생성하는 변환기를 구현하는 데 자주 사용되며 그 반대의 경우도 마찬가지입니다. 예를 들어 단일 파일 생성기는 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] *.settings* 및 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] *.resx* 파일에서 코드를 만들고 소스합니다. 생성된 소스 코드는 *.settings* 및 *.resx* 파일의 데이터에 대한 강력한 형식의 액세스를 제공합니다. 및 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트 유형은 사용자 지정 도구를 지원합니다. [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트 유형은 그렇지 않습니다. 사용자 지정 도구도 사용자 지정 도구를 지원할 수 있습니다.

 사용자 지정 도구는 인터페이스를 `IVsSingleFileGenerator` 구현하는 등록된 구성 요소입니다.

 사용자 지정 도구는 `ProjectItem` 인터페이스 개체와 연결되며 디자이너 및 편집자와 같습니다. 사용자 지정 도구는 입력으로 `ProjectItem` 표시된 파일을 가져와 `DefaultExtension` 메서드에서 파일 이름이 제공되는 새 파일을 씁니다.

## <a name="in-this-section"></a>섹션 내용
- [단일 파일 생성기 구현](../../extensibility/internals/implementing-single-file-generators.md)

 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 사용하여 사용자 지정 도구를 구현하는 방법을 설명합니다.

- [단일 파일 생성기 등록](../../extensibility/internals/registering-single-file-generators.md)

 사용자 지정 도구에 대한 모든 레지스트리 항목에 대한 설명을 제공합니다.

- [시각적 디자이너에게 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)

 프로젝트 시스템이 임시 PE(이식 가능한 실행 파일) 파일을 통해 생성된 클래스 및 형식에 액세스할 수 있도록 지원하는 방법을 설명합니다.

- [프로젝트 항목의 속성 유지](../../extensibility/persisting-the-property-of-a-project-item.md)

 프로젝트 파일에서 원본 파일의 작성자와 같은 프로젝트 항목 속성을 유지하는 방법을 보여 주습니다.

## <a name="reference"></a>참조
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>단일 입력 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>파일을 프로젝트에 컴파일하거나 추가할 수 있는 단일 출력 파일로 변환하는 에 대한 세부 정보를 제공합니다.

 <xref:EnvDTE.ProjectItem>프로젝트의 `ProjectItem` 항목을 나타내는 인터페이스에 대해 설명합니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>출력 파일 `DefaultExtension` 이름에 지정된 파일 이름 확장명을 검색하는 메서드에 대한 세부 정보를 제공합니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 확장](../../extensibility/extending-projects.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 및 솔루션을 사용하여 코드 파일 및 리소스 파일을 구성하는 방법 및 소스 제어를 구현하는 방법을 설명합니다.
