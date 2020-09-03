---
title: Visual Basic 편집 하며 계속 하기에서 지원 되지 않는 편집 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94a151a7adab5c8246cec38c2e62d76788beb6e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155441"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Visual Basic 편집하며 계속하기에서 지원되지 않는 편집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집하며 계속하기를 사용하면 중단 모드에서 프로그램 실행을 중지하고 실행 코드를 변경한 다음 새로 통합된 변경 내용을 사용하여 프로그램 실행을 다시 시작할 수 있습니다. 클래스의 공용 구조체에 영향을 주는 선언 코드 편집은 일반적으로 허용되지 않지만, 클래스 내의 private 선언, 속성 본문 또는 메서드에 대한 다양한 편집이 허용됩니다.  
  
 지원되지 않는 변경을 수행해야 하는 경우에는 디버깅을 중지하고 변경한 다음 디버깅 세션을 새로 시작해야 합니다.  
  
### <a name="method-and-property-body-edits"></a><a name="BKMK_MethodandPropertyBodyEdits"></a> 메서드 및 속성 본문 편집  
 **정적 지역 변수에 대 한 지원 되지 않는 변경**: 지역 변수를 추가 또는 업데이트 하거나, 컴파일 오류가 발생할 경우 정적 지역 변수를 제거 합니다.  
  
 제네릭 **에 대해 지원 되지 않는 변경 내용**: 제네릭 메서드 자체 나 제네릭 메서드 본문은 변경할 수 없습니다. 기존 제네릭 메서드에 대한 호출이나 제네릭 형식의 인스턴스화는 추가, 삭제 또는 변경할 수 있습니다.  
  
 **기타 지원되지 않는 변경**  
  
- 호출 스택에 있는 메서드의 호출 문 변경  
  
- 명령 포인터가 `Try...Catch` 블록이나 `Catch` 블록에서 끝나는 경우 `Finally` 블록 추가  
  
- `Try...Catch`명령 포인터가 `Catch` 블록이 나 블록에 있는 경우 블록 제거 `Finally`  
  
- 현재 명령 포인터 주위에 `Using` 블록 추가  
  
- 현재 명령 포인터 주위에 `SynchLock` 블록 추가  
  
### <a name="attribute-edits"></a><a name="BKMK_AttributeEdits"></a> 특성 편집  
 편집하며 계속하기에서는 특성 수정을 지원하지 않습니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 특성 클래스 정의, 편집 또는 삭제  
  
- 특성 추가  
  
- 기존 특성 편집 또는 제거  
  
### <a name="class-declaration-edits"></a><a name="BKMK_ClassDeclarationEdits"></a> 클래스 선언 편집  
 클래스 선언에 대한 대부분의 변경은 중단 모드에 있는 동안 편집하며 계속하기에서 허용되지 않습니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 기존 클래스의 상속 이름 바꾸기, 삭제 또는 변경  
  
- 새 인터페이스 구현 또는 인터페이스의 구현 제거  
  
- 클래스의 한정자 변경  
  
- `ComClass` 상태 추가, 변경 또는 제거  
  
- 제네릭 클래스 선언 편집  
  
### <a name="class-member-declaration-edits"></a><a name="BKMK_ClassMemberDeclarationEdits"></a> 클래스 멤버 선언 편집  
 멤버 선언에 대한 변경은 편집하며 계속하기에서 대부분의 경우 허용되지 않습니다. 예를 들어 멤버의 서명 또는 액세스 수준을 변경할 수 없고 컴파일 오류를 발생시킬 수 있는 멤버를 완전히 제거할 수 없습니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 포함하는 블록 안에 이름이 같은 전역 또는 멤버 변수를 선언하여 기존 멤버 변수 숨김  
  
- 블록 안에 새 인스턴스를 선언하여 정적 지역 변수 숨김  
  
- 이벤트 처리기 제거. 이벤트 처리기를 추가할 수는 있습니다.  
  
- 오버로드하는 새 속성 또는 메서드 추가(이 속성이나 메서드가 `Private`이고 활성 문에 해당 이름이 나타나지 않는 경우 제외)  
  
- 멤버 변수에 대한 `WithEvents` 절 추가 또는 제거  
  
- 멤버 삭제  
  
- 인터페이스 구현을 중지하는 속성 또는 메서드 선언 변경  
  
- 제네릭을 사용하는 메서드 편집  
  
- private이 아닌 속성이나 메서드의 시그니처 또는 반환 형식 변경  
  
- 기본 클래스에서 멤버 재정의 또는 숨기기  
  
- `SequentialLayout` 또는 `ExplicitLayout`으로 표시된 클래스에 새 필드 추가  
  
- 메서드의 `MustInherit` 또는 `NotOverridable` 상태 변경  
  
- 속성 또는 메서드의 액세스 한정자 변경  
  
- 필드의 형식 또는 읽기 전용 상태 변경  
  
- public 필드 변경  
  
### <a name="compiler-option-edits"></a><a name="BKMK_CompilerOptionEdits"></a> 컴파일러 옵션 편집  
 중단 모드에서 편집하며 계속하기를 사용할 때는 다음과 같은 컴파일러 옵션을 변경, 추가 또는 제거할 수 없습니다.  
  
- **Option Strict**  
  
- **Option Explicit**  
  
- **Option Compare**  
  
### <a name="constants-edits"></a><a name="BKMK_ConstantsEdits"></a> 상수 편집  
 편집하며 계속하기 모드에서 상수에 대한 변경은 매우 제한적입니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 상수 변수 추가 또는 업데이트  
  
- 상수의 형식 또는 값 변경  
  
