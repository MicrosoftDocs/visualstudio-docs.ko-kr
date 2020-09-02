---
title: 프로젝트 계층 구조 노드 이름 바꾸기 (c + +) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686581"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>프로젝트 계층 구조 노드 이름 바꾸기(C++)
관리 되지 않는 c + + 용 HierUtil7 프로젝트 프레임 워크를 사용 하 여 프로젝트 폴더 계층 노드의 이름을 바꿀 수 있습니다. 자세한 내용은 [HierUtil7 샘플](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11)을 참조 하세요.  
  
## <a name="expanding-the-hierarchy-node"></a>계층 노드 확장  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>계층 노드를 확장 하 고 폴더 이름을 바꾸려면  
  
1. 다음 방법을 사용 하 여 계층 노드를 선택 합니다.  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` 는 폴더에 해당 하는 계층 컨테이너 이며 `EXPF_SelectItem` <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> 열거형에 있습니다. 는 `GUID_MacroExplorer` Vsshell. idl에 정의 된 GUID 상수 이며 `rguidPersistenceSlot` `ExtExpand` , Hu_node에 정의 된의 함수 시그니처에 대 한 예제입니다.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Hu_node 파일은 파일 \ 사용자 _ _ \ EnvSDK\common\hierutil7에서 찾을 수 있습니다. \<installation root>  
  
2. 다음을 사용 하 여 이름 바꾸기 명령을 게시 하 여 폴더 이름을 바꿉니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` 는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 포인터 `<IVsUIShell>``srpVsUIShell` 입니다. `guiVSStd97` 는 명령이 속한 명령 그룹의 고유 식별자 이며 `cmdidRename` , Vsshlids .h에 정의 되어 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 형식 만들기](../extensibility/internals/creating-project-types.md)   
 [VSSDK 샘플](../misc/vssdk-samples.md)