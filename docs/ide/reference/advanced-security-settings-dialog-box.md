---
title: 고급 보안 설정 대화 상자
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d34d1b16f36c90f4200a091050d1646fc563d33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419083"
---
# <a name="advanced-security-settings-dialog-box"></a>고급 보안 설정 대화 상자

이 대화 상자를 사용하면 영역 디버깅과 관련된 보안 설정을 지정할 수 있습니다.

![Visual Studio의 고급 보안 설정 대화 상자](../media/advanced-security-settings.png)

이 대화 상자에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음 **프로젝트** 메뉴에서 **속성**을 클릭합니다. **프로젝트 디자이너**가 나타나면 **보안** 탭을 클릭합니다. **보안** 페이지에서 **ClickOnce 보안 설정 사용**을 선택하고 **부분 신뢰 애플리케이션**을 클릭한 후 **고급**을 클릭합니다.

## <a name="uielement-list"></a>UI 요소 목록

**원본 사이트에 애플리케이션 액세스 허용**

이 확인란을 선택하면 애플리케이션은 게시된 웹 사이트 또는 서버 공유에 액세스할 수 있습니다. 기본적으로 이 옵션이 선택됩니다.

**다음 URL에서 다운로드한 것처럼 이 애플리케이션을 디버깅**

애플리케이션이 **게시** 페이지에 지정한 **설치 URL**에 해당하는 웹 사이트 또는 서버 공유에 액세스하도록 허용하려면 여기에 해당 URL을 입력합니다. 이 옵션은 **원본 사이트에 애플리케이션 액세스 허용**을 선택한 경우에만 사용 가능합니다.

## <a name="see-also"></a>참조

- [프로젝트 디자이너, 보안 페이지](../../ide/reference/security-page-project-designer.md)
