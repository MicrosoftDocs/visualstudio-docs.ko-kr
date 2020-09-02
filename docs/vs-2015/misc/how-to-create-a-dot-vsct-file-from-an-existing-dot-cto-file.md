---
title: '방법: 만들기 기존에서 vsct 파일 Cto 파일 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: 83608d768940158dcdab427a557577677e56f7c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822440"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>방법: 기존 .Cto 파일에서 .Vsct 파일 만들기
기존 이진 .cto 파일에서 XML 기반 .vsct 파일을 만들 수 있습니다. 이렇게 하면 새 명령 테이블 컴파일러 형식을 이용할 수 있습니다. 이 프로세스는 .ctc 파일에서 .cto 파일이 컴파일된 경우에도 작동합니다. .vsct 파일을 편집하여 다른 .cto 파일로 컴파일할 수 있습니다.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>.cto 파일에서 .vsct 파일을 만들려면  
  
1. .cto 파일 및 해당 .ctsym 파일의 복사본을 가져옵니다.  
  
2. vsct.exe 컴파일러와 같은 디렉터리에 파일을 배치합니다.  
  
3. Visual Studio 명령 프롬프트에서 .cto 및 .ctsym 파일이 들어 있는 디렉터리로 이동합니다.  
  
4. **vsct.exe** _ctofilename_**.cto** _vsctfilename_**.vsct -S**_symfilename_**.ctsym**를 입력합니다.  
  
     `ctofilename`은 .cto 파일의 이름이고, `vsctfilename`은 만들려는 vsct 파일의 이름이고, `symfilename`은 .ctsym 파일의 이름입니다.  
  
     이 프로세스는 새 .vsct XML 명령 테이블 컴파일러 파일을 만듭니다. vsct 컴파일러인 vsct.exe를 사용하여 다른 .vsct 파일처럼 파일을 편집 및 컴파일할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: 만들기 Vsct 파일](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)