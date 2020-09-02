---
title: ClickOnce에서 응용 프로그램 업데이트를 수행 하는 방법 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9217558c68d47ef8f2bf34b10db16463ee76f857
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900026"
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce에서 애플리케이션 업데이트가 수행되는 방식
ClickOnce는 응용 프로그램의 배포 매니페스트에 지정 된 파일 버전 정보를 사용 하 여 응용 프로그램의 파일을 업데이트할지 여부를 결정 합니다. 업데이트가 시작 된 후 ClickOnce는 *파일 패치* 라는 기법을 사용 하 여 응용 프로그램 파일의 중복 다운로드를 방지 합니다.

## <a name="file-patching"></a>파일 패치
 응용 프로그램을 업데이트할 때 파일이 변경 되지 않은 경우 ClickOnce는 새 버전의 응용 프로그램에 대 한 모든 파일을 다운로드 하지 않습니다. 대신, 현재 응용 프로그램의 응용 프로그램 매니페스트에 지정 된 파일의 해시 서명을 새 버전에 대 한 매니페스트의 시그니처와 비교 합니다. 파일의 서명이 다른 경우 ClickOnce는 새 버전을 다운로드 합니다. 서명이 일치 하면 파일이 한 버전에서 다음 버전으로 변경 되지 않은 것입니다. 이 경우 ClickOnce는 기존 파일을 복사 하 여 새 버전의 응용 프로그램에서 사용 합니다. 이 방법을 사용 하면 한 개 또는 두 개의 파일만 변경 된 경우에도 ClickOnce에서 전체 응용 프로그램을 다시 다운로드 하지 않아도 됩니다.

 파일 패치는 및 메서드를 사용 하 여 요청 시 다운로드 되는 어셈블리에 대해서도 작동 <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> 합니다.

 Visual Studio를 사용 하 여 응용 프로그램을 컴파일하면 전체 프로젝트를 다시 빌드할 때마다 모든 파일에 대 한 새 해시 서명을 생성 합니다. 이 경우 일부 어셈블리만 변경 될 수 있지만 모든 어셈블리가 클라이언트에 다운로드 됩니다.

 데이터로 표시 되 고 데이터 디렉터리에 저장 된 파일에 대해서는 파일 패치가 적용 되지 않습니다. 이러한 파일은 항상 파일의 해시 서명과 관계 없이 다운로드 됩니다. 데이터 디렉터리에 대 한 자세한 내용은 [ClickOnce 응용 프로그램의 로컬 및 원격 데이터 액세스](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)
- [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)