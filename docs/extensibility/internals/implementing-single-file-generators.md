---
title: 단일 파일 생성기 구현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707652"
---
# <a name="implementing-single-file-generators"></a>단일 파일 생성기 구현
단일 파일 생성기라고도 하는 사용자 지정 도구를 사용하여 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 에서 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 및 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]프로젝트 시스템을 확장할 수 있습니다. 사용자 지정 도구는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 인터페이스를 구현하는 COM 구성 요소입니다. 이 인터페이스를 사용하여 사용자 지정 도구는 단일 입력 파일을 단일 출력 파일로 변환합니다. 변환의 결과는 소스 코드 또는 유용한 다른 출력일 수 있습니다. 사용자 지정 도구 생성 코드 파일의 두 가지 예는 시각적 디자이너의 변경에 대한 응답으로 생성된 코드와 WSDL(웹 서비스 설명 언어)을 사용하여 생성된 파일입니다.

 사용자 지정 도구가 로드되거나 입력 파일이 저장되면 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 시스템은 메서드를 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> 콜백 인터페이스에 대한 참조를 전달하여 도구가 진행 상황을 사용자에게 보고할 수 있습니다.

 사용자 지정 도구가 생성하는 출력 파일은 입력 파일에 종속되어 프로젝트에 추가됩니다. 프로젝트 시스템은 사용자 지정 도구의 구현에서 반환되는 문자열에 따라 출력 파일의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>이름을 자동으로 결정합니다.

 사용자 지정 도구는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 인터페이스를 구현해야 합니다. 선택적으로 사용자 지정 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> 도구는 입력 파일이 아닌 다른 소스에서 정보를 검색하는 인터페이스를 지원합니다. 어쨌든 사용자 지정 도구를 사용하려면 먼저 시스템 이나 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 로컬 레지스트리에 등록해야 합니다. 사용자 지정 도구 등록에 대한 자세한 내용은 [단일 파일 생성기 등록을](../../extensibility/internals/registering-single-file-generators.md)참조하십시오.

## <a name="see-also"></a>참조
- [비주얼 디자이너에 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)
