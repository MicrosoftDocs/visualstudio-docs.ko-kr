---
title: '새 프로젝트 생성: 내부에서 1 부 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f26c093f09cd5b7b99f00ee69a81be99c769e2e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184196"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>새 프로젝트 생성: 내부 살펴보기, 1부
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자 고유의 프로젝트 형식을 만드는 방법에 대해 생각 하 고 있나요? 새 프로젝트를 만들 때 실제로 발생 하는 일은 궁금 하십니까? 내부적으로 살펴보기를 수행 하 고 정말 진행 되 고 있는 것을 확인해 보겠습니다.  
  
 Visual Studio에서 조정 하는 몇 가지 작업은 다음과 같습니다.  
  
- 사용 가능한 모든 프로젝트 형식의 트리를 표시 합니다.  
  
- 각 프로젝트 형식에 대 한 응용 프로그램 템플릿 목록을 표시 하 고 하나를 선택할 수 있습니다.  
  
- 프로젝트 이름 및 경로와 같은 응용 프로그램에 대 한 프로젝트 정보를 수집 합니다.  
  
- 이 정보를 프로젝트 팩터리에 전달 합니다.  
  
- 현재 솔루션에 프로젝트 항목 및 폴더를 생성 합니다.  
  
## <a name="the-new-project-dialog-box"></a>새 프로젝트 대화 상자  
 새 프로젝트에 대 한 프로젝트 형식을 선택 하면 모두 시작 됩니다. **파일** 메뉴에서 **새 프로젝트** 를 클릭 하 여 시작 해 보겠습니다. **새 프로젝트** 대화 상자가 표시 되 고 다음과 같은 내용이 표시 됩니다.  
  
 ![새 프로젝트 대화 상자](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 측정값에 대해 좀 더 자세히 살펴보겠습니다. **프로젝트 형식** 트리에는 만들 수 있는 다양 한 프로젝트 형식이 나열 되어 있습니다. **Visual c # Windows**와 같은 프로젝트 형식을 선택 하면 시작 하는 데 사용할 수 있는 응용 프로그램 템플릿 목록이 표시 됩니다. **Visual studio에 설치 된 템플릿은** visual studio에 의해 설치 되며 컴퓨터의 모든 사용자가 사용할 수 있습니다. 만들거나 수집 하는 새 템플릿은 **내 템플릿에** 추가할 수 있으며 사용자만 사용할 수 있습니다.  
  
 **Windows 응용 프로그램과**같은 템플릿을 선택 하면 해당 응용 프로그램 유형에 대 한 설명이 대화 상자에 표시 됩니다. 이 경우 **Windows 사용자 인터페이스를 사용 하 여 응용 프로그램을 만드는 프로젝트**입니다.  
  
 **새 프로젝트** 대화 상자의 맨 아래에 추가 정보를 수집 하는 여러 컨트롤이 표시 됩니다. 표시 되는 컨트롤은 프로젝트 형식에 따라 달라 지지만 일반적으로 프로젝트 **이름** 텍스트 상자, **위치** 입력란 및 관련 **찾아보기** 단추, **솔루션 이름** 텍스트 상자 및 **솔루션용 디렉터리 만들기** 확인란을 포함 합니다.  
  
## <a name="populating-the-new-project-dialog-box"></a>새 프로젝트 대화 상자 채우기  
 **새 프로젝트** 대화 상자의 정보는 어디서 얻을 까 요? 여기에서 작업에는 두 가지 메커니즘이 사용 되지 않습니다. **새 프로젝트** 대화 상자는 두 메커니즘에서 가져온 정보를 결합 하 고 표시 합니다.  
  
 이전 (사용 되지 않음) 메서드는 시스템 레지스트리 항목과 .vsdir 파일을 사용 합니다. 이 메커니즘은 Visual Studio를 열 때 실행 됩니다. 최신 메서드는 .vstemplate 파일을 사용 합니다. 이 메커니즘은 예를 들어를 실행 하 여 Visual Studio를 초기화할 때 실행 됩니다.  
  
```  
devenv /setup  
```  
  
 또는  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>프로젝트 형식  
 **프로젝트 형식** 루트 노드 (예: **Visual c #** 및 **기타 언어**)의 위치와 이름은 시스템 레지스트리 항목에 의해 결정 됩니다. **데이터베이스** 및 **스마트 장치와**같은 자식 노드의 구성은 해당 .vstemplate 파일을 포함 하는 폴더의 계층 구조를 미러링합니다. 먼저 루트 노드를 살펴보겠습니다.  
  
#### <a name="project-type-root-nodes"></a>프로젝트 형식 루트 노드  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]가 초기화 되 면 \software\microsoft\visualstudio\14.0\newprojecttemplates\templatedirs HKEY_LOCAL_MACHINE 시스템 레지스트리 키의 하위 키를 순회 하 여 **프로젝트 형식** 트리의 루트 노드를 빌드하고 이름을 입력 합니다. 이 정보는 나중에 사용 하기 위해 캐시 됩니다. TemplateDirs \\ {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 키를 확인 합니다. 각 항목은 VSPackage GUID입니다. 하위 키의 이름 (/1)은 무시 되지만 해당 상태는 **프로젝트 형식** 루트 노드인지 여부를 나타냅니다. 루트 노드에는 **프로젝트 형식** 트리에서 해당 모양을 제어 하는 여러 하위 키가 있을 수 있습니다. 그 중 일부를 살펴보겠습니다.  
  
##### <a name="default"></a>(기본값)  
 루트 노드의 이름을로 하는 지역화 된 문자열의 리소스 ID입니다. 문자열 리소스는 VSPackage GUID에 의해 선택 된 위성 DLL에 있습니다.  
  
 이 예제에서 VSPackage GUID는  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 루트 노드 (/1)의 리소스 ID (기본값)는 #2345  
  
 근처의 패키지 키에서 GUID를 조회 하 고 SatelliteDll 하위 키를 검사 하는 경우 문자열 리소스가 포함 된 어셈블리의 경로를 찾을 수 있습니다.  
  
 \<Visual Studio installation path>\VC # \VCSPackages\1033\csprojui.dll  
  
 이를 확인 하려면 파일 탐색기를 열고 csprojui.dll을 Visual Studio 디렉터리로 끌어 옵니다. 문자열 테이블에는 리소스 #2345에 **Visual c #** 캡션이 있음을 보여 줍니다.  
  
##### <a name="sortpriority"></a>SortPriority  
 이는 **프로젝트 형식** 트리에서 루트 노드의 위치를 결정 합니다.  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 우선 순위 번호가 낮을수록 트리에서 위치가 높아집니다.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 이 하위 키가 있는 경우 루트 노드의 위치는 개발자 설정 대화 상자에 의해 제어 됩니다. 예를 들면 다음과 같습니다.  
  
 DeveloperActivity REG_SZ VC #  
  
 Visual Studio가 개발용으로 설정 된 경우 Visual c #이 루트 노드가 됨을 나타냅니다 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] . 그렇지 않으면 **다른 언어**의 자식 노드가 됩니다.  
  
##### <a name="folder"></a>폴더  
 이 하위 키가 있는 경우 루트 노드는 지정 된 폴더의 자식 노드가 됩니다. 키 아래에 사용할 수 있는 폴더 목록이 표시 됩니다.  
  
 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 예를 들어 데이터베이스 프로젝트 항목에는 PseudoFolders의 다른 프로젝트 형식 항목과 일치 하는 폴더 키가 있습니다. 따라서 **프로젝트 형식** 트리에서 **데이터베이스 프로젝트** 는 **다른 프로젝트 형식의**자식 노드가 됩니다.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>프로젝트 형식 자식 노드 및 vstdir 파일  
 **프로젝트 형식** 트리에서 자식 노드의 위치는 projecttemplates 폴더에 있는 폴더의 계층 구조를 따릅니다. 컴퓨터 템플릿 (**Visual Studio에 설치 된 템플릿**)의 경우 일반적인 위치는 FileFiles\Microsoft Visual studio 14.0 \ Common7\IDE\ProjectTemplates\이 고 사용자 템플릿 (**내 템플릿**)의 경우 일반적인 위치는 \My documents\visual studio 14.0 \ Templates\ProjectTemplates입니다 \\ . 이러한 두 위치에서 폴더 계층 구조가 병합 되어 **프로젝트 형식** 트리를 만듭니다.  
  
 Visual Studio에서 c # 개발자 설정을 사용 하는 경우 **프로젝트 형식** 트리는 다음과 같습니다.  
  
 ![프로젝트 형식](../../extensibility/internals/media/projecttypes.png "ProjectTypes"):  
  
 해당 ProjectTemplates 폴더는 다음과 같습니다.  
  
 ![프로젝트 템플릿](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 **새 프로젝트** 대화 상자가 열리면 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projecttemplates 폴더를 탐색 하 고 **프로젝트 형식** 트리에서 다음과 같이 변경 하 여 해당 구조를 다시 만듭니다.  
  
- **프로젝트 형식** 트리의 루트 노드는 응용 프로그램 템플릿에 의해 결정 됩니다.  
  
- 노드 이름은 지역화할 수 있으며 특수 문자를 포함할 수 있습니다.  
  
- 정렬 순서를 변경할 수 있습니다.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>프로젝트 형식에 대 한 루트 노드 찾기  
 Visual Studio는 ProjectTemplates 폴더를 트래버스하 면 모든 .zip 파일을 열고 .vstemplate 파일을 추출 합니다. .Vstemplate 파일은 XML을 사용 하 여 응용 프로그램 템플릿을 설명 합니다. 자세한 내용은 [새 프로젝트 생성: 내부에서 2 부를](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)참조 하세요.  
  
 \<ProjectType>태그는 응용 프로그램에 대 한 프로젝트 형식을 결정 합니다. 예를 들어 \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip 파일에는이 태그가 있는 EmptyProject 파일이 포함 되어 있습니다.  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 \<ProjectType>ProjectTemplates 폴더의 하위 폴더가 아닌 태그는 **프로젝트 형식** 트리에서 응용 프로그램의 루트 노드를 결정 합니다. 이 예제에서 Windows CE 응용 프로그램은 **visual c #** 루트 노드 아래에 표시 되 고 WindowsCE 폴더를 microsoft.visualbasic Windows CE 폴더로 이동 하는 경우에도 **visual c #** 루트 노드 아래에 응용 프로그램이 계속 표시 됩니다.  
  
##### <a name="localizing-the-node-name"></a>노드 이름 지역화  
 Visual Studio는 ProjectTemplates 폴더를 트래버스하 면 찾은 vstdir 파일을 검사 합니다. Vstdir 파일은 **새 프로젝트** 대화 상자에서 프로젝트 형식의 모양을 제어 하는 XML 파일입니다. Vstdir 파일에서 태그를 사용 하 여 \<LocalizedName> **프로젝트 형식** 노드의 이름을로 입력 합니다.  
  
 예를 들어 \CSharp\Database\TemplateIndex.vstdir 파일에는 다음 태그가 포함 됩니다.  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 이는 루트 노드의 이름을 지정 하는 지역화 된 문자열의 위성 DLL 및 리소스 ID (이 경우에는 **데이터베이스**)를 결정 합니다. 지역화 된 이름에는 폴더 이름에 사용할 수 없는 특수 문자 (예: **.net**)가 포함 될 수 있습니다.  
  
 태그가 없는 경우 \<LocalizedName> 프로젝트 형식은 폴더 자체 ( **SmartPhone2003**)로 지정 됩니다.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>프로젝트 형식에 대 한 정렬 순서 찾기  
 프로젝트 형식의 정렬 순서를 결정 하기 위해 vstdir 파일은 태그를 사용 합니다. \<SortOrder>  
  
 예를 들어 \CSharp\Windows\Windows.vstdir 파일에는 다음 태그가 포함 됩니다.  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 \CSharp\Database\TemplateIndex.vstdir 파일에는 더 큰 값이 포함 된 태그가 있습니다.  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 태그의 숫자가 낮을수록 \<SortOrder> 트리에서 위치가 높을수록 **Windows** 노드가 **프로젝트 형식** 트리의 **데이터베이스** 노드 보다 높게 표시 되는 것입니다.  
  
 \<SortOrder>프로젝트 형식에 대해 태그가 지정 되지 않은 경우에는 사양을 포함 하는 프로젝트 형식에 따라 사전순으로 표시 됩니다 \<SortOrder> .  
  
 내 문서 (**내 템플릿**) 폴더에 vstdir 파일이 없습니다. 사용자 응용 프로그램 프로젝트 형식 이름은 지역화 되지 않으며 사전순으로 표시 됩니다.  
  
#### <a name="a-quick-review"></a>빠른 검토  
 **새 프로젝트** 대화 상자를 수정 하 고 새 사용자 프로젝트 템플릿을 만들어 보겠습니다.  
  
1. Files\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates\CSharp 폴더에 MyProjectNode 하위 폴더를 추가 합니다.  
  
2. 모든 텍스트 편집기를 사용 하 여 MyProjectNode 폴더에 vstdir 파일을 만듭니다.  
  
3. 다음 줄을 vstdir 파일에 추가 합니다.  
  
   ```  
   <TemplateDir Version="1.0.0">  
       <SortOrder>6</SortOrder>  
   </TemplateDir>  
   ```  
  
4. Vstdir 파일을 저장 하 고 닫습니다.  
  
5. 모든 텍스트 편집기를 사용 하 여 MyProjectNode 폴더에 MyProject 파일을 만듭니다.  
  
6. .Vstemplate 파일에 다음 줄을 추가 합니다.  
  
   ```  
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
       <TemplateData>  
           <ProjectType>CSharp</ProjectType>  
       </TemplateData>  
   </VSTemplate>  
   ```  
  
7. .Vstemplate 파일을 저장 하 고 편집기를 닫습니다.  
  
8. .Vstemplate 파일을 새 압축 된 MyProjectNode\MyProject.zip 폴더로 보냅니다.  
  
9. Visual Studio 명령 창에서 다음을 입력 합니다.  
  
    ```  
    devenv /installvstemplates  
    ```  
  
   Visual Studio를 엽니다.  
  
10. **새 프로젝트** 대화 상자를 열고 **Visual c #** 프로젝트 노드를 확장 합니다.  
  
    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
    **Myprojectnode** 는 Windows 노드 바로 아래에 Visual c #의 자식 노드로 표시 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [새 프로젝트 생성: 내부 살펴보기, 2부](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
