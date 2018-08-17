---
title: VSCT XML スキーマの条件付き属性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b31b99e38eeec2ff1e5e31bc6bdaeed3d3be3d83
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586822"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML スキーマの条件付き属性
条件付き属性は、すべてのリストとアイテムに適用できます。 論理演算子およびシンボルの拡張の式は、true または false に評価されます。 True の場合、結果の出力で、関連付けられているリストまたは項目が含まれます。  
  
 その他のトークンの拡張や定数に対してトークンの拡張をテストすることができます。 関数は、`Defined()`値が存在しない場合でも、特定の名前が定義されているかどうかをテストします。  
  
 Condition 属性がリストに適用されると、条件は、リスト内のすべての子要素に適用されます。 子要素自体に条件属性が含まれている場合、その条件が結合親式 AND 演算によって。  
  
 True の場合、値 1、'1' および 'true' に評価して 0、'0' および 'false' が false として評価されます。  
  
## <a name="operators"></a>演算子  
 条件付きの式を評価するのにには、次の演算子を使用します。  
  
|演算子|定義|  
|--------------|----------------|  
|(,)|グループ化|  
|!|論理 NOT|  
|\<, >, \<=, >=, ==, !=|関係と比較|  
|と、呼び出し|ブール型|  
|または|ブール型|  
  
## <a name="examples"></a>使用例  
  
```xml  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)