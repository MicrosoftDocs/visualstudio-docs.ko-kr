---
title: 방법 - WPF 추적 정보 표시 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 362376176cfb95c4e285f6837c53d277110e3439
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349785"
---
# <a name="how-to-display-wpf-trace-information"></a>방법: WPF 추적 정보 표시
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]에서는 WPF 애플리케이션에서 디버그 추적 정보를 받아서 **출력** 창에 표시할 수 있습니다. 디버그 추적 정보를 표시하려면 WPF 추적을 사용하도록 설정해야 합니다.

 WPF 추적 설정에는 App.Config 파일을 사용하거나 <xref:System.Diagnostics.PresentationTraceSources> 클래스를 통한 프로그래밍 방식을 사용할 수 있습니다. 더 쉽게 WPF 추적을 사용하도록 설정하는 방법은 **옵션** 창을 사용하는 것입니다. 애플리케이션에 대한 WPF 추적은 지원되지 않습니다.

### <a name="to-enable-or-customize-wpf-trace-information"></a>WPF 추적 정보를 사용하도록 설정하거나 사용자 지정하려면

1. **도구** 메뉴에서 **옵션**을 선택합니다.

2. **옵션** 대화 상자의 왼쪽에 있는 상자에서 **디버깅** 노드를 엽니다.

3. **디버깅**에서 **출력 창**을 클릭합니다.

4. **일반 출력 설정**에서 **모든 디버그 출력**을 선택합니다.

5. 오른쪽에 있는 상자에서 **WPF 추적 설정**을 찾습니다.

6. **WPF 추적 설정** 노드를 엽니다.

7. **WPF 추적 설정**에서 사용하도록 설정할 설정의 범주(예: **데이터 바인딩**)를 클릭합니다.

     드롭다운 목록 컨트롤이 **데이터 바인딩** 또는 클릭한 범주 옆의 설정 열에 나타납니다.

8. 드롭다운 목록을 클릭하고 다음과 같이 보려는 추적 정보 형식을 선택합니다. **All**, **Critical**, **Error**, **Warning**, **Information**, **Verbose** 또는 **ActivityTracing**.

     **Critical**은 중요 이벤트만 추적하도록 설정합니다.

     **Error**는 중요 및 오류 이벤트를 추적하도록 설정합니다.

     **Warning**은 중요, 오류 및 경고 이벤트를 추적하도록 설정합니다.

     **Information**은 중요, 오류, 경고 및 정보 이벤트를 추적하도록 설정합니다.

     **Verbose**는 중요, 오류, 경고, 정보 및 자세한 이벤트를 추적하도록 설정합니다.

     **ActivityTracing**은 중지, 시작, 일시 중단, 전송 및 다시 시작 이벤트를 추적하도록 설정합니다.

     이러한 추적 정보 수준의 의미에 대한 자세한 내용은 <xref:System.Diagnostics.SourceLevels>를 참조하십시오.

9. **확인**을 클릭합니다.

### <a name="to-disable-wpf-trace-information"></a>WPF 추적 정보를 사용하지 않도록 설정하려면

1. **도구** 메뉴에서 **옵션**을 선택합니다.

2. **옵션** 대화 상자의 왼쪽에 있는 상자에서 **디버깅** 노드를 엽니다.

3. **디버깅**에서 **출력 창**을 클릭합니다.

4. 오른쪽에 있는 상자에서 **WPF 추적 설정**을 찾습니다.

5. **WPF 추적 설정** 노드를 엽니다.

6. **WPF 추적 설정**에서 사용하도록 설정할 설정의 범주(예: **데이터 바인딩**)를 클릭합니다.

     드롭다운 목록 컨트롤이 **데이터 바인딩** 또는 클릭한 범주 옆의 설정 열에 나타납니다.

7. 드롭다운 목록을 클릭하고 **해제**를 선택합니다.

8. **확인**을 클릭합니다.

## <a name="see-also"></a>참조
- [WPF 디버그](../debugger/debugging-wpf.md)