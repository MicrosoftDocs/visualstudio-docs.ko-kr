---
title: 레거시 언어 Service2를 등록 하는 중 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 07d70bb1d77dc3022b06c4036317e31692307f98
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188845"
---
# <a name="registering-a-legacy-language-service"></a>레거시 언어 서비스 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음 섹션에서는에서 사용할 수 있는 다양 한 언어 서비스 옵션에 대 한 레지스트리 항목 목록을 제공 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 다음 레지스트리 항목 목록에서 *VS Reg Root* 는 HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ *x. y*와 같습니다. 여기서 *X. y* 는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 버전 번호입니다.  
  
## <a name="registry-entries-for-language-service-options"></a>언어 서비스 옵션에 대 한 레지스트리 항목  
 *VS Reg Root*\Languages\Language Services \\ *언어 이름* 키에는 다음 값이 포함 될 수 있습니다.  
  
|Name|Type|범위|설명|  
|----------|----------|-----------|-----------------|  
|(기본값)|REG_SZ|*\<GUID>*|언어 서비스의 GUID입니다.|  
|LangResID|REG_DWORD|0x0-0xffff|언어의 지역화 된 텍스트 이름에 대 한 Resid로 (문자열 리소스 식별자)입니다.|  
|패키지|REG_SZ|*\<GUID>*|VSPackage의 GUID입니다.|  
|ShowCompletion|REG_DWORD|0-1|**옵션** 대화 상자의 **문 완성** 옵션을 사용할 수 있는지 여부를 지정 합니다.|  
|ShowSmartIndent|REG_DWORD|0-1|**옵션** 대화 상자에서 **스마트** 들여쓰기를 선택 하는 옵션이 설정 되어 있는지 여부를 지정 합니다.|  
|RequestStockColors|REG_DWORD|0-1|사용자 지정 또는 기본 색을 사용 하 여 키워드를 색으로 지정 하는지 여부를 지정 합니다.|  
|ShowHotURLs|REG_DWORD|0-1|사용자가 Url을 클릭할 수 있는지 여부를 지정 합니다.|  
|비 핫 Url의 기본값|REG_DWORD|0-1|**옵션** 대화 상자의 **단일 클릭 URL 탐색 사용** 옵션에 대 한 초기 설정을 지정 합니다.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|언어 서비스에 "공백 삽입"이 기본 탭 옵션으로 포함 되는지 여부를 지정 합니다.|  
|ShowDropdownBarOption|REG_DWORD|0-1|**탐색 모음**을 표시 하거나 숨기는 **옵션** 대화 상자에서 **탐색 모음** 옵션을 사용 하거나 사용 하지 않도록 설정 합니다.|  
|단일 코드 창만|REG_DWORD|0-1|언어 서비스의 **창** 메뉴에서 **새 창** 선택을 사용 하거나 사용 하지 않도록 설정 합니다.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|**고급 멤버 숨기기**에 대 한 **옵션** 대화 상자 설정을 사용 하거나 사용 하지 않도록 설정 합니다.|  
|지원 CF_HTML|REG_DWORD|0-1|편집기에서 HTML 데이터를 복사 하 고 붙여 넣을 수 있는지 여부를 지정 합니다.|  
|EnableLineNumbersOption|REG_DWORD|0-1|언어 서비스에 대해 **옵션** 대화 상자의 **줄 번호** 옵션을 사용할 수 있는지 여부를 지정 합니다.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|완성 목록에서 private 필드와 같은 고급 멤버를 숨길지 여부를 지정 합니다.|  
|ShowBraceCompletion|REG_DWORD|0-1|**옵션** 대화 상자의 **중괄호 완성** 옵션을 사용할 수 있는지 여부를 지정 합니다.|  
  
### <a name="example"></a>예  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## <a name="registry-entries-for-debugger-languages-options"></a>디버거 언어 옵션에 대 한 레지스트리 항목  
 *VS Reg Root*\Languages\Language Services \\ *언어 이름*\debugger 언어 \\ *GUID*\ 키에는 다음 값이 포함 될 수 있습니다.  
  
|Name|Type|범위|설명|  
|----------|----------|-----------|-----------------|  
|(기본값)|REG_SZ|text|기본값을 사용 하 여 언어 이름을 문서화할 수 있습니다. 이 키의 이름은 \AD7Metrics\Expression 계산기에서 해당 항목을 포함 하는 식 계산기의 GUID입니다 *\<VS Reg Root>* .|  
  
