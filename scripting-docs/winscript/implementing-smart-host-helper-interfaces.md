---
title: 스마트 호스트 도우미 인터페이스 구현 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: deac5827aa38039099f1d0f5e621d473db96743d
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835604"
---
# <a name="implementing-smart-host-helper-interfaces"></a>스마트 호스트 도우미 인터페이스 구현
[IDebugDocumentHelper 인터페이스](../winscript/reference/idebugdocumenthelper-interface.md)는 스마트 호스팅에 필요한 많은 인터페이스에 대한 구현을 제공하기 때문에 활성 디버깅을 위한 스마트 호스트를 만드는 작업을 크게 간소화합니다.  
  
 `IDebugDocumentHelper`를 사용하는 스마트 호스트가 되려면 호스트 애플리케이션에서 다음 세 가지 작업만 수행해야 합니다.  
  
1. 프로세스 디버그 관리자를 공동으로 만들고(`CoCreate`) [IProcessDebugManager 인터페이스](../winscript/reference/iprocessdebugmanager-interface.md)를 사용하여 디버깅 가능한 애플리케이션 목록에 애플리케이션을 추가합니다.  
  
2. [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) 메서드를 사용하여 각 스크립트 개체에 대한 디버그 문서 도우미를 만듭니다. 문서 이름, 부모 문서, 텍스트 및 스크립트 블록이 정의되어 있는지 확인합니다.  
  
3. [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) 인터페이스(액티브 스크립팅에 필요함)를 구현하는 개체에 [IActiveScriptSiteDebug 인터페이스](../winscript/reference/iactivescriptsitedebug-interface.md)를 구현합니다. `IActiveScriptSiteDebug` 인터페이스에서 유일한 특수 메서드는 간단히 도우미에 위임합니다.  
  
   필요에 따라 호스트는 구문 색, 문서 컨텍스트 만들기 및 기타 확장 기능에 대한 추가 제어가 필요한 경우 [IDebugDocumentHost 인터페이스](../winscript/reference/idebugdocumenthost-interface.md)를 구현할 수 있습니다.  
  
   스마트 호스트 도우미에 대한 주요 제한 사항은 문서가 확장될 수 있지만 추가된 후에 내용이 변경되거나 축소된 문서만 처리할 수 있다는 것입니다. 그러나 많은 스마트 호스트의 경우 제공되는 기능은 반드시 필요한 기능입니다.  
  
   다음 섹션에서는 각 단계에 대해 자세히 설명합니다.  
  
## <a name="create-an-application-object"></a>애플리케이션 개체 만들기  
 스마트 호스트 도우미를 사용하려면 먼저 디버거에서 애플리케이션을 나타내는 [IDebugApplication 인터페이스](../winscript/reference/idebugapplication-interface.md) 개체를 만들어야 합니다.  
  
#### <a name="to-create-an-application-object"></a>애플리케이션 개체를 만들려면  
  
1. `CoCreateInstance`를 사용하여 프로세스 디버그 관리자의 인스턴스를 만듭니다.  
  
2. [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md)을 호출합니다.  
  
3. [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md)을 사용하여 애플리케이션의 이름을 설정합니다.  
  
4. [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md)을 사용하여 애플리케이션 개체를 디버깅 가능한 애플리케이션 목록에 추가합니다.  
  
     아래 코드는 프로세스에 대해 간략히 설명하지만 오류 검사 또는 기타 강력한 프로그래밍 기법은 포함하지 않습니다.  
  
    ```cpp
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>IDebugDocumentHelper 사용  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>도우미를 사용하려면(일련의 최소 단계)  
  
1. 각 호스트 문서에 대해 [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)를 사용하여 도우미를 만듭니다.  
  
2. 도우미에서 [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md)를 호출하여 이름, 문서 특성 등을 제공합니다.  
  
3. 문서에 대한 부모 도우미가 있는 [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md)(문서가 루트인 경우 NULL)를 호출하여 트리에서 문서의 위치를 정의하고 디버거에서 해당 문서를 볼 수 있게 합니다.  
  
4. [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) 또는 [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md)를 호출하여 문서의 텍스트를 정의합니다. (브라우저와 마찬가지로 문서를 증분 방식으로 다운로드하는 경우 이러한 도우미를 여러 번 호출할 수 있습니다.)  
  
5. [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md)을 호출하여 각 스크립트 블록 및 관련된 스크립트 엔진에 대한 범위를 정의합니다.  
  
## <a name="implementing-iactivescriptsitedebug"></a>IActiveScriptSiteDebug 구현  
 [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)을 구현하려면 지정된 사이트에 해당하는 도우미를 가져온 다음 다음과 같이 지정된 원본 컨텍스트에 대한 시작 문서 오프셋을 가져옵니다.  
  
```cpp
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 그런 다음 도우미를 사용하여 지정된 문자 오프셋에 대한 새 문서 컨텍스트를 만듭니다.  
  
```cpp
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)를 구현하려면 `IDebugApplication::GetRootNode`([IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)에서 상속됨)를 호출하면 됩니다.  
  
 [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)를 구현하려면 프로세스 디버그 관리자를 사용하여 처음 만든 `IDebugApplication`을 반환하면 됩니다.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>선택적 IDebugDocumentHost 인터페이스  
 호스트는 도우미를 추가로 제어하기 위해 [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)를 사용하여 [IDebugDocumentHost 인터페이스](../winscript/reference/idebugdocumenthost-interface.md) 구현을 제공할 수 있습니다. 다음은 호스트 인터페이스를 사용하여 수행할 수 있는 몇 가지 주요 작업입니다.  
  
- 호스트에서 실제 문자를 즉시 제공할 필요가 없도록 [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md)를 사용하여 텍스트를 추가합니다. 문자가 실제로 필요하면 도우미는 호스트에서 [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md)를 호출합니다.  
  
- 도우미에서 제공하는 기본 구문 색 지정을 재정의합니다. 도우미는 [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md)를 호출하여 문자 범위에 대한 색 지정을 결정하고, 호스트에서 `E_NOTIMPL`을 반환하면 기본 구현으로 대체합니다.  
  
- [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)를 구현하여 도우미가 만든 문서 컨텍스트에 대해 알 수 없는 제어를 제공합니다. 이렇게 하면 호스트에서 기본 문서 컨텍스트 구현의 기능을 재정의할 수 있습니다.  
  
- 문서에 대한 파일 시스템에서 경로 이름을 제공합니다. 일부 디버깅 UI는 이를 사용하여 사용자가 문서의 변경 내용을 편집하고 저장할 수 있도록 합니다. 문서를 저장한 후 호스트에 알리기 위해 [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md)가 호출됩니다.  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버깅 개요](../winscript/active-script-debugging-overview.md)