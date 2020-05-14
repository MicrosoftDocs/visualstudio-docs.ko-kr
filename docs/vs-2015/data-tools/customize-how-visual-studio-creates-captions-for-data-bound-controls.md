---
title: Visual Studio 2015가 데이터 바인딩된 컨트롤에 대 한 캡션을 만드는 방식 사용자 지정 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0e54f68ab7e34f1cfb6abb228f552cc3792a8b7
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476914"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio에서 데이터 바인딩된 컨트롤에 대한 캡션을 만드는 방식 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) 에서 Windows Forms 디자이너로 항목을 끌어 오면 특별 한 고려 사항이 있습니다. 두 개 이상의 단어가 함께 연결 될 경우 캡션 레이블의 열 이름이 더 읽기 쉬운 문자열로 다시 포맷 됩니다. **HKEY_CURRENT_USER \Software\microsoft\visualstudio\10.0\data designer** 레지스트리 키에서 **Smartcaptionexpression**, **Smartcaptionexpression**및 **smartcaptionexpression** 값을 설정 하 여 이러한 레이블이 생성 되는 방식을 사용자 지정할 수 있습니다.

> [!NOTE]
> 이 레지스트리 키는 만들 때까지 존재 하지 않습니다.

 스마트 캡션은 **Smartcaptionexpression** 값의 값에 입력 된 정규식에 의해 제어 됩니다. **데이터 디자이너** 레지스트리 키를 추가 하면 캡션 레이블을 제어 하는 기본 정규식이 재정의 됩니다. 정규식에 대 한 자세한 내용은 [Visual Studio에서 정규식 사용](../ide/using-regular-expressions-in-visual-studio.md)을 참조 하세요.

 다음 표에서는 캡션 레이블을 제어 하는 레지스트리 값에 대해 설명 합니다.

|레지스트리 항목|설명|
|-------------------|-----------------|
|**SmartCaptionExpression**|패턴을 일치 시키는 데 사용 되는 정규식입니다.|
|**SmartCaptionReplacement**|**Smartcaptionexpression**에 일치 하는 그룹을 표시 하는 형식입니다.|
|**SmartCaptionSuffix**|캡션의 끝에 추가할 선택적 문자열입니다.|

 다음 표에서는 이러한 레지스트리 값에 대 한 내부 기본 설정을 나열 합니다.

|레지스트리 항목|기본값|설명|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\P{lu}는) &#124;_+|소문자와 대문자 또는 밑줄을 찾습니다.|
|**SmartCaptionReplacement**|$1 $2|$1은 식의 첫 번째 괄호에서 일치 하는 문자를 나타내며, $2은 두 번째 괄호에 일치 하는 모든 문자를 나타냅니다. 첫 번째 일치 항목, 공백, 두 번째 일치 항목을 대체 합니다.|
|**SmartCaptionSuffix**|:|반환 된 문자열에 추가 되는 문자를 나타냅니다. 예를 들어 캡션이 `Company Name`되는 경우 접미사를 사용 하 여 `Company Name:`|

> [!CAUTION]
> 레지스트리 편집기에서 작업을 수행할 때는 주의 해야 합니다. 레지스트리를 편집 하기 전에 백업 합니다. 레지스트리 편집기를 잘못 사용 하면 운영 체제를 다시 설치 해야 할 수 있는 심각한 문제가 발생할 수 있습니다. Microsoft는 레지스트리 편집기를 잘못 사용 하 여 발생 하는 문제를 해결할 수 있도록 보장 하지 않습니다. 레지스트리 편집기 사용에 따른 결과는 사용자의 책임입니다.

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>데이터 소스 창의 스마트 캡션 동작을 수정 하려면

1. **시작** 을 클릭 한 다음 **실행**을 클릭 하 여 명령 창을 엽니다.

2. **실행** 대화 상자에 `regedit`을 입력 하 고 **확인**을 클릭 합니다.

