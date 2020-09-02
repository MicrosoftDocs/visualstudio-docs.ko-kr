---
title: 을 사용 하 여 격리 된 셸 수정 .Pkgundef 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538396"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>.Pkgundef 파일을 사용하여 격리 셸 수정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.Pkgundef 파일을 수정 하 여 격리 된 셸 응용 프로그램에서 지정 된 레지스트리 항목을 제외할 수 있습니다. 일반적으로 컴퓨터에서 응용 프로그램을 처음 시작 하는 경우 Visual Studio shell은 기존 Visual Studio 레지스트리 항목을 응용 프로그램의 루트 레지스트리 키에 복사 합니다. 여기에는 현재 설치 된 Vspackage에 대 한 참조가 포함 됩니다.  
  
 격리 된 셸 응용 프로그램에서 특정 레지스트리 항목을 제외 하려면 .pkgundef 파일에 항목을 추가 하 고 패키지 키를 추가 합니다. 키와 항목은 .pkgdef 파일에서와 같이 표시 됩니다. 즉, [$RootKey $] 또는 [$RootKey $ \\ *하위 키*] 및 "*entry*" =*value*로, 여기서 *subkey* 는 영향을 주는 하위 키입니다. *항목* 은 제거할 항목이 고, *value* 는 `""` 또는 `dword:00000000` 입니다.  
  
 레지스트리 키에서 여러 항목을 제외 하려면 키를 한 번 나열한 다음 제외할 각 항목에 대 한 줄을 표시 하면 됩니다.  
  
 격리 된 셸 응용 프로그램에서 전체 레지스트리 키를 제외 하려면 .pkgundef 파일에 키를 추가 하지만 해당 키에 대 한 레지스트리 항목을 지정 하지 않습니다.  
  
 .Pkgundef 파일에 주석을 추가할 수 있습니다. 한 줄로 된 주석에는 처음 두 문자로 두 개의 슬래시가 있어야 합니다.  
  
 예를 들어 **데이터베이스에 연결** 및 **도구** 메뉴에서 **r 명령을 제공 하기 위해 연결** 을 제거 하려면 줄의 주석 처리를 제거 하면 됩니다.  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 다음 줄을 추가 합니다.  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 응용 프로그램의 .pkgundef 파일입니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 기능의 패키지 Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [격리 셸 사용자 지정](../extensibility/customizing-the-isolated-shell.md)
