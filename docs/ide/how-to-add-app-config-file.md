---
title: 프로젝트에 app.config 파일을 추가하는 방법
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 48e6516b48b524c3da4d80bc5171608ac1aea03d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654257"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>방법: C# 프로젝트에 애플리케이션 구성 파일 추가

C# 프로젝트에 애플리케이션 구성 파일(*app.config* 파일)을 추가하면 공용 언어 런타임에서 어셈블리 파일을 찾고 로드하는 방법을 사용자 지정할 수 있습니다. 애플리케이션 구성 파일에 대한 자세한 내용은 [런타임에서 어셈블리를 찾는 방법(.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)을 참조하세요.

> [!NOTE]
> UWP 앱에는 *app.config* 파일이 없습니다.

프로젝트를 빌드할 때 개발 환경에서 자동으로 *app.config* 파일을 복사하고, 복사본의 파일 이름을 실행 파일과 일치하도록 변경한 다음, 복사본을 **bin** 디렉터리로 이동합니다.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>C# 프로젝트에 애플리케이션 구성 파일을 추가하려면

1. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

     **새 항목 추가** 대화 상자가 나타납니다.

1. **설치됨** > **Visual C# 항목**을 확장한 다음, **애플리케이션 구성 파일** 템플릿을 선택합니다.

1. **이름** 텍스트 상자에서 이름을 입력하고 **추가** 항목을 선택합니다.

     *app.config*라는 파일을 프로젝트에 추가합니다.

## <a name="see-also"></a>참고 항목

- [애플리케이션 설정 관리(.NET)](../ide/managing-application-settings-dotnet.md)
- [구성 파일 스키마(.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [앱 구성(.NET Framework)](/dotnet/framework/configure-apps/index)
