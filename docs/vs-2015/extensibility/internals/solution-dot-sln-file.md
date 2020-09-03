---
title: 솔루션 (. Sln) 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d9e045ab707620fe985e34174238081f6168e5af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154969"
---
# <a name="solution-sln-file"></a>솔루션(.Sln) 파일
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

솔루션은 Visual Studio에서 프로젝트를 구성 하는 구조입니다. 솔루션은 .sln (텍스트 기반, 공유) 및 .suo (이진, 사용자 관련 솔루션 옵션) 파일의 프로젝트에 대 한 상태 정보를 유지 관리 합니다. .Suo 파일에 대 한 자세한 내용은 [솔루션 사용자 옵션 (을 참조 하세요. .Suo) 파일](../../extensibility/internals/solution-user-options-dot-suo-file.md)  
  
 .Sln 파일에서 참조 된 결과로 VSPackage이 로드 되 면 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> 를 호출 하 여 .sln 파일을 읽습니다.  
  
 .Sln 파일에는 지속 되는 데이터에 대 한 이름-값 매개 변수를 찾고 로드 하는 데 사용 하는 텍스트 기반 정보 (환경에서 참조 하는 Vspackage)가 포함 되어 있습니다. 사용자가 솔루션을 열면 환경에서는 `preSolution` `Project` .sln 파일의, 및 정보를 순환 `postSolution` 하 여 솔루션, 솔루션 내의 프로젝트 및 솔루션에 연결 된 지속형 정보를 로드 합니다.  
  
 각 프로젝트의 파일에는 계층 구조를 해당 프로젝트의 항목으로 채우도록 환경에서 읽은 추가 정보가 포함 되어 있습니다. 계층 데이터 지 속성은 프로젝트에 의해 제어 됩니다. 데이터는 일반적으로 .sln 파일에 저장 되지 않습니다 .이 작업을 수행 하도록 선택한 경우에는 프로젝트 정보를 .sln 파일에 의도적으로 쓸 수 있습니다. 지 속성과 관련 된 자세한 내용은 [프로젝트 지 속성](../../extensibility/internals/project-persistence.md) 및 [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)을 참조 하세요.  
  
## <a name="solution-file-contents"></a>솔루션 파일 콘텐츠  
 .Sln 파일은 다음 코드에 나와 있는 것 처럼 여러 섹션으로 구성 됩니다.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 솔루션을 로드 하기 위해 환경에서는 다음과 같은 일련의 작업을 수행 합니다.  
  
1. 환경에서는 .sln 파일의 전역 섹션을 읽고로 표시 된 모든 섹션을 처리 `preSolution` 합니다. 이 경우 다음 문이 하나 있습니다.  
  
   ```  
   GlobalSection(SolutionConfiguration) = preSolution  
        ConfigName.0 = Debug  
        ConfigName.1 = Release  
   ```  
  
    환경에서 태그를 읽으면 `GlobalSection('name')` 레지스트리를 사용 하 여 이름을 VSPackage에 매핑합니다. 키 이름은 레지스트리에 [HKLM \\<APPLICATION ID Registry Root \SolutionPersistence\AggregateGUIDs] 아래에 있어야 합니다 \> . 키의 기본값은 항목을 쓴 VSPackage의 패키지 GUID (REG_SZ)입니다.  
  
2. 환경에서는 VSPackage를 로드 하 고, `QueryInterface` 인터페이스에 대해 VSPackage를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> 하 고, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> VSPackage에서 데이터를 저장할 수 있도록 섹션의 데이터를 사용 하 여 메서드를 호출 합니다. 환경에서 각 섹션에 대해이 프로세스를 반복 `preSolution` 합니다.  
  
