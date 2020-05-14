---
title: 레거시 언어 서비스 등록2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705883"
---
# <a name="registering-a-legacy-language-service"></a>레거시 언어 서비스 등록
다음 섹션에서는 에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]사용할 수 있는 다양한 언어 서비스 옵션에 대한 레지스트리 항목 목록을 제공합니다.

 다음 레지스트리 항목 목록에서 *VS Reg 루트는* \\ *x.Y가* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 버전 번호인 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y와*같습니다.

## <a name="registry-entries-for-language-service-options"></a>언어 서비스 옵션에 대한 레지스트리 항목
 *VS Reg 루트*\Languages\Language 서비스\\언어*이름* 키에는 다음 값이 포함될 수 있습니다.

|이름|Type|범위|설명|
|----------|----------|-----------|-----------------|
|(기본값)|REG_SZ|*\<지침>*|언어 서비스의 GUID.|
|랑그르시드|REG_DWORD|0x0-0xffff|언어의 지역화된 텍스트 이름에 대한 문자열 리소스 식별자(ResID)입니다.|
|패키지|REG_SZ|*\<지침>*|VS패키지의 GUID입니다.|
|쇼 완성|REG_DWORD|0-1|**옵션** 대화 상자에서 **명령문 완료** 옵션이 활성화되어 있는지 여부를 지정합니다.|
|쇼스마트인덴트|REG_DWORD|0-1|**옵션** 대화 상자에서 **스마트** 들여쓰기를 선택하는 옵션이 활성화되어 있는지 여부를 지정합니다.|
|요청스톡 색상|REG_DWORD|0-1|맞춤 또는 기본 색상이 키워드에 색상을 지정할지 여부를 지정합니다.|
|쇼호틀|REG_DWORD|0-1|사용자가 URL을 클릭할 수 있는지 여부를 지정합니다.|
|비핫 URL기본값|REG_DWORD|0-1|**옵션** 대화 상자에서 **단일 클릭 URL 탐색** 활성화 옵션의 초기 설정을 지정합니다.|
|기본토인더스페이스|REG_DWORD|0-1|언어 서비스에 기본 탭 옵션으로 "삽입 공백"이 있는지 여부를 지정합니다.|
|쇼드롭다운바옵션|REG_DWORD|0-1|탐색 **모음을** 표시하거나 숨기는 **옵션** 대화 상자에서 **탐색**모음 옵션을 사용 설정하거나 사용하지 않도록 설정합니다.|
|단일 코드 창만|REG_DWORD|0-1|언어 서비스에 대한 **창** 메뉴에서 **새 창** 선택을 활성화하거나 사용하지 않도록 설정합니다.|
|인에이블고급 회원 옵션|REG_DWORD|0-1|**고급 멤버 숨기기의** **옵션** 대화 상자 설정을 사용 하거나 사용하지 않도록 설정합니다.|
|지원 CF_HTML|REG_DWORD|0-1|편집기에서 HTML 데이터를 복사하고 붙여넣기를 사용할 수 있는지 여부를 지정합니다.|
|인에이블라인번호 옵션|REG_DWORD|0-1|**옵션** 대화 상자의 **줄 번호** 옵션이 언어 서비스에 대해 활성화되어 있는지 여부를 지정합니다.|
|하이드어드어밴스드 멤버디폴|REG_DWORD|0-1|개인 필드와 같은 고급 멤버가 완료 목록에 숨겨져 있는지 여부를 지정합니다.|
|쇼브레이완성|REG_DWORD|0-1|**옵션** 대화 상자에서 **중괄호 완료** 옵션이 활성화되어 있는지 여부를 지정합니다.|

### <a name="example"></a>예제

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

## <a name="registry-entries-for-debugger-languages-options"></a>디버거 언어 옵션에 대한 레지스트리 항목
 *VS Reg 루트*\언어 서비스\\언어*이름*\디버거\\언어*GUID*\ 키에는 다음 값이 포함될 수 있습니다.

|이름|Type|범위|설명|
|----------|----------|-----------|-----------------|
|(기본값)|REG_SZ|text|기본값은 언어의 이름을 문서화하는 데 사용할 수 있습니다. 이 키의 이름은 * \<VS Reg 루트>* \AD7Metrics\표현식 평가기에서 해당 항목이 있는 식 계산기의 GUID입니다.|