- 상수 제거  
  
### <a name="delegate-and-event-declaration-edits"></a><a name="BKMK_DelegateandEventDeclarationEdits"></a> 대리자 및 이벤트 선언 편집  
 대리자와 이벤트에 대한 일부 변경은 중단 모드에 있는 동안 편집하며 계속하기에서 허용되지 않습니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 대리자 정의 변경 또는 삭제  
  
- 이벤트 삭제  
  
### <a name="enumeration-edits"></a><a name="BKMK_EnumerationEdits"></a> 열거형 편집  
 열거형(`Enums`)에 대한 변경은 중단 모드에 있는 동안 편집하며 계속하기에서 허용되지 않습니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- `Enum`의 내부 형식 수정  
  
- `Enum` 멤버 추가, 변경 또는 제거  
  
- `Enum`의 액세스 한정자 변경  
  
### <a name="external-declarations-edits"></a><a name="BKMK_ExternalDeclarationsEdits"></a> 외부 선언 편집  
 일반적으로 편집하며 계속하기 중에는 외부 메서드의 선언을 변경할 수 없습니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 외부 선언 추가 또는 제거  
  
- 외부 선언의 시그니처 또는 마샬링 특성 변경  
  
### <a name="imports-edits"></a><a name="BKMK_ImportsEdits"></a> 편집 내용 가져오기  
 편집하며 계속하기에서는 중단 모드에 있는 동안 `Imports` 문의 추가, 변경 또는 제거를 허용하지 않습니다.  
  
### <a name="interface-definition-edits"></a><a name="BKMK_InterfaceDefinitionEdits"></a> 인터페이스 정의 편집  
 인터페이스를 구현하는 멤버를 변경할 수 있는 경우는 흔하지만 실제 인터페이스 정의에 대한 변경은 편집하며 계속하기에서 일반적으로 허용되지 않습니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 인터페이스 멤버 추가, 변경 또는 제거  
  
- 기존 인터페이스 삭제  
  
- 인터페이스의 액세스 한정자 변경  
  
- 인터페이스 상속 계층 구조 변경  
  
### <a name="module-declaration-edits"></a><a name="BKMK_ModuleDeclarationEdits"></a> 모듈 선언 편집  
 모듈 선언에 대한 대부분의 변경은 중단 모드에 있는 동안 편집하며 계속하기에서 허용되지 않습니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 새 모듈 만들기  
  
- 기존 모듈 이름 바꾸기 또는 삭제  
  
- 모듈의 액세스 한정자 변경  
  
### <a name="module-member-declaration-edits"></a><a name="BKMK_ModuleMemberDeclarationEdits"></a> 모듈 멤버 선언 편집  
 편집하며 계속하기를 사용하는 경우 중단 모드에서 속성, 메서드 및 필드와 같은 모듈 멤버를 다양하게 변경할 수 있습니다. 그러나 일부 변경은 지원되지 않습니다. 특히 편집하며 계속하기에서는 모든 멤버에 대한 서명이나 형식의 추가, 삭제 또는 변경을 지원하지 않습니다.  
  
 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 새 멤버 추가(활성 문에 해당 이름이 나타나지 않는 경우 제외)  
  
- 속성 또는 메서드 제거  
  
- 속성 또는 메서드의 시그니처 변경  
  
- 필드 추가, 이름 바꾸기, 이동 또는 삭제  
  
- 제네릭을 사용하는 메서드 편집  
  
- 속성 또는 메서드의 액세스 한정자 변경(예: `Public`을 `Private`로 변경)  
  
- 기존 필드의 형식 삭제 또는 변경  
  
### <a name="nested-type-declaration-edits"></a><a name="BKMK_NestedTypeDeclarationEdits"></a> 중첩 형식 선언 편집  
 편집하며 계속하기는 다른 네임스페이스 또는 형식으로 중첩 형식 이동을 지원하지 않습니다.  
  
### <a name="structure-declaration-edits"></a><a name="BKMK_StructureDeclarationEdits"></a> 구조체 선언 편집  
 **중단** 모드에 있는 동안에는 편집 하며 계속 하기에서 구조 선언에 대 한 대부분의 변경 작업을 수행할 수 없습니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 기존 구조체 이름 바꾸기 또는 삭제  
  
- 새 인터페이스 구현 또는 인터페이스의 구현 제거  
  
- 구조체의 액세스 한정자 변경  
  
### <a name="structure-member-declaration-edits"></a><a name="BKMK_StructureMemberDeclarationEdits"></a> 구조체 멤버 선언 편집  
 편집하며 계속하기를 사용하는 경우 중단 모드에서 구조체 멤버(속성, 메서드 및 필드)를 다양하게 변경할 수 있습니다. 그러나 구조체 멤버의 선언에 영향을 주는 변경을 비롯한 일부 변경은 지원되지 않습니다. 특히 편집하며 계속하기에서는 다음과 같은 변경을 지원하지 않습니다.  
  
- 속성 또는 메서드 제거  
  
- 필드 추가 또는 제거  
  
- 속성 또는 메서드의 시그니처 변경  
  
- 제네릭을 사용하는 메서드 편집  
  
- 속성 또는 메서드 선언에서 인터페이스를 구현하는지 여부 변경  
  
- 속성 또는 메서드의 액세스 한정자 변경 (예: `Public` **Private**으로 변경)  
  
- 필드 제거  
  
- 필드의 형식 변경  
  
## <a name="see-also"></a>관련 항목  
 [방법: 편집 하며 계속 하기를 사용 하 여 중단 모드에서 편집 적용](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [편집하며 계속하기(Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
