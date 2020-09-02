---
title: '방법: 만들기 Vsct 파일 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158349"
---
# <a name="how-to-create-a-vsct-file"></a>방법: .Vsct 파일 만들기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

XML 기반 Visual Studio 명령 테이블 구성 (vsct) 파일을 만드는 방법에는 여러 가지가 있습니다.  
  
- 패키지 템플릿에서 새 VSPackage을 만들 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- XML 기반 명령 테이블 구성 컴파일러 Vsct.exe를 사용 하 여 기존. c tc 파일에서 파일을 생성할 수 있습니다.  
  
- Vsct.exe를 사용 하 여 기존. cto 파일에서 .cvsct 파일을 생성할 수 있습니다.  
  
- 새. vsct 파일을 수동으로 만들 수 있습니다.  
  
  이 항목에서는 새. vsct 파일을 수동으로 만드는 방법을 설명 합니다.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>새 vsct 파일을 수동으로 만들려면  
  
1. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 시작합니다.  
  
2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **파일**을 클릭합니다.  
  
3. **템플릿** 창에서 **XML 파일** 을 클릭 한 다음 **열기**를 클릭 합니다.  
  
4. **보기** 메뉴에서 **속성 창** 을 클릭 하 여 XML 파일의 속성을 표시 합니다.  
  
5. **속성** 창의 스키마 속성에서 찾아보기 (...) 단추를 클릭 합니다.  
  
6. XSD 스키마 목록에서 vsct .xsd 스키마를 선택 합니다. 목록에 없으면 **추가** 를 클릭 하 고 로컬 드라이브에서 파일을 찾습니다. 작업이 완료 되 면 **확인을** 클릭 합니다.  
  
7. XML 파일에서를 입력 한 `<CommandTable` 다음 tab 키를 누릅니다. 을 입력 하 여 태그를 닫습니다 `>` .  
  
     이렇게 하면 기본 vsct 파일이 생성 됩니다.  
  
8. 추가 하려는 XML 파일의 요소를 [Vsct 스키마](../../extensibility/vsct-xml-schema-reference.md)에 따라 입력 합니다. 자세한 내용은 제작을 참조 하세요 [. Vsct 파일](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
## <a name="compiling-the-code"></a>코드 컴파일  
 프로젝트에. vsct 파일을 추가 하면 컴파일이 되지 않습니다. 빌드 프로세스에 통합 해야 합니다.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>프로젝트 컴파일에 vsct 파일을 추가 하려면  
  
1. 편집기에서 프로젝트 파일을 엽니다. 프로젝트가 로드 되 면 먼저 언로드해야 합니다.  
  
2. 다음 예제와 같이 VSCTCompile 요소를 포함 하는 [ItemGroup 요소](../../msbuild/itemgroup-element-msbuild.md) 를 추가 합니다.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     Context.resourcename 요소는 항상로 설정 해야 합니다 `Menus.ctmenu` .  
  
3. 프로젝트에 .resx 파일이 포함 되어 있는 경우 다음 예제와 같이 MergeWithCTO 요소를 포함 하는 EmbeddedResource 요소를 추가 합니다.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     이 태그는 포함 된 리소스를 포함 하는 ItemGroup 요소 내에 있어야 합니다.  
  
4. 편집기에서 일반적으로 이름이 *projectname*Package.cs 또는 *projectname*package .vb 인 패키지 파일을 엽니다.  
  
5. 다음 예제와 같이 package 클래스에 ProvideMenuResource 특성을 추가 합니다.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     첫 번째 매개 변수 값은 프로젝트 파일에 정의 된 Context.resourcename 특성의 값과 일치 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [만들. Vsct 파일](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio 명령 테이블 (. Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [방법: 만들기 기존에서 vsct 파일 Ctc 파일](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [방법: 만들기 기존에서 vsct 파일 Cto 파일](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
