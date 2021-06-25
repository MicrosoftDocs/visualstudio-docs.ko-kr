---
title: Single-File 생성기 | 구현 Microsoft Docs
description: IVsSingleFileGenerator 인터페이스를 구현하는 사용자 지정 도구를 사용하여 Visual Studio Visual Basic 및 Visual C# 프로젝트 시스템을 확장하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11ce8a69841d18d383e9d8e12c14d7af652d9cb8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900046"
---
# <a name="implementing-single-file-generators"></a>단일 파일 생성기 구현
단일 파일 생성기라고도 하는 사용자 지정 도구를 사용하여 에서 및 프로젝트 시스템을 확장할 수 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 있습니다. 사용자 지정 도구는 인터페이스를 구현하는 COM 구성 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 요소입니다. 사용자 지정 도구는 이 인터페이스를 사용하여 단일 입력 파일을 단일 출력 파일로 변환합니다. 변환의 결과는 소스 코드이거나 유용한 다른 출력일 수 있습니다. 사용자 지정 도구 생성 코드 파일의 두 가지 예는 비주얼 디자이너의 변경 내용에 대한 응답으로 생성된 코드와 WSDL(웹 서비스 설명 언어)을 사용하여 생성된 파일입니다.

 사용자 지정 도구가 로드되거나 입력 파일이 저장되면 프로젝트 시스템은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 메서드를 호출하고 콜백 인터페이스에 참조를 전달하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> 도구가 사용자에게 진행 상황을 보고할 수 있습니다.

 사용자 지정 도구에서 생성하는 출력 파일은 입력 파일에 대한 종속성을 사용하여 프로젝트에 추가됩니다. 프로젝트 시스템은 사용자 지정 도구의 구현에서 반환된 문자열에 따라 출력 파일의 이름을 자동으로 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> 결정합니다.

 사용자 지정 도구는 인터페이스를 구현해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 합니다. 필요에 따라 사용자 지정 도구는 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> 인터페이스를 지원하여 입력 파일 이외의 소스에서 정보를 검색합니다. 어떤 경우든 사용자 지정 도구를 사용하려면 먼저 시스템 또는 로컬 레지스트리에 등록해야 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. 사용자 지정 도구 등록에 대한 자세한 내용은 [단일 파일 생성기 등록을 참조하세요.](../../extensibility/internals/registering-single-file-generators.md)

## <a name="see-also"></a>참조
- [비주얼 디자이너에 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)
