---
title: Office 솔루션 배포
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24ec10c42935ac961218f910fbef98d51f5f5569
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79416512"
---
# <a name="deploy-an-office-solution"></a>Office 솔루션 배포
  ClickOnce 또는 Windows Installer를 사용하여 Office 솔루션을 배포할 수 있습니다. ClickOnce를 사용하면 솔루션의 배포 및 업데이트에 필요한 단계 수를 줄일 수 있습니다. Windows Installer를 사용하는 경우, 솔루션이 설치되는 방법과 사용자가 솔루션을 설치할 때 설치 프로그램에서 표시되는 페이지를 제어할 수 있습니다.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>ClickOnce를 사용 하 여 솔루션 배포
 ClickOnce를 사용하여 솔루션을 배포할 때는 사용자가 설치하고 실행할 수 있는 중앙 위치에 게시합니다. 새로운 설치 프로그램을 사용자에게 배포하지 않고도 솔루션을 업데이트할 수 있습니다.  이 배포 옵션은 더 간단하긴 하지만 사용자에게 사용자 지정 설치 페이지를 표시할 수 없습니다. 또한 둘 이상의 사용자가 있는 컴퓨터에는 솔루션을 여러 번 설치해야 합니다. [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)를 참조 하세요.

## <a name="deploy-a-solution-by-using-windows-installer"></a>Windows Installer를 사용 하 여 솔루션 배포
 Windows Installer를 사용하여 솔루션을 배포할 때는 설치 프로그램을 사용자에게 배포하면 사용자가 이 프로그램을 사용하여 솔루션을 설치합니다. 설치 프로그램을 사용하면 현재 사용자뿐 아니라 컴퓨터의 모든 사용자가 동시에 솔루션을 설치할 수 있습니다. 또한 솔루션을 설치할 때 사용자에게 표시되는 옵션을 좀 더 제어할 수 있습니다. 예를 들어, 사용권 계약을 표시할 수도 있고 사용자에게 솔루션의 특정 구성 요소 설치 권한을 줄 수도 있습니다. 그러나 솔루션을 업데이트하는 경우 새 설치 프로그램을 배포해야 합니다. [Windows Installer를 사용 하 여 Office 솔루션 배포](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Windows Installer를 사용 하 여 Office 솔루션 배포](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)
- [Office 솔루션 배포 문제 해결](../vsto/troubleshooting-office-solution-deployment.md)
