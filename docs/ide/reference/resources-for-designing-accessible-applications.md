---
title: 액세스 가능한 애플리케이션 설계를 위한 리소스
description: 장애가 있는 사용자가 더욱 쉽게 사용할 수 있도록 액세스 가능한 애플리케이션을 만드는 방법에 대해 알아봅니다.
ms.date: 08/27/2019
ms.topic: conceptual
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
helpviewer_keywords:
- accessibility, Windows applications
- Windows applications, accessibility
- Web applications, accessibility
- accessibility, Web applications
ms.assetid: 426bf023-bb34-43c4-9edb-c307191c8170
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49963df35aa5bebd126aa241fca6cb1712a0b111
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808996"
---
# <a name="resources-for-designing-accessible-applications"></a>액세스 가능한 애플리케이션 설계를 위한 리소스

액세스 가능한 설계를 지원하는 기술에 대해 자세히 알아보세요. 또한 액세스 가능한 Windows 앱 및 웹 사이트를 개발하는 데 도움이 되는 팁과 자습서 링크가 포함되어 있습니다.

>[!NOTE]
>모든 사용자에게 권한을 부여하는 제품 개발 방법에 대한 자세한 내용은 [Microsoft 접근성](https://www.microsoft.com/accessibility/)을 참조하세요.

## <a name="technologies"></a>기술

* **Microsoft Active Accessibility** 내게 필요한 옵션이 Microsoft Windows에서 실행되는 애플리케이션 작업을 도와주는 방식을 개선하는 COM 기반 기술입니다. 이 기능은 운영 체제 및 COM 인터페이스에 통합된 동적 연결 라이브러리를 제공합니다. 또한 사용자 인터페이스 요소에 대한 정보를 노출하기 위한 메서드를 제공하는 애플리케이션 프로그래밍 요소가 있습니다. 자세한 내용은 [Microsoft Active Accessibility](/windows/desktop/WinAuto/microsoft-active-accessibility)를 참조하세요.

* **Microsoft .NET Speech 기술** Microsoft.NET Speech SDK는 Microsoft [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] 컨트롤, Microsoft Internet Explorer Speech 추가 기능, 샘플 애플리케이션 및 설명서 집합을 제공합니다. 웹 개발자는 이러한 도구를 사용하여 음성 지원 [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] 애플리케이션을 만들고, 디버그하고, 배포할 수 있습니다. 이러한 도구는 개발자가 친숙한 개발 환경에서 작업할 수 있도록 Microsoft Visual Studio에 원활하게 통합되어 있습니다. 자세한 내용은 [Speech 서버](/previous-versions/office/developer/speech-technologies/ms950383\(v\=msdn.10\))를 참조하세요.

* **SAMI 1.0 이해** Microsoft SAMI(Synchronized Accessible Media Interchange) 기술을 사용하면 개발자가 PC 멀티미디어용 오디오 콘텐츠에 캡션을 추가할 수 있습니다. 자세한 내용은 [SAMI 1.0 이해](/previous-versions/windows/desktop/dnacc/understanding-sami-1.0)를 참조하세요.

## <a name="windows-applications"></a>Windows 애플리케이션

* **[연습: 내게 필요한 옵션이 지원되는 Windows 기반 애플리케이션 만들기](/dotnet/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application)** 이 문서에서는 샘플 Windows 애플리케이션에서 "Certified for Windows" 로고를 취득하기 위해 5가지 내게 필요한 옵션 요구 사항을 포함한 단계별 지침을 설명합니다.

* **키보드 사용자 인터페이스 설계 지침** 이 기술 문서에서는 사용자가 키보드에서 탐색할 수 있는 Windows 애플리케이션을 설계하는 방법을 설명합니다. 자세한 내용은 [키보드 사용자 인터페이스 디자인에 대한 지침](/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)을 참조하세요.

* **내게 필요한 옵션이 있는 콘솔** 이 기술 문서에서는 Windows XP에서 내게 필요한 옵션 보조 도구를 사용할 수 있도록 콘솔을 노출하는 데 사용되는 API와 이벤트에 대해 설명합니다. 자세한 내용은 [콘솔 내게 필요한 옵션](/previous-versions/windows/desktop/dnacc/console-accessibility)을 참조하세요.

## <a name="websites"></a>Websites

- [연습: 이미지 컨트롤, 메뉴 컨트롤 및 자동 포스트백을 사용하기 위한 내게 필요한 옵션 지침](/previous-versions/3has1x30(v=vs.140)) 이 문서에서는 샘플 웹 페이지에서 액세스 가능한 컨트롤을 포함하는 단계별 지침을 제공합니다. 또한 웹에서 일부 내게 필요한 옵션 디자인 팁을 제공합니다.

- **DHTML을 사용하여 내게 필요한 옵션이 있는 웹 페이지 만들기** 이 기술 문서에서는 내게 필요한 옵션을 지원하는 HTML 4.0 요소와 내게 필요한 옵션의 웹 설계 팁을 설명합니다. 자세한 내용은 [DHTML을 사용하여 액세스 가능한 웹 페이지 만들기](/previous-versions//ms528445(v=vs.85))를 참조하세요.

### <a name="third-party-resources"></a>타사 리소스

- **W3C(World Wide Web 컨소시엄)의 웹 콘텐츠에 대한 내게 필요한 옵션 지침** 이 웹 사이트에는 내게 필요한 옵션이 있는 웹 사이트 개발에 필요한 지침 및 기술이 있습니다. 자세한 내용은 [https://www.w3.org/WAI/GL/](https://www.w3.org/WAI/GL/)를 참조하세요.

## <a name="see-also"></a>참고 항목

* [Visual Studio의 접근성 기능](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Mac용 Visual Studio 접근성](/visualstudio/mac/accessibility/)