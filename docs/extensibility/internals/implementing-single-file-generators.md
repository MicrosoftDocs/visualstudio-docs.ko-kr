---
title: 단일 파일 생성기 구현 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707652"
---
# <a name="implementing-single-file-generators"></a>단일 파일 생성기 구현
사용자 지정 도구 (단일 파일 생성기 라고도 함)는 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 에서 및 프로젝트 시스템을 확장 하는 데 사용할 수 있습니다 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 사용자 지정 도구는 인터페이스를 구현 하는 COM 구성 요소입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> . 사용자 지정 도구는이 인터페이스를 사용 하 여 단일 입력 파일을 단일 출력 파일로 변환 합니다. 변환 결과는 소스 코드 또는 유용한 기타 출력 일 수 있습니다. 사용자 지정 도구에서 생성 된 코드 파일의 두 가지 예는 비주얼 디자이너의 변경 내용에 대 한 응답으로 생성 된 코드와 WSDL (웹 서비스 기술 언어)을 사용 하 여 생성 된 파일입니다.

 사용자 지정 도구를 로드 하거나 입력 파일을 저장 하면 프로젝트 시스템에서 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 하 고 콜백 인터페이스에 대 한 참조를 전달 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> 도구에서 사용자에 게 진행률을 보고할 수 있습니다.

 사용자 지정 도구가 생성 하는 출력 파일은 입력 파일에 대 한 종속성이 있는 프로젝트에 추가 됩니다. 프로젝트 시스템은 사용자 지정 도구의 구현에서 반환 된 문자열을 기반으로 출력 파일의 이름을 자동으로 결정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 사용자 지정 도구는 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> . 필요에 따라 사용자 지정 도구는 인터페이스를 지원 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> 하 여 입력 파일이 아닌 소스에서 정보를 검색 합니다. 어떤 경우 든 사용자 지정 도구를 사용 하려면 먼저 시스템 또는 로컬 레지스트리에 등록 해야 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 사용자 지정 도구를 등록 하는 방법에 대 한 자세한 내용은 [단일 파일 생성기 등록](../../extensibility/internals/registering-single-file-generators.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [비주얼 디자이너에 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)
