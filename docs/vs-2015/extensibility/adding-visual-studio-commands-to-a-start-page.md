---
title: 시작 페이지에 Visual Studio 명령 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a2042ef9a96eed99636ea0a2f5f09d99cd35ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699160"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>시작 페이지에 Visual Studio 명령 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 지정 시작 페이지를 만들 때 Visual Studio 명령을 추가할 수 있습니다. 이 문서에서는 시작 페이지에서 Visual Studio 명령을 XAML 개체에 바인딩하는 다양 한 방법을 설명 합니다.  
  
 XAML의 명령에 대 한 자세한 내용은 명령 [개요](https://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81) 를 참조 하세요.  
  
## <a name="adding-commands-from-the-command-well"></a>명령 웰에서 명령 추가  
 [사용자 지정 시작 페이지를 만들](../extensibility/creating-a-custom-start-page.md) 때 생성 된 시작 페이지에 <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> 다음과 같이 및 네임 스페이스가 추가 되었습니다.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Microsoft.VisualStudio.Shell.Immutable.11.0.dll 어셈블리에서 VisualStudio에 대 한 다른 네임 스페이스를 추가 합니다. 이 어셈블리에 대 한 참조를 프로젝트에 추가 해야 할 수도 있습니다.  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 이 별칭을 사용 하 여 `vscom:` 컨트롤의 속성을로 설정 하 여 Visual Studio 명령을 페이지의 XAML 컨트롤에 바인딩할 수 있습니다 <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> `vscom:VSCommands.ExecuteCommand` . 그런 다음 <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> , 다음 예제와 같이 실행할 명령의 이름으로 속성을 설정할 수 있습니다.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
> `x:`모든 명령의 시작 부분에는 XAML 스키마를 참조 하는 별칭이 필요 합니다.  
  
 `Command` **명령** 창에서 액세스할 수 있는 명령으로 속성의 값을 설정할 수 있습니다. 사용할 수 있는 명령 목록은 [Visual Studio 명령 별칭](../ide/reference/visual-studio-command-aliases.md)을 참조 하세요.  
  
 추가할 명령에 추가 매개 변수가 필요한 경우 속성의 값에 추가할 수 있습니다 `CommandParameter` . 다음 예제와 같이 공백을 사용 하 여 명령의 매개 변수를 구분 합니다.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>명령 웰에서 확장 호출  
 다른 Visual Studio 명령을 호출 하는 데 사용 되는 것과 동일한 구문을 사용 하 여 등록 된 Vspackage에서 명령을 호출할 수 있습니다. 예를 들어 설치 된 VSPackage **홈 페이지** 명령을 **보기** 메뉴에 추가 하는 경우를로 설정 하 여 해당 명령을 호출할 수 있습니다 `CommandParameter` `View.HomePage` .  
  
> [!NOTE]
> VSPackage와 연결 된 명령을 호출 하는 경우 명령이 호출 될 때 패키지를 로드 해야 합니다.  
  
## <a name="adding-commands-from-assemblies"></a>어셈블리에서 명령 추가  
 어셈블리에서 명령을 호출 하거나 메뉴 명령과 연결 되지 않은 VSPackage의 코드에 액세스 하려면 어셈블리에 대 한 별칭을 만든 다음 별칭을 호출 해야 합니다.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>어셈블리에서 명령을 호출 하려면  
  
1. 솔루션에서 어셈블리에 대 한 참조를 추가 합니다.  
  
2. 다음 예제와 같이 StartPage 파일의 맨 위에서 어셈블리에 대 한 네임 스페이스 지시문을 추가 합니다.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3. `Command`다음 예제와 같이 XAML 개체의 속성을 설정 하 여 명령을 호출 합니다.  
  
     Page.xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
> 어셈블리를 복사 하 여에 \\ 붙여넣어야 합니다. *Visual Studio 설치 폴더가*\Common7\IDE\PrivateAssemblies\ 호출 되기 전에 로드 되는지 확인 합니다.  
  
## <a name="adding-commands-with-the-dte-object"></a>DTE 개체를 사용 하 여 명령 추가  
 태그와 코드 모두의 시작 페이지에서 DTE 개체에 액세스할 수 있습니다.  
  
 태그에서 개체를 호출 하는 [바인딩 태그 확장](https://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) 구문을 사용 하 여 액세스할 수 있습니다 <xref:EnvDTE.DTE> . 이 방법을 사용 하 여 컬렉션을 반환 하는 것과 같은 간단한 속성에 바인딩할 수 있지만 메서드나 서비스에 바인딩할 수는 없습니다. 다음 예제에서는 속성 <xref:System.Windows.Controls.TextBlock> 에 바인딩되는 컨트롤과 속성에 <xref:EnvDTE._DTE.Name%2A> 의해 반환 되는 <xref:System.Windows.Controls.ListBox> 컬렉션의 속성을 열거 하는 컨트롤을 보여 줍니다 <xref:EnvDTE.Window.Caption%2A> <xref:EnvDTE._DTE.Windows%2A> .  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 예제는 [연습: 시작 페이지에 사용자 설정 저장](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [시작 페이지에 사용자 컨트롤 추가](../extensibility/adding-user-control-to-the-start-page.md)
