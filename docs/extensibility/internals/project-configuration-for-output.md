---
title: 출력을 위한 프로젝트 구성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b95457af4c5d806fdfcc20f49ac4e82df36488
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706666"
---
# <a name="project-configuration-for-output"></a>출력에 대한 프로젝트 구성
모든 구성은 실행 파일 또는 리소스 파일과 같은 출력 항목을 생성하는 빌드 프로세스 집합을 지원할 수 있습니다. 이러한 출력 항목은 사용자에게 비공개이며 실행 파일(.exe, .dll, .lib) 및 소스 파일(.idl, .h 파일)과 같은 관련 유형의 출력을 연결하는 그룹에 배치할 수 있습니다.

 출력 항목은 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> 통해 사용할 수 있고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> 메서드로 열거할 수 있습니다. 출력 항목을 그룹화하려면 프로젝트에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> 인터페이스도 구현해야 합니다.

 구현을 `IVsOutputGroup` 통해 개발된 구문은 프로젝트가 사용량에 따라 출력을 그룹화할 수 있도록 합니다. 예를 들어 DLL은 프로그램 데이터베이스(PDB)로 그룹화될 수 있습니다.

> [!NOTE]
> PDB 파일에는 디버깅 정보가 포함되어 있으며 .dll 또는 .exe를 빌드할 때 '디버그 정보 생성' 옵션이 지정될 때 만들어집니다. .pdb 파일은 일반적으로 디버그 프로젝트 구성에 대해서만 생성됩니다.

 프로젝트는 그룹에 포함된 출력 수가 구성마다 다를 수 있더라도 지원하는 각 구성에 대해 동일한 수의 그룹을 반환해야 합니다. 예를 들어 프로젝트 매트의 DLL은 디버그 구성에서 mattd.dll 및 mattd.pdb를 포함할 수 있지만 소매용 구성에는 matt.dll만 포함됩니다.

 또한 그룹에는 표준 이름, 표시 이름 및 그룹 정보와 같은 동일한 식별자 정보가 프로젝트 내의 구성에서 구성에 이르기까지 있습니다. 이러한 일관성을 통해 구성이 변경되더라도 배포 및 패키징이 계속 작동할 수 있습니다.

 그룹에는 패키징 바로 가기가 의미 있는 것을 가리킬 수 있는 키 출력이 있을 수도 있습니다. 지정된 구성에서 모든 그룹이 비어 있을 수 있으므로 그룹 크기에 대해 가정하지 않아야 합니다. 모든 구성에서 각 그룹의 크기(출력 수)는 동일한 구성의 다른 그룹의 크기와 다를 수 있습니다. 또한 다른 구성에서 동일한 그룹의 크기와 다를 수 있습니다.

 ![출력 그룹 그래픽](../../extensibility/internals/media/vsoutputgroups.gif "대 출력 그룹") 출력 그룹

 인터페이스의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> 주요 용도는 빌드, 배포 및 디버그 관리 개체에 대한 액세스를 제공하고 프로젝트에서 출력을 자유롭게 그룹화할 수 있도록 하는 것입니다. 이 인터페이스의 사용에 대한 자세한 내용은 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)를 참조하십시오.

 이전 다이어그램에서 Group Built는 구성(bD.exe 또는 b.exe)에 걸쳐 키 출력을 가지므로 사용자가 빌드에 대한 바로 가기를 만들고 배포된 구성에 관계없이 바로 가기를 작동할 수 있음을 알 수 있습니다. 그룹 소스에는 키 출력이 없으므로 사용자는 바로 가기를 만들 수 없습니다. 디버그 그룹 빌드에 키 출력이 있지만 빌드된 소매 그룹이 그렇지 않으면 잘못된 구현이 됩니다. 그런 다음 모든 구성에 출력이 없는 그룹이 있고 결과적으로 키 파일이 없는 경우 출력을 포함하는 해당 그룹의 다른 구성에는 키 파일이 있을 수 없습니다. 설치 관리자 편집기는 표준 이름과 그룹 이름 및 키 파일의 존재가 구성에 따라 변경되지 않는다고 가정합니다.

 프로젝트에 패키지 또는 배포를 원하지 않는 프로젝트가 있는 `IVsOutputGroup` 경우 해당 출력을 그룹에 넣지 않는 것으로 충분합니다. 그룹화에 관계없이 구성의 모든 출력을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> 반환하는 메서드를 구현하여 출력을 정상적으로 열거할 수 있습니다.

 자세한 내용은 프로젝트에 대한 `IVsOutputGroup` [MPF의](https://github.com/tunnelvisionlabs/MPFProj10)사용자 지정 프로젝트 샘플의 구현을 참조하십시오.

## <a name="see-also"></a>참조
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)
- [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)
- [솔루션 구성](../../extensibility/internals/solution-configuration.md)
