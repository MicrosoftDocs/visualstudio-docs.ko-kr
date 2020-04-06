---
title: '방법: 을 만듭니다. Vsct 파일 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5a5f53ec87c9447af232e9d0528108ddbaea01a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708114"
---
# <a name="how-to-create-a-vsct-file"></a>방법: .vsct 파일 만들기

XML 기반 Visual Studio 명령 테이블*구성(.vsct)* 파일을 만드는 방법에는 여러 가지가 있습니다.

- 패키지 템플릿에서 새 VSPackage를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 만들 수 있습니다.

- XML 기반 명령 테이블 컴파일러 인 *Vsct.exe를*사용하여 기존 *.ctc* 파일에서 파일을 생성할 수 있습니다.

- *Vsct.exe를* 사용하여 기존 *.cto* 파일에서 *.vsct* 파일을 생성할 수 있습니다.

- 새 *.vsct* 파일을 수동으로 만들 수 있습니다.

  이 문서에서는 새 *.vsct* 파일을 수동으로 만드는 방법을 설명합니다.

### <a name="to-manually-create-a-new-vsct-file"></a>수동으로 새 .vsct 파일을 만들려면

1. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **파일**을 클릭합니다.

3. **템플릿** 창에서 **XML 파일을** 클릭한 다음 **을 클릭합니다.**

4. **보기** 메뉴에서 **속성을** 클릭하여 XML 파일의 속성을 표시합니다.

5. **속성** 창에서 **스키마** 속성의 **찾아보기** 단추를 클릭합니다.

6. XSD 스키마 목록에서 *vsct.xsd 스키마를* 선택합니다. 목록에 없는 경우 **추가를** 클릭한 다음 로컬 드라이브에서 파일을 찾습니다. 작업이 완료되면 **확인을** 클릭합니다.

7. XML 파일에서 *명령<* 입력한 다음 **탭 을**누릅니다. 을 입력하여 *>* 태그를 닫습니다.

    이 작업은 기본 *.vsct* 파일을 만듭니다.

8. [VSCT XML 스키마 참조에](../../extensibility/vsct-xml-schema-reference.md)따라 추가할 XML 파일의 요소를 채웁니다. 자세한 내용은 [.vsct 파일 작성을 참조하십시오.](../../extensibility/internals/authoring-dot-vsct-files.md)

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>방법: 기존 .ctc 파일에서 .vsct 파일 만들기

기존 명령 테이블 *.ctc* 소스 파일에서 XML 기반 *.vsct* 파일을 만들 수 있습니다. 이렇게 하면 새 XML 기반 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 명령 테이블(VSCT) 컴파일러 형식을 이용할 수 있습니다.

### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>.ctc 파일에서 .vsct 파일을 만들려면

1. Perl 언어의 복사본을 가져옵니다.

2. 일반적으로 * \<Visual Studio SDK 설치 경로>\VisualStudioIntegration\Tools\bin* 폴더에 있는 Perl 스크립트 *ConvertCTCToVSCT.pl*복사본을 가져옵니다.

3. 변환할 *.ctc* 소스 파일의 복사본을 가져옵니다.

4. 동일한 디렉터리에 파일을 배치합니다.

5. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 명령 프롬프트 창에서 디렉터리로 이동합니다.

6. 형식

   ```
   perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct
   ```

    *여기서 PkgCmd.ctc는* *.ctc* 파일의 이름이며 *PkgCmd.vsct는* 만들려는 *.vsct* 파일의 이름입니다.

    이 작업은 새 *.vsct* XML 명령 테이블 소스 파일을 만듭니다. VsCT 컴파일러인 *Vsct.exe를*사용하여 다른 *.vsct* 파일과 마찬가지로 파일을 컴파일할 수 있습니다.

   > [!NOTE]
   > XML 주석을 다시 포메이팅하여 *.vsct* 파일의 가독성을 향상시킬 수 있습니다.

<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>방법: 기존 .cto 파일에서 .vsct 파일 만들기

기존 이진 *.cto* 파일에서 XML 기반 *.vsct* 파일을 만들 수 있습니다. 이렇게 하면 새 명령 테이블 컴파일러 형식을 이용할 수 있습니다. 이 프로세스는 *.cto 파일이* *.ctc* 파일에서 컴파일된 경우에도 작동합니다. *.vsct* 파일을 편집하고 다른 .cto 파일로 컴파일할 수 있습니다.

### <a name="to-create-a-vsct-file-from-a-cto-file"></a>.cto 파일에서 .vsct 파일을 만들려면

1. *.cto* 파일및 해당 *.ctsym* 파일의 복사본을 가져옵니다.

2. *vsct.exe* 컴파일러와 동일한 디렉토리에 파일을 배치합니다.

3. Visual Studio 명령 프롬프트에서 *.cto* 및 *.ctsym* 파일이 포함된 디렉토리로 이동합니다.

4. 형식

    ```
    vsct.exe <ctofilename>.cto <vsctfilename>.vsct -S<symfilename>.ctsym
    ```

     \<ctofilename이\> *.cto* 파일의 이름인 \<경우 vsctfilename은\> 만들려는 *.vsct* 파일의 \<이름이며\> 심파일 이름은 *.ctsym* 파일의 이름입니다.

     이 프로세스는 새 *.vsct* XML 명령 테이블 컴파일러 파일을 만듭니다. 다른 *.vsct* 파일과 마찬가지로 *vsct.exe*, vsct 컴파일러로 파일을 편집하고 컴파일할 수 있습니다.

## <a name="compile-the-code"></a>코드 컴파일
 *프로젝트에 .vsct* 파일을 추가하기만 해도 컴파일되지는 않습니다. 빌드 프로세스에 통합해야 합니다.

### <a name="to-add-a-vsct-file-to-project-compilation"></a>프로젝트 컴파일에 .vsct 파일을 추가하려면

1. 편집기에서 프로젝트 파일을 엽니다. 프로젝트가 로드된 경우 먼저 프로젝트를 언로드해야 합니다.

2. 다음 예제와 같이 `VSCTCompile` 요소가 포함된 [ItemGroup 요소를](../../msbuild/itemgroup-element-msbuild.md) 추가합니다.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="TopLevelMenu.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>

    ```

     `ResourceName` 요소는 항상 로 `Menus.ctmenu`설정되어야 합니다.

3. 프로젝트에 *.resx* 파일이 포함된 경우 `EmbeddedResource` 다음 예제와 같이 `MergeWithCTO` 요소가 포함된 요소를 추가합니다.

    ```xml
    <EmbeddedResource Include="VSPackage.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <ManifestResourceName>VSPackage</ManifestResourceName>
    </EmbeddedResource>

    ```

     이 태그는 포함된 `ItemGroup` 리소스를 포함하는 요소 내부로 이동해야 합니다.

4. 편집기에서 일반적으로 * \<ProjectName\>Package.cs* 또는 * \<\>ProjectName Package.vb라는*패키지 파일을 엽니다.

5. 다음 `ProvideMenuResource` 예제와 같이 패키지 클래스에 특성을 추가합니다.

    ```csharp
    [ProvideMenuResource("Menus.ctmenu", 1)]
    ```

     첫 번째 매개 변수 값은 `ResourceName` 프로젝트 파일에 정의한 특성값과 일치해야 합니다.

## <a name="see-also"></a>참조
- [작성자 .vsct 파일](../../extensibility/internals/authoring-dot-vsct-files.md)
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)
