---
title: 비주얼 디자이너에 형식 노출 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708432"
---
# <a name="expose-types-to-visual-designers"></a>비주얼 디자이너에 형식 노출
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 비주얼 디자이너를 표시 하기 위해 디자인 타임에 클래스 및 형식 정의에 대 한 액세스 권한이 있어야 합니다. 클래스는 현재 프로젝트의 전체 종속성 집합 (참조 및 해당 종속성)을 포함 하는 미리 정의 된 어셈블리 집합에서 로드 됩니다. 또한 비주얼 디자이너에서 사용자 지정 도구에 의해 생성 된 파일에 정의 된 클래스 및 형식에 액세스 해야 할 수도 있습니다.

 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]및 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 프로젝트 시스템은 임시 pe (임시 이식 가능한 실행 파일)를 통해 생성 된 클래스 및 형식에 액세스 하기 위한 지원을 제공 합니다. 사용자 지정 도구를 통해 생성 된 모든 파일은 해당 어셈블리에서 로드 되 고 디자이너에 노출 될 수 있도록 임시 어셈블리로 컴파일될 수 있습니다. 각 사용자 지정 도구의 출력은 별도의 임시 PE로 컴파일되고,이 임시 컴파일의 성공 또는 실패는 생성 된 파일을 컴파일할 수 있는지 여부에 따라 달라 집니다. 프로젝트가 전체적으로 빌드되지 않을 수도 있지만, 개별 임시 Pe는 디자이너에서 계속 사용할 수 있습니다.

 프로젝트 시스템은 사용자 지정 도구를 실행 한 결과를 변경 하는 경우 사용자 지정 도구의 출력 파일에 대 한 변경 내용 추적을 완벽 하 게 지원 합니다. 사용자 지정 도구가 실행 될 때마다 새 임시 PE가 생성 되 고 디자이너에 적절 한 알림이 전송 됩니다.

> [!NOTE]
> 임시 프로그램 실행 파일 생성 파일은 백그라운드에서 발생 하므로 컴파일이 실패할 경우 사용자에 게 오류를 보고 하지 않습니다.

 임시 PE 지원을 활용 하는 사용자 지정 도구는 다음 규칙을 따라야 합니다.

- **GeneratesDesignTimeSource** 는 레지스트리에서 1로 설정 되어야 합니다.

     이 설정을 사용 하지 않으면 프로그램 실행 파일 컴파일이 발생 하지 않습니다.

- 생성 된 코드는 전역 프로젝트 설정과 동일한 언어 여야 합니다.

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>레지스트리에서 **GeneratesDesignTimeSource** 가 1로 설정 된 경우 사용자 지정 도구에서 요청 된 확장 프로그램으로 보고 하는 내용에 관계 없이 임시 PE가 컴파일됩니다. 확장명은 .vb, *.cs*또는 *.jsl*일 필요가 없습니다 *.* 모든 확장이 가능 합니다.

- 사용자 지정 도구에서 생성 된 코드는 유효 해야 하며, 실행이 완료 될 때 프로젝트에 있는 참조 집합만 사용 하 여 자체적으로 컴파일해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> .

     임시 PE가 컴파일되면 컴파일러에 제공 되는 유일한 소스 파일은 사용자 지정 도구 출력입니다. 따라서 임시 PE를 사용 하는 사용자 지정 도구는 프로젝트의 다른 파일과 독립적으로 컴파일할 수 있는 출력 파일을 생성 해야 합니다.

## <a name="see-also"></a>참고 항목
- [BuildManager 개체 소개](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [단일 파일 생성기 구현](../../extensibility/internals/implementing-single-file-generators.md)
- [단일 파일 생성기 등록](../../extensibility/internals/registering-single-file-generators.md)
