---
title: "VSCT XML スキーマの条件付き属性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "条件付き属性、VSCT XML スキーマ要素"
  - "条件付きの属性 (VSCT XML スキーマ)"
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# VSCT XML スキーマの条件付き属性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

条件付き属性は、すべてのリストとアイテムに適用することがあります。 論理演算子およびシンボルの拡張の式は、true または false に評価されます。 True の場合、関連付けられているリストまたは項目が結果の出力で含まれています。  
  
 その他のトークンの拡張や定数に対しては、トークンの拡張をテストできます。 知り関数は値が存在しない場合でも、特定の名前が定義されているかどうかをテストするために使用します。  
  
 一覧には、Condition 属性を適用するときに、条件は、リスト内のすべての子要素に適用します。 子要素自体に Condition 属性が含まれている場合、その条件が結合親式と操作を実行しました。  
  
 値 1、'1' および 'true' が true として評価され、0、'0' および 'false' が false に評価されました。  
  
## 演算子  
 次の演算子は、条件式の評価に使用可能性があります。  
  
|演算子|定義|  
|---------|--------|  
|\(,\)|グループ化|  
|\!|論理 NOT|  
|\<, \>, \<\=, \>\=, \=\=, \!\=|リレーショナルと等しいかどうか|  
|および|ブール型|  
|、または|ブール型|  
  
## 例  
  
```  
<Menu Condition="Defined(DEBUG)" … </Menu> <Menu Condition="%(SKU_MODE) = 'Demo'" … </Menu> <Menus Condition="Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menus Condition="Defined(DEMO_SKU)"> <Menus Condition="!Defined(DEBUG)"> <Menu … </Menu> </Menus> <Menu … </Menu> </Menus> <Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU)) and !Defined(DEBUG)"> <Menu … </Menu> </Menus>  
```  
  
## 参照  
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)