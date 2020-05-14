---
title: 마법사 인터페이스(IDT마법사) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703272"
---
# <a name="wizard-interface-idtwizard"></a>마법사 인터페이스(IDTWizard)
IDE(통합 개발 환경)는 <xref:EnvDTE.IDTWizard> 인터페이스를 사용하여 마법사와 통신합니다. 마법사는 IDE에 설치하려면 이 인터페이스를 구현해야 합니다.

 메서드는 <xref:EnvDTE.IDTWizard.Execute%2A> <xref:EnvDTE.IDTWizard> 인터페이스와 연결된 유일한 방법입니다. 마법사는 이 메서드를 구현하고 IDE는 인터페이스에서 메서드를 호출합니다. 다음 예제에서는 메서드의 서명을 보여 주다.

```
/* IDTWizard Method */
STDMETHOD(Execute)(THIS_
   /* [in] */ IDispatch *Application,
   /* [in] */ long hwndOwner,
   /* [in] */ SAFEARRAY * *ContextParams,
   /* [in] */ SAFEARRAY * *CustomParams,
   /* [out] [in] */ wizardResult *RetVal
   );
```

 시작 메커니즘은 **새 프로젝트와** **새 항목 추가** 마법사 모두에 대해 비슷합니다. 둘 중 하나를 시작하려면 Dteinternal.h에 정의된 <xref:EnvDTE.IDTWizard> 인터페이스를 호출합니다. 유일한 차이점은 인터페이스가 호출될 때 인터페이스에 전달되는 컨텍스트 및 사용자 지정 매개 변수 집합입니다.

 다음 정보는 마법사가 <xref:EnvDTE.IDTWizard> IDE에서 작동하도록 구현해야 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 하는 인터페이스에 대해 설명합니다. IDE는 마법사에서 메서드를 <xref:EnvDTE.IDTWizard.Execute%2A> 호출하여 다음을 전달합니다.

- DTE 개체

     DTE 개체는 자동화 모델의 루트입니다.

- 코드 세그먼트에 표시된 대로 창 대화 상자에 `hwndOwner ([in] long)`대한 핸들입니다.

     마법사는 이 `hwndOwner` 것을 마법사 대화 상자의 부모로 사용합니다.

- 코드 세그먼트에 표시된 대로 SAFEARRAY에 대한 변형으로 인터페이스에 전달된 컨텍스트 매개 변수입니다. `[in] SAFEARRAY (VARIANT)* ContextParams`

     컨텍스트 매개 변수에는 시작되는 마법사의 종류와 프로젝트의 현재 상태에 특정한 값 배열이 포함됩니다. IDE는 컨텍스트 매개 변수를 마법사에 전달합니다. 자세한 내용은 [컨텍스트 매개 변수 를](../../extensibility/internals/context-parameters.md)참조하십시오.

- 사용자 지정 매개 변수는 코드 세그먼트에 표시된 대로 SAFEARRAY의 변형으로 인터페이스에 `[in] SAFEARRAY (VARIANT)* CustomParams`전달됩니다.

     사용자 지정 매개 변수에는 사용자 정의 매개 변수의 배열이 포함됩니다. .vsz 파일은 사용자 지정 매개 변수를 IDE에 전달합니다. 값은 `Param=` 문에 의해 결정됩니다. 자세한 내용은 [사용자 지정 매개 변수 를](../../extensibility/internals/custom-parameters.md)참조하십시오.

- 인터페이스에 대한 반환 값은 다음과 같습니다.

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>참조
- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)
- [사용자 지정 매개 변수](../../extensibility/internals/custom-parameters.md)
- [마법사](../../extensibility/internals/wizards.md)
- [마법사(.Vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)
