---
title: Updater에서 정보 검색 중에 오류가 발생했습니다.
description: ‘업데이트 정보를 검색하는 동안 오류가 발생했습니다.’라는 오류가 나타나는 경우 수정하는 방법에 대한 지침입니다. Mac용 Visual Studio 2019에서
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75405469"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>문제 해결: Updater에서 정보 검색 중에 오류가 발생했습니다.

드문 경우지만, [Mac용 Visual Studio를 업데이트](update.md)하려고 할 때 “업데이트 정보를 검색하는 동안 오류가 발생했습니다.”라는 오류 메시지가 표시될 수 있습니다. 이 경우 다음 단계를 시도하여 수정하세요.

- 인터넷 연결을 확인합니다. 연결이 끊어지는 것이 이 오류의 가장 일반적인 원인입니다.
  - 구성 요소 다운로드에 실패하면 구성 요소 이름 옆에 있는 다시 시도 단추를 클릭하여 다시 다운로드를 시도할 수 있습니다.
- IDE를 다시 시작합니다.
- 이 오류 메시지가 계속 표시되면 **.dmg**가 여전히 머신에 있는 경우 설치 관리자를 사용하여 업데이트를 시도할 수 있으며 [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)을 통해 다운로드할 수도 있습니다.
  - 설치 관리자는 머신에 설치되어 있는 구성 요소를 업데이트합니다.
  - 설치 관리자를 다시 실행하면 이전에 설치하지 않은 누락된 구성 요소도 설치할 수 있습니다.
- `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml`에 있는 파일을 삭제하여 캐시된 다운로드를 지울 수도 있습니다.
- 이전 버전의 Mac용 Visual Studio를 사용하는 경우 `VisualStudio` 디렉터리 아래에 다른 버전 번호가 있을 수 있습니다. 이러한 경로에서도 `index.xml` 파일을 삭제합니다.
