---
title: 도구 창 표시 구성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186390"
---
# <a name="tool-window-display-configuration"></a>도구 창 표시 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage가 도구 창을 등록 하면 기본 위치, 크기, 도킹 스타일 및 기타 표시 유형 정보가 선택적 값에 지정 됩니다. 도구 창 등록에 대 한 자세한 내용은 [레지스트리의 도구 창](../extensibility/tool-windows-in-the-registry.md) 을 참조 하세요.  
  
## <a name="window-display-information"></a>창 표시 정보  
 도구 창의 기본 표시 구성은 최대 6 개의 선택적 값에 저장 됩니다.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Name|형식|데이터|Description|  
|----------|----------|----------|-----------------|  
|Name|REG_SZ|"짧은 이름 이동"|도구 창을 설명 하는 짧은 이름입니다. 레지스트리의 참조에만 사용 됩니다.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|쉼표로 구분 된 네 개의 값입니다. X1, Y1은 도구 창의 왼쪽 위 모퉁이에 대 한 좌표입니다. X2, Y2는 오른쪽 아래 모퉁이의 좌표입니다. 모든 값은 화면 좌표에 있습니다.|  
|스타일|REG_SZ|M<br /><br /> F<br /><br /> #B0<br /><br /> 탭<br /><br /> "AlwaysFloat"|도구 창의 초기 표시 상태를 지정 하는 키워드입니다.<br /><br /> "MDI" = MDI 창에 도킹 되었습니다.<br /><br /> "Float" = 부동 소수점입니다.<br /><br /> "연결 됨" = 다른 창 (창 항목에 지정 됨)과 연결 되어 있습니다.<br /><br /> "탭" = 다른 도구 창과 결합 되었습니다.<br /><br /> "AlwaysFloat" =를 고정할 수 없습니다.<br /><br /> 자세한 내용은 아래의 설명 섹션을 참조 하세요.|  
|시간 범위|REG_SZ|*\<GUID>*|도구 창을 연결 하거나 탭 할 수 있는 창의 GUID입니다. GUID는 사용자 고유의 창이 나 IDE의 창 중 하나에 속할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|방향|REG_SZ|비어<br /><br /> 오른쪽<br /><br /> 왼쪽<br /><br /> 하위별|아래의 설명 섹션을 참조 하세요.|  
|DontForceCreate|REG_DWORD|0 또는 1|이 항목이 있고 해당 값이 0이 아니면 창이 로드 되지만 즉시 표시 되지 않습니다.|  
  
### <a name="comments"></a>의견  
 방향 항목은 제목 표시줄을 두 번 클릭할 때 도구 창이 도킹 하는 위치를 정의 합니다. 위치는 창 항목에 지정 된 기간을 기준으로 합니다. 스타일 항목이 "연결 됨"으로 설정 된 경우 방향 항목은 "왼쪽", "오른쪽", "위쪽" 또는 "아래쪽"이 될 수 있습니다. 스타일 항목이 "탭" 인 경우 방향 항목은 "왼쪽" 또는 "오른쪽" 일 수 있으며 탭이 추가 되는 위치를 지정 합니다. 스타일 항목이 "Float" 이면 도구 창이 먼저 배치 됩니다. 제목 표시줄을 두 번 클릭 하면 방향 및 창 항목이 적용 되 고 창에는 "탭" 스타일이 사용 됩니다. 스타일 항목이 "AlwaysFloat" 인 경우 도구 창을 도킹할 수 없습니다. 스타일 항목이 "MDI" 인 경우 도구 창은 MDI 영역에 연결 되 고 창 항목은 무시 됩니다.  
  
### <a name="example"></a>예  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>도구 창 표시 유형  
 선택적인 표시 하위 키의 값에 따라 도구 창의 표시 유형 설정이 결정 됩니다. 값의 이름은 창의 표시 유형이 필요한 명령의 Guid를 저장 하는 데 사용 됩니다. 명령이 실행 되는 경우 IDE는 도구 창이 만들어지고 표시 되도록 합니다.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Name|형식|데이터|Description|  
|----------|----------|----------|-----------------|  
|(기본값)|REG_SZ|없음|비워 둡니다.|  
|*\<GUID>*|REG_DWORD 또는 REG_SZ|0 또는 설명이 포함 된 문자열입니다.|선택 사항입니다. 항목의 이름은 표시 유형이 필요한 명령의 GUID 여야 합니다. 값은 정보 문자열을 포함 합니다. 일반적으로이 값은 `reg_dword` 0으로 설정 된입니다.|  
  
### <a name="example"></a>예제  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>참고 항목  
 [VSPackage Essentials](../misc/vspackage-essentials.md)
