---
title: Microsoft Fakes의 코드 생성, 컴파일 및 명명 규칙 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffcab2800168ab6d66426c2e7beb77a158ced1eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851826"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Microsoft Fakes의 코드 생성, 컴파일 및 명명 규칙
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 Fakes 코드 생성 및 컴파일의 옵션과 문제에 대해 설명하고 Fakes 생성 형식, 멤버 및 매개 변수에 대한 명명 규칙을 설명합니다.

 **요구 사항**

- Visual Studio Enterprise

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 항목 내용
 [코드 생성 및 컴파일](#BKMK_Code_generation_and_compilation)

- [스텁의 코드 생성 구성](#BKMK_Configuring_code_generation_of_stubs) • [형식 필터링](#BKMK_Type_filtering) • [구체적인 클래스 및 가상 메서드 스텁](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [내부 형식](#BKMK_Internal_types) • [빌드 시간 최적화](#BKMK_Optimizing_build_times) • [어셈블리 이름 충돌 방지](#BKMK_Avoiding_assembly_name_clashing)

  [Fakes 명명 규칙](#BKMK_Fakes_naming_conventions)

- [Shim 형식 및 스텁 형식 명명 규칙](#BKMK_Shim_type_and_stub_type_naming_conventions) • [Shim 대리자 속성 또는 스텁 대리자 필드 명명 규칙](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) • [매개 변수 형식 명명 규칙](#BKMK_Parameter_type_naming_conventions) • [재귀 규칙](#BKMK_Recursive_rules)

  [외부 리소스](#BKMK_External_resources)

- [지침](#BKMK_Guidance)

## <a name="code-generation-and-compilation"></a><a name="BKMK_Code_generation_and_compilation"></a> 코드 생성 및 컴파일

### <a name="configuring-code-generation-of-stubs"></a><a name="BKMK_Configuring_code_generation_of_stubs"></a> 스텁의 코드 생성 구성
 스텁 형식의 생성은 .fakes 파일 확장명을 가진 XML 파일에서 구성됩니다. Fakes 프레임워크는 사용자 지정 MSBuild 작업을 통해 빌드 프로세스에서 통합되고 빌드 시 해당 파일을 검색합니다. Fakes 코드 생성기는 스텁 형식을 어셈블리로 컴파일하고 프로젝트에 대한 참조를 추가합니다.

 다음 예제에서는 FileSystem.dll에 정의된 스텁 형식을 보여 줍니다.

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>

```

### <a name="type-filtering"></a><a name="BKMK_Type_filtering"></a> 형식 필터링
 .fakes 파일에서 필터를 설정하여 스텁해야 하는 형식을 제한할 수 있습니다. StubGeneration 요소 아래에 Clear, Add, Remove 요소를 무제한으로 추가하여 선택한 형식 목록을 빌드할 수 있습니다.

 예를 들어 이 .fakes 파일은 형식에 대한 스텁을 System 및 System.IO 네임스페이스에 생성하지만 System에서 "Handle"을 포함하는 형식은 제외합니다.

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Clear />
    <Add Namespace="System!" />
    <Add Namespace="System.IO!"/>
    <Remove TypeName="Handle" />
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

 필터 문자열은 간단한 문법을 사용하여 일치를 수행하는 방법을 정의합니다.

- 필터는 기본적으로 대/소문자를 구분하지 않으며 부분 문자열 일치를 수행합니다.

     `el`는 "hello"와 일치합니다.

- 필터의 끝에 `!`를 추가하여 정확하게 대/소문자를 구분하여 일치하도록 합니다.

     `el!`는 "hello"와 일치하지 않습니다.

     `hello!`는 "hello"와 일치합니다.

- 필터의 끝에 `*`를 추가하여 문자열의 접두사가 일치하도록 합니다.

     `el*`는 "hello"와 일치하지 않습니다.

     `he*`는 "hello"와 일치합니다.

- 세미콜론으로 구분된 목록의 여러 필터는 분리로 결합됩니다.

     `el;wo`는 "hello" 및 "world"와 일치합니다.

### <a name="stubbing-concrete-classes-and-virtual-methods"></a><a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a> 구체적인 구체적인 클래스 및 가상 메서드
 기본적으로 스텁 형식은 봉인되지 않은 모든 클래스에 대해 생성됩니다. .fakes 구성 파일을 통해 스텁 형식을 추상 클래스로 제한할 수 있습니다.

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Types>
      <Clear />
      <Add AbstractClasses="true"/>
    </Types>
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

### <a name="internal-types"></a><a name="BKMK_Internal_types"></a> 내부 형식
 Fakes 코드 생성기는 생성된 Fakes 어셈블리에 표시되는 형식에 대해 shim 형식 및 스텁 형식을 생성합니다. Fakes에 표시되는 shim된 어셈블리 및 테스트 어셈블리의 내부 형식을 만들려면 생성된 Fakes 어셈블리 및 테스트 어셈블리에 표시 유형을 지정하는 shim된 어셈블리 코드에 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 특성을 추가합니다. 예를 들면 다음과 같습니다.

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

 **강력한 이름이 지정된 어셈블리의 내부 형식**

 shim된 어셈블리에 강력한 이름을 지정하고 어셈블리의 내부 형식에 액세스하려는 경우:

- 테스트 어셈블리와 Fakes 어셈블리에 모두 강력한 이름을 지정해야 합니다.

- 테스트 및 Fakes 어셈블리의 공용 키를 shim된 어셈블리의 **InternalsVisibleToAttribute** 특성에 추가해야 합니다. 다음은 shim된 어셈블리에 강력한 이름을 지정할 경우 shim된 어셈블리 코드의 예제 특성이 표시되는 모양입니다.

  ```csharp
  // FileSystem\AssemblyInfo.cs
  [assembly: InternalsVisibleTo("FileSystem.Fakes",
      PublicKey=<Fakes_assembly_public_key>)]
  [assembly: InternalsVisibleTo("FileSystem.Tests",
      PublicKey=<Test_assembly_public_key>)]
  ```

  shim된 어셈블리에 강력한 이름을 지정하는 경우 Fakes 프레임워크는 생성된 Fakes 어셈블리에 자동으로 강력하게 설명합니다. 테스트 어셈블리에 강력하게 서명해야 합니다. [강력한 이름의 어셈블리 만들기 및 사용](https://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9)을 참조하세요.

  Fakes 프레임워크는 동일한 키를 사용하여 생성된 모든 어셈블리에 서명하므로 이 코드 조각을 시작 지점으로 사용하여 fakes 어셈블리에 대한 **InternalsVisibleTo** 특성을 shim된 어셈블리 코드에 추가할 수 있습니다.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

 **.snk** `KeyFile` `Fakes` \\ `Compilation` **Fakes** 파일의 요소에서 대체 키를 특성 값으로 포함 하는 .snk 파일의 전체 경로를 지정 하 여 shim 어셈블리에 대해 만든 키와 같은 Fakes 어셈블리에 대해 다른 공개 키를 지정할 수 있습니다. 예를 들면 다음과 같습니다.

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>

```

 그런 다음 대체 **.snk** 파일의 공용 키를 Fakes 어셈블리에 대한 InternalVisibleTo 특성의 두 번째 매개 변수로 shim된 어셈블리 코드에서 사용해야 합니다.

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

 위의 예제에서 `Alternate_public_key` 및 `Test_assembly_public_key` 값은 같을 수 있습니다.

### <a name="optimizing-build-times"></a><a name="BKMK_Optimizing_build_times"></a> 빌드 시간 최적화
 Fakes 어셈블리를 컴파일하면 빌드 시간이 현저하게 길어질 수 있습니다. .NET 시스템 어셈블리 및 타사 어셈블리에 대한 Fakes 어셈블리를 별도의 중앙 집중식 프로젝트에 생성하면 빌드 시간을 최소화할 수 있습니다. 이러한 어셈블리는 컴퓨터에서 거의 변경되지 않으므로 생성된 Fakes 어셈블리를 다른 프로젝트에서 다시 사용할 수 있습니다.

 단위 테스트 프로젝트에서 프로젝트 폴더의 FakesAssemblies 아래에 배치된 컴파일된 Fakes 어셈블리에 대한 참조를 사용할 수 있습니다.

1. 테스트 프로젝트와 일치하는 .NET 런타임 버전을 사용하여 새 클래스 라이브러리를 만듭니다. 이 라이브러리를 Fakes.Prebuild라고 하겠습니다. 프로젝트에서 필요 없는 class1.cs 파일을 제거합니다.

2. Fakes가 필요한 모든 시스템 및 타사 어셈블리에 대한 참조를 추가합니다.

3. 각 어셈블리에 대한 .fakes 파일을 추가하고 빌드합니다.

4. 테스트 프로젝트에서 다음을 수행합니다.

    - Fakes 런타임 DLL에 대한 참조가 있는지 확인합니다.

         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll

    - Fakes를 만든 각 어셈블리에 대해 프로젝트의 Fakes.Prebuild\FakesAssemblies 폴더에서 해당 DLL 파일에 대한 참조를 추가합니다.

### <a name="avoiding-assembly-name-clashing"></a><a name="BKMK_Avoiding_assembly_name_clashing"></a> 어셈블리 이름 충돌 방지 방지
 팀 빌드 환경에서는 모든 빌드 출력이 단일 디렉터리에 병합됩니다. Fakes를 사용하는 프로젝트가 여러 개인 경우 서로 다른 버전의 Fakes 어셈블리가 서로를 재정의할 수 있습니다. 예를 들어 .NET Framework 2.0의 TestProject1 fakes mscorlib.dll과 .NET Framework 4의 TestProject2 fakes mscorlib.dll 모두 mscorlib.Fakes.dll Fakes 어셈블리를 생성할 수 있습니다.

 이 문제를 방지하려면 Fakes가 .fakes 파일을 추가할 때 프로젝트 이외 참조에 대해 버전 정규화된 Fakes 어셈블리 이름을 자동으로 만들어야 합니다. 버전 정규화된 Fakes 어셈블리 이름은 Fakes 어셈블리 이름을 만들 때 버전 번호를 포함합니다.

 어셈블리에 MyAssembly 및 버전 1.2.3.4를 지정하는 경우 Fakes 어셈블리 이름은 MyAssembly.1.2.3.4.Fakes입니다.

 이 버전은 .fakes에서 어셈블리 요소의 버전 특성을 편집하여 변경하거나 제거할 수 있습니다.

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>

```

## <a name="fakes-naming-conventions"></a><a name="BKMK_Fakes_naming_conventions"></a> Fakes 명명 규칙

### <a name="shim-type-and-stub-type-naming-conventions"></a><a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a> Shim 형식 및 스텁 형식 명명 규칙
 **네임스페이스**

- 네임스페이스에 .Fakes 접미사를 추가합니다.

   예를 들어 `System.Fakes` 네임스페이스에는 System 네임스페이스의 shim 형식이 포함됩니다.

- Global.Fakes에는 빈 네임스페이스의 shim 형식이 포함됩니다.

  **형식 이름**

- Shim 접두사를 형식 이름에 추가하여 shim 형식 이름을 작성합니다.

   예를 들어 ShimExample은 Example 형식의 shim 형식입니다.

- 스텁 접두사를 형식 이름에 추가하여 스텁 형식 이름을 작성합니다.

   예를 들어 StubIExample은 IExample 형식의 스텁 형식입니다.

  **형식 인수 및 중첩된 형식 구조**

- 제네릭 형식 인수가 복사됩니다.

- 중첩된 형식 구조는 shim 형식에 대해 복사됩니다.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a><a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a> Shim 대리자 속성 또는 스텁 대리자 필드 명명 규칙
 필드 명명에 대한 **기본 규칙**이며, 빈 이름에서 시작합니다.

- 메서드 이름을 추가합니다.

- 메서드 이름이 명시적 인터페이스 구현인 경우 점이 제거됩니다.

- 메서드가 제네릭인 경우 `Of`*n*이 추가됩니다. 여기서 *n*은 제네릭 메서드 인수 수입니다.

  속성 getter 또는 setter와 같은 **특수 메서드 이름은** 다음 표에 설명 된 대로 처리 됩니다.

|메서드 특성...|예|추가되는 메서드 이름|
|-------------------|-------------|--------------------------|
|**생성자**|`.ctor`|`Constructor`|
|정적 **생성자**|`.cctor`|`StaticConstructor`|
|메서드 이름이 "_"로 구분되는 두 부분으로 구성된 **접근자**(예: 속성 getter)|*kind_name*(일반적인 경우이지만 ECMA에 의해 강제되지 않음)|*NameKind*, 여기서 두 부분이 대문자로 처리되고 교환됨|
||`Prop` 속성의 getter|`PropGet`|
||`Prop` 속성의 setter|`PropSet`|
||이벤트 adder|`Add`|
||이벤트 remover|`Remove`|
|두 부분으로 구성된 **연산자**|`op_name`|`NameOp`|
|예: + 연산자|`op_Add`|`AddOp`|
|**변환 연산자**의 경우 반환 형식이 추가됩니다.|`T op_Implicit`|`ImplicitOpT`|

 **참고**

- **인덱서의 getter 및 setter**는 속성과 유사하게 처리됩니다. 인덱서의 기본 이름은 `Item`입니다.

- **매개 변수 형식** 이름은 변형되고 연결됩니다.

- **반환 형식**은 오버로드 모호성이 제거될 때까지 무시됩니다. 이런 경우 반환 형식은 이름의 끝에 추가됩니다.

### <a name="parameter-type-naming-conventions"></a><a name="BKMK_Parameter_type_naming_conventions"></a> 매개 변수 형식 명명 규칙

|조건|추가되는 문자열...|
|-----------|-------------------------|
|**형식**`T`|T<br /><br /> 네임스페이스, 중첩 구조 및 제네릭 tics가 삭제됩니다.|
|**Out 매개 변수**`out T`|`TOut`|
|**ref 매개 변수** `ref T`|`TRef`|
|**배열 형식**`T[]`|`TArray`|
|**다차원 배열** 형식 `T[ , , ]`|`T3`|
|**포인터** 형식 `T*`|`TPtr`|
|**제네릭 형식**`T<R1, …>`|`TOfR1`|
|형식의 **제네릭 형식 인수** `!i``C<TType>`|`Ti`|
|메서드의 **제네릭 메서드 인수** `!!i``M<MMethod>`|`Mi`|
|**중첩 형식**`N.T`|`N`이 추가된 다음 `T`|

### <a name="recursive-rules"></a><a name="BKMK_Recursive_rules"></a> 재귀 규칙
 다음 규칙은 재귀적으로 적용됩니다.

- Fakes는 C#을 사용하여 Fakes 어셈블리를 생성하므로 잘못된 C# 토큰을 생성하는 모든 문자는 "_"(밑줄)로 이스케이프됩니다.

- 결과 이름이 선언 형식의 멤버와 충돌하는 경우 01부터 시작하는 두 자리 카운터를 추가하여 번호 매기기 구성표를 사용합니다.

## <a name="external-resources"></a><a name="BKMK_External_resources"></a> 외부 리소스

### <a name="guidance"></a><a name="BKMK_Guidance"></a> 지침
 [Visual Studio 2012를 사용한 연속 배달 테스트 - 2장: 단위 테스트: 내부 테스트](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>관련 항목
 [Microsoft Fakes를 사용하여 테스트 중인 코드 격리](../test/isolating-code-under-test-with-microsoft-fakes.md)
