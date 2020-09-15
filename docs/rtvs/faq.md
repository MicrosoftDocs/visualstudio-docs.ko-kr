---
title: Visual Studio용 R 도구 FAQ
description: Visual Studio의 R에 대한 질문과 대답
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8c89f1d59405fb7475e827cac9624c6623d7041e
ms.sourcegitcommit: 1d74273a50ede5a90d9d64372d93aad357daef42
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89365667"
---
# <a name="frequently-asked-questions"></a>질문과 대답

## <a name="visual-studio-support"></a>Visual Studio 지원

**질문: RTVS가 OS X 또는 Linux에서 작동하나요?**

A. 현재 RTVS는 Windows 전용 구현인 Visual Studio에서 구축되었습니다. Microsoft에서 Visual Studio 코드 및 Visual Studio for Mac에서의 지원을 연구 중입니다. [RTVS 문제 #1295](https://github.com/Microsoft/RTVS/issues/1295)를 참조하세요.

**질문: RTVS가 Visual Studio Express Edition에서 작동하나요?**

A. 아니요.

**질문: RTVS에서 Visual Studio 확장을 사용할 수 있나요?**

A. 물론 그렇습니다. 실제로 R을 사용하는 사용자들이 많이 사용하는 몇 가지 확장은 다음과 같습니다.

- [vim 키 바인딩을 위한 VsVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [실시간 미리 보기를 제공하는 Markdown 편집기](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

자세한 내용은 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)를 참조하세요.

**질문: RTVS가 Visual Studio에 있기 때문에, C#, C++ 및 다른 Microsoft 언어와 함께 R을 쉽게 사용할 수 있나요?**

A. 아니요. RTVS는 R 코드를 개발하기 위한 도구이며, 표준 네이티브 R 인터프리터를 사용합니다. R과 다른 언어 간의 상호 운용성은 현재 지원되지 않습니다.

**질문: RTVS는 영어가 아닌 로캘에서 작동하나요?**

A. RTVS 1.0 릴리스는 영어 전용입니다. 1.1 릴리스는 Visual Studio 자체가 사용하는 언어와 동일한 언어 집합으로 지역화될 예정입니다. 당분간은 [Visual Studio 2015용 언어 팩(영어)](https://www.microsoft.com/download/details.aspx?id=48157)을 사용하거나 Visual Studio 2017에서 설치 관리자를 실행하고 **언어 팩** 탭에서 영어를 선택합니다.

![Visual Studio 2017에 대한 국가별 설정](media/FAQ-international-settings.png)

**질문: 실제로 저는 현재 Visual Studio 설정을 좋아하지만 새 데이터 과학 설정을 사용해 보고 싶습니다. 어떻게 할까요?**

A. **도구** > **설정 가져오기 및 내보내기**를 사용하여 현재 Visual Studio 설정을 저장하고 데이터 과학 설정으로 전환합니다. 저장된 설정을 복원하려면 **설정 가져오기 및 내보내기** 명령을 다시 사용합니다.

**질문: 네트워크 공유에 내 Visual Studio 프로젝트를 저장할 수 있나요?**

A. 아니요, Visual Studio는 네트워크 공유에서 프로젝트 로드를 지원하지 않습니다.

## <a name="r-interpretersintegration"></a>R 인터프리터/통합

**질문: RTVS는 어떤 R 인터프리터에서 작동하나요?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R Client 및 Microsoft Machine Learning Server](/machine-learning-server/)

**질문: 이러한 인터프리터는 어디서 다운로드할 수 있나요?**

A. [설치](installing-r-tools-for-visual-studio.md)를 참조하세요.

Q **Microsoft R Server가 무엇인가요?**

A. R Server는 [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server)의 이전 이름입니다.

**질문: RTVS가 32비트 버전의 R에서 작동하나요?**

A. 아니요, RTVS는 64비트 버전의 Windows에서 실행되는 64비트 버전의 R만 지원합니다.

**질문: RTVS가 내 소스 제어 시스템에서 작동하나요?**

A. 예, Visual Studio에 통합된 모든 소스 제어 시스템을 사용할 수 있습니다.

**질문: RTVS 프로젝트에 대해 권장되는 *.gitignore* 설정은 무엇인가요?**

A. GitHub는 권장되는 *.gitignore* 파일의 리포지토리를 유지 관리합니다. 이 항목은 [R.gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)에서 볼 수 있습니다.

## <a name="remote-services"></a>원격 서비스

17. **Visual Studio의 원격 서비스가 무엇인가요?**

A. Visual Studio용 원격 R 서비스를 사용하면 Windows 또는 Linux 컴퓨터를 설정한 다음 RTVS에서 해당 컴퓨터에 연결할 수 있습니다. [원격 작업 영역 설정](setting-up-remote-r-workspaces.md)을 참조하세요.

17. **RTVS에서 Microsoft Machine Learning Server에 연결할 수 있나요?**

A. 아니요, Microsoft ML Server는 다른 기술이며 RTVS에서 요구하는 같은 연결 메커니즘을 제공하지 않습니다.

17. **RTVS가 Azure의 데이터 과학 VM 이미지를 사용하여 만든 VM에 연결할 수 있나요?**

A. 예. [데이터 과학 VM - Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) 이미지는 Visual Studio용 원격 R 서비스에 미리 설치되어 제공됩니다.

Q **RTVS가 R이 설치된 원격 컴퓨터에 연결할 수 있나요?**

원격 컴퓨터에서 R 코드를 실행하려면 요청을 수신하고, 코드를 받고, 결과를 다시 클라이언트 컴퓨터로 보내는 서비스가 있어야 합니다. 이것이 Visual Studio용 원격 R 서비스의 작업입니다. [원격 작업 영역 설정](setting-up-remote-r-workspaces.md)을 참조하세요.

17. **원격 세션이 무엇인가요?**

A. Machine Learning Server 문서의 [원격 서버에서 실행](/machine-learning-server/r/how-to-execute-code-remotely) 문서를 참조하세요.

## <a name="rtvs-development-and-features"></a>RTVS 개발 및 기능

**질문: 기능 X는 없지만 RStudio에 있습니다.**

A. RStudio는 수년 동안 개발되어 온 우수하며 완성된 R용 IDE입니다. RTVS는 성공적인 업무에 필요한 모든 핵심 기능을 유지하려고 합니다. [GitHub](https://github.com/Microsoft/RTVS/issues/)에 이슈를 제출하여 향후에 우선적으로 고려될 수 있도록 할 수 있습니다.

**질문: RTVS에 기고할 수 있나요?**

A. 그렇습니다. 소스 코드는 [Github](https://github.com/microsoft/RTVS)에 제공됩니다. 문제 추적기를 사용해서 버그와 이미 제출된 버그에 대한 설명을 제출하세요.

이 설명서에 기고하실 수도 있습니다. 페이지 오른쪽 위에 있는 **편집** 명령을 선택하기만 하면 됩니다. 문서에 대한 의견도 환영합니다. 이러한 의견은 페이지 아래쪽에서 추가할 수 있습니다.
