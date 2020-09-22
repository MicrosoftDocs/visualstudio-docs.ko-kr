---
title: '방법: 만들기 기존에서 vsct 파일 Ctc 파일 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 7b963436e9d968dd5ba3829e97d0fd0c52e49641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841607"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>방법: 기존 .Ctc 파일에서 .Vsct 파일 만들기
기존 명령 테이블 .ctc 소스 파일에서 XML 기반 .vsct 파일을 만들 수 있습니다. 이렇게 하면 새 XML 기반 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 명령 테이블(VSCT) 컴파일러 형식을 이용할 수 있습니다.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>.ctc 파일에서 .vsct 파일을 만들려면  
  
1. Perl 언어의 복사본을 가져옵니다.  
  
2. 일반적으로 \VisualStudioIntegration\Tools\bin 폴더에 있는 Perl 스크립트 ConvertCTCToVSCT.pl 복사본을 가져옵니다 *\<Visual Studio SDK installation path>* .  
  
3. 변환하려는 .ctc 소스 파일의 복사본을 가져옵니다.  
  
4. 동일한 디렉터리에 파일을 배치합니다.  
  
5. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 명령 프롬프트 창에서 디렉터리로 이동합니다.  
  
6. 유형  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     여기서 PkgCmd.ctc는 .ctc 파일의 이름이고 PkgCmd.vsct는 만들려는 .vsct 파일의 이름입니다.  
  
     이 경우 새 .vsct XML 명령 테이블 소스 파일이 생성됩니다. VSCT 컴파일러인 Vsct.exe를 사용하여 다른 .vsct 파일처럼 파일을 컴파일할 수 있습니다.  
  
    > [!NOTE]
    > XML 주석의 형식을 다시 지정하여 .vsct 파일의 가독성을 향상시킬 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 만들기 Vsct 파일](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)