3. 환경에서 프로젝트 지 속성 블록을 반복 합니다. 이 경우 하나의 프로젝트가 있습니다.  
  
   ```  
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
   EndProject  
   ```  
  
    이 문에는 고유한 프로젝트 GUID 및 프로젝트 형식 GUID가 포함 됩니다. 이 정보는 환경에서 솔루션에 속한 프로젝트 파일을 찾는 데 사용 되며 각 프로젝트에 필요한 VSPackage입니다. 프로젝트와 관련 된 특정 VSPackage를 로드 하기 위해 프로젝트 GUID가에 전달 되 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 고 프로젝트는 VSPackage에 의해 로드 됩니다. 이 경우이 프로젝트에 대해 로드 된 VSPackage가 Visual Basic 됩니다.  
  
    각 프로젝트는 솔루션의 다른 프로젝트에서 필요에 따라 액세스할 수 있도록 고유한 프로젝트 인스턴스 ID를 유지할 수 있습니다. 이상적으로 솔루션과 프로젝트가 소스 코드 제어에 있는 경우 프로젝트에 대 한 경로는 솔루션 경로를 기준으로 해야 합니다. 솔루션이 처음 로드 될 때 프로젝트 파일은 사용자의 컴퓨터에 있을 수 없습니다. 프로젝트 파일을 솔루션 파일을 기준으로 서버에 저장 하 여 프로젝트 파일을 검색 하 고 사용자의 컴퓨터에 복사 하는 것은 비교적 간단 합니다. 그런 다음 프로젝트에 필요한 파일의 나머지 부분을 복사 하 고 로드 합니다.  
  
4. .Sln 파일의 프로젝트 섹션에 포함 된 정보를 기반으로 환경에서 각 프로젝트 파일을 로드 합니다. 프로젝트 자체는 프로젝트 계층 구조를 채우고 중첩 된 프로젝트를 로드 하는 일을 담당 합니다.  
  
5. .Sln 파일의 모든 섹션을 처리 한 후에는 솔루션이 솔루션 탐색기 표시 되며 사용자가 수정할 수 있습니다.  
  
   솔루션에서 프로젝트를 구현 하는 VSPackage가 로드 되지 않는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> 메서드가 호출 되 고 솔루션의 다른 모든 프로젝트에서 로드 하는 동안 수행 된 변경 내용을 무시할 수 있습니다. 구문 분석 오류가 발생 하면 가능한 한 많은 정보가 솔루션 파일에 유지 되 고 환경에서 사용자에 게 솔루션이 손상 되었다는 경고를 표시 하는 대화 상자를 표시 합니다.  
  
   솔루션이 저장 되거나 닫힐 때 메서드를 호출 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> 고 계층에 전달 하 여 .sln 파일에 입력 해야 하는 솔루션이 변경 되었는지 확인 합니다. 에서에 전달 된 null 값은 `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> 솔루션에 대 한 정보가 유지 되 고 있음을 나타냅니다. 값이 null이 아닌 경우 저장 된 정보는 인터페이스에 대 한 포인터에 의해 결정 되는 특정 프로젝트에 대 한 정보입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .  
  
   저장할 정보가 있는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 메서드에 대 한 포인터를 사용 하 여 인터페이스가 호출 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>그러면 환경에서 메서드를 호출 하 여 인터페이스에서 이름-값 쌍을 검색 하 `IPropertyBag` 고이 정보를 .sln 파일에 씁니다.  
  
   `SaveSolutionProps` 및 `WriteSolutionProps` 개체는 `IPropertyBag` 모든 변경 내용이 .sln 파일에 입력 될 때까지 인터페이스에서 저장할 정보를 검색 하기 위해 환경에서 재귀적으로 호출 됩니다. 이러한 방식으로 정보는 솔루션과 함께 유지 되 고 다음에 솔루션을 열 때 사용할 수 있도록 할 수 있습니다.  
  
   로드 된 모든 VSPackage은 .sln 파일에 저장할 내용이 있는지 여부를 확인 하기 위해 열거 됩니다. 레지스트리 키를 쿼리 하는 경우에만 로드 됩니다. 환경에서는 솔루션을 저장할 때 메모리에 있으므로 로드 된 모든 패키지에 대해 알고 있습니다.  
  
   .Sln 파일에만 `preSolution` 및 섹션의 항목이 포함 됩니다 `postSolution` . 솔루션이 제대로 로드 하려면이 정보가 필요 하므로 .suo 파일에는 유사한 섹션이 없습니다. .Suo 파일에는 소스 코드 제어에서 공유 하거나 저장 하지 않으려는 전용 메모와 같은 사용자별 옵션이 포함 되어 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [솔루션 사용자 옵션 () .Suo) 파일](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [솔루션](../../extensibility/internals/solutions-overview.md)
