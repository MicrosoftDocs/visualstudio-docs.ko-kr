---
title: '새로운 프로젝트 생성: 후드 아래, 1부 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aca35e85e57a07a2b411a23d81b99cff9983b9c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707063"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>새 프로젝트 생성: 내부 살펴보기, 1부
나만의 프로젝트 유형을 만드는 방법에 대해 생각해 본 적이 있습니까? 새 프로젝트를 만들 때 실제로 어떤 일이 일어나는지 궁금하십니까? 의 후드 아래 들여다 정말 무슨 일이 일어나고 있는지 볼 수 있습니다.

 Visual Studio에서 조정하는 몇 가지 작업이 있습니다.

- 사용 가능한 모든 프로젝트 유형의 트리를 표시합니다.

- 각 프로젝트 유형에 대한 응용 프로그램 템플릿 목록을 표시하고 하나를 선택할 수 있습니다.

- 프로젝트 이름 및 경로와 같은 응용 프로그램에 대한 프로젝트 정보를 수집합니다.

- 이 정보를 프로젝트 팩터리로 전달합니다.

- 현재 솔루션에서 프로젝트 항목 및 폴더를 생성합니다.

## <a name="the-new-project-dialog-box"></a>새 프로젝트 대화 상자
 새 프로젝트에 대한 프로젝트 유형을 선택하면 모든 것이 시작됩니다. **파일** 메뉴에서 **새 프로젝트를** 클릭하여 시작해 보겠습니다. **새 프로젝트** 대화 상자가 나타납니다.

 ![새 프로젝트 대화 상자](../../extensibility/internals/media/newproject.gif "NewProject")

 좀 더 자세히 살펴보겠습니다. **프로젝트 유형** 트리에는 만들 수 있는 다양한 프로젝트 유형이 나열됩니다. **Visual C# Windows와**같은 프로젝트 유형을 선택하면 시작할 응용 프로그램 템플릿 목록이 표시됩니다. **Visual Studio에 설치된 템플릿은** Visual Studio에서 설치하며 컴퓨터의 모든 사용자가 사용할 수 있습니다. 만들거나 수집하는 새 템플릿은 내 **템플릿에** 추가할 수 있으며 사용자만 사용할 수 있습니다.

 **Windows 응용 프로그램과**같은 템플릿을 선택하면 대화 상자에 응용 프로그램 유형에 대한 설명이 나타납니다. 이 경우 **Windows 사용자 인터페이스를 사용하여 응용 프로그램을 만드는 프로젝트입니다.**

 **새 프로젝트** 대화 상자 의 하단에 더 많은 정보를 수집 하는 몇 가지 컨트롤을 볼 수 있습니다. 표시되는 컨트롤은 프로젝트 유형에 따라 다르지만 일반적으로 프로젝트 **이름** 텍스트 상자, **위치** 텍스트 상자 및 관련 **찾아보기** 단추, **솔루션 이름** 텍스트 상자 및 관련 **솔루션 디렉터리 만들기** 확인란이 포함됩니다.

## <a name="populating-the-new-project-dialog-box"></a>새 프로젝트 대화 상자 채우기
 **새 프로젝트** 대화 상자는 어디에서 정보를 얻습니까? 여기에는 두 가지 메커니즘이 있는데, 그 중 하나는 더 이상 사용되지 않습니다. **새 프로젝트** 대화 상자는 두 메커니즘에서 얻은 정보를 결합하고 표시합니다.

 이전(더 이상 사용되지 않습니다) 메서드는 시스템 레지스트리 항목 및 .vsdir 파일을 사용합니다. 이 메커니즘은 Visual Studio를 열었을 때 실행됩니다. 최신 메서드는 .vstemplate 파일을 사용합니다. 이 메커니즘은 Visual Studio를 초기화할 때 실행됩니다.

```
devenv /setup
```

 또는

```
devenv /installvstemplates
```

### <a name="project-types"></a>프로젝트 형식
 **프로젝트 유형** 루트 노드(예: **Visual C#** 및 **기타 언어)의**위치와 이름은 시스템 레지스트리 항목에 의해 결정됩니다. **데이터베이스** 및 **스마트 장치와**같은 자식 노드의 조직은 해당 .vstemplate 파일을 포함하는 폴더의 계층 구조를 미러합니다. 먼저 루트 노드를 살펴보겠습니다.

#### <a name="project-type-root-nodes"></a>프로젝트 유형 루트 노드
 초기화되면 시스템 레지스트리 키 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs를 통과하여 프로젝트 유형 트리의 루트 노드를 빌드하고 이름을 지정합니다. **Project types** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 이 정보는 나중에 사용할 수 위해 캐시됩니다. 템플릿디르\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}\\/1 키를 살펴보십시오. 각 항목은 VS패키지 GUID입니다. 하위 키(/1)의 이름은 무시되지만 현재 상태는 **프로젝트 유형** 루트 노드임을 나타냅니다. 루트 노드에는 **프로젝트 유형** 트리에서 모양을 제어하는 여러 하위 키가 있을 수 있습니다. 그 중 일부를 살펴 보겠습니다.

