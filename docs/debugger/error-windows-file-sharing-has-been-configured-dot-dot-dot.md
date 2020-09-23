---
title: Windows 파일 공유가 구성되었음... | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 17dbb1f3493ead985ac946331fdbff7933b6d604
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851673"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>오류: Windows 파일 공유가 구성되었음...
원격 컴퓨터에 다른 사용자 이름을 사용하여 연결하도록 Windows 파일 공유가 구성되었습니다. 이러한 구성은 원격 디버깅과 호환되지 않습니다.

 현재 파일 공유 구성은 다른 사용자 이름을 사용하여 원격 컴퓨터에 연결하도록 설정되어 있습니다. 이러한 상황에서는 원격으로 디버깅할 수 없습니다.

 이 오류를 해결하려면 다른 계정 이름을 사용하여 컴퓨터에 로그온하거나 디버깅할 때 사용하는 계정 이름을 사용하도록 파일 공유를 변경하십시오.

 이 사용자 이름을 사용하여 원격 컴퓨터에 연결하려면 먼저 원격 컴퓨터와의 연결을 끊어야 합니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 다른 계정 이름을 사용하여 로컬 컴퓨터 즉, 디버깅하고 있는 컴퓨터에 로그온합니다.

     또는

     을 선택합니다. 원격 컴퓨터와의 연결을 끊고 사용자의 계정 이름을 사용하여 다른 컴퓨터에 연결하도록 파일 공유를 다시 구성합니다.

    1. **시작** 메뉴에서 **보조 프로그램**을 가리킨 다음, **명령 프롬프트**를 클릭합니다.

    2. Windows 명령 프롬프트에 다음과 같이 입력합니다.

         `net use /delete computer_name`

    3. Windows 도움말에 문서화된 방법을 사용하여 파일 공유 설정을 변경합니다.