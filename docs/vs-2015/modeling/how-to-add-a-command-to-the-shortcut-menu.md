---
title: '방법: 바로 가기 메뉴에 명령 추가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: cd550399-05fc-4dbf-be4c-f5094bb752ce
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d5ddea477aa7295c41097177265b43483b7aa45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850412"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>방법: 바로 가기 메뉴에 명령 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자가 DSL(Domain-Specific Language) 관련 작업을 수행할 수 있도록 DSL에 메뉴 명령을 추가할 수 있습니다. 사용자가 다이어그램을 마우스 오른쪽 단추로 클릭하면 상황에 맞는(바로 가기) 메뉴에 명령이 표시됩니다. 특정 상황에서만 메뉴에 표시되도록 명령을 정의할 수 있습니다. 예를 들어 사용자가 특정 형식의 요소나 특정 상태의 요소를 클릭할 때만 메뉴가 표시되도록 지정할 수 있습니다.

 요약하자면 DslPackage 프로젝트에서 다음과 같은 단계를 수행합니다.

1. [명령에서 명령을 선언 합니다. vsct](#VSCT)

2. [Package.tt에서 패키지 버전 번호를 업데이트](#version)합니다. Commands.vsct를 변경할 때마다 이 작업을 수행해야 합니다.

3. [CommandSet 클래스의 메서드를 작성](#CommandSet) 하 여 명령을 표시 하 고 명령이 수행할 작업을 정의 합니다.

   샘플은 [시각화 및 모델링 SDK 웹 사이트](https://www.visualstudio.com/)를 참조 하세요.

> [!NOTE]
> CommandSet.cs의 메서드를 재정의하여 잘라내기, 붙여넣기, 모두 선택, 인쇄 등의 몇 가지 기존 명령 동작도 수정할 수 있습니다. 자세한 내용은 [방법: 표준 메뉴 명령 수정](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)을 참조 하세요.

## <a name="defining-a-command-using-mef"></a>MEF를 사용하여 명령 정의
 MEF(Managed Extension Framework)는 다이어그램 메뉴의 메뉴 명령을 정의하는 다른 방법을 제공합니다. MEF는 주로 명령의 개발자 또는 다른 사용자가 DSL을 확장하는 데 사용됩니다. 사용자는 DSL만 설치할 수도 있고 DSL과 확장을 모두 설치할 수도 있습니다. 이와 동시에 MEF를 사용하면 DSL에서 MEF를 사용하도록 설정하는 초기 작업을 수행한 후 바로 가기 메뉴 명령을 정의하는 작업도 줄어듭니다.

 다음과 같은 경우 이 항목에서 소개하는 메서드를 사용합니다.

1. 오른쪽 클릭 바로 가기 메뉴 이외의 메뉴 명령을 메뉴에 정의하려는 경우

2. 메뉴에서 특정 명령 그룹을 정의하려는 경우

3. 다른 사용자가 고유한 명령으로 DSL을 확장하지 못하도록 지정하려는 경우

4. 명령을 하나만 정의하려는 경우

   그 외의 경우에는 MEF 메서드를 사용하여 명령을 정의하는 것이 좋습니다. 자세한 내용은 [MEF를 사용 하 여 DSL 확장](../modeling/extend-your-dsl-by-using-mef.md)을 참조 하세요.

## <a name="declare-the-command-in-commandsvsct"></a><a name="VSCT"></a> 명령에서 명령을 선언 합니다. Vsct
 DslPackage\Commands.vsct에서 메뉴 명령을 선언합니다. 이러한 정의는 메뉴 항목의 레이블 및 메뉴에서 항목이 표시되는 위치를 지정합니다.

 편집 하는 파일의 명령인 vsct는 디렉터리 *Visual STUDIO SDK 설치 경로*\VisualStudioIntegration\Common\Inc.에 있는 여러 .h 파일에서 정의를 가져옵니다. 여기에는 DSL 정의에서 생성 되는 GeneratedVsct도 포함 됩니다.

 . Vsct 파일에 대 한 자세한 내용은 [Visual Studio 명령 테이블 (를 참조 하세요. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

#### <a name="to-add-the-command"></a>명령을 추가하려면

1. **솔루션 탐색기**의 **dslpackage** 프로젝트에서 명령을. vsct를 엽니다.

2. `Commands` 요소에서 하나 이상의 단추와 하나의 그룹을 정의합니다. *단추* 는 메뉴의 항목입니다. *그룹* 은 메뉴의 섹션입니다. 이러한 항목을 정의하려면 다음 요소를 추가합니다.

    ```
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    > 각 단추나 그룹은 GUID 및 정수 ID로 식별됩니다. 같은 GUID로 여러 그룹과 단추를 만들 수 있지만 이러한 항목의 ID는 각각 달라야 합니다. GUID 이름과 ID 이름은 노드의 실제 Guid와 숫자 Id로 변환 됩니다 `<Symbols>` .

3. 명령이 DSL 컨텍스트에서만 로드되도록 명령에 대한 표시 유형 제약 조건을 추가합니다. 자세한 내용은 [VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)를 참조 하세요.

     이렇게 하려면 `CommandTable` 요소에서 `Commands` 요소 뒤에 다음 요소를 추가합니다.

    ```
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. GUID 및 ID에 사용되는 이름을 정의합니다. 이렇게 하려면 `Symbols` 요소에서 `CommandTable` 요소 뒤에 `Commands` 요소를 추가합니다.

    ```
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5. `{000...000}`는 그룹 및 메뉴 항목을 식별하는 GUID로 바꿉니다. 새 GUID를 얻으려면 **도구** 메뉴에서 **guid 만들기** 도구를 사용 합니다.

    > [!NOTE]
    > 그룹 또는 메뉴 항목을 더 추가하는 경우 같은 GUID를 사용할 수 있습니다. 그러나 `IDSymbols`에는 새 값을 사용해야 합니다.

6. 이 절차에서 복사한 코드에서 다음 문자열이 나오면 실제 환경에 맞는 문자열로 바꿉니다.

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="update-the-package-version-in-packagett"></a><a name="version"></a> Package.tt에서 패키지 버전 업데이트
 명령을 추가하거나 변경할 때마다 새 DSL 버전을 릴리스하기 전에 패키지 클래스에 적용되는 `version`의 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 매개 변수를 업데이트합니다.

 패키지 클래스는 생성된 파일에서 정의되므로 Package.cs 파일을 생성하는 텍스트 템플릿 파일에서 특성을 업데이트합니다.

#### <a name="to-update-the-packagett-file"></a>Package.tt 파일을 업데이트하려면

1. **솔루션 탐색기**의 **dslpackage** 프로젝트에서 **generatedcode** 폴더에 있는 Package.tt 파일을 엽니다.

2. `ProvideMenuResource` 특성을 찾습니다.

3. 특성의 `version` 매개 변수(두 번째 매개 변수)를 증분합니다. 원하는 경우 용도에 맞게 매개 변수 이름을 명시적으로 작성할 수 있습니다. 예를 들면 다음과 같습니다.

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="define-the-behavior-of-the-command"></a><a name="CommandSet"></a> 명령의 동작을 정의 합니다.
 DS에는 DslPackage\GeneratedCode\CommandSet.cs에서 선언된 partial 클래스에서 구현되는 일부 명령이 이미 포함되어 있습니다. 새 명령을 추가하려면 같은 클래스의 partial 선언을 포함하는 새 파일을 만들어 이 클래스를 확장해야 합니다. 클래스의 이름은 일반적으로 *\<YourDslName>* `CommandSet` 입니다. 먼저 클래스 이름을 확인하고 해당 내용을 검사하면 유용합니다.

 명령 집합 클래스는 <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>에서 파생됩니다.

#### <a name="to-extend-the-commandset-class"></a>CommandSet 클래스를 확장하려면

1. 솔루션 탐색기의 DslPackage 프로젝트에서 GeneratedCode 폴더를 열고 CommandSet.tt를 확인하여 생성된 CommandSet.cs 파일을 엽니다. 이 파일에 정의된 첫 번째 클래스의 이름과 네임스페이스를 확인합니다. 예를 들어 다음과 같은 코드가 표시될 수 있습니다.

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. **Dslpackage**에서 **custom Code**라는 폴더를 만듭니다. 이 폴더에서 라는 새 클래스 파일을 만듭니다 `CommandSet.cs` .

3. 새 파일에 생성된 partial 클래스와 이름 및 네임스페이스가 같은 partial 선언을 작성합니다. 예를 들면 다음과 같습니다.

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     **참고** 클래스 템플릿을 사용 하 여 새 파일을 만든 경우 네임 스페이스와 클래스 이름을 모두 수정 해야 합니다.

### <a name="extend-the-command-set-class"></a>명령 집합 클래스 확장
 명령 집합 코드는 일반적으로 다음 네임스페이스를 가져와야 합니다.

```
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

 생성된 commandSet.cs와 일치하도록 네임스페이스 및 클래스 이름을 조정합니다.

```
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

 명령이 상황에 맞는 메뉴에 표시되는 경우를 결정하는 메서드와 명령을 수행하는 메서드 등 두 메서드를 정의해야 합니다. 이러한 메서드는 재정의가 아니며, 명령 목록에 등록해야 합니다.

### <a name="define-when-the-command-will-be-visible"></a>명령이 표시되는 경우 정의
 각 명령에 대해 `OnStatus...` 명령이 메뉴에 표시 되는지 여부와 명령이 사용 되는지 또는 회색으로 표시 되는지 여부를 결정 하는 메서드를 정의 합니다. `Visible` `Enabled` `MenuCommand` 다음 예제와 같이의 및 속성을 설정 합니다. 이 메서드는 사용자가 다이어그램을 마우스 오른쪽 단추로 클릭할 때마다 바로 가기 메뉴를 생성하기 위해 호출되므로 빠르게 작동해야 합니다.

 이 예에서 명령은 사용자가 특정 형식의 모양을 선택한 경우에만 표시되며 선택한 요소 중 하나 이상이 특정 상태일 때만 사용하도록 설정됩니다. 이 명령은 클래스 다이어그램 DSL 템플릿을 기준으로 하며 ClassShape 및 ModelClass는 DSL에서 정의되는 형식입니다.

```
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

 OnStatus 메서드에서는 다음 코드 조각이 유용하게 사용되는 경우가 많습니다.

- `this.CurrentSelection`. 사용자가 마우스 오른쪽 단추로 클릭한 모양은 항상 이 목록에 포함됩니다. 사용자가 다이어그램의 빈 부분을 클릭하는 경우의 목록 멤버는 Diagram뿐입니다.

- `this.IsDiagramSelected()` - `true` 사용자가 다이어그램의 빈 부분을 클릭 한 경우

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` -사용자가 여러 개체를 선택 하지 않았습니다.

- `this.SingleSelection` -사용자가 마우스 오른쪽 단추로 클릭 한 모양 또는 다이어그램

- `shape.ModelElement as MyLanguageElement` -도형이 나타내는 모델 요소입니다.

  일반적으로는 선택한 항목에 따라 `Visible` 속성이 설정되고 선택한 요소의 상태에 따라 `Enabled` 속성이 설정되도록 지정합니다.

  OnStatus 메서드가 Store의 상태를 변경해서는 안 됩니다.

### <a name="define-what-the-command-does"></a>명령을 통해 수행할 작업 정의
 각 명령에 대해 사용자가 메뉴 명령을 클릭하면 필요한 작업을 수행하는 `OnMenu...` 메서드를 정의합니다.

 모델 요소를 변경하는 경우에는 트랜잭션 내에서 변경해야 합니다. 자세한 내용은 [방법: 표준 메뉴 명령 수정](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)을 참조 하세요.

 이 예에서 `ClassShape`, `ModelClass` 및 `Comment`는 클래스 다이어그램 DSL 템플릿에서 파생된 DSL에서 정의되는 형식입니다.

```
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 모델의 개체에서 개체로 이동 하는 방법과 개체 및 링크를 만드는 방법에 대 한 자세한 내용은 [방법: 표준 메뉴 명령 수정](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)을 참조 하세요.

### <a name="register-the-command"></a>명령 등록
 CommandSet.vsct의 Symbols 섹션에서 작성한 GUID 및 ID 값 선언을 C#에서 반복합니다.

```
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 **명령. vsct**에서 삽입 한 것과 동일한 GUID 값을 사용 합니다.

> [!NOTE]
> VSCT 파일의 Symbols 섹션을 변경하는 경우 이러한 선언도 일치하도록 변경해야 합니다. 또한 Package.tt에서 버전 번호도 증분해야 합니다.

 이 명령 집합의 일부분으로 메뉴 명령을 등록합니다. `GetMenuCommands()` 는 다이어그램이 초기화 될 때 한 번 호출 됩니다.

```
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>명령 테스트
 Visual Studio의 실험적 인스턴스에서 DSL을 빌드하고 실행합니다. 지정한 상황에서 바로 가기 메뉴에 명령이 표시되어야 합니다.

#### <a name="to-exercise-the-command"></a>명령을 실행해 보려면

1. **솔루션 탐색기** 도구 모음에서 **모든 템플릿 변환**을 클릭 합니다.

2. **F5** 키를 눌러 솔루션을 다시 빌드하고 실험적 빌드에서 도메인별 언어 디버깅을 시작 합니다.

3. 실험적 빌드에서 샘플 다이어그램을 엽니다.

4. 다이어그램의 여러 항목을 마우스 오른쪽 단추로 클릭하여 명령을 정상적으로 사용하거나 사용하지 않도록 설정하며 선택한 항목에 따라 적절하게 표시되거나 숨겨지는지를 확인합니다.

## <a name="troubleshooting"></a>문제 해결
 **메뉴에 명령이 표시되지 않습니다.**

- DSL 패키지를 설치할 때까지 명령은 Visual Studio의 디버깅 인스턴스에만 표시됩니다. 자세한 내용은 [도메인 특정 언어 솔루션 배포](../modeling/deploying-domain-specific-language-solutions.md)를 참조하세요.

- 실험적 샘플에서 이 DSL의 파일 이름 확장명이 정확한지 확인합니다. 파일 이름 확장명을 확인하려면 Visual Studio 주 인스턴스에서 DslDefinition.dsl을 엽니다. 그런 다음 DSL 탐색기에서 편집기 노드를 마우스 오른쪽 단추로 클릭하고 속성을 클릭합니다. 속성 창에서 FileExtension 속성을 점검합니다.

- [패키지 버전 번호를 증분](#version)했습니까?

- OnStatus 메서드 시작 부분에 중단점을 설정합니다. 그러면 다이어그램의 아무 곳이나 마우스 오른쪽 단추로 클릭할 때 메서드가 중단되어야 합니다.

   **Onstatus 메서드는 호출 되지 않습니다**.

  - CommandSet 코드의 GUID 및 ID가 Commands.vsct의 Symbols 섹션에 포함된 GUID 및 ID와 일치하는지 확인합니다.

  - Commands.vsct에서 모든 Parent 노드의 GUID 및 ID가 올바른 부모 그룹을 식별하는지 확인합니다.

  - Visual Studio 명령 프롬프트에서 devenv /rootsuffix exp /setup을 입력합니다. 그런 다음 Visual Studio 디버깅 인스턴스를 다시 시작합니다.

- OnStatus 메서드를 단계별로 실행하여 command.Visible 및 command.Enabled가 true로 설정되는지 확인합니다.

  **잘못 된 메뉴 텍스트가 나타나거나 명령이 잘못 된 위치에 표시 됩니다**.

- GUID 및 ID 조합이 해당 명령에 대해 고유한지 확인합니다.

- 이전 버전 패키지를 제거했는지 확인합니다.

## <a name="see-also"></a>관련 항목
 [도메인별 언어를 지정 하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md) [방법: 표준 메뉴 명령 수정](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md) [도메인별 언어 솔루션 배포](../modeling/deploying-domain-specific-language-solutions.md)
