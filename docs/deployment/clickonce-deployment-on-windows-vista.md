---
title: Windows Vista의 ClickOnce 배포 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4beefddd429384fadda71d9742e8c0fac606c38e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900504"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista의 ClickOnce 배포

Windows Vista에서 UAC (사용자 계정 컨트롤)에 대해 Visual Studio에서 응용 프로그램을 빌드하면 일반적으로 응용 프로그램의 실행 파일에 이진 XML 데이터로 인코딩된 포함 된 매니페스트가 생성 됩니다.  ClickOnce 및 등록이 필요 없는 COM 응용 프로그램에는 외부 매니페스트가 필요 하기 때문에 Visual Studio에서 포함 된 매니페스트 대신 UAC 데이터를 포함 하는 이러한 프로젝트에 대 한 파일을 생성 합니다. ClickOnce 및 등록이 필요 없는 COM 배포의 경우 Visual Studio는 *응용 프로그램 매니페스트* 라는 파일의 정보를 사용 하 여 외부 UAC 매니페스트 정보를 생성 합니다. 다른 모든 경우에는 Visual Studio에서 응용 프로그램의 실행 파일에 UAC 데이터를 포함 합니다.

Visual Studio에서는 매니페스트 생성에 대해 다음과 같은 옵션을 제공 합니다.

- 포함 된 매니페스트를 사용 합니다. 응용 프로그램의 실행 파일에 UAC 데이터를 포함 하 고 일반 사용자로 실행 합니다.

   이는 기본 설정입니다 (ClickOnce를 사용 하지 않는 경우). 이 설정은를 사용 하 여 내부 및 외부 매니페스트를 생성 하는 방식으로 Windows Vista에서 Visual Studio가 작동 하는 일반적인 방법을 지원 `AsInvoker` 합니다.

- 외부 매니페스트를 사용 합니다. *응용 프로그램 매니페스트*를 사용 하 여 외부 매니페스트를 생성 합니다.

   이렇게 하면 *응용 프로그램 매니페스트의*정보를 사용 하 여 외부 매니페스트만 생성 됩니다. ClickOnce 또는 등록이 필요 없는 COM을 사용 하 여 응용 프로그램을 게시 하는 경우 Visual Studio는 프로젝트에 응용 프로그램 *매니페스트* 를 추가 하 고이 옵션을 추가 합니다.

- 매니페스트를 사용 하지 않습니다. 매니페스트 없이 응용 프로그램을 만듭니다.

   이 방법을 *가상화*라고도 합니다. 이전 버전의 Visual Studio에서 기존 응용 프로그램과의 호환성을 위해이 옵션을 사용 합니다.

  새 속성은 프로젝트 디자이너의 **응용 프로그램** 페이지 (Visual c # 프로젝트에만 해당) 및 MSBuild 프로젝트 파일 형식으로 사용할 수 있습니다.

  Visual Studio IDE에서 UAC 매니페스트 생성을 구성 하는 방법은 프로젝트 형식 (Visual c # 또는 Visual Basic)에 따라 달라 집니다.

  * 매니페스트 생성에 대 한 Visual c # 프로젝트 구성에 대 한 자세한 내용은 [응용 프로그램 페이지, 프로젝트 디자이너 (c #)](../ide/reference/application-page-project-designer-csharp.md)를 참조 하세요.

  * 매니페스트 생성에 대 한 Visual Basic 프로젝트를 구성 하는 방법에 대 한 자세한 내용은 [응용 프로그램 페이지, 프로젝트 디자이너 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [사용자 권한 및 Visual Studio](https://msdn.microsoft.com/library/d5c55084-1e7b-4b61-b478-137db01c0fc0)
- [프로젝트 디자이너, 애플리케이션 페이지(C#)](../ide/reference/application-page-project-designer-csharp.md)
- [프로젝트 디자이너, 애플리케이션 페이지(Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)