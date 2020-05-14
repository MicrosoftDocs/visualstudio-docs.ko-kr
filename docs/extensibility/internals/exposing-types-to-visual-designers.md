---
title: 비주얼 디자이너에 형식 노출 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9067f88b4bf1334e23a548bc6a2cbeb3eac6ad33
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708432"
---
# <a name="expose-types-to-visual-designers"></a>시각적 디자이너에게 형식 노출
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]시각적 디자이너를 표시하려면 디자인 시간에 클래스 및 형식 정의에 액세스할 수 있어야 합니다. 클래스는 현재 프로젝트의 전체 종속성 집합(참조와 해당 종속성)을 포함하는 미리 정의된 어셈블리 집합에서 로드됩니다. 또한 시각적 디자이너가 사용자 지정 도구에서 생성된 파일에 정의된 클래스 및 형식에 액세스해야 할 수도 있습니다.

 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 및 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 프로젝트 시스템은 임시 이식 가능한 실행 파일(임시 PE)을 통해 생성된 클래스 및 형식에 액세스할 수 있도록 지원합니다. 사용자 지정 도구에서 생성된 모든 파일을 임시 어셈블리로 컴파일하여 해당 어셈블리에서 형식을 로드하고 디자이너에 노출할 수 있습니다. 각 사용자 지정 도구의 출력은 별도의 임시 PE로 컴파일되며 이 임시 컴파일의 성공 여부는 생성된 파일을 컴파일할 수 있는지 여부에 따라 달라집니다. 프로젝트가 전체적으로 빌드되지 않더라도 개별 임시 P는 설계자가 계속 사용할 수 있습니다.

 프로젝트 시스템은 이러한 변경 사항이 사용자 지정 도구를 실행한 결과인 경우 사용자 지정 도구의 출력 파일에 대한 변경 내용을 추적할 수 있도록 완전한 지원을 제공합니다. 사용자 지정 도구를 실행할 때마다 새 임시 PE가 생성되고 적절한 알림이 디자이너에게 전송됩니다.

> [!NOTE]
> 임시 프로그램 실행 파일 생성 파일이 백그라운드에서 발생하기 때문에 컴파일에 실패하면 사용자에게 오류가 보고되지 않습니다.

 임시 PE 지원을 활용하는 사용자 지정 도구는 다음 규칙을 따라야 합니다.

- **생성디자인타임소스는** 레지스트리에서 1로 설정해야 합니다.

     이 설정없이 프로그램 실행 파일 컴파일이 수행되지 않습니다.

- 생성된 코드는 전역 프로젝트 설정과 동일한 언어여야 합니다.

     임시 PE는 **생성DesignTimeSource가** 레지스트리에서 1로 설정된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> 경우 요청된 확장으로 사용자 지정 도구가 보고하는 내용에 관계없이 컴파일됩니다. 확장은 *.vb,* *.cs,* 또는 *.jsl일*필요는 없습니다. 그것은 어떤 확장 될 수 있습니다.

- 사용자 지정 도구에서 생성된 코드는 유효해야 하며 실행이 완료될 때 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 프로젝트에 있는 참조 집합만 사용하여 자체적으로 컴파일해야 합니다.

     임시 PE가 컴파일될 때 컴파일러에 제공되는 유일한 소스 파일은 사용자 지정 도구 출력입니다. 따라서 임시 PE를 사용하는 사용자 지정 도구는 프로젝트의 다른 파일과 독립적으로 컴파일할 수 있는 출력 파일을 생성해야 합니다.

## <a name="see-also"></a>참조
- [BuildManager 개체 소개](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [단일 파일 생성기 구현](../../extensibility/internals/implementing-single-file-generators.md)
- [단일 파일 생성기 등록](../../extensibility/internals/registering-single-file-generators.md)
