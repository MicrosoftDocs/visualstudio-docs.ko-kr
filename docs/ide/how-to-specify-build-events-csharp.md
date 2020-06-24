---
title: '방법: 빌드 이벤트 지정(C#)'
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e1a3083b59ad0cec727f753395768a214ff571b7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283998"
---
# <a name="how-to-specify-build-events-c"></a>방법: 빌드 이벤트 지정(C#)

빌드 이벤트를 사용하여 빌드 시작 전 또는 빌드 완료 후 실행되는 명령을 지정합니다. 빌드 이벤트는 빌드가 빌드 프로세스의 해당 지점에 성공적으로 도달하는 경우에만 실행됩니다.

프로젝트가 빌드될 때 빌드 전 이벤트는 *PreBuildEvent.bat*라는 파일에 추가되고 빌드 후 이벤트는 *PostBuildEvent.bat*라는 파일에 추가됩니다. 오류 확인을 보장하려면 자체적인 오류 확인 명령을 빌드 단계에 추가합니다.

## <a name="specify-a-build-event"></a>빌드 이벤트 지정

1. **솔루션 탐색기**에서 빌드 이벤트를 지정할 프로젝트를 선택합니다.

2. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

3. **빌드 이벤트** 탭을 선택합니다.

4. **빌드 전 이벤트 명령줄** 상자에서 빌드 이벤트의 구문을 지정합니다.

   > [!NOTE]
   > 프로젝트가 최신 상태이고 빌드가 트리거되지 않으면 빌드 전 이벤트가 실행되지 않습니다.

5. **빌드 후 이벤트 명령줄** 상자에서 빌드 이벤트의 구문을 지정합니다.

   > [!NOTE]
   > *.bat* 파일을 실행하는 모든 빌드 후 이벤트 명령 앞에 `call` 문을 추가합니다. 예를 들어 `call C:\MyFile.bat` 또는 `call C:\MyFile.bat call C:\MyFile2.bat`입니다.

6. **빌드 후 이벤트 실행** 상자에서 빌드 후 이벤트를 실행할 조건을 지정합니다.

   > [!NOTE]
   > 긴 구문을 추가하거나 [빌드 전 이벤트/빌드 후 이벤트 명령줄 대화 상자](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)에서 임의의 빌드 매크로를 선택하려면, 줄임표 단추( **...** )를 클릭하여 편집 상자를 표시합니다.

   빌드 이벤트 구문에는 명령 프롬프트 또는 *.bat* 파일에서 유효한 모든 명령이 포함될 수 있습니다. 일괄 처리 파일의 이름 앞에 `call`을 사용하여 모든 후속 명령이 실행되도록 합니다.

   > [!NOTE]
   > 빌드 전 또는 빌드 후 이벤트가 성공적으로 완료되지 않으면 성공적인 작업을 나타내는 0(영) 이외의 코드로 이벤트 작업이 종료되도록 하여 빌드를 종료할 수 있습니다.

## <a name="example"></a>예제

다음 절차에서는 빌드 후 이벤트에서 호출된 *.exe* 명령을 사용하여 애플리케이션 매니페스트의 최소 운영 체제 버전을 설정하는 방법을 보여줍니다(프로젝트 디렉터리의 *.exe.manifest* 파일). 최소 운영 체제 버전은 네 부분으로 구성된 번호입니다(예: 4.10.0.0). 최소 운영 체제 버전을 설정하기 위해 명령은 매니페스트의 `<dependentOS>` 섹션을 변경합니다.

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>.exe 명령을 만들어 애플리케이션 매니페스트 변경

1. 명령에 대한 새 **콘솔 앱** 프로젝트를 만듭니다. 프로젝트 이름을 **ChangeOSVersionCS**로 지정합니다.

2. *Program.cs*에서 파일 맨 위의 다른 `using` 지시문에 다음 줄을 추가합니다.

   ```csharp
   using System.Xml;
   ```

3. `ChangeOSVersionCS` 네임스페이스에서 `Program` 클래스 구현을 다음 코드로 바꿉니다.

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
      /// 1 - Version of OS
      ///</param>
      static void Main(string[] args)
      {
         string applicationManifestPath = args[0];
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

         // Get version name.
         Version osVersion = null;
         if (args.Length >=2 ){
            osVersion = new Version(args[1]);
         }else{
            throw new ArgumentException("OS Version not specified.");
         }
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());

         XmlDocument document;
         XmlNamespaceManager namespaceManager;
         namespaceManager = new XmlNamespaceManager(new NameTable());
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

         document = new XmlDocument();
         document.Load(applicationManifestPath);

         string baseXPath;
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

         // Change minimum required operating system version.
         XmlNode node;
         node = document.SelectSingleNode(baseXPath, namespaceManager);
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

         document.Save(applicationManifestPath);
      }
   }
   ```

   이 명령은 두 개의 인수인 애플리케이션 매니페스트의 경로(매니페스트를 만드는 빌드 프로세스의 폴더, 일반적으로 *Projectname.publish*) 및 새 운영 체제 버전을 사용합니다.

4. 프로젝트를 빌드합니다.

5. *.exe* 파일을 *C:\TEMP\ChangeOSVersionVB.exe*와 같은 디렉터리에 복사합니다.

다음으로 빌드 후 이벤트에서 이 명령을 호출하여 애플리케이션 매니페스트를 수정합니다.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>빌드 후 이벤트를 호출하여 애플리케이션 매니페스트 수정

1. 새 **Windows Forms 앱** 프로젝트를 만들고 이름을 **CSWinApp**으로 지정합니다.

2. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 선택합니다.

3. **프로젝트 디자이너**에서 **게시** 페이지를 찾고 **게시 위치**를 *C:\TEMP*로 설정합니다.

4. **지금 게시**를 클릭하여 프로젝트를 게시합니다.

   매니페스트 파일이 빌드되고 *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*에 저장됩니다. 매니페스트를 보려면 파일을 마우스 오른쪽 단추로 클릭하고, **연결 프로그램**을 클릭하고, **목록에서 프로그램 선택**을 선택하고 나서, **메모장**을 클릭합니다.

   파일에서 `<osVersionInfo>` 요소를 검색합니다. 예를 들어 버전은 다음과 같습니다.

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. **프로젝트 디자이너**로 돌아가서 **빌드 이벤트** 탭을 클릭한 다음, **빌드 후 편집**을 클릭합니다.

6. **빌드 후 이벤트 명령줄** 상자에서 다음 명령을 입력합니다.

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   프로젝트를 빌드할 때 이 명령은 애플리케이션 매니페스트의 최소 운영 체제 버전을 5.1.2600.0으로 변경합니다.

   `$(TargetPath)` 매크로는 생성되는 실행 파일의 전체 경로를 표현하므로 `$(TargetPath).manifest`는 *bin* 디렉터리에서 생성되는 애플리케이션 매니페스트를 지정합니다. 게시를 수행하면 이 매니페스트가 이전에 설정한 게시 위치에 복사됩니다.

7. 프로젝트를 다시 게시합니다.

   이제 매니페스트 버전은 다음을 읽어야 합니다.

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>참고 항목

- [빌드 이벤트 페이지, 프로젝트 디자이너(C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [빌드 전 이벤트/빌드 후 이벤트 명령줄 대화 상자](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [방법: 빌드 이벤트 지정(Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md)
