---
title: DebuggerDisplay 특성 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aba6feb17a4e7bd4cabfe40bd45480a0f7a9f552
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683932"
---
# <a name="using-the-debuggerdisplay-attribute"></a>DebuggerDisplay 특성 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Diagnostics.DebuggerDisplayAttribute>는 개체, 속성 또는 필드가 디버거 변수 창에 표시되는 방식을 제어합니다. 이 특성은 형식, 대리자, 속성, 필드 및 어셈블리에 적용할 수 있습니다.  
  
 `DebuggerDisplay` 특성에는 형식 인스턴스에 대한 값 열에 표시되는 문자열인 단일 인수가 있습니다. 이 문자열에는 중괄호(`{` 및 `}`)가 포함될 수 있습니다. 중괄호 쌍 안의 텍스트는 필드, 속성 또는 메서드로 확인됩니다.  
  
 클래스에 재정의된 `ToString()` 메서드가 있는 경우 디버거에서는 기본 `{<typeName>}`대신 재정의된 메서드를 사용합니다. 따라서 `ToString()` 메서드를 재정의한 경우 디버거는 기본`{<typeName>}`대신 재정의된 메서드를 사용하므로 `DebuggerDisplay`를 사용할 필요가 없습니다. 둘 모두 사용하는 경우에는 `DebuggerDisplay` 특성이 재정의된 `ToString()` 메서드보다 우선합니다.  
  
 디버거가 이 암시적 `ToString()` 호출을 평가할지 여부는 **도구/옵션/디버깅** 대화 상자의 사용자 설정에 따라 결정됩니다. Visual Basic에서는 이 암시적 `ToString()` 평가를  구현하지 않습니다.  
  
> [!IMPORTANT]
> **변수 창에서 개체의 원시 구조체 표시** 확인란이 **도구/옵션/디버깅** 대화 상자에서 선택되어 있는 경우 `DebuggerDisplay` 특성이 무시됩니다.  
  
 다음 표에서는 `DebuggerDisplay` 특성의 사용 예와 예제 출력을 보여 줍니다.  
  
|특성|**값** 열에 표시 되는 출력|  
|---------------|------------------------------------------------|  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> `x` 및 `y`필드가 있는 형식에서 사용됩니다.|`x = 5 y = 18`|  
|`[DebuggerDisplay("String value is {getString()}")]`매개 변수 구문은 언어에 따라 다를 수 있으므로 주의하여 사용하십시오.|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` 는 명명된 매개 변수도 받아들일 수 있습니다.  
  
|매개 변수|용도|  
|----------------|-------------|  
|`Name`, `Type`|이러한 매개 변수는 변수 창의 **이름** 및 **형식** 열에 영향을 주며, 생성자와 동일한 구문을 사용하여 문자열로 설정될 수 있습니다. 이러한 매개 변수를 지나치게 사용하거나 올바르지 않게 사용하면 혼란스러운 출력이 발생할 수 있습니다.|  
|`Target`, `TargetTypeName`|특성이 어셈블리 수준에서 사용되는 경우 대상 형식을 지정합니다.|  
  
 autoexp.cs 파일은 어셈블리 수준에서 DebuggerDisplay 특성을 사용합니다. autoexp.cs 파일은 Visual Studio에서 .NET 개체에 사용하는 기본 확장을 결정합니다. DebuggerDisplay 특성 사용 방법의 예제에서 autoexp.cs 파일을 검토하거나, autoexp.cs 파일을 수정하고 컴파일하여 기본 확장을 변경할 수 있습니다. autoexp.cs 파일은 수정하기 전에 백업해야 합니다.  
  
 Autoexp.cs를 빌드하려면 VS2015용 개발자 명령 프롬프트를 열고 다음 명령을 실행합니다.  
  
```  
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 Autoexp.dll에 대한 변경 내용은 다음 디버그 세션에서 선택됩니다.  
  
