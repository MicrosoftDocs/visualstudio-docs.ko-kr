---
title: 출력에 대 한 프로젝트 구성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: addd7e8630ce35c6bdbbbb4c063197f75a74c97d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300676"
---
# <a name="project-configuration-for-output"></a>출력에 대한 프로젝트 구성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

모든 구성은 실행 파일, 리소스 파일 등의 출력 항목을 생성 하는 빌드 프로세스 집합을 지원할 수 있습니다. 이러한 출력 항목은 사용자에 게 전용 이며 실행 파일 (.exe, .dll, .lib) 및 소스 파일 (.idl, .h 파일)과 같은 관련 된 출력 형식을 연결 하는 그룹에 배치할 수 있습니다.  
  
 출력 항목은 메서드를 통해 사용할 수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> 있고 메서드로 열거할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> . 출력 항목을 그룹화 하려는 경우 프로젝트도 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> .  
  
 을 구현 하 여 개발한 구문을 `IVsOutputGroup` 사용 하면 프로젝트에서 사용에 따라 출력을 그룹화 할 수 있습니다. 예를 들어 DLL은 PDB (프로그램 데이터베이스)와 함께 그룹화 될 수 있습니다.  
  
> [!NOTE]
> PDB 파일은 디버깅 정보를 포함 하며 .dll 또는 .exe를 빌드할 때 ' 디버그 정보 생성 ' 옵션이 지정 된 경우에 생성 됩니다. .Pdb 파일은 일반적으로 디버그 프로젝트 구성에 대해서만 생성 됩니다.  
  
 그룹에 포함 된 출력 수가 구성 마다 다를 수 있지만 프로젝트는 지 원하는 각 구성에 대해 동일한 수의 그룹을 반환 해야 합니다. 예를 들어, 프로젝트 Matt의 DLL은 디버그 구성에 mattd.dll 및 mattd를 포함할 수 있지만, 소매점 구성에는 matt.dll 포함 합니다.  
  
 또한 그룹은 구성에서 프로젝트 내의 구성으로의 정식 이름, 표시 이름 및 그룹 정보와 같은 동일한 식별자 정보를 가집니다. 이러한 일관성을 통해 구성이 변경 되는 경우에도 배포 및 패키징을 계속 작동할 수 있습니다.  
  
 그룹에는 의미 있는 항목을 가리키는 패키징 바로 가기를 허용 하는 키 출력이 있을 수 있습니다. 지정 된 구성에서 모든 그룹이 비어 있을 수 있으므로 그룹 크기에 대 한 가정을 수행할 필요가 없습니다. 모든 구성에서 각 그룹의 크기 (출력 수)는 동일한 구성의 다른 그룹 크기와 다를 수 있습니다. 다른 구성에서 동일한 그룹의 크기와 다를 수도 있습니다.  
  
 ![출력 그룹 그래픽](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
출력 그룹  
  
 인터페이스의 주요 용도는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> 관리 개체를 빌드, 배포 및 디버그할 수 있는 액세스를 제공 하 고 프로젝트에서 출력을 그룹화 할 수 있도록 허용 하는 것입니다. 이 인터페이스를 사용 하는 방법에 대 한 자세한 내용은 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)를 참조 하세요.  
  
 위의 다이어그램에서 구성 된 그룹에는 구성에 대 한 키 출력이 있습니다 (bD.exe 또는 b.exe) .이를 통해 사용자는 빌드에 대 한 바로 가기를 만들어 배포 된 구성에 관계 없이 바로 가기가 작동 한다는 것을 알 수 있습니다. 그룹 원본에 키 출력이 없으므로 사용자는 바로 가기를 만들 수 없습니다. 빌드된 디버그 그룹에 키 출력이 있지만 기본 정품 그룹이 빌드되지 않은 경우에는 잘못 된 구현입니다. 그런 다음 구성에 출력이 포함 되지 않은 그룹이 있고 그 결과 키 파일이 없는 경우 출력이 포함 된 해당 그룹의 다른 구성에는 키 파일이 있을 수 없습니다. 설치 관리자 편집기는 그룹의 정식 이름과 표시 이름이 구성에 따라 변경 되지 않는 것으로 가정 합니다.  
  
 프로젝트에 `IVsOutputGroup` 패키지 또는 배포를 원하지 않는가 있는 경우 해당 출력을 그룹에 넣지 않아도 됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>그룹화에 관계 없이 모든 구성의 출력을 반환 하는 메서드를 구현 하 여 출력을 정상적으로 계속 열거할 수 있습니다.  
  
 자세한 내용은 `IVsOutputGroup` [프로젝트에 대 한 MPF](https://archive.codeplex.com/?p=mpfproj12)의 사용자 지정 프로젝트 샘플에서 구현을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)   
 [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)   
 [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)   
 [솔루션 구성](../../extensibility/internals/solution-configuration.md)
