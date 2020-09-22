---
title: 배포 된 웹 응용 프로그램 디버깅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9608643801255d6c2cbf278cbfd96908f1f3911d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842238"
---
# <a name="debugging-deployed-web-applications"></a>배포된 웹 애플리케이션 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로덕션 서버에서 실행 중인 웹 애플리케이션을 디버깅해야 하는 경우에는 이 작업을 수행할 때 주의해야 합니다. 예를 들어 디버깅하기 위해 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 작업자 프로세스에 연결하여 중단점을 적중하는 경우 작업자 프로세스의 모든 관리 코드가 중단되어 서버의 모든 사용자에 대해 작업이 중지될 수 있습니다. 프로덕션 서버에서 디버깅하려면 프로덕션 작업에 미칠 수 있는 모든 영향을 고려해야 합니다.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 사용하여 배포된 애플리케이션을 디버깅하려면 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 작업자 프로세스에 연결하고 디버거에서 해당 애플리케이션에 대한 기호에 액세스할 수 있는지 확인해야 합니다. 또한 해당 애플리케이션의 소스 파일도 찾아서 열어야 합니다. 자세한 내용은 [기호 파일(.pdb) 및 소스 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [방법: ASP.NET 프로세스의 이름 찾기](../debugger/how-to-find-the-name-of-the-aspnet-process.md) 및 [시스템 요구 사항](../debugger/aspnet-debugging-system-requirements.md)을 참조하세요.  
  
> [!NOTE]
> 대부분의 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션에서는 비즈니스 논리나 다른 유용한 코드가 포함된 DLL을 참조합니다. 참조되는 이러한 DLL은 로컬 컴퓨터에서 해당 웹 애플리케이션의 가상 디렉터리에 있는 \bin 폴더로 자동 복사됩니다. 디버깅하는 경우 웹 애플리케이션이 로컬 컴퓨터에 있는 DLL 복사본이 아니라 가상 디렉터리에 있는 DLL 복사본을 참조한다는 점에 주의합니다.  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 작업자 프로세스에 연결하는 프로세스는 다른 모든 원격 프로세스에 연결하는 방법과 동일합니다. 연결된 상태에서 적절한 프로젝트가 열려 있지 않으면 애플리케이션이 중단될 때 대화 상자가 표시됩니다. 이 대화 상자에는 애플리케이션의 소스 파일 위치를 지정하라는 메시지가 표시됩니다. 대화 상자에서 지정한 파일 이름은 웹 서버에 있는 디버그 기호에 지정한 파일 이름과 일치해야 합니다. 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [ASP.NET 및 AJAX 응용 프로그램 디버깅](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [웹 응용 프로그램 및 스크립트 디버깅](../debugger/debugging-web-applications-and-script.md)   
 [방법: ASP.NET 응용 프로그램에 디버깅 사용](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [방법: ASP.NET 프로세스의 이름 찾기](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