## <a name="using-expressions-in-debuggerdisplay"></a>DebuggerDisplay에서 식 사용  
 DebuggerDisplay 특성에서는 중괄호 사이에 일반 식을 사용할 수 있지만 이런 방식은 사용하지 않는 것이 좋습니다.  
  
 DebuggerDisplay의 일반 식에서는 대상 형식의 현재 인스턴스에 한해 `this` 포인터에 암시적으로 액세스할 수 있습니다. 식에서 별칭, 지역 변수 또는 포인터에는 액세스할 수 없습니다. 식에서 속성을 참조하는 경우 해당 속성의 특성은 처리되지 않습니다. 예를 들어 C# 코드 `[DebuggerDisplay("Object {count - 2}"`  는 `Object 6` 필드가 8인 경우 `count` 을 표시합니다.  
  
 DebuggerDisplay에서 식을 사용하면 다음과 같은 문제가 발생할 수 있습니다.  
  
- 식 계산은 디버거에서 가장 비용이 많이 드는 작업이며 식은 표시될 때마다 계산됩니다. 이는 코드를 단계별로 수행하는 동안 성능 문제를 야기할 수 있습니다. 예를 들어 컬렉션 또는 목록의 값을 표시하는 데 사용되는 복합 식은 요소 수가 많으면 매우 느려질 수 있습니다.  
  
- 식은 식을 작성한 언어의 식 계산기가 아닌 현재 스택 프레임 언어의 식 계산기에 의해 계산됩니다. 언어가 서로 다를 경우 이로 인해 예기치 않은 결과가 발생할 수 있습니다.  
  
- 식을 계산하면 애플리케이션의 상태가 변경될 수 있습니다. 예를 들어 속성의 값을 설정하는 식은 실행 코드에서 속성 값을 변경합니다.  
  
  식 계산의 가능한 문제를 줄이는 한 가지 방법은 작업을 수행하고 문자열을 반환하는 private 속성을 만드는 것입니다. 이렇게 하면 DebuggerDisplay 특성이 private 속성 값을 표시할 수 있습니다. 다음 예제에서는 이 패턴을 구현합니다.  
  
```csharp  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
public sealed class MyClass   
{      
    public int count { get; set; }      
    public bool flag { get; set; }      
    private string DebuggerDisplay  
   {         
        get  
        {  
             return string.Format("("Object {0}", count - 2);  
        }      
    }  
}  
```  
  
## <a name="example"></a>예제  
 다음 코드 예제에서는 `DebuggerDisplay`와 `DebuggerBrowseable` 및 `DebuggerTypeProxy`를 함께 사용하는 방법을 보여 줍니다. **조사식** 창과 같은 디버거 변수 창에 이 코드가 표시될 때는 다음과 같은 확장이 생성됩니다.  
  
|**이름**|**값**|**Type**|  
|--------------|---------------|--------------|  
|Key|"three"|object {string}|  
|값|3|object {int}|  
  
```csharp  
[DebuggerDisplay("{value}", Name = "{key}")]  
internal class KeyValuePairs  
{  
    private IDictionary dictionary;  
    private object key;  
    private object value;  
    public KeyValuePairs(IDictionary dictionary, object key, object value)  
    {  
        this.value = value;  
        this.key = key;  
        this.dictionary = dictionary;  
    }  
  
    public object Key  
    {  
        get { return key; }  
        set  
        {  
            object tempValue = dictionary[key];  
            dictionary.Remove(key);  
            key = value;  
            dictionary.Add(key, tempValue);  
        }  
    }  
  
    public object Value  
    {  
        get { return this.value; }  
        set  
        {  
            this.value = value;  
            dictionary[key] = this.value;  
        }  
    }  
}  
  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable  
{  
    public Hashtable hashtable;  
  
    public MyHashtable()  
    {  
        hashtable = new Hashtable();    
    }    private string DebuggerDisplay    {        get { return "Count = " + hashtable.Count); }    }  
  
    private class HashtableDebugView  
    {  
        private MyHashtable myhashtable;  
        public HashtableDebugView(MyHashtable myhashtable)  
        {  
            this.myhashtable = myhashtable;  
        }  
  
        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]  
        public KeyValuePairs[] Keys  
        {  
            get  
            {  
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];  
  
                int i = 0;  
                foreach (object key in myhashtable.hashtable.Keys)  
                {  
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);  
                    i++;  
                }  
                return keys;  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [DebuggerTypeProxy 특성을 사용 하](../debugger/using-debuggertypeproxy-attribute.md) 여 [디버거 표시 특성을 사용 하 여 디버깅 향상](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
