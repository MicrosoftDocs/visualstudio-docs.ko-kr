---
title: 프로젝트 디자이너, 서명 페이지 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5707ef277892c37cab16f78ac11113194a95e190
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663505"
---
# <a name="signing-page-project-designer"></a>프로젝트 디자이너, 서명 페이지
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**프로젝트 디자이너**의 **서명** 페이지를 사용하여 애플리케이션 및 배포 매니페스트에 서명하고 어셈블리에도 서명합니다(강력한 이름 서명).

 애플리케이션 및 배포 매니페스트 서명 및 어셈블리 서명은 둘 다 **서명** 페이지에서 수행되는 작업이지만 서로 다른 프로세스입니다.

 또한 매니페스트 서명 및 어셈블리 서명에 대한 키 파일 정보의 스토리지가 다릅니다. 매니페스트 서명의 경우 키 정보는 컴퓨터의 암호화 스토리지 데이터베이스 및 현재 사용자의 Windows 인증서 저장소에 저장됩니다. 어셈블리 서명의 경우 키 정보는 컴퓨터의 암호화 스토리지 데이터베이스에만 저장됩니다.

 이 **서명** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음 **프로젝트** 메뉴에서 **속성**을 클릭합니다. **프로젝트 디자이너** 가 나타나면 **서명** 탭을 클릭합니다.

## <a name="application-and-deployment-manifest-signing"></a>애플리케이션 및 배포 매니페스트 서명
 **ClickOnce 매니페스트 서명** 확인란을 선택 하면 공개/개인 키 쌍을 사용 하 여 응용 프로그램 및 배포 매니페스트에 서명할 수 있습니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 [방법: 애플리케이션 및 배포 매니페스트 서명](../../ide/how-to-sign-application-and-deployment-manifests.md)을 참조하세요.

 **저장소에서 선택** 단추를 사용 하 여 현재 사용자의 개인 인증서 저장소에서 기존 인증서를 선택할 수 있습니다. 이러한 인증서 중 하나를 선택하여 애플리케이션 및 배포 매니페스트에 서명할 수 있습니다.

 **저장소에서 선택**을 클릭하면 **인증서 선택** 대화 상자가 열리고 현재 유효하고(만료되지 않음) 프라이빗 키가 포함된 개인 인증서 저장소의 인증서가 나열됩니다. 선택한 인증서의 목적에는 코드 서명이 포함되어야 합니다.

 **인증서 속성 보기**를 클릭하면 **인증서 세부 정보** 대화 상자가 나타납니다. 이 대화 상자에는 인증서에 대한 세부 정보 및 추가 옵션이 포함됩니다. **인증서에 대한 자세한 정보**를 클릭하여 추가 도움말 정보를 볼 수 있습니다.

 **파일에서 선택** 단추를 사용 하 여 기존 키 파일의 인증서를 선택할 수 있습니다.

 **파일에서 선택**을 클릭하면 **파일 선택** 대화 상자가 열리고 여기에서 인증서 키(.pfx) 파일을 선택할 수 있습니다. 파일은 암호로 보호되어야 하고 개인 인증서 저장소에 없어야 합니다.

 **파일을 여는 데 필요한 암호 입력** 대화 상자에서 암호를 입력하여 인증서 키(.pfx) 파일을 엽니다. 암호 정보는 개인 키 컨테이너 목록 및 개인 인증서 저장소에 저장됩니다.

 **테스트 인증서 만들기** 단추를 사용 하 여 테스트용 인증서를 만들 수 있습니다. 테스트 인증서는 ClickOnce 애플리케이션 및 배포 매니페스트에 서명하는 데 사용됩니다.

 **테스트 인증서 만들기**를 클릭하면 **테스트 인증서 만들기** 대화 상자가 열리고 여기에서 테스트 인증서에 대한 강력한 이름 키 파일의 암호를 입력할 수 있습니다. 파일 이름은 *projectname*_TemporaryKey.pfx입니다. 암호를 입력하지 않고 **확인**을 클릭하면 .pfx 파일이 암호로 보호되지 않습니다.

 **타임 스탬프 서버 URL** 상자 시그니처의 타임 스탬프를 지정 하는 서버의 주소를 지정 합니다. 인증서를 제공할 때 이 외부 사이트는 애플리케이션이 서명된 시간을 확인합니다.

