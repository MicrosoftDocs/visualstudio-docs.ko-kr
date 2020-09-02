---
title: 사용자 지정 등록 특성을 사용 하 여 확장 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935786"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>사용자 지정 등록 특성을 사용하여 확장 등록
특정 한 경우에는 확장에 대 한 새 등록 특성을 만들어야 할 수 있습니다. 등록 특성을 사용 하 여 새 레지스트리 키를 추가 하거나 기존 키에 새 값을 추가할 수 있습니다. 새 특성은에서 파생 되 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> 고 및 메서드를 재정의 해야 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> 합니다 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .  
  
## <a name="creating-a-custom-attribute"></a>사용자 지정 특성 만들기  
 다음 코드에서는 새 등록 특성을 만드는 방법을 보여 줍니다.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 는 특성 <xref:System.AttributeUsageAttribute> 클래스에서 특성을 사용 하는 프로그램 요소 (클래스, 메서드 등)를 지정 하는 데 사용 되며, 두 번 이상 사용할 수 있는지 여부 및 상속 될 수 있는지 여부를 지정 합니다.  
  
### <a name="creating-a-registry-key"></a>레지스트리 키 만들기  
 다음 코드에서 사용자 지정 특성은 등록 되는 VSPackage에 대 한 키 아래에 **사용자 지정** 하위 키를 만듭니다.  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>기존 레지스트리 키 아래에 새 값을 만듭니다.  
 기존 키에 사용자 지정 값을 추가할 수 있습니다. 다음 코드에서는 VSPackage 등록 키에 새 값을 추가 하는 방법을 보여 줍니다.  
  
```  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
  
```