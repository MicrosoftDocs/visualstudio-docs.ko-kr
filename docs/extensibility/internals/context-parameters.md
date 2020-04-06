---
title: 컨텍스트 매개 변수 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709304"
---
# <a name="context-parameters"></a>컨텍스트 매개 변수
통합 개발 환경(IDE)에서 **새 프로젝트에**마법사를 추가하거나 새 **항목을 추가하거나**하위 프로젝트 대화 상자를 추가할 수 있습니다. **Add Sub Project** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 추가된 마법사는 **파일** 메뉴또는 **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭하여 사용할 수 있습니다. IDE는 컨텍스트 매개 변수를 마법사의 구현에 전달합니다. 컨텍스트 매개 변수는 IDE가 마법사를 호출할 때 프로젝트의 상태를 정의합니다.

 IDE는 프로젝트에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> 메서드에 대한 IDE 호출에서 플래그를 설정하여 마법사를 시작합니다. 설정하면 프로젝트는 등록된 마법사 `IVsExtensibility::RunWizardFile` 이름 또는 GUID 및 IDE가 전달하는 기타 컨텍스트 매개 변수를 사용하여 메서드를 실행해야 합니다.

## <a name="context-parameters-for-new-project"></a>새 프로젝트에 대한 컨텍스트 매개 변수

| 매개 변수 | 설명 |
|-------------------------| - |
| `WizardType` | 등록된 마법사<xref:EnvDTE.Constants.vsWizardNewProject>유형 () 또는 마법사의 유형을 나타내는 GUID입니다. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 구현에서 마법사의 GUID는 {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}입니다. |
| `ProjectName` | 고유한 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 이름인 문자열입니다. |
| `LocalDirectory` | 작업 프로젝트 파일의 로컬 위치입니다. |
| `InstallationDirectory` | 의 디렉터리 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 경로는 설치입니다. |
| `FExclusive` | 프로젝트가 열린 솔루션을 닫아야 한다는 부울 플래그입니다. |
| `SolutionName` | 디렉터리 부분 또는 *.sln* 확장자가 없는 솔루션 파일의 이름입니다. *.suo* 파일 이름도 을 `SolutionName`사용하여 만들어집니다. 이 인수가 빈 문자열이 아닌 <xref:EnvDTE._Solution.Create%2A> 경우 마법사는 <xref:EnvDTE._Solution.AddFromTemplate%2A>프로젝트를 로 추가하기 전에 사용합니다. 이 이름이 빈 문자열인 <xref:EnvDTE._Solution.AddFromTemplate%2A> 경우 <xref:EnvDTE._Solution.Create%2A>를 호출하지 않고 사용합니다. |
| `Silent` | **마법사가 마치 마침()을** 클릭한 것처럼 자동으로`TRUE`실행되어야 하는지 여부를 나타내는 부울입니다. |

## <a name="context-parameters-for-add-new-item"></a>새 항목 추가에 대한 컨텍스트 매개변수

| 매개 변수 | 설명 |
|-------------------------| - |
| `WizardType` | 등록된 마법사<xref:EnvDTE.Constants.vsWizardAddItem>유형 () 또는 마법사의 유형을 나타내는 GUID입니다. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 구현에서 마법사의 GUID는 {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}입니다. |
| `ProjectName` | 고유한 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 이름인 문자열입니다. |
| `ProjectItems` | 작업 중인 프로젝트 파일이 포함된 로컬 위치입니다. |
| `ItemName` | 추가할 항목의 이름입니다. 이 이름은 기본 파일 이름 또는 사용자가 **항목 추가** 대화 상자에서 입력하는 파일 이름입니다. 이름은 *.vsdir* 파일에 설정된 플래그를 기반으로 합니다. 이름은 null 값일 수 있습니다. |
| `InstallationDirectory` | 의 디렉터리 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 경로는 설치입니다. |
| `Silent` | **마법사가 마치 마침()을** 클릭한 것처럼 자동으로`TRUE`실행되어야 하는지 여부를 나타내는 부울입니다. |

## <a name="context-parameters-for-add-sub-project"></a>하위 프로젝트 추가에 대한 컨텍스트 매개변수

| 매개 변수 | 설명 |
|-------------------------| - |
| `WizardType` | 등록된 마법사<xref:EnvDTE.Constants.vsWizardAddSubProject>유형 () 또는 마법사의 유형을 나타내는 GUID입니다. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 구현에서 마법사의 GUID는 {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}입니다. |
| `ProjectName` | 고유한 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 이름인 문자열입니다. |
| `ProjectItems` | 마법사가 `ProjectItems` 작동하는 컬렉션에 대한 포인터입니다. 이 포인터는 프로젝트 계층 구조 선택에 따라 마법사에 전달됩니다. 사용자는 일반적으로 항목을 넣을 폴더를 선택한 다음 프로젝트의 **항목 추가** 대화 상자를 호출합니다. |
| `LocalDirectory` | 작업 프로젝트 파일의 로컬 위치입니다. |
| `ItemName` | 추가할 항목의 이름입니다. 이 이름은 기본 파일 이름 또는 사용자가 **항목 추가** 대화 상자에서 입력하는 파일 이름입니다. 이름은 *.vsdir* 파일에 설정된 플래그를 기반으로 합니다. 이름은 null 값일 수 있습니다. |
| `InstallationDirectory` | 설치의 디렉터리 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 경로입니다. |
| `Silent` | **마법사가 마치 마침()을** 클릭한 것처럼 자동으로`TRUE`실행되어야 하는지 여부를 나타내는 부울입니다. |

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)
- [마법사](../../extensibility/internals/wizards.md)
- [마법사(.vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
- [마법사 를 시작하기 위한 컨텍스트 매개 변수](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