##### <a name="default"></a>(기본값)
 루트 노드의 이름을 지정하는 지역화된 문자열의 리소스 ID입니다. 문자열 리소스는 VSPackage GUID에서 선택한 위성 DLL에 있습니다.

 이 예제에서 VSPackage GUID는

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 루트 노드(/1)의 리소스 ID(기본값)가 #2345

 근처 패키지 키에서 GUID를 조회하고 SatelliteDll 하위 키를 검사하면 문자열 리소스가 포함된 어셈블리 경로를 찾을 수 있습니다.

 \<비주얼 스튜디오 설치 경로>\VC#\VCSPackages\1033\csprojui.dll

 이를 확인하려면 파일 탐색기를 열고 csprojui.dll을 시각적 스튜디오 디렉토리로 드래그합니다. 문자열 테이블에는 리소스 #2345 **Visual C#** 캡션이 있음을 보여 주며 있습니다.

##### <a name="sortpriority"></a>정렬 우선 순위
 이렇게 하면 **프로젝트 유형** 트리에서 루트 노드의 위치가 결정됩니다.

 정렬 우선 순위 REG_DWORD 0x00000014 (20)

 우선 순위 수가 낮을수록 트리의 위치가 높아집니다.

##### <a name="developeractivity"></a>개발자 활동
 이 하위 키가 있으면 루트 노드의 위치는 개발자 설정 대화 상자에 의해 제어됩니다. 예를 들면 다음과 같습니다.

 개발자 활동 REG_SZ VC #

 은 Visual Studio가 개발용으로 설정된 경우 Visual [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] C#이 루트 노드가 된다는 것을 나타냅니다. 그렇지 않으면 **다른 언어의**자식 노드가 됩니다.

##### <a name="folder"></a>폴더
 이 하위 키가 있으면 루트 노드가 지정된 폴더의 자식 노드가 됩니다. 가능한 폴더 목록이 키 아래에 나타납니다.

 HKEY_LOCAL_MACHINE\SOFTWARE\마이크로소프트\비주얼 스튜디오\11.0\NewProjectTemplates\PseudoFolders

 예를 들어 데이터베이스 프로젝트 항목에는 PseudoFolders의 다른 프로젝트 유형 항목과 일치하는 폴더 키가 있습니다. 따라서 프로젝트 **유형** 트리에서 **데이터베이스 프로젝트는** 다른 프로젝트 **형식의**자식 노드가 됩니다.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>프로젝트 유형 자식 노드 및 .vstdir 파일
 **프로젝트 유형** 트리에서 자식 노드의 위치는 ProjectTemplates 폴더의 폴더 계층 구조를 따릅니다. 컴퓨터 템플릿 **(Visual Studio 설치 템플릿)의**경우 일반적인 위치는 \Program 파일\Microsoft 비주얼 스튜디오 14.0\Common7\IDE\ProjectTemplates\와 사용자 템플릿(내**템플릿)의**경우 일반적인 위치는 \My\\Documents\Visual Studio 14.0\Templates\ProjectTemplates입니다. 이 두 위치의 폴더 계층구조가 병합되어 **프로젝트 유형** 트리를 만듭니다.

 C# 개발자 설정이 있는 Visual Studio의 경우 **프로젝트 유형** 트리는 다음과 같습니다.

 ![프로젝트 유형](../../extensibility/internals/media/projecttypes.png "프로젝트 유형")

 해당 ProjectTemplates 폴더는 다음과 같습니다.

 ![프로젝트 템플릿](../../extensibility/internals/media/projecttemplates.png "프로젝트 템플릿")

 새 **프로젝트** 대화 상자가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 열리면 ProjectTemplates 폴더를 통과하고 몇 가지 변경 사항을 통해 **프로젝트 유형** 트리에서 해당 구조를 다시 만듭니다.

- **프로젝트 유형** 트리의 루트 노드는 응용 프로그램 템플릿에 의해 결정됩니다.

- 노드 이름은 지역화할 수 있으며 특수 문자를 포함할 수 있습니다.

- 정렬 순서를 변경할 수 있습니다.

##### <a name="finding-the-root-node-for-a-project-type"></a>프로젝트 유형에 대한 루트 노드 찾기
 Visual Studio에서 ProjectTemplates 폴더를 통과하면 모든 .zip 파일을 열고 .vstemplate 파일을 추출합니다. .vstemplate 파일은 XML을 사용하여 응용 프로그램 템플릿을 설명합니다. 자세한 내용은 [새 프로젝트 생성: 아래 두번째, 파트 2를](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)참조하십시오.

 \<ProjectType> 태그는 응용 프로그램의 프로젝트 유형을 결정합니다. 예를 들어, \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip 파일에는 이 태그가 있는 EmptyProject.vstemplate 파일이 포함되어 있습니다.

