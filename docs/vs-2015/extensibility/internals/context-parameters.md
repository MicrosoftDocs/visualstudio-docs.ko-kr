---
title: 컨텍스트 매개 변수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 679bf567d2f44564d31d70b62c8663e665e1ea65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697282"
---
# <a name="context-parameters"></a>컨텍스트 매개 변수
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE (통합 개발 환경)에서 마법사를 **새 프로젝트**, **새 항목 추가**또는 **하위 프로젝트 추가** 대화 상자에 추가할 수 있습니다. 추가 된 마법사는 **파일** 메뉴 또는 **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 여 사용할 수 있습니다. IDE는 컨텍스트 매개 변수를 마법사의 구현에 전달 합니다. 컨텍스트 매개 변수는 IDE에서 마법사를 호출할 때 프로젝트의 상태를 정의 합니다.  
  
 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> ide의 호출에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> 프로젝트의 메서드에 대 한 플래그를 설정 하 여 마법사를 시작 합니다. 설정 되 면 프로젝트에서 `IVsExtensibility::RunWizardFile` 등록 된 마법사 이름 또는 GUID 및 IDE가 전달 하는 기타 컨텍스트 매개 변수를 사용 하 여 메서드를 실행 해야 합니다.  
  
## <a name="context-parameters-for-new-project"></a>새 프로젝트에 대 한 컨텍스트 매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`WizardType`|등록 된 마법사 유형 ( <xref:EnvDTE.Constants.vsWizardNewProject> ) 또는 마법사의 유형을 나타내는 GUID입니다. 구현에서 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 마법사의 GUID는 {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}입니다.|  
|`ProjectName`|고유한 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 이름인 문자열입니다.|  
|`LocalDirectory`|작업 중인 프로젝트 파일의 로컬 위치입니다.|  
|`InstallationDirectory`|설치의 디렉터리 경로입니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .|  
|`FExclusive`|프로젝트에서 열려 있는 솔루션을 닫아야 함을 나타내는 부울 플래그입니다.|  
|`SolutionName`|디렉터리 부분이 나 .sln 확장명이 없는 솔루션 파일의 이름입니다. 를 사용 하 여 .suo 파일 이름도 만들 수도 있습니다 `SolutionName` . 이 인수가 빈 문자열이 아닌 경우 마법사는를 사용 하 여 <xref:EnvDTE._Solution.Create%2A> 프로젝트를 추가 하기 전에를 사용 <xref:EnvDTE._Solution.AddFromTemplate%2A> 합니다. 이 이름이 빈 문자열이 면를 <xref:EnvDTE._Solution.AddFromTemplate%2A> 호출 하지 않고를 사용 <xref:EnvDTE._Solution.Create%2A> 합니다.|  
|`Silent`|**마침** 을 클릭 하면 마법사가 자동으로 실행 되어야 하는지 여부 ()를 나타내는 부울입니다 `TRUE` .|  
  
## <a name="context-parameters-for-add-new-item"></a>새 항목 추가에 대 한 컨텍스트 매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`WizardType`|등록 된 마법사 유형 ( <xref:EnvDTE.Constants.vsWizardAddItem> ) 또는 마법사의 유형을 나타내는 GUID입니다. 구현에서 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 마법사의 GUID는 {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}입니다.|  
|`ProjectName`|고유한 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 이름인 문자열입니다.|  
|`ProjectItems`|작업 프로젝트 파일을 포함 하는 로컬 위치입니다.|  
|`ItemName`|추가할 항목의 이름입니다. 이 이름은 기본 파일 이름 이거나 **항목 추가** 대화 상자에서 사용자가 입력 하는 파일 이름입니다. 이름은 .vsdir 파일에 설정 된 플래그를 기반으로 합니다. 이름은 null 값일 수 있습니다.|  
|`InstallationDirectory`|설치의 디렉터리 경로입니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .|  
|`Silent`|**마침** 을 클릭 하면 마법사가 자동으로 실행 되어야 하는지 여부 ()를 나타내는 부울입니다 `TRUE` .|  
  
## <a name="context-parameters-for-add-sub-project"></a>하위 프로젝트 추가에 대 한 컨텍스트 매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`WizardType`|등록 된 마법사 유형 ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) 또는 마법사의 유형을 나타내는 GUID입니다. 구현에서 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 마법사의 GUID는 {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}입니다.|  
|`ProjectName`|고유한 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트 이름인 문자열입니다.|  
|`ProjectItems`|마법사가 작동 하는 컬렉션에 대 한 포인터 `ProjectItems` 입니다. 이 포인터는 프로젝트 계층 구조 선택에 따라 마법사로 전달 됩니다. 일반적으로 사용자는 항목을 배치할 폴더를 선택 하 고 프로젝트의 **항목 추가** 대화 상자를 호출 합니다.|  
|`LocalDirectory`|작업 중인 프로젝트 파일의 로컬 위치입니다.|  
|`ItemName`|추가할 항목의 이름입니다. 이 이름은 기본 파일 이름 이거나 **항목 추가** 대화 상자에서 사용자가 입력 하는 파일 이름입니다. 이름은 .vsdir 파일에 설정 된 플래그를 기반으로 합니다. 이름은 null 값일 수 있습니다.|  
|`InstallationDirectory`|설치의 디렉터리 경로입니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .|  
|`Silent`|**마침** 을 클릭 하면 마법사가 자동으로 실행 되어야 하는지 여부 ()를 나타내는 부울입니다 `TRUE` .|  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)   
 [마법사로](../../extensibility/internals/wizards.md)   
 [마법사 (. .Vsz 파일](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [마법사를 시작하는 데 사용되는 컨텍스트 매개 변수](https://msdn.microsoft.com/library/051a10f4-9e45-4604-b344-123044f33a24)
