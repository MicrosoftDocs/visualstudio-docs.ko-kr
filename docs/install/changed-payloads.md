---
title: 릴리스 후 패키지 페이로드가 변경되는 경우
description: 레이아웃을 만들 때 릴리스가 이미 배송된 후 패키지 페이로드가 변경되었는지 확인하는 방법을 알아봅니다.
ms.date: 05/22/2019
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: dec1478314e752ddace8fae822747e7c8e328b70
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114579"
---
# <a name="package-payload-changes"></a>패키지 페이로드 변경 내용

일부 패키지 페이로드는 릴리스가 이미 배송된 후에 변경될 변경될 수 있습니다. 사용자 또는 다른 사람이 레이아웃을 만들 때 레이아웃이 생성된 시점에 따라 이 동작이 다른 레이아웃 콘텐츠가 될 수 있습니다.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>레이아웃이 패키지 페이로드 변경 내용을 포함하고 있는지 확인

이전에 만든 레이아웃이 릴리스 배송 후 수정된 패키지 페이로드를 획득했는지 확인하는 방법은 다음과 같습니다.

1. 설치 로그를 엽니다. 로그는 일반적으로 `%TEMP%\dd_setup_[date].log`에 있습니다. 여기서 `[date]`는 레이아웃 작업이 시작된 `yyyyMMddHHmmss` 형식의 날짜입니다.

2. 다음 텍스트와 같이 구조화된 로그에서 줄을 찾습니다.

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. 그런 다음 [경로]에 대한 다운로드가 성공했는지 여부를 나타내는 로그의 뒷부분에 나오는 줄을 확인합니다. 다음 텍스트와 비슷합니다.

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>참고 항목

* [Visual Studio의 네트워크 설치 만들기](create-a-network-installation-of-visual-studio.md)
* [Visual Studio의 네트워크 기반 설치 업데이트](update-a-network-installation-of-visual-studio.md)
