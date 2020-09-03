---
title: '방법: 만들기 Vsct 파일 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a571098deeeca0e8262d855c24d0bf1ce66be08e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905531"
---
# <a name="how-to-create-a-vsct-file"></a>방법: vsct 파일 만들기

XML 기반 Visual Studio 명령 테이블 구성 (*vsct*) 파일을 만드는 방법에는 여러 가지가 있습니다.

- 패키지 템플릿에서 새 VSPackage을 만들 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- XML 기반 명령 테이블 구성 컴파일러 *Vsct.exe*를 사용 하 여 기존 *. c tc* 파일에서 파일을 생성할 수 있습니다.

- *Vsct.exe* 를 사용 하 여 기존 *. cto* 파일에서 *.cvsct* 파일을 생성할 수 있습니다.

- 새 *. vsct* 파일을 수동으로 만들 수 있습니다.

  이 문서에서는 새 *. vsct* 파일을 수동으로 만드는 방법을 설명 합니다.

### <a name="to-manually-create-a-new-vsct-file"></a>새 vsct 파일을 수동으로 만들려면

1. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **파일**을 클릭합니다.

3. **템플릿** 창에서 **XML 파일** 을 클릭 한 다음 **열기**를 클릭 합니다.

4. **보기** 메뉴에서 **속성** 을 클릭 하 여 XML 파일의 속성을 표시 합니다.

5. **속성** 창에서 **스키마** 속성의 **찾아보기** 단추를 클릭 합니다.

6. XSD 스키마 목록에서 *vsct .xsd* 스키마를 선택 합니다. 목록에 없으면 **추가** 를 클릭 하 고 로컬 드라이브에서 파일을 찾습니다. 작업이 완료 되 면 **확인을** 클릭 합니다.

7. XML 파일에 *<CommandTable* 을 입력 한 다음 **tab**키를 누릅니다. 을 입력 하 여 태그를 닫습니다 *>* .

    이 작업을 수행 하면 기본 *vsct* 파일이 만들어집니다.

8. 추가 하려는 XML 파일의 요소를 [Vsct xml 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)에 따라 입력 합니다. 자세한 내용은 [Author. vsct 파일](../../extensibility/internals/authoring-dot-vsct-files.md)을 참조 하세요.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>방법: 기존 .ctc 파일에서 .cvsct 파일 만들기

기존 명령 테이블인 *ctc* 원본 파일에서 XML 기반 *.cvsct* 파일을 만들 수 있습니다. 이렇게 하면 새 XML 기반 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 명령 테이블(VSCT) 컴파일러 형식을 이용할 수 있습니다.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>.ctc 파일에서 .vsct 파일을 만들려면

1. Perl 언어의 복사본을 가져옵니다.

2. 일반적으로 * \<Visual Studio SDK installation path> \VisualStudioIntegration\Tools\bin* 폴더에 있는 Perl 스크립트 *ConvertCTCToVSCT.pl*복사본을 가져옵니다.

3. 변환 하려는 *.ctc* 소스 파일의 복사본을 가져옵니다.

4. 동일한 디렉터리에 파일을 배치합니다.

5. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]명령 프롬프트 창에서 디렉터리로 이동 합니다.

6. 형식

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    여기서 *pkgcmd.ctc* 은 *.ctc* 파일의 이름이 고, *pkgcmd.ctc* 는 만들려는 *.vsct* 파일의 이름입니다.

    이 작업을 수행 하면 새 *. vsct* XML 명령 테이블 원본 파일이 만들어집니다. 다른 모든 *vsct* 파일과 마찬가지로 vsct 컴파일러 *Vsct.exe*를 사용 하 여 파일을 컴파일할 수 있습니다.

   > [!NOTE]
   > XML 주석을 다시 포맷 하 여 *vsct* 파일의 가독성을 향상 시킬 수 있습니다.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>방법: 기존. cto 파일로 .vsct 파일 만들기

기존 binary *. cto* 파일에서 XML 기반 *.cvsct* 파일을 만들 수 있습니다. 이렇게 하면 새 명령 테이블 컴파일러 형식을 이용할 수 있습니다. 이 프로세스는 *.* c a d 파일을 *.ctc* 파일에서 컴파일한 경우에도 작동 합니다. *.Cvsct* 파일을 편집 하 고 다른. cto file로 컴파일할 수 있습니다.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>.cto 파일에서 .vsct 파일을 만들려면

1. *.Cto* 파일 및 해당 *.ctsym* 파일의 복사본을 가져옵니다.

2. *vsct.exe* 컴파일러와 동일한 디렉터리에 파일을 저장 합니다.

3. Visual Studio 명령 프롬프트에서 *. cto* 및 *. .ctsym* 파일이 포함 된 디렉터리로 이동 합니다.

4. 형식

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     여기서 \<ctofilename\> 는 *.cto* 파일의 이름이 고, \<vsctfilename\> 은 만들려는 *.cvsct* 파일의 이름이 고,은 \<symfilename\> *.ctsym* 파일의 이름입니다.

     이 프로세스는 새 *. vsct* XML 명령 테이블 컴파일러 파일을 만듭니다. 다른 모든 *vsct* 파일과 마찬가지로 vsct 컴파일러 *vsct.exe*사용 하 여 파일을 편집 하 고 컴파일할 수 있습니다.

## <a name="compile-the-code"></a>코드 컴파일
 프로젝트에 *. vsct* 파일을 추가 하면 컴파일이 되지 않습니다. 빌드 프로세스에 통합 해야 합니다.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>프로젝트 컴파일에 vsct 파일을 추가 하려면

1. 편집기에서 프로젝트 파일을 엽니다. 프로젝트가 로드 되 면 먼저 언로드해야 합니다.

2. 다음 예제와 같이 요소를 포함 하는 [ItemGroup 요소](../../msbuild/itemgroup-element-msbuild.md) `VSCTCompile` 를 추가 합니다.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     `ResourceName`요소는 항상로 설정 해야 합니다 `Menus.ctmenu` .

3. 프로젝트에 *.resx* 파일이 포함 되어 있는 경우 `EmbeddedResource` 다음 예제와 같이 요소를 포함 하는 요소를 추가 합니다 `MergeWithCTO` .

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     이 태그 `ItemGroup` 는 포함 된 리소스를 포함 하는 요소 내에 있어야 합니다.

4. 편집기에서 일반적으로 이름이 * \<ProjectName\> Package.cs* 또는 * \<ProjectName\> 패키지인*패키지 파일을 엽니다.

5. `ProvideMenuResource`다음 예제와 같이 package 클래스에 특성을 추가 합니다.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     첫 번째 매개 변수 값은 `ResourceName` 프로젝트 파일에 정의 된 특성의 값과 일치 해야 합니다.

## <a name="see-also"></a>추가 정보
- [. Vsct 파일 작성](../../extensibility/internals/authoring-dot-vsct-files.md)
- [Visual Studio 명령 테이블 (.vvsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