3. **HKEY_CURRENT_USER** 노드를 확장 합니다.

4. **소프트웨어** 노드를 확장 합니다.

5. **Microsoft** 노드를 확장 합니다.

6. **VisualStudio** 노드를 확장 합니다.

7. **10.0** 노드를 마우스 오른쪽 단추로 클릭 하 고 `Data Designers`이라는 새 **키** 를 만듭니다.

8. **데이터 디자이너** 노드를 마우스 오른쪽 단추로 클릭 하 고 `SmartCaptionExpression`이라는 새 **문자열 값** 을 만듭니다.

9. **데이터 디자이너** 노드를 마우스 오른쪽 단추로 클릭 하 고 `SmartCaptionReplacement`이라는 새 **문자열 값** 을 만듭니다.

10. **데이터 디자이너** 노드를 마우스 오른쪽 단추로 클릭 하 고 `SmartCaptionSuffix`이라는 새 **문자열 값** 을 만듭니다.

11. **Smartcaptionexpression** 항목을 마우스 오른쪽 단추로 클릭 하 고 **수정**을 선택 합니다.

12. **데이터 소스** 창에서 사용 하려는 정규식을 입력 합니다.

13. **Smartcaptionreplacement** 항목을 마우스 오른쪽 단추로 클릭 하 고 **수정**을 선택 합니다.

14. 정규식에서 일치 하는 패턴을 표시 하려는 방식으로 형식이 지정 된 대체 문자열을 입력 합니다.

15. **Smartcaptionsuffix** 항목을 마우스 오른쪽 단추로 클릭 하 고 **수정**을 선택 합니다.

16. 캡션의 끝에 표시할 문자를 입력 합니다.

     다음 번에 **데이터 소스** 창에서 항목을 끌면 제공 된 새 레지스트리 값을 사용 하 여 캡션 레이블이 생성 됩니다.

### <a name="to-turn-off-the-smart-captioning-feature"></a>스마트 캡션 기능을 해제 하려면

1. **시작** 을 클릭 한 다음 **실행**을 클릭 하 여 명령 창을 엽니다.

2. **실행** 대화 상자에 `regedit`을 입력 하 고 **확인**을 클릭 합니다.

3. **HKEY_CURRENT_USER** 노드를 확장 합니다.

4. **소프트웨어** 노드를 확장 합니다.

5. **Microsoft** 노드를 확장 합니다.

6. **VisualStudio** 노드를 확장 합니다.

7. **10.0** 노드를 마우스 오른쪽 단추로 클릭 하 고 `Data Designers`이라는 새 **키** 를 만듭니다.

8. **데이터 디자이너** 노드를 마우스 오른쪽 단추로 클릭 하 고 `SmartCaptionExpression`이라는 새 **문자열 값** 을 만듭니다.

9. **데이터 디자이너** 노드를 마우스 오른쪽 단추로 클릭 하 고 `SmartCaptionReplacement`이라는 새 **문자열 값** 을 만듭니다.

10. **데이터 디자이너** 노드를 마우스 오른쪽 단추로 클릭 하 고 `SmartCaptionSuffix`이라는 새 **문자열 값** 을 만듭니다.

11. **Smartcaptionexpression** 항목을 마우스 오른쪽 단추로 클릭 하 고 **수정**을 선택 합니다.

12. 값에 `(.*)`을 입력 합니다. 그러면 전체 문자열이 일치 합니다.

13. **Smartcaptionreplacement** 항목을 마우스 오른쪽 단추로 클릭 하 고 **수정**을 선택 합니다.

14. 값에 `$1`을 입력 합니다. 이렇게 하면 문자열을 일치 하는 값으로 대체 하 여 변경 되지 않은 상태로 유지 되도록 전체 문자열을 대체 합니다.

     다음 번에 **데이터 소스** 창에서 항목을 끌면 수정 되지 않은 캡션으로 캡션 레이블이 생성 됩니다.

## <a name="see-also"></a>참고 항목
 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
