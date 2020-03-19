---
title: 프로젝트 디자이너, 보안 페이지
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1834713ad114ab8a86e314bbe052f4873b308956
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593579"
---
# <a name="security-page-project-designer"></a>프로젝트 디자이너, 보안 페이지

**프로젝트 디자이너**의 **보안** 페이지는 ClickOnce 배포를 사용하여 배포된 애플리케이션에 대한 코드 액세스 보안 설정을 구성하는 데 사용됩니다. 자세한 내용은 [ClickOnce 애플리케이션의 코드 액세스 보안](../../deployment/code-access-security-for-clickonce-applications.md)을 참조하세요.

이 **보안** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 클릭한 다음 **프로젝트** 메뉴에서 **속성**을 클릭합니다. **프로젝트 디자이너**가 나타나면 **보안** 탭을 클릭합니다.

## <a name="security-settings"></a>보안 설정

 **ClickOnce 보안 설정 사용**

디자인 타임 시 보안 설정을 사용할지를 결정합니다. 이 옵션의 선택을 취소하면 **보안** 페이지의 다른 모든 옵션을 사용할 수 없습니다.

> [!NOTE]
> **게시** 마법사를 사용하여 애플리케이션을 게시하면 이 옵션은 자동으로 사용됩니다.

이 옵션을 선택하면 **완전 신뢰 애플리케이션** 또는 **부분 신뢰 애플리케이션**이라는 두 개의 라디오 단추 중 하나를 선택합니다.

WPF 웹 브라우저 애플리케이션 프로젝트의 경우 이 옵션이 기본적으로 선택됩니다.

다른 모든 프로젝트 형식의 경우 이 옵션의 선택은 기본적으로 취소됩니다.

 **완전 신뢰 애플리케이션**

이 옵션을 선택하면 애플리케이션은 클라이언트 컴퓨터에서 설치되거나 실행될 때 완전 신뢰 권한을 요청합니다. 애플리케이션에 파일 시스템 및 레지스트리 등의 리소스에 대한 무제한 액세스를 부여하기 때문에 가능하면 완전 신뢰를 사용하지 않도록 합니다.

WPF 웹 브라우저 애플리케이션 프로젝트의 경우 이 옵션은 기본적으로 부분 신뢰로 설정됩니다.

다른 모든 프로젝트 형식의 경우 이 옵션의 선택은 기본적으로 완전 신뢰로 설정됩니다.

 **부분 신뢰 애플리케이션**

이 옵션을 선택하면 애플리케이션은 클라이언트 컴퓨터에서 설치되거나 실행될 때 부분 신뢰 권한을 요청합니다. *부분 신뢰*는 요청된 코드 액세스 보안 권한 하에서 허용된 작업만이 실행됨을 의미합니다. 보안 권한을 구성하는 방법에 대한 자세한 내용은 [ClickOnce 애플리케이션의 코드 액세스 보안](../../deployment/code-access-security-for-clickonce-applications.md)을 참조하세요.

**ClickOnce 보안 권한** 영역에서 옵션을 구성하여 부분 신뢰 보안 설정을 지정할 수 있습니다.

## <a name="clickonce-security-permissions"></a>ClickOnce 보안 권한

 **설치할 애플리케이션을 가져올 영역**

코드 액세스 보안 권한의 기본 집합을 지정합니다. 제한된 권한 집합에 **인터넷** 또는 **로컬 인트라넷**을 선택하거나 **(사용자 지정)** 을 선택하여 사용자 지정 권한 집합을 구성합니다. 애플리케이션이 영역에 부여된 것보다 많은 권한을 요청할 경우 추가 권한을 부여할 최종 사용자에게 ClickOnce 신뢰 프롬프트가 표시됩니다. 보안 권한을 구성하는 방법에 대한 자세한 내용은 [ClickOnce 애플리케이션의 코드 액세스 보안](../../deployment/code-access-security-for-clickonce-applications.md)을 참조하세요.

WPF 웹 브라우저 애플리케이션 프로젝트의 경우 이 옵션은 기본적으로 **인터넷**으로 설정됩니다.

 **권한 XML 편집**

애플리케이션 매니페스트 템플릿(app.manifest)을 열고 **(사용자 지정)** 권한 집합에 대한 권한을 구성합니다.

 **고급**

[고급 보안 설정 대화 상자](../../ide/reference/advanced-security-settings-dialog-box.md)를 열어 제한된 권한으로 애플리케이션을 디버깅하는 설정을 구성하는 데 사용합니다. 이 설정은 디버깅하는 동안 검사됩니다. 권한 예외는 애플리케이션에 영역에 정의된 것보다 많은 권한이 필요할 수 있음을 나타냅니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Security.Permissions.WebBrowserPermission>
- <xref:System.Security.Permissions.MediaPermission>
- [ClickOnce 애플리케이션의 코드 액세스 보안](../../deployment/code-access-security-for-clickonce-applications.md)
- [방법: ClickOnce 보안 설정 사용](../../deployment/how-to-enable-clickonce-security-settings.md)
- [방법: ClickOnce 애플리케이션의 보안 영역 설정](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [방법: ClickOnce 애플리케이션에 대한 사용자 지정 권한 설정](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [방법: 제한된 권한으로 ClickOnce 애플리케이션 디버그](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [ClickOnce 보안 및 배포](../../deployment/clickonce-security-and-deployment.md)
- [프로젝트 속성 참조](../../ide/reference/project-properties-reference.md)
- [고급 보안 설정 대화 상자](../../ide/reference/advanced-security-settings-dialog-box.md)
