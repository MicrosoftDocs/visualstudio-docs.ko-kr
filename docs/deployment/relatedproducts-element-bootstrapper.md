---
title: '&lt;RelatedProducts &gt; 요소 (부트스트래퍼) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42756b21e631ec14e9c590833f6f0e95a317cc22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66747466"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts &gt; 요소 (부트스트래퍼)
`RelatedProducts`요소는 현재 제품에 종속 되거나 포함 된 다른 제품을 정의 합니다.

## <a name="syntax"></a>Syntax

```xml
<RelatedProducts>
    <DependsOnProduct
        Code
    />
    <EitherProducts>
        <DependsOnProduct
            Code
        />
    </EitherProducts>
    <IncludesProduct
        Code
    />
</RelatedProducts>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 요소는 `RelatedProducts` 요소의 자식입니다 `Product` . 특성이 없습니다.

## <a name="dependsonproduct"></a>DependsOnProduct
 `DependsOnProduct`요소는 현재 제품이 명명 된 제품에 의존 하 고 명명 된 제품이 현재 설치 되어 있어야 함을 나타냅니다. 요소의 자식입니다 `RelatedProducts` . 요소에는 `RelatedProducts` 하나 이상의 요소가 있을 수 있습니다 `DependsOnProduct` .

 `DependsOnProduct` 에는 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Code`|요소의 특성에 지정 된 대로 포함 된 제품의 코드 이름 `ProductCode` `Product` 입니다. 자세한 내용은 [\<Product> 요소](../deployment/product-element-bootstrapper.md)를 참조하세요.|

## <a name="eitherproducts"></a>EitherProducts
 `EitherProducts`요소는 0 개 이상의 `DependsOnProduct` 요소를 정의 하며에는 특성이 없습니다. 이 집합에 있는 하나 이상의를 `DependsOnProduct` 현재 제품 보다 먼저 설치 해야 합니다. 요소에는 `RelatedProducts` 0 개 이상의 요소가 있을 수 있습니다 `EitherProducts` .

## <a name="includesproduct"></a>IncludesProduct
 `IncludesProduct`요소는 제품이 현재 설치에 포함 되어 있으며 별도의 설치를 요구 하지 않음을 나타냅니다. 요소의 자식입니다 `RelatedProducts` . 요소에는 `RelatedProducts` 하나 이상의 요소가 있을 수 있습니다 `IncludesProduct` .

 `IncludesProduct` 에는 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`Code`|요소의 특성에 지정 된 대로 포함 된 제품의 코드 이름 `ProductCode` `Product` 입니다. 자세한 내용은 [\<Product> 요소](../deployment/product-element-bootstrapper.md)를 참조하세요.|

## <a name="example"></a>예
 다음 코드 예제에서는 Microsoft 설치 관리자가 .NET Framework와 함께 설치 되도록 지정 하므로 별도의 설치가 필요 하지 않습니다.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>추가 정보
- [\<Product> 요소인](../deployment/product-element-bootstrapper.md)