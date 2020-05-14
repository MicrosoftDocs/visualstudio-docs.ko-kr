---
title: Updater에서 정보 검색 중에 오류가 발생했습니다.
description: ‘업데이트 정보를 검색하는 동안 오류가 발생했습니다.’라는 오류가 나타나는 경우 수정하는 방법에 대한 지침입니다. Mac용 Visual Studio 2017에서
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 8825BBAD-65C0-480F-9868-A01E64F28250
ms.openlocfilehash: 2ff0703171f5854baed2dd9be3767571a930bcb7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983489"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>문제 해결: Updater에서 정보 검색 중에 오류가 발생했습니다.

드문 경우지만, [Mac용 Visual Studio를 업데이트](update.md)하려고 할 때 “업데이트 정보를 검색하는 동안 오류가 발생했습니다.”라는 오류 메시지가 표시될 수 있습니다. 이 경우 다음 단계를 시도하여 수정하세요.

- 인터넷 연결을 확인합니다. 연결이 끊어지는 것이 이 오류의 가장 일반적인 원인입니다.
  - 구성 요소 다운로드에 실패하면 구성 요소 이름 옆에 있는 다시 시도 단추를 클릭하여 다시 다운로드를 시도할 수 있습니다.
- IDE를 다시 시작합니다.
- 이 오류 메시지가 계속 표시되면 **.dmg**가 여전히 머신에 있는 경우 Mac용 Visual Studio 2017 설치 관리자를 사용하여 업데이트를 시도할 수 있으며 [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%20for%20Mac)을 통해 다운로드할 수도 있습니다.
  - 설치 관리자는 머신에 설치되어 있는 구성 요소를 업데이트합니다.
  - 설치 관리자를 다시 실행하면 이전에 설치하지 않은 누락된 구성 요소도 설치할 수 있습니다.
