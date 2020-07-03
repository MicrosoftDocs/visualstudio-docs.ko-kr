---
title: 메뉴 명령 지역화 | Microsoft Docs
ms.date: 10/08/2019
ms.topic: how-to
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
ms.openlocfilehash: 1c1c158fd689cbcae18fec5d3306e6d6fadb169f
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904551"
---
# <a name="localize-menu-commands"></a>메뉴 명령 지역화

VSPackage에 대 한 지역화 된 *. vsct* 파일 및 지역화 된 *.resx* 파일을 만든 다음 변경 내용을 통합 하기 위해 프로젝트 파일을 업데이트 하 여 메뉴 및 도구 모음 명령에 대 한 지역화 된 텍스트를 제공할 수 있습니다.

설치 환경을 지역화 하는 방법에 대 한 자세한 내용은 [VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)를 참조 하세요.

## <a name="localize-command-names"></a>명령 이름 지역화

Vspackage에서 메뉴 명령 및 도구 모음 단추는 *. vsct* 파일에 정의 되어 있습니다.

1. **솔루션 탐색기**에서 *vsct* 파일의 이름을 파일 *이름에서 파일 이름으로 변경* *합니다.*

2. 지역화 된 각 언어에 대해 *파일 이름. en-us. vsct* 의 복사본을 만듭니다.

    각 복사본의 이름을 파일 이름으로 * Locale}. vsct*. 여기서 *{Locale}* 은 특정 문화권 이름입니다. 문화권 이름 값 목록은 [Microsoft에서 할당 한 로캘 id](/windows/uwp/publish/supported-languages)를 참조 하세요.

    이러한 *파일 이름입니다. Locale. vsct* 파일에는 패키지에 대 한 지역화 된 메뉴 텍스트가 포함 됩니다.

3. 각 *파일 이름을 엽니다. *텍스트를 지역화 하는 Locale vsct 파일입니다.

   1. 특정 언어에 맞게 [Buttontext](../extensibility/buttontext-element.md) 요소 값을 적절 하 게 수정 합니다.

   2. 지역화 된 아이콘을 제공 하는 경우 대상 파일을 가리키도록 [비트맵](../extensibility/bitmap-element.md) 값을 수정 합니다.

      다음 예제에서는 제품군 트리 탐색기 도구 창을 여는 명령에 대 한 영어 및 스페인어 단추 텍스트를 보여 줍니다.

      [*FamilyTree*] (영문)

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

    [*FamilyTree.es*]

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

명령 이름 이외의 텍스트 리소스는 리소스 (*.resx*) 파일에 정의 됩니다.

1. *VSPackage* 의 이름을 *VSPackage*로 바꿉니다.

2. 지역화 된 각 언어에 대해 *VSPackage* 파일의 복사본을 만듭니다.

     각 복사본의 이름을 *VSPackage. { Locale} .resx*. 여기서 *{Locale}* 은 특정 문화권 이름입니다.

3. *리소스를 .resx* 로 이름 변경 *합니다.*

4. 지역화 된 각 언어에 대 한 *리소스. en-us* 파일의 복사본을 만듭니다.

     각 복사 리소스의 이름을로 *합니다. Locale} .resx*. 여기서 *{Locale}* 은 특정 문화권 이름입니다.

5. 각 *.resx* 파일을 열어 특정 언어 및 문화권에 맞게 문자열 값을 수정 합니다. 다음 예제에서는 도구 창의 제목 표시줄에 대 한 지역화 된 리소스 정의를 보여 줍니다.

     [*Resources. en-us. .resx*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Family Tree Explorer</value>
    </data>
    ```

     [*Resources.es*]

    ```xml
    <data name="ToolWindowTitle" xml:space="preserve">
      <value>Explorador del arbol genealogico</value>
    </data>
    ```

## <a name="incorporate-localized-resources-into-the-project"></a>지역화 된 리소스를 프로젝트에 통합

지역화 된 리소스를 통합 하려면 *assemblyinfo.cs* 파일 및 프로젝트 파일을 수정 해야 합니다.

1. **솔루션 탐색기**의 **속성** 노드에서 편집기에서 *assemblyinfo.cs* 또는 *assemblyinfo* 를 엽니다.

2. 다음 항목을 추가 합니다.

    ```csharp
    [assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]
    ```

     이는 미국 영어를 기본 언어로 설정 합니다.

3. 프로젝트를 언로드합니다.

4. 편집기에서 프로젝트 파일을 엽니다.

5. Root 요소에서 요소를 `Project` 사용 하 `PropertyGroup` 여 `UICulture` 기본 언어와 일치 하는 요소를 추가 합니다.

    ```xml
    <PropertyGroup>
      <UICulture>en-US</UICulture>
    </PropertyGroup>
    ```

     이는 Windows Presentation Foundation (WPF) 컨트롤에 대 한 기본 UI 문화권으로 미국 영어를 설정 합니다.

6. `ItemGroup`요소가 포함 된 요소를 찾습니다 `EmbeddedResource` .

7. `EmbeddedResource` *VSPackage*를 호출 하는 요소에서 다음과 `ManifestResourceName` 같이 요소를 `LogicalName` 로 설정 된 요소로 바꿉니다 `VSPackage.en-US.Resources` .

    ```xml
    <EmbeddedResource Include="VSPackage.en-US.resx">
      <MergeWithCTO>true</MergeWithCTO>
      <LogicalName>VSPackage.en-US.Resources</LogicalName>
    </EmbeddedResource>
    ```

8. 지역화 된 각 언어에 대해 요소를 복사 하 `EmbeddedResource` `VsPackage.en-US` 고 복사본의 **Include** 특성 및 **logicalname** 요소를 대상 로캘로 설정 합니다.

9. `VSCTCompile` `ResourceName` 다음 예제와 같이 지역화 된 각 요소에를 가리키는 요소를 추가 합니다 `Menus.ctmenu` .

    ```xml
    <ItemGroup>
      <VSCTCompile Include="LocalizedPackage.es-ES.vsct">
        <ResourceName>Menus.ctmenu</ResourceName>
      </VSCTCompile>
    </ItemGroup>
    ```

10. 프로젝트 파일을 저장 하 고 프로젝트를 다시 로드 합니다.

11. 프로젝트를 빌드합니다.

     그러면 주 어셈블리와 각 언어에 대 한 리소스 어셈블리가 생성 됩니다. 배포 프로세스를 지역화 하는 방법에 대 한 자세한 내용은 [VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md) 를 참조 하세요.

## <a name="see-also"></a>참조

- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
- [응용 프로그램 전역화 및 지역화](../ide/globalizing-and-localizing-applications.md)
