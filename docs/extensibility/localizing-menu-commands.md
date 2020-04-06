---
title: 메뉴 지역화 명령 | 마이크로 소프트 문서
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- localize
- localization
- vsct
- menu commands
- localize visual studio
- localize vsct
ms.assetid: b04ee0f6-82ea-47e6-853a-72382267d6da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d363b495eb84dc3bfeabd7bf7c5d05fabcbc4d36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702954"
---
# <a name="localize-menu-commands"></a>메뉴 명령 지역화

VSPackage에 대한 지역화된 *.vsct* 파일 및 지역화된 *.resx* 파일을 만든 다음 변경 내용을 통합하도록 프로젝트 파일을 업데이트하여 메뉴 및 도구 모음 명령에 대한 지역화된 텍스트를 제공할 수 있습니다.

설치 환경을 지역화하는 방법에 대한 자세한 내용은 [VSIX 패키지 지역화를](../extensibility/localizing-vsix-packages.md)참조하십시오.

## <a name="localize-command-names"></a>명령 이름 지역화

VSPackages에서 메뉴 명령 및 도구 모음 단추는 *.vsct* 파일에 정의 됩니다.

1. **솔루션 탐색기에서** *.vsct* 파일 *이름.vsct에서* *filename.en-US.vsct로*.vsct 파일 의 이름을 변경합니다.

2. 지역화된 각 언어에 대해 *filename.en-US.vsct의* 복사본을 만듭니다.

    각 복사 파일 이름 이름 *지정.{ 로케일}.vsct*, *{Locale}는* 특정 문화권 이름입니다. 문화권 이름 값 목록은 [Microsoft에서 할당한 로캘 아이디를](/windows/uwp/publish/supported-languages)참조하십시오.

    이러한 *파일 이름입니다. Locale.vsct* 파일에는 패키지에 대한 지역화된 메뉴 텍스트가 포함됩니다.

3. 각 *파일 이름을 엽니다. 텍스트를 지역화할 로케일.vsct* 파일입니다.

   1. 특정 언어에 적합한 [ButtonText](../extensibility/buttontext-element.md) 요소 값을 수정합니다.

   2. 지역화된 아이콘을 제공하는 경우 [Bitmap](../extensibility/bitmap-element.md) 값을 수정하여 대상 파일을 가리킵니다.

      다음 예제에서는 패밀리 트리 탐색기 도구 창을 여는 명령에 대한 영어 및 스페인어 단추 텍스트를 보여 주십니까?

      [*패밀리트리.en-US.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Family Tree Explorer</ButtonText>
     </Strings>
   </Button>
   ```

    [*FamilyTree.es-ES.vsct*]

   ```xml
   <Button guid="guidLocalizedPackageCmdSet" id="cmdidFamilyTree" priority="0x0100" type="Button">
     <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>
     <Icon guid="guidImages" id="bmpPic2" />
     <Strings>
       <CommandName>cmdidFamilyTree</CommandName>
       <ButtonText>Explorar el arbol genealogico</ButtonText>
     </Strings>
   </Button>
   ```

## <a name="localize-other-text-resources"></a>다른 텍스트 리소스 지역화

명령 이름 이외의 텍스트 리소스는*리소스(.resx)* 파일에 정의되어 있습니다.

1. *VSPackage.resx를* *VSPackage.en-US.resx로*변경합니다.

2. 지역화된 각 언어에 대해 *VSPackage.en-US.resx* 파일의 복사본을 만듭니다.

     각 복사본 의 이름 *VSPackage.{ 로케일}.resx*, *{Locale}는* 특정 문화권 이름입니다.

3. *리소스.resx를* *Resources.en-US.resx로*이름을 바꿉니다.

4. 지역화된 각 언어에 대해 *Resources.en-US.resx* 파일의 복사본을 만듭니다.

     각 복사본 리소스 이름 *지정.{ 로케일}.resx*, *{Locale}는* 특정 문화권 이름입니다.

5. 각 *.resx* 파일을 열어 특정 언어 및 문화문화에 적합한 문자열 값을 수정합니다. 다음 예제에서는 도구 창의 제목 표시줄에 대한 지역화된 리소스 정의를 보여 주습니다.

     *[Resources.en-US.resx]*

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es-ES.resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>프로젝트에 지역화된 리소스 통합

지역화된 리소스를 통합하려면 *assemblyinfo.cs* 파일과 프로젝트 파일을 수정해야 합니다.

1. **솔루션 탐색기의** **속성** 노드에서 assemblyinfo.cs *또는* *어셈블리info.vb를* 엽니다.

2. 다음 항목을 추가합니다.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     이렇게 하면 미국 영어가 기본 언어로 설정됩니다.

3. 프로젝트를 언로드합니다.

4. 편집기에서 프로젝트 파일을 엽니다.

5. 루트 `Project` 요소에서 기본 `PropertyGroup` 언어와 `UICulture` 일치하는 요소가 있는 요소를 추가합니다.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     이렇게 하면 미국 영어가 WPF(Windows 프레젠테이션 재단) 컨트롤의 기본 UI 문화로 설정됩니다.

6. 요소가 `ItemGroup` 포함된 `EmbeddedResource` 요소를 찾습니다.

7. `EmbeddedResource` *VSPackage.en-US.resx를*호출하는 요소에서 `ManifestResourceName` 요소를 다음과 `LogicalName` 같이 로 설정된 `VSPackage.en-US.Resources`요소로 바꿉꿉습니다.

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. 지역화된 `EmbeddedResource` 각 언어에 대해 `VsPackage.en-US`에 대한 요소를 복사하고 복사본의 **Include** 특성 및 **LogicName** 요소를 대상 로캘에 설정합니다.

9. 지역화된 `VSCTCompile` 각 요소에 다음 `ResourceName` 예제와 `Menus.ctmenu`같이 을 가리키는 요소를 추가합니다.

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. 프로젝트 파일을 저장하고 프로젝트를 다시 로드합니다.

11. 프로젝트를 빌드합니다.

     이렇게 하면 각 언어에 대한 주 어셈블리 및 리소스 어셈블리가 만들어집니다. 배포 프로세스 지역화에 대한 자세한 내용은 [VSIX 패키지 지역화를](../extensibility/localizing-vsix-packages.md) 참조하십시오.

## <a name="see-also"></a>참조

- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
- [응용 프로그램 전역화 및 지역화](../ide/globalizing-and-localizing-applications.md)
