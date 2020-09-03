---
title: '방법: 애플리케이션 및 배포 매니페스트 서명 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
caps.latest.revision: 61
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7924201f4cf58e1066434707a8453b0fe1913bc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670727"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>방법: 애플리케이션 및 배포 매니페스트 서명
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce 배포를 사용하여 애플리케이션을 게시하려면 애플리케이션 및 배포 매니페스트가 퍼블릭/프라이빗 키 쌍으로 서명되고 Authenticode 기술로 서명되어야 합니다. Windows 인증서 저장소의 인증서 또는 키 파일을 사용하여 매니페스트에 서명할 수 있습니다.

 ClickOnce 배포에 대 한 자세한 내용은 [Clickonce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)를 참조 하세요.

 .exe 기반 애플리케이션의 경우 ClickOnce 매니페스트에 서명하는 것은 선택 사항입니다. 자세한 내용은 이 문서에서 "서명되지 않은 매니페스트 생성" 섹션을 참조하세요.

 키 파일 만들기에 대 한 자세한 내용은 [방법: 공개-개인 키 쌍 만들기](https://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)를 참조 하세요.

> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서는 .pfx 확장명을 가진 PFX(개인 정보 교환) 키 파일만 지원합니다. 그러나 프로젝트 속성의 **서명** 페이지에서 **저장소에서 선택**을 클릭하여 현재 사용자의 Windows 인증서 저장소에서 다른 형식의 인증서를 선택할 수 있습니다.

### <a name="to-sign-application-and-deployment-manifests-using-a-certificate"></a>인증서를 사용하여 애플리케이션 및 배포 매니페스트에 서명하려면

1. [프로젝트 속성] 창으로 이동합니다(**솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택하거나, **빠른 실행** 창에 **프로젝트 속성**을 입력하거나, **솔루션 탐색기** 창 내에서 ALT+ ENTER를 누름). **서명** 탭에서 **ClickOnce 매니페스트 서명** 확인란을 선택합니다.

2. **저장소에서 선택** 단추를 클릭합니다.

     **인증서 선택** 대화 상자가 나타나고 Windows 인증서 저장소의 콘텐츠가 표시됩니다.

    > [!TIP]
    > **인증서 속성을 보려면 여기를 클릭하십시오.** 를 클릭하면 **인증서 세부 정보** 대화 상자가 나타납니다. 이 대화 상자에는 인증서에 대한 세부 정보 및 추가 옵션이 포함됩니다. **인증서** 를 클릭 하 여 추가 도움말 정보를 볼 수 있습니다.

3. 매니페스트에 서명하는 데 사용할 인증서를 선택합니다.

4. 또한 **타임스탬프 서버 URL** 입력란에 타임스탬프 서버의 주소를 지정할 수 있습니다. 이 서버는 매니페스트가 서명되었을 때 지정한 타임스탬프를 제공합니다.

### <a name="to-sign-application-and-deployment-manifests-using-an-existing-key-file"></a>기존 키 파일을 사용하여 애플리케이션 및 배포 매니페스트에 서명하려면

1. **서명** 페이지에서 **ClickOnce 매니페스트 서명** 확인란을 선택합니다.

2. **파일에서 선택** 단추를 클릭합니다.

     **파일 선택** 대화 상자가 나타납니다.

3. **파일 선택 대화** 상자에서 사용 하려는 키 파일 (.pfx)의 위치를 찾은 다음 **열기**를 클릭 합니다.

    > [!NOTE]
    > 이 옵션은 .pfx 확장명을 가진 파일만 지원합니다. 다른 형식의 키 파일 또는 인증서가 있다면 이를 Windows 인증서 저장소에 저장하고 이전 절차에서 설명된 대로 인증서를 선택합니다. 선택된 인증서의 목적에는 코드 서명이 포함되어야 합니다.

     **파일을 여는 데 필요한 암호 입력** 대화 상자가 나타납니다. .pfx 파일이 이미 Windows 인증서 저장소에 저장되거나 암호로 보호되지 않는 경우에는 암호 입력 프롬프트가 표시되지 않습니다.

4. 암호를 입력하여 키 파일에 액세스하고 ENTER 키를 누릅니다.

### <a name="to-sign-application-and-deployment-manifests-using-a-test-certificate"></a>테스트 인증서를 사용하여 애플리케이션 및 배포 매니페스트에 서명하려면

1. **서명** 페이지에서 **ClickOnce 매니페스트 서명** 확인란을 선택합니다.

2. 테스트용으로 새 인증서를 만들려면 **테스트 인증서 만들기** 단추를 클릭합니다.

3. **테스트 인증서 만들기** 대화 상자에서 테스트 인증서를 보호하는 데 도움이 되는 암호를 입력합니다.

## <a name="generating-unsigned-manifests"></a>서명되지 않은 매니페스트 생성
 .exe 기반 애플리케이션의 경우 ClickOnce 매니페스트에 서명하는 것은 선택 사항입니다. 다음 절차에서는 서명되지 않은 ClickOnce 매니페스트를 생성하는 방법을 보여 줍니다.

> [!IMPORTANT]
> 서명되지 않은 매니페스트를 사용하여 애플리케이션의 개발과 테스트를 간소화할 수 있습니다. 그러나 서명되지 않은 매니페스트를 사용하면 프로덕션 환경에 상당한 보안 위험이 추가됩니다. ClickOnce 애플리케이션이 인터넷 또는 악성 코드의 기타 출처와 완전히 격리된 인트라넷 내의 컴퓨터에서 실행되는 경우에만 서명되지 않은 매니페스트를 사용하는 것이 좋습니다.

 기본적으로 ClickOnce는 하나 이상의 파일이 생성된 해시에서 특별히 제외되는 경우가 아니면 서명된 매니페스트를 자동으로 생성합니다. 즉, **ClickOnce 매니페스트 서명** 확인란이 선택 취소되더라도 모든 파일이 해시에 포함된 경우에는 애플리케이션을 게시하면 서명된 매니페스트가 생성됩니다.

#### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>서명되지 않은 매니페스트를 생성하고 생성된 해시에 모든 파일을 포함하려면

1. 해시에 모든 파일이 포함된 서명되지 않은 매니페스트를 생성하려면 먼저 애플리케이션을 서명된 매니페스트와 함께 게시해야 합니다. 따라서 이전 절차 중 하나를 수행하여 먼저 ClickOnce 매니페스트에 서명하고 애플리케이션을 게시합니다.

2. **서명** 페이지에서 **ClickOnce 매니페스트 서명** 확인란을 선택 취소합니다.

3. 하나의 애플리케이션 버전만 사용할 수 있도록 게시 버전을 다시 설정합니다. 기본적으로 Visual Studio에서는 애플리케이션을 게시할 때마다 게시 버전의 수정 버전을 증분합니다. 자세한 내용은 [방법: ClickOnce 게시 버전 설정](../deployment/how-to-set-the-clickonce-publish-version.md)을 참조 하세요.

4. 애플리케이션을 게시합니다.

#### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>서명되지 않은 매니페스트를 생성하고 생성된 해시에서 하나 이상의 파일을 제외하려면

1. **서명** 페이지에서 **ClickOnce 매니페스트 서명** 확인란을 선택 취소합니다.

2. **애플리케이션 파일** 대화 상자를 열고 생성된 해시에서 제외할 파일에 대해 **해시**를 **제외**로 설정합니다.

    > [!NOTE]
    > 해시에서 파일을 제외하면 ClickOnce는 매시페스트의 자동 서명을 사용하지 않도록 구성되므로 이전 절차의 설명처럼 서명된 매니페스트와 함께 먼저 게시할 필요가 없습니다.

3. 애플리케이션을 게시합니다.

## <a name="see-also"></a>관련 항목
 [강력한 이름의 어셈블리](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) [방법: 공개-개인 키 쌍 서명 만들기](https://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114) [페이지, 프로젝트 디자이너](../ide/reference/signing-page-project-designer.md) [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
