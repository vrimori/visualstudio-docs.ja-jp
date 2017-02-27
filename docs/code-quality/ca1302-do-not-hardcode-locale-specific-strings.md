---
title: "CA1302: ロケール特有の文字列をハードコードしません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
helpviewer_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1302: ロケール特有の文字列をハードコードしません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|分類|Microsoft.Globalization|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドで、特殊なシステム フォルダーのパスの一部を表すリテラル文字列を使用しています。  
  
## 規則の説明  
 <xref:System.Environment.SpecialFolder?displayProperty=fullName> 列挙体には、特殊なシステム フォルダーを参照するメンバーが含まれます。  このフォルダーの位置は、オペレーティング システムによって異なる場合、ユーザーが位置を変更する場合、および位置がローカライズされる場合があります。  特別なフォルダーの例として、システム フォルダーがあります。これは、[!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] では C:\\WINDOWS\\system32 ですが、[!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)] では C:\\WINNT\\system32 です。  <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> メソッドは、<xref:System.Environment.SpecialFolder> 列挙に関連付けられた位置を返します。  <xref:System.Environment.GetFolderPath%2A> から返された位置は、現在実行されているコンピューターに合わせてローカライズされます。  
  
 この規則は、<xref:System.Environment.GetFolderPath%2A> メソッドを使用して取得したフォルダーのパスを、別のディレクトリ レベルにトークン化します。  各リテラル文字列はこのトークンと比較されます。  一致するものが見つかった場合、メソッドによって、トークンに関連付けられたシステム フォルダーを参照する文字列が構築されると想定されます。  特殊なシステム フォルダーの位置を取得するには、移植性と地域性を考慮して、リテラル文字列ではなく <xref:System.Environment.GetFolderPath%2A> メソッドを使用します。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Environment.GetFolderPath%2A> メソッドを使用して位置を取得します。  
  
## 警告を抑制する状況  
 <xref:System.Environment.SpecialFolder> 列挙体に関連付けられたシステム フォルダーのいずれかを参照するときに、リテラル文字列を使用していない場合は、この規則による警告を抑制しても安全です。  
  
## 使用例  
 共通のアプリケーション データ フォルダーのパスをビルドする方法を次の例に示します。この規則によって 3 つの警告が生成されます。  次に、<xref:System.Environment.GetFolderPath%2A> メソッドを使用してパスを取得します。  
  
 [!code-cs[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## 関連規則  
 [CA1303: ローカライズされたパラメーターとしてリテラルを渡さないでください](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)