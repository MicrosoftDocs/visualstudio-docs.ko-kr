---
title: 데이터 바인딩된 컨트롤에 대 한 캡션 사용자 지정
ms.date: 11/03/2017
ms.topic: how-to
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 085542f912cc5747c2012adb05e6097b5891ed60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282581"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio에서 데이터 바인딩된 컨트롤에 대한 캡션을 만드는 방식 사용자 지정

[데이터 소스 창](add-new-data-sources.md#data-sources-window) 에서 디자이너로 항목을 끌어 오면 특별 한 고려 사항이 있습니다. 두 개 이상의 단어가 함께 연결 될 경우 캡션 레이블의 열 이름이 더 읽기 쉬운 문자열로 다시 포맷 됩니다.

::: moniker range="vs-2017"

**HKEY_CURRENT_USER \Software\microsoft\visualstudio\15.0\data designer** 레지스트리 키에서 **Smartcaptionexpression**, **Smartcaptionexpression**및 **smartcaptionexpression** 값을 설정 하 여 이러한 레이블이 생성 되는 방식을 사용자 지정할 수 있습니다.

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER \Software\microsoft\visualstudio\16.0\data designer** 레지스트리 키에서 **Smartcaptionexpression**, **Smartcaptionexpression**및 **smartcaptionexpression** 값을 설정 하 여 이러한 레이블이 생성 되는 방식을 사용자 지정할 수 있습니다.

::: moniker-end

> [!NOTE]
> 이 레지스트리 키는 만들 때까지 존재 하지 않습니다.

스마트 캡션은 **Smartcaptionexpression** 값의 값에 입력 된 정규식에 의해 제어 됩니다. **데이터 디자이너** 레지스트리 키를 추가 하면 캡션 레이블을 제어 하는 기본 정규식이 재정의 됩니다. 정규식에 대 한 자세한 내용은 [Visual Studio에서 정규식 사용](../ide/using-regular-expressions-in-visual-studio.md)을 참조 하세요.

다음 표에서는 캡션 레이블을 제어 하는 레지스트리 값에 대해 설명 합니다.

|레지스트리 항목|설명|
|-------------------|-----------------|
|**SmartCaptionExpression**|패턴을 일치 시키기 위해 사용 하는 정규식입니다.|
|**SmartCaptionReplacement**|**Smartcaptionexpression**에 일치 하는 그룹을 표시 하는 형식입니다.|
|**SmartCaptionSuffix**|캡션의 끝에 추가할 선택적 문자열입니다.|

다음 표에서는 이러한 레지스트리 값에 대 한 내부 기본 설정을 나열 합니다.

|레지스트리 항목|기본값|설명|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**( \\ \p{Ll}) ( \\ \p{lu}는) &#124;_ +**|소문자와 대문자 또는 밑줄을 찾습니다.|
|**SmartCaptionReplacement**|**$1 $2**|**$1** 은 식의 첫 번째 괄호에서 일치 하는 문자를 나타내며, **$2** 은 두 번째 괄호에 일치 하는 모든 문자를 나타냅니다. 첫 번째 일치 항목, 공백, 두 번째 일치 항목을 대체 합니다.|
|**SmartCaptionSuffix**|**:**|반환 된 문자열에 추가 되는 문자를 나타냅니다. 예를 들어 캡션이 인 경우 접미사가이를 `Company Name` 사용 합니다. `Company Name:`|

> [!CAUTION]
> 레지스트리 편집기에서 원하는 작업을 수행 하는 경우에는 주의 해야 합니다. 레지스트리를 편집 하기 전에 백업 합니다. 레지스트리 편집기를 잘못 사용 하면 운영 체제를 다시 설치 해야 할 수 있는 심각한 문제가 발생할 수 있습니다. Microsoft는 레지스트리 편집기를 잘못 사용 하 여 발생 하는 문제를 해결할 수 있도록 보장 하지 않습니다. 레지스트리 편집기 사용에 따른 위험은 사용자가 책임져야 합니다.
>
> 레지스트리 백업, 편집 및 복원에 대 한 자세한 내용은 [advanced users에 대 한 Windows 레지스트리 정보](https://support.microsoft.com/help/256986/windows-registry-information-for-advanced-users)를 참조 하십시오.

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>데이터 소스 창의 스마트 캡션 동작 수정

1. **시작** 을 클릭 한 다음 **실행**을 클릭 하 여 명령 창을 엽니다.

2. `regedit` **실행** 대화 상자에를 입력 하 고 **확인**을 클릭 합니다.

3. **HKEY_CURRENT_USER**  >  **Software**  >  **Microsoft**  >  **VisualStudio** 노드를 확장 합니다.

::: moniker range="vs-2017"

4. **15.0** 노드를 마우스 오른쪽 단추로 클릭 하 고 라는 새 **키** 를 만듭니다 `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. **16.0** 노드를 마우스 오른쪽 단추로 클릭 하 고 라는 새 **키** 를 만듭니다 `Data Designers` .

::: moniker-end

5. **데이터 디자이너** 노드를 마우스 오른쪽 단추로 클릭 하 고 다음과 같은 세 개의 새 문자열 값을 만듭니다.

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. **Smartcaptionexpression** 값을 마우스 오른쪽 단추로 클릭 하 고 **수정**을 선택 합니다.

7. **데이터 소스** 창에서 사용 하려는 정규식을 입력 합니다.

8. **Smartcaptionreplacement** 값을 마우스 오른쪽 단추로 클릭 하 고 **수정**을 선택 합니다.

9. 정규식에서 일치 하는 패턴을 표시 하려는 방식으로 형식이 지정 된 대체 문자열을 입력 합니다.

10. **Smartcaptionsuffix** 값을 마우스 오른쪽 단추로 클릭 하 고 **수정**을 선택 합니다.

11. 캡션의 끝에 표시할 문자를 입력 합니다.

    다음 번에 **데이터 소스** 창에서 항목을 끌면 제공 된 새 레지스트리 값을 사용 하 여 캡션 레이블이 생성 됩니다.

## <a name="turn-off-the-smart-captioning-feature"></a>스마트 캡션 기능 해제

1. **시작** 을 클릭 한 다음 **실행**을 클릭 하 여 명령 창을 엽니다.

2. `regedit` **실행** 대화 상자에를 입력 하 고 **확인**을 클릭 합니다.

3. **HKEY_CURRENT_USER**  >  **Software**  >  **Microsoft**  >  **VisualStudio** 노드를 확장 합니다.

::: moniker range="vs-2017"

4. **15.0** 노드를 마우스 오른쪽 단추로 클릭 하 고 라는 새 **키** 를 만듭니다 `Data Designers` .

::: moniker-end

::: moniker range=">=vs-2019"

4. **16.0** 노드를 마우스 오른쪽 단추로 클릭 하 고 라는 새 **키** 를 만듭니다 `Data Designers` .

::: moniker-end

5. **데이터 디자이너** 노드를 마우스 오른쪽 단추로 클릭 하 고 다음과 같은 세 개의 새 문자열 값을 만듭니다.

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

6. **Smartcaptionexpression** 항목을 마우스 오른쪽 단추로 클릭 하 고 **수정**을 선택 합니다.

7. `(.*)`값으로을 입력 합니다. 그러면 전체 문자열이 일치 합니다.

8. **Smartcaptionreplacement** 항목을 마우스 오른쪽 단추로 클릭 하 고 **수정**을 선택 합니다.

9. `$1`값으로을 입력 합니다. 이렇게 하면 문자열을 일치 하는 값으로 대체 하 여 변경 되지 않은 상태로 유지 되도록 전체 문자열을 대체 합니다.

    다음 번에 **데이터 소스** 창에서 항목을 끌면 수정 되지 않은 캡션으로 캡션 레이블이 생성 됩니다.

## <a name="see-also"></a>추가 정보

- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