### <a name="example"></a>예  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## <a name="registry-entries-for-editor-tools-options"></a>편집기 도구 옵션에 대 한 레지스트리 항목  
 속성 페이지 및 속성 노드에 대 한 EditorToolsOptions 키 아래에 레지스트리 키를 추가할 수 있습니다. 이러한 키와 해당 값은 언어 서비스를 구성 하는 데 사용 되는 **옵션** 대화 상자 ( **도구** 메뉴)의 속성 페이지를 식별 합니다. 다음 예제에서 *페이지 이름* 은 속성 페이지의 이름이 고, *Node name* 은 **옵션** 대화 상자의 트리에 있는 노드의 이름입니다. 페이지 항목 및 노드 항목은 별도로 지정 해야 합니다.  
  
|Name|Type|범위|설명|  
|----------|----------|-----------|-----------------|  
|(기본값)|REG_SZ|Resid로|이 옵션 페이지의 지역화 된 표시 이름입니다. 이름은 리터럴 텍스트 또는 # 일 수 있습니다 `nnn` `nnn` . 여기서는 지정 된 VSPackage의 위성 DLL에 있는 문자열 리소스 ID입니다.|  
|패키지|REG_SZ|*GUID*|이 옵션 페이지를 구현 하는 VSPackage의 GUID입니다.|  
|페이지|REG_SZ|*GUID*|메서드를 호출 하 여 VSPackage에서 요청할 속성 페이지의 GUID입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> . 이 레지스트리 항목이 없는 경우 레지스트리 키는 페이지가 아닌 노드에 대해 설명 합니다.|  
  
### <a name="example"></a>예  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## <a name="registry-entries-for-file-name-extension-options"></a>파일 이름 확장명 옵션에 대 한 레지스트리 항목  
 파일 확장명에 대 한 항목에는 선행 마침표 (예: ".myext")가 포함 되어야 합니다.  
  
|Name|Type|범위|설명|  
|----------|----------|-----------|-----------------|  
|(기본값)|REG_SZ|*GUID*|이 파일 이름 확장명 형식에 대 한 기본 언어 서비스의 서비스 GUID입니다.|  
  
### <a name="example"></a>예  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>편집기 옵션에 대 한 레지스트리 항목  
 *VS Reg Root*\editors 키에는 다음 값이 포함 될 수 있습니다.  
  
|Name|Type|범위|설명|  
|----------|----------|-----------|-----------------|  
|(기본값)|REG_SZ|""|사용 되지 않는 설명서를 위해 여기에 이름을 입력할 수 있습니다.|  
|DefaultToolboxTab|REG_SZ|""|편집기가 활성화 되어 있을 때 기본값을 만드는 도구 상자 탭의 이름입니다.|  
|DisplayName|REG_SZ|Resid로|**연결 프로그램** 대화 상자에 표시할 이름입니다. 이름은 문자열 리소스 ID 또는 표준 형식의 이름입니다.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|**연결 프로그램** 메뉴 명령에 사용 됩니다. 특정 파일 형식에 대해 사용 가능한 편집기 목록에 기본 텍스트 편집기를 나열 하지 않으려면이 값을 1로 설정 합니다.|  
|LinkedEditorGUID|REG_SZ|*\<GUID>*|코드 페이지가 지원 되는 파일을 열 수 있는 모든 언어 서비스에 사용 됩니다. 예를 들어 **연결 프로그램** 명령을 사용 하 여 .txt 파일을 여는 경우 소스 코드 편집기를 사용 하거나 인코딩하지 않고 사용 하기 위한 옵션이 제공 됩니다.<br /><br /> 하위 키 이름에 지정 된 GUID는 codepage 편집기 팩터리에 대 한 것입니다. 이 특정 레지스트리 항목에 지정 된 연결 된 GUID는 일반 편집기 팩터리에 대 한 것입니다. 이 항목의 목적은 IDE가 기본 편집기를 사용 하 여 파일을 열지 않는 경우 IDE는 목록에서 다음 편집기를 사용 하려고 합니다. 이 편집기 팩터리는 기본적으로 실패 한 편집기 팩터리와 같기 때문에 다음 편집기는 codepage 편집기 팩터리가 아니어야 합니다.|  
|패키지|REG_SZ|*\<GUID>*|표시 이름의 Resid로에 대 한 VSPackage GUID입니다.|  
  
### <a name="example"></a>예  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## <a name="registry-entries-for-logical-view-options"></a>논리적 뷰 옵션에 대 한 레지스트리 항목  
 *VS Reg Root* \\ *\editors 편집기 GUI>* \logicalviews 키에는 다음 값이 포함 될 수 있습니다.  
  
|Name|Type|범위|설명|  
|----------|----------|-----------|-----------------|  
|(기본값)|REG_SZ||사용되지 않습니다.|  
|*\<GUID>*|REG_SZ|""|지원 되는 논리 뷰에 대 한 키입니다. 필요에 따라이 중 상당수를 사용할 수 있습니다. 레지스트리 항목의 이름은 값이 아니라 항상 빈 문자열인 경우에 중요 합니다.|  
  
### <a name="example"></a>예  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## <a name="registry-entries-for-editor-extension-options"></a>편집기 확장 옵션에 대 한 레지스트리 항목  
 *VS Reg Root* \\ *\Editors 편집기 GUID*\editors 키에는 다음 값이 포함 될 수 있습니다. 파일 이름 확장명에는 선행 기간이 포함 되지 않습니다.  
  
|Name|Type|범위|설명|  
|----------|----------|-----------|-----------------|  
|(기본값)|REG_SZ||사용되지 않습니다.|  
|*\<ext>*|REG_DWORD|0-0xffffffff|확장의 상대적 우선 순위입니다. 둘 이상의 언어가 동일한 확장을 공유 하는 경우 우선 순위가 높은 언어가 선택 됩니다.|  
  
 또한 편집기에 대 한 현재 사용자의 기본 선택은 HKEY_Current_User \Software\Microsoft\VisualStudio \\ *X\기본*편집기 \\ *ext*에 저장 됩니다. 선택한 언어 서비스의 GUID는 사용자 지정 항목에 있습니다. 이는 현재 사용자에 게 우선적으로 적용 됩니다.  
  
### <a name="example"></a>예  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>관리 되는 패키지 프레임 워크 언어 서비스 옵션에 대 한 레지스트리 항목  
 다음 레지스트리 항목은 MPF (관리 패키지 프레임 워크) 언어 서비스 클래스와 관련 되어 있습니다. 이러한 레지스트리 항목은 다양 한 IntelliSense 기능 및 기타 고급 편집 기능을 위한 언어 서비스의 지원을 표시 합니다.  
  
 이러한 레지스트리 항목은 클래스를 통해 액세스 됩니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  
  
|Name|Type|범위|설명|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|IntelliSense 작업 지원.|  
|MatchBraces|REG_DWORD|0-1|중괄호, 괄호, 대괄호 등의 언어 쌍 일치를 지원 합니다.|  
|QuickInfo|REG_DWORD|0-1|IntelliSense 요약 정보 작업을 지원 합니다.|  
|ShowMatchingBrace|REG_DWORD|0-1|상태 표시줄에 일치 하는 언어 쌍을 표시할 수 있도록 지원 합니다.|  
|MatchBracesAtCaret|REG_DWORD|0-1|일반적으로 두 요소를 강조 표시 하 여 일치 하는 언어 쌍 표시를 지원 합니다.|  
|MaxErrorMessages|REG_DWORD|0-n|**오류 목록** 창에 표시할 수 있는 최대 오류 수입니다.|  
|Codeasesedelay|REG_DWORD|0-n|IntelliSense 작업에 대 한 백그라운드 구문 분석을 시작 하기 전에 지연할 시간 (밀리초)입니다.|  
|EnableAsyncCompletion|REG_DWORD|0-1|백그라운드 구문 분석 지원.|  
|EnableCommenting|REG_DWORD|0-1|선택한 텍스트 블록을 주석으로 처리 하는 기능을 지원 하며, 선택한 텍스트 주석 처리에 대 한 지원도 제공 합니다.|  
|EnableFormatSelection|REG_DWORD|0-1|자동 들여쓰기 또는 중괄호 위치 조정과 같은 텍스트 서식 지정을 지원 합니다.|  
|자동 개요 표시|REG_DWORD|0-1|개요 (축소 가능 영역)를 지원 합니다.|  
|MaxRegions|REG_DWORD|0-n|파일당 최대 숨겨진 영역 수입니다.|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## <a name="see-also"></a>관련 항목  
 [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