```
<ProjectType>CSharp</ProjectType>
```

 ProjectType> 태그는 ProjectTemplates 폴더의 하위 폴더가 아니라 프로젝트 유형 트리에서 응용 프로그램의 루트 노드를 결정합니다. **Project types** \< 이 예제에서는 Windows CE 응용 프로그램이 **Visual C#** 루트 노드 아래에 표시되며 WindowsCE 폴더를 VisualBasic 폴더로 이동하더라도 Windows CE 응용 프로그램은 여전히 **Visual C#** 루트 노드 아래에 나타납니다.

##### <a name="localizing-the-node-name"></a>노드 이름 지역화
 Visual Studio에서 ProjectTemplates 폴더를 통과하면 찾은 .vstdir 파일을 검사합니다. .vstdir 파일은 **새 프로젝트** 대화 상자에서 프로젝트 유형의 모양을 제어하는 XML 파일입니다. .vstdir 파일에서 \<LocalizedName> 태그를 사용하여 **프로젝트 유형** 노드의 이름을 지정합니다.

 예를 들어\CSharp\Database\TemplateIndex.vstdir 파일에는 다음 태그가 포함되어 있습니다.

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 이렇게 하면 루트 노드의 이름을 지정하는 지역화된 문자열의 위성 DLL 및 리소스 ID(이 경우 **데이터베이스.** 지역화된 이름에는 .NET 과 같은 폴더 이름에 사용할 수 없는 특수 문자가 포함될 수 **있습니다.**

 지역화된Name> 태그가 없는 \<경우 프로젝트 유형은 폴더 자체인 **SmartPhone2003에**의해 이름이 지정됩니다.

##### <a name="finding-the-sort-order-for-a-project-type"></a>프로젝트 유형에 대한 정렬 순서 찾기
 프로젝트 형식의 정렬 순서를 확인하려면 .vstdir \<파일은 SortOrder> 태그를 사용합니다.

 예를 들어\CSharp\Windows\Windows.vstdir 파일에는 이 태그가 포함되어 있습니다.

```
<SortOrder>5</SortOrder>
```

 \CSharp\Database\TemplateIndex.vstdir 파일에는 더 큰 값을 가진 태그가 있습니다.

```
<SortOrder>5000</SortOrder>
```

 \<SortOrder> 태그의 숫자가 낮을수록 트리의 위치가 높아지므로 **Windows** 노드가 프로젝트 **유형** 트리의 **데이터베이스** 노드보다 높게 나타납니다.

 프로젝트 \<유형에 대해 SortOrder> 태그가 지정되지 않은 경우 SortOrder> \<사양을 포함하는 모든 프로젝트 유형에 따라 사전순으로 표시됩니다.

 내**문서(내 템플릿)** 폴더에는 .vstdir 파일이 없습니다. 사용자 응용 프로그램 프로젝트 유형 이름은 지역화되지 않으며 사전순으로 표시됩니다.

#### <a name="a-quick-review"></a>빠른 검토
 **새 프로젝트** 대화 상자를 수정하고 새 사용자 프로젝트 템플릿을 만들어 보겠습니다.

1. \프로그램 파일\마이크로소프트 비주얼 스튜디오 14.0\Common7\IDE\프로젝트템플릿\C샤프 폴더에 MyProjectNode 하위 폴더를 추가합니다.

2. 텍스트 편집기에서 MyProject.vstdir 파일을 MyProjectNode 폴더에 만듭니다.

3. .vstdir 파일에 이러한 줄을 추가합니다.

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. .vstdir 파일을 저장하고 닫습니다.

5. 텍스트 편집기에서 MyProject.vs 템플릿 파일을 MyProjectNode 폴더에 만듭니다.

6. 이러한 줄을 .vstemplate 파일에 추가합니다.

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. .vstemplate 파일을 저장하고 편집기닫습니다.

8. .vs템플릿 파일을 압축된 새 MyProjectNode\MyProject.zip 폴더로 보냅니다.

9. Visual Studio 명령 창에서 다음을 입력합니다.

    ```
    devenv /installvstemplates
    ```

   Visual Studio를 엽니다.

10. 새 **프로젝트** 대화 상자를 열고 **Visual C#** 프로젝트 노드를 확장합니다.

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode는** Windows 노드 바로 아래에 Visual C#의 자식 노드로 나타납니다.

## <a name="see-also"></a>참조
- [새 프로젝트 생성: 내부 살펴보기, 2부](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
