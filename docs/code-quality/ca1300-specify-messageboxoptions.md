---
title: "CA1300: MessageBoxOption を指定します | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
helpviewer_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1300: MessageBoxOption を指定します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|分類|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドで、<xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> 引数を使用しない <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> メソッドのオーバーロードが呼び出されています。  
  
## 規則の説明  
 右から左への読み取り順序を使用するカルチャでメッセージ ボックスを正しく表示するには、<xref:System.Windows.Forms.MessageBoxOptions> 列挙体の <xref:System.Windows.Forms.MessageBoxOptions> メンバーと <xref:System.Windows.Forms.MessageBoxOptions> メンバーを、<xref:System.Windows.Forms.MessageBox.Show%2A> メソッドに渡す必要があります。  格納しているコントロールの <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> プロパティを検証し、右から左への読み取り順序を使用するかどうかを判断します。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Windows.Forms.MessageBoxOptions> 引数を使用する <xref:System.Windows.Forms.MessageBox.Show%2A> メソッドのオーバーロードを呼び出します。  
  
## 警告を抑制する状況  
 右から左への読み取り順序を使用するカルチャ向けにコード ライブラリをローカライズしない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 カルチャの読み取り順序に合わせたオプションが含まれるメッセージ ボックスを表示するメソッドを次の例に示します。  ここにリソース ファイルは示しませんが、この例をビルドする場合には必要です。  リソース ファイルなしでこの例をビルドして、右から左への読み取り機能をテストするには、コードのコメントを参照してください。  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-cs[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## 参照  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [デスクトップ アプリケーションのリソース](../Topic/Resources%20in%20Desktop%20Apps.md)