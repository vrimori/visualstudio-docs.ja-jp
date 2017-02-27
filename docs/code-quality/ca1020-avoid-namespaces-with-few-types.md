---
title: "CA1020: 型をほとんど含まない名前空間を使用しません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1020"
  - "AvoidNamespacesWithFewTypes"
helpviewer_keywords: 
  - "AvoidNamespacesWithFewTypes"
  - "CA1020"
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1020: 型をほとんど含まない名前空間を使用しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 グローバル名前空間以外に、型数が 5 つ未満である名前空間があります。  
  
## 規則の説明  
 配置する型数の少ない名前空間を作成する場合、各名前空間を論理的に構成し、有効な理由を付けます。  名前空間には、ほとんどの状況で併用される型を含めます。  このとき、複数のアプリケーションが同時に指定できなければ、型を別の名前空間に配置します。  たとえば、<xref:System.Web.UI> 名前空間には Web アプリケーションで使用される型を含め、<xref:System.Windows.Forms> 名前空間には [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] ベースのアプリケーションで使用される型を含めます。  名前空間の両方にユーザー インターフェイス \(UI\) を制御する型が含まれる場合でも、これらの型は同じアプリケーションで使用するためのものではありません。  そのため、別の名前空間にあります。  名前空間を慎重に構築することで、機能の発見可能性も改善されます。  名前空間の階層構造を検討することで、ライブラリを使用するときに、機能を実装する型の位置を特定できるようになります。  
  
> [!NOTE]
>  このガイドラインに準拠するには、デザイン時の型とアクセス許可を別の名前空間にマージしないようにします。  このような型は、メインの名前空間の下位にある独自の名前空間に所属します。また、名前空間の末尾にはそれぞれ `.Design` と `.Permissions` が付きます。  
  
## 違反の修正方法  
 この規則違反を修正するには、型数が少ない複数の名前空間を 1 つの名前空間に結合します。  
  
## 警告を抑制する状況  
 名前空間に別の名前空間の型と併用される型が含まれない場合は、この規則による警告を抑制しても安全です。