### <a name="example"></a>예제

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>편집기 도구 옵션에 대한 레지스트리 항목
 속성 페이지 및 속성 노드에 대한 EditorToolsOptions 키 아래에 레지스트리 키를 추가할 수 있습니다. 이러한 키와 해당 값은 언어 서비스를 구성하는 데 사용되는 **옵션** 대화 **상자(도구** 메뉴)에서 속성 페이지를 식별합니다. 다음 예제에서 *페이지 이름은* 속성 페이지의 이름이며 *노드 이름은* **옵션** 대화 상자의 트리에 있는 노드의 이름입니다. 페이지 항목과 노드 항목은 별도로 지정해야 합니다.

|이름|Type|범위|설명|
|----------|----------|-----------|-----------------|
|(기본값)|REG_SZ|레시드 (것)들|이 옵션 페이지의 지역화된 표시 이름입니다. 이름은 리터럴 텍스트 또는 #이`nnn` `nnn` 될 수 있습니다.|
|패키지|REG_SZ|*Guid*|이 옵션 페이지를 구현하는 VSPackage의 GUID입니다.|
|호출|REG_SZ|*Guid*|메서드를 호출하여 VSPackage에서 요청하는 속성 페이지의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> GUID입니다. 이 레지스트리 항목이 없는 경우 레지스트리 키는 페이지가 아닌 노드를 설명합니다.|

### <a name="example"></a>예제

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

## <a name="registry-entries-for-file-name-extension-options"></a>파일 이름 확장자 옵션에 대한 레지스트리 항목
 파일 확장자의 항목에는 선행 기간(예: ".myext")이 포함되어야 합니다.

|이름|Type|범위|설명|
|----------|----------|-----------|-----------------|
|(기본값)|REG_SZ|*Guid*|이 파일 이름 확장자 유형에 대한 기본 언어 서비스에 대한 서비스 GUID입니다.|

### <a name="example"></a>예제

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>편집기 옵션에 대한 레지스트리 항목
 *VS Reg 루트*\Editors 키에는 다음 값이 포함될 수 있습니다.

|이름|Type|범위|설명|
|----------|----------|-----------|-----------------|
|(기본값)|REG_SZ|""|사용하지 않은; 당신은 문서화 여기에 이름을 넣을 수 있습니다.|
|DefaultToolboxTab|REG_SZ|""|편집기활성 상태일 때 기본값으로 만들 수 있는 도구 상자 탭의 이름입니다.|
|DisplayName|REG_SZ|레시드 (것)들|대화 상자 열기에 표시할 **이름입니다.** 이름은 문자열 리소스 ID 또는 표준 형식의 이름입니다.|
|제외데프텍스트에디터|REG_DWORD|0-1|**메뉴** 열기 명령에 사용됩니다. 특정 파일 형식에 사용할 수 있는 편집기 목록에 기본 텍스트 편집기를 나열하지 않으려면 이 값을 1로 설정합니다.|
|링크드에디터GUID|REG_SZ|*\<지침>*|코드 페이지 지원을 사용하여 파일을 열 수 있는 모든 언어 서비스에 사용됩니다. 예를 들어 **열기** 명령을 사용하여 .txt 파일을 열 때 인코딩 유무에 관계없이 소스 코드 편집기 사용에 대한 옵션이 제공됩니다.<br /><br /> 하위 키의 이름에 지정된 GUID는 코드 페이지 편집기 팩터리용입니다. 이 특정 레지스트리 항목에 지정된 연결된 GUID는 일반 편집기 팩터리를 위한 것입니다. 이 항목의 목적은 기본 편집기를 사용하여 IDE가 파일을 열지 않으면 IDE가 목록의 다음 편집기를 사용하려고 시도하는 것입니다. 이 편집기 팩터리는 기본적으로 실패한 편집기 팩터리와 동일하기 때문에 이 다음 편집기는 코드페이지 편집기 팩터리여야 합니다.|
|패키지|REG_SZ|*\<지침>*|디스플레이 이름의 ResID에 대한 VS 패키지 GUID입니다.|

