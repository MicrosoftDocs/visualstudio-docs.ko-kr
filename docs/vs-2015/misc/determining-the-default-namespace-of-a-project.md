---
title: 프로젝트의 기본 네임 스페이스 결정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705768"
---
# <a name="determining-the-default-namespace-of-a-project"></a>프로젝트의 기본 네임스페이스 확인
의 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 경우 `CustomToolNamespace` 입력 파일에 속성이 설정 되어 있으면 값이 `CustomToolNamespace` 메서드에 전달 된 기본 네임 스페이스 매개 변수의 값이 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> . 그렇지 않으면 `wszDefaultNamespace` 에 전달 된 매개 변수는 `Generate` 항상 루트 네임 스페이스와 같습니다. 네임 스페이스에 대 한 자세한 내용은 [네임 스페이스 키워드](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b)를 참조 하세요.  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 폴더 기반 네임 스페이스를 사용 합니다. 즉, 네임 스페이스는 루트 네임 스페이스와 사용자 지정 도구를 포함 하는 폴더의 이름으로 구성 됩니다. 각 폴더 이름은 유효한 식별자로 변환 되며 마침표는 모든 이름을 구분 합니다. 예를 들어 입력 파일을 FolderA\FolderB\FolderC\MyInput.txt 하 고 루트 네임 스페이스를 CL9 경우 계산 된 기본 네임 스페이스는 CL9가 됩니다 **. Folder.folderb.folderc**.  
  
 이 규칙의 예외는 계층 체인이 웹 참조 폴더를 포함 하는 경우에 발생 합니다. 예를 들면 다음과 같습니다.  
  
- FolderC는 웹 참조 폴더입니다. 네임 스페이스는 **CL9입니다. FolderC**.  
  
- FolderB는 웹 참조 폴더입니다. 네임 스페이스는 **CL9입니다. FolderB Folderb**.  
  
  즉, 네임 스페이스는 다음 형식을 사용 합니다.  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>관련 항목  
 [단일 파일 생성기 구현](../extensibility/internals/implementing-single-file-generators.md)   
 [단일 파일 생성기 등록](../extensibility/internals/registering-single-file-generators.md)   
 [비주얼 디자이너에 형식 노출](../extensibility/internals/exposing-types-to-visual-designers.md)