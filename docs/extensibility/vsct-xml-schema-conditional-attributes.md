---
title: "VSCT XML スキーマの条件付き属性 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0a434800fef7029460854107e79f29a71c75285
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML スキーマの条件付き属性
条件付き属性は、すべてのリストと項目に適用可能性があります。 論理演算子およびシンボル拡張式は、true または false に評価されます。 True の場合、関連付けられているリストまたは項目が、結果の出力に含まれます。  
  
 トークンの拡張は、その他のトークンの拡張や定数に対してテストできます。 知り関数は値が存在しない場合でも、特定の名前が定義されているかどうかをテストするために使用します。  
  
 Condition 属性は、一覧に適用するときに、条件は、リスト内のすべての子要素に適用されます。 子要素自体に、Condition 属性が含まれている場合、その条件が結合親式 AND 演算によってです。  
  
 True として 1、'1' と 'true' の値が評価され、0、'0' および 'false' が false として評価されます。  
  
## <a name="operators"></a>演算子  
 次の演算子は、条件付きの式の評価に使用できます。  
  
|演算子|定義|  
|--------------|----------------|  
|(,)|グループ化|  
|!|論理 NOT|  
|\<, >, \<=, >=, ==, !=|関係と比較|  
|と、呼び出し|ブール型|  
|または|ブール型|  
  
## <a name="examples"></a>例  
  
```  
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
 [Visual Studio Command Table (.Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)