### <a name="example"></a>예제

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

## <a name="registry-entries-for-logical-view-options"></a>논리보기 옵션에 대한 레지스트리 항목
 *VS Reg 루트*\편집자\\*편집기 GUI>* \LogicViews 키에는 다음 값이 포함될 수 있습니다.

|이름|Type|범위|설명|
|----------|----------|-----------|-----------------|
|(기본값)|REG_SZ||사용되지 않습니다.|
|*\<지침>*|REG_SZ|""|지원되는 논리 보기의 키입니다. 필요한 만큼 이 중 많은 것을 가질 수 있습니다. 레지스트리 항목의 이름은 항상 빈 문자열인 값이 아니라 중요한 것입니다.|

### <a name="example"></a>예제

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

## <a name="registry-entries-for-editor-extension-options"></a>편집기 확장 옵션에 대한 레지스트리 항목
 *VS Reg 루트*\편집자\\*편집기 GUID*\확장 키에는 다음 값이 포함될 수 있습니다. 파일 이름 확장명에는 선행 기간이 포함되지 않습니다.

|이름|Type|범위|설명|
|----------|----------|-----------|-----------------|
|(기본값)|REG_SZ||사용되지 않습니다.|
|*\<내외>*|REG_DWORD|0-0xffffffff|확장의 상대우선 순위입니다. 두 개 이상의 언어가 동일한 확장을 공유하는 경우 우선 순위가 높은 언어가 선택됩니다.|

 또한 현재 편집자에 대한 기본 선택은\\HKEY_Current_User\Software\Microsoft\VisualStudio*X.Y*\기본 편집기\\*내선에*저장됩니다. 선택한 언어 서비스의 GUID가 사용자 지정 항목에 있습니다. 현재 사용자에 대 한 우선 순위를 차지 합니다.

### <a name="example"></a>예제

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>관리되는 패키지 프레임워크 언어 서비스 옵션에 대한 레지스트리 항목
 다음 레지스트리 항목은 MPF(관리되는 패키지 프레임워크) 언어 서비스 클래스와 관련이 있습니다. 이러한 레지스트리 항목은 다양한 IntelliSense 기능 및 기타 고급 편집 기능에 대한 언어 서비스 지원을 나타냅니다.

 이러한 레지스트리 항목은 클래스를 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 통해 액세스됩니다.

|이름|Type|범위|설명|
|----------|----------|-----------|-----------------|
|코드 센스|REG_DWORD|0-1|IntelliSense 운영 지원.|
|매치브레이스|REG_DWORD|0-1|중괄호, 괄호 및 대괄호와 같은 언어 쌍을 일치시키는 데 대한 지원입니다.|
|QuickInfo|REG_DWORD|0-1|IntelliSense 빠른 정보 작업에 대한 지원.|
|쇼매칭브레이스|REG_DWORD|0-1|상태 표시줄에 일치하는 언어 쌍을 표시하기 위한 지원입니다.|
|매치브레이스애트케어|REG_DWORD|0-1|일반적으로 두 요소를 강조 표시하여 일치하는 언어 쌍을 표시할 수 있습니다.|
|최대 오류 메시지|REG_DWORD|0-n|**오류 목록** 창에 표시할 수 있는 최대 오류 수입니다.|
|코드센스지연|REG_DWORD|0-n|IntelliSense 작업에 대한 배경 구문 분석 작업을 시작하기 전에 지연할 밀리초입니다.|
|인에이블Async완료|REG_DWORD|0-1|백그라운드 구문 분석 지원.|
|사용 하기 주석|REG_DWORD|0-1|선택한 텍스트 블록에 주석을 달기 위한 지원및 선택한 텍스트의 주석 달기 해제에 대한 지원도 의미합니다.|
|사용 형식 선택|REG_DWORD|0-1|자동 들여쓰기 또는 중괄호 위치 조정과 같은 텍스트 서식 지정을 지원합니다.|
|자동 아웃라이닝|REG_DWORD|0-1|개요(축소할 수 있는 영역)에 대한 지원입니다.|
|최대 지역|REG_DWORD|0-n|파일당 숨겨진 영역의 최대 수입니다.|

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

## <a name="see-also"></a>참조
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