## <a name="assembly-signing"></a>어셈블리 서명
 **어셈블리 서명** 확인란 어셈블리에 서명 하 고 강력한 이름의 키 파일을 만들려면이 확인란을 선택 합니다. **프로젝트 디자이너**를 사용하여 어셈블리에 서명하는 방법에 대한 자세한 내용은 [방법: 어셈블리 서명(Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564)을 참조하세요.

 이 옵션은 [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]에서 제공된 Al.exe 도구를 사용하여 어셈블리에 서명합니다. Al.exe에 대한 자세한 내용은 [방법: 강력한 이름으로 어셈블리 서명](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)을 참조하세요.

 **강력한 이름 키 파일 목록 선택** 을 사용 하 여 어셈블리에 서명 하는 데 사용 되는 새로운 또는 기존의 강력한 이름의 키 파일을 지정할 수 있습니다. **\<Browse...>** 를 선택하여 기존 키 파일을 선택합니다.

 **\<New...>** 를 선택하여 어셈블리 서명에 사용할 새 키 파일을 만듭니다. **강력한 이름 키 만들기** 대화 상자가 나타나고 이를 사용하여 키 파일 이름을 지정하고 암호로 키 파일을 보호할 수 있습니다. 암호 길이는 6자 이상이어야 합니다. 암호를 지정할 경우 개인 정보 교환(.pfx) 파일이 만들어집니다. 암호를 지정하지 않으면 강력한 이름 키(.snk) 파일이 만들어집니다.

 **암호 변경** 단추 어셈블리에 서명 하는 데 사용 되는 개인 정보 교환 (.pfx) 키 파일의 암호를 변경 합니다.

 **암호 변경**을 클릭하면 **키 암호 변경** 대화 상자가 열립니다. 이 대화 상자에서 **이전 암호**는 키 파일의 현재 암호입니다. **새 암호**의 길이는 6자 이상이어야 합니다. 암호 정보는 현재 사용자의 Windows 인증서 저장소에 저장됩니다.

 **서명 연기** 확인란을 선택 하 여 서명 연기를 사용 하도록 설정 합니다.

 지연 서명된 프로젝트가 실행되지 않고 디버그될 수 없습니다. 그러나 [Sn.exe(강력한 이름 도구)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)를 `-Vr` 옵션과 함께 사용하여 개발 중에 확인을 건너뛸 수 있습니다.

> [!NOTE]
> 어셈블리에 서명할 때 항상 프라이빗 키에 액세스할 수 있는 것은 아닙니다. 예를 들어 조직에 개발자가 일상적으로 액세스할 수 없는 엄격하게 보호된 키 쌍이 있을 수 있습니다. 퍼블릭 키를 사용할 수 있지만 프라이빗 키에 대한 액세스는 몇몇 개인으로 제한됩니다. 이 경우 *지연* 또는 *일부 서명*을 통해 퍼블릭 키를 제공하여 어셈블리가 전달될 때까지 프라이빗 키 추가를 연기할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [프로젝트 속성 참조](../../ide/reference/project-properties-reference.md) [어셈블리 및 매니페스트 서명](../../ide/managing-assembly-and-manifest-signing.md) 관리 [응용 프로그램에 대 한 강력한 이름 서명](https://msdn.microsoft.com/5fef3490-c519-4363-94fd-8b1ad260dab5) [방법: 응용 프로그램 및 배포 매니페스트 서명](../../ide/how-to-sign-application-and-deployment-manifests.md) [방법: 어셈블리 서명 (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564) [방법: 강력한 이름의 어셈블리를 사용 하 여 어셈블리 서명](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Strong-Named Assemblies](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)
