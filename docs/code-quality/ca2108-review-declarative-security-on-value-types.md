---
title: "CA2108: 値型での宣言セキュリティを確認します | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewDeclarativeSecurityOnValueTypes"
  - "CA2108"
helpviewer_keywords: 
  - "CA2108"
  - "ReviewDeclarativeSecurityOnValueTypes"
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2108: 値型での宣言セキュリティを確認します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|なし|  
  
## 原因  
 パブリックまたはプロテクトの値型が、[データとモデリング](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)または[リンク確認要求](../Topic/Link%20Demands.md)で保護されています。  
  
## 規則の説明  
 値型は、既定のコンストラクターが割り当てて初期化してから、別のコンストラクターが実行します。  値型が Demand または LinkDemand によって保護され、呼び出し元にそのセキュリティ チェックに適合するアクセス許可がない場合、既定以外のコンストラクターは失敗し、セキュリティ例外がスローされます。  値型の領域は解放されません。既定のコンストラクターで設定された状態のままになります。  値型のインスタンスを渡す呼び出し元に、そのインスタンスの作成またはアクセスの許可があると仮定しないでください。  
  
## 違反の修正方法  
 この規則違反を修正するには、型からセキュリティ チェックを取り除き、代わりにメソッド レベルのセキュリティ チェックを使用する必要があります。  この方法で違反を修正すると、適切なアクセス許可を持たない呼び出し元が、その値型のインスタンスを取得することを防ぐことはできません。  既定の状態にある値型のインスタンスによって機密情報が公開されないこと、不正な方法でそのインスタンスを使用できないことを確認します。  
  
## 警告を抑制する状況  
 呼び出し元が既定の状態にある値型のインスタンスを取得するときに、セキュリティ上の脅威がない場合は、この規則による警告を抑制できます。  
  
## 使用例  
 この規則に違反する値型を含むライブラリの例を次に示します。  `StructureManager` 型では、その値型のインスタンスを渡す呼び出し元に、そのインスタンスの作成またはアクセスの許可があると仮定しています。  
  
 [!code-cs[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## 使用例  
 ライブラリの弱点を説明するアプリケーション例を次に示します。  
  
 [!code-cs[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
  **Structure custom constructor: Request failed.**  
**New values SecuredTypeStructure 100 100**  
**New values SecuredTypeStructure 200 200**   
## 参照  
 [リンク確認要求](../Topic/Link%20Demands.md)   
 [データとモデリング](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)