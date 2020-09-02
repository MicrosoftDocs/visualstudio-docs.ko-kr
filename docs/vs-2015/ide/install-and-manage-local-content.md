---
title: 로컬 콘텐츠 설치 및 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer 2.0]
- updating local content [Help Viewer 2.0]
- Help Viewer 2.0, content installation source
- Help Viewer 2.0, updating local content
- Help Viewer 2.0, changing content installation source
- installing local content [Help Viewer 2.0]
- content installation source [Help Viewer 2.0]
- downloading content [Help Viewer 2.0]
- removing local content [Help Viewer 2.0]
- Help Viewer 2.0, removing local content
- Help Viewer 2.0, installing local content
- Help Viewer 2.0, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 569254c9df668c7755116f37a819fe65a3ecaa59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670468"
---
# <a name="install-and-manage-local-content"></a>로컬 콘텐츠 설치 및 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft 도움말 뷰어를 사용하여 소프트웨어 개발 요구 사항에 따라 컴퓨터에 설치된 도움말 콘텐츠를 추가, 제거, 업데이트 및 이동할 수 있습니다.

 로컬 컴퓨터에서 콘텐츠를 관리하려면 관리 권한이 있는 계정으로 로그온해야 합니다. 또한 엔터프라이즈 환경에서 작업하는 경우에는 로컬 콘텐츠를 관리하지 못할 수도 있습니다. 시스템 관리자가 조직을 위해 해당 결정을 내릴 수도 있기 때문입니다. 자세한 내용은 [도움말 뷰어 관리자 가이드](../ide/help-viewer-administrator-guide.md)를 참조 하세요.

## <a name="changing-the-content-installation-source"></a>콘텐츠 설치 소스 변경
 기본적으로 도움말 뷰어는 Microsoft 온라인 서비스를 소스로 사용하여 콘텐츠를 설치합니다. 시스템 관리자가 다른 위치에 이미 콘텐츠를 설치한 엔터프라이즈 환경에서 작업하지 않는 한 일반적으로 콘텐츠 소스를 변경하지 않아야 합니다.

#### <a name="to-change-the-content-installation-source"></a>콘텐츠 설치 소스를 변경하려면

1. **콘텐츠 관리** 탭에서 **디스크** 옵션 단추를 선택합니다.

    > [!NOTE]
    > **디스크** 옵션은 관리자가 콘텐츠 설치 소스를 수정하지 못하게 한 경우 사용할 수 없습니다. 자세한 내용은 [도움말 뷰어 관리자 가이드](../ide/help-viewer-administrator-guide.md)를 참조 하세요.

2. 다음 단계 중 하나를 수행합니다.

    - .msha 파일의 경로 또는 서비스 엔드포인트의 URL을 입력합니다.

    - 찾아보기(**...**) 단추를 선택하여 .msha 파일로 이동합니다.

    - 목록에서 가장 최근에 사용된 항목을 선택합니다.

## <a name="download-and-install-content-locally"></a>로컬로 콘텐츠 다운로드 및 설치
 로컬 컴퓨터에 콘텐츠를 다운로드하고 설치하는 경우 인터넷에 연결하지 않고 항목을 볼 수 있습니다.

> [!IMPORTANT]
> 콘텐츠를 설치하려면 관리 권한이 있는 계정으로 로그온해야 합니다.

 Visual Studio IDE가 영어 이외의 언어로 설정된 경우 영어 콘텐츠나 지역화된 콘텐츠 중 하나나 둘 모두를 설치할 수 있습니다. 그러나 영어 버전만 설치하고 **뷰어 옵션** 대화 상자에서 **모든 탐색 탭과 F1 요청에 영어 콘텐츠 포함** 확인란의 선택을 취소한 경우 콘텐츠가 나타나지 않습니다.

#### <a name="to-download-and-install-content"></a>콘텐츠를 다운로드하고 설치하려면

1. **콘텐츠 관리** 탭을 선택합니다.

2. 콘텐츠 목록에서 다운로드하고 설치하려는 책 옆의 **추가** 링크를 선택합니다.

     책이 **보류 중인 변경 내용** 목록에 추가되고 지정한 책의 예상 크기가 해당 목록 아래에 나타납니다. 일부 책이 항목을 공유하기 때문에 여러 책의 총 다운로드 크기는 지정한 각 책의 크기를 모두 더한 결과보다 작을 수도 있습니다.

3. **업데이트** 단추를 선택합니다.

     지정한 책이 컴퓨터에 이미 있는 책의 업데이트와 함께 설치됩니다. 설치 시간은 각기 다르지만 상태 표시줄에서 진행률을 볼 수 있습니다.

## <a name="removing-local-content"></a>로컬 콘텐츠 제거
 원하지 않는 콘텐츠를 컴퓨터에서 제거하여 디스크 공간을 절약할 수 있습니다.

> [!IMPORTANT]
> 콘텐츠를 제거하려면 관리 권한이 있어야 합니다.

 Visual Studio IDE가 영어 이외의 언어로 설정되어 있고 **뷰어 옵션** 대화 상자에서 **모든 탐색 탭과 F1 요청에 영어 콘텐츠 포함** 확인란의 선택이 취소된 경우 지역화된 콘텐츠를 제거하면 콘텐츠가 표시되지 않습니다.

#### <a name="to-remove-content"></a>콘텐츠를 제거하려면

1. **콘텐츠 관리** 탭을 선택합니다.

2. 콘텐츠 목록에서 제거하려는 책 옆의 **제거** 링크를 선택합니다.

     책이 **보류 중인 변경 내용** 목록에 추가됩니다.

3. **업데이트** 단추를 선택합니다.

     지정한 책이 컴퓨터에서 제거됩니다.

## <a name="updating-local-content"></a>로컬 콘텐츠 업데이트
 설치된 콘텐츠의 업데이트를 사용할 수 있을 때 상태 표시줄에 알림이 표시됩니다.

> [!IMPORTANT]
> 도움말 뷰어에서 온라인 업데이트를 자동으로 확인하도록 하려면 **뷰어 옵션** 대화 상자를 연 다음, **온라인으로 콘텐츠 업데이트 확인** 확인란을 선택해야 합니다.

#### <a name="to-update-local-content"></a>로컬 콘텐츠를 업데이트하려면

- 상태 표시줄의 오른쪽 아래에서 **지금 다운로드하려면 여기를 클릭하세요.** 링크를 선택합니다.

  업데이트 시간은 각기 다를 수 있지만 상태 표시줄에서 업데이트 진행률을 볼 수 있습니다.

## <a name="moving-local-content"></a>로컬 콘텐츠 이동
 설치된 콘텐츠를 로컬 컴퓨터에서 네트워크 공유나 로컬 컴퓨터의 다른 파티션으로 이동하여 디스크 공간을 절약할 수 있습니다.

> [!IMPORTANT]
> 콘텐츠를 이동하려면 관리 권한이 있는 계정으로 로그온해야 합니다.

#### <a name="to-move-local-content"></a>로컬 콘텐츠를 이동하려면

1. **콘텐츠 관리** 탭의 **로컬 저장소 경로**에서 **이동** 단추를 선택합니다.

     **콘텐츠 이동** 대화 상자가 열립니다.

2. **대상** 텍스트 상자에 콘텐츠의 다른 위치를 입력한 다음 **확인** 단추를 선택합니다.

3. 콘텐츠가 이동되면 **닫기** 단추를 선택합니다.

## <a name="see-also"></a>관련 항목
 [Microsoft 도움말 뷰어](../ide/microsoft-help-viewer.md)
