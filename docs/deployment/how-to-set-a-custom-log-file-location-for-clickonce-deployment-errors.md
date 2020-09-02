---
title: ClickOnce 배포 오류에 대 한 사용자 지정 로그 파일 위치 설정
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05ffd1cf32f8c7ea93e63232f7026c6c926f9308
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382174"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>방법: ClickOnce 배포 오류에 대한 사용자 지정 로그 파일 위치 설정
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 모든 배포에 대 한 활성화 로그 파일을 유지 관리 합니다. 이러한 로그는 배포 설치 및 초기화와 관련 된 모든 오류를 문서화 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다. 기본적으로는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 각 배포 활성화에 대해 하나의 로그 파일을 만듭니다. 이러한 로그 파일은 임시 인터넷 파일 폴더에 저장 됩니다. 활성화 오류가 발생 하 고 사용자가 결과 오류 대화 상자에서 **세부 정보** 를 클릭 하면 배포에 대 한 로그 파일이 사용자에 게 표시 됩니다.

 레지스트리 편집기 (**regedit.exe**)를 사용 하 여 사용자 지정 로그 파일 경로를 설정 하 여 특정 클라이언트에 대해이 동작을 변경할 수 있습니다. 이 경우는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 단일 파일에 모든 배포에 대 한 활성화 성공 및 실패를 기록 합니다.

> [!CAUTION]
> 레지스트리 편집기를 잘못 사용하면 심각한 문제가 발생하여 운영 체제를 다시 설치해야 할 수도 있습니다. 레지스트리 편집기를 사용할 때는 특별히 주의해야 합니다.

> [!NOTE]
> 너무 커지지 않도록 로그 파일을 가끔씩 자르거나 삭제 해야 합니다.

 다음 절차에서는 단일 클라이언트에 대 한 사용자 지정 로그 파일 위치를 설정 하는 방법을 설명 합니다.

### <a name="to-set-a-custom-log-file-location"></a>사용자 지정 로그 파일 위치를 설정 하려면

1. **Regedit.exe**를 엽니다.

2. 노드로 이동 `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` 합니다.

3. 문자열 값을 `LogFilePath` 원하는 사용자 지정 로그 위치의 전체 경로 및 파일 이름으로 설정 합니다.

     이 위치는 사용자에 게 쓰기 권한이 있는 디렉터리에 있어야 합니다. 예를 들어 Windows Vista에서 다음 폴더 구조를 만들고 `LogFilePath` 를 *C:\Users \\ \<username> \Documents\Logs\ClickOnce\installation.log*로 설정 합니다.

## <a name="see-also"></a>참조
- [ClickOnce 배포 문제 해결](../deployment/troubleshooting-clickonce-deployments.md)