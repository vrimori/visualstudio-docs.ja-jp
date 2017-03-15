---
title: "CLS に準拠していない &#39;MustOverride&#39; メンバーは、CLS に準拠している &lt;classname&gt; に使用できません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40034"
  - "vbc40034"
helpviewer_keywords: 
  - "BC40034"
ms.assetid: 4eb36b3a-1bbe-4e99-9ecb-a12b8729b128
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CLS に準拠していない &#39;MustOverride&#39; メンバーは、CLS に準拠している &lt;classname&gt; に使用できません
クラスは `<CLSCompliant(True)>` としてマークされていますが、`MustOverride` プロパティが含まれているか、`<CLSCompliant(False)>` としてマークされているプロシージャまたはマークされていないプロシージャが含まれています。  
  
 クラスが [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) に準拠している場合、そのクラスを使用するアプリケーションは、`<CLSCompliant(True)>` としてもマークされているメンバーにのみアクセスし、そのようにマークされていないメンバーは無視します。 ただし、アプリケーションは `MustOverride` プロパティやプロシージャを無視できません。アプリケーションは、そのプロパティまたはプロシージャをオーバーライドするためにそれにアクセスする必要があるためです。  
  
 プログラミング要素に <xref:System.CLSCompliantAttribute> を適用する場合は、準拠または非準拠を示すために、属性の `isCompliant` パラメーターを `True` または `False` のどちらかに設定します。 このパラメーターには既定値がありません。値を指定する必要があります。  
  
 要素に <xref:System.CLSCompliantAttribute> を適用しないと、その要素は非準拠と見なされます。  
  
 既定では、このメッセージは警告です。 警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](../ide/configuring-warnings-in-visual-basic.md)」を参照してください。  
  
 **エラー ID:** BC40034  
  
### このエラーを解決するには  
  
-   CLS への準拠が必要なときに、クラス ソース コードを制御できる場合は、メンバーを `<CLSCompliant(True)>` としてマークします。  
  
-   CLS への準拠が必要なときに、クラス ソース コードを制御できない場合や、クラス ソース コードが準拠のための要件を満たしていない場合は、このメンバーを別のクラス内で定義します。  
  
-   このメンバーを非準拠のままにしておく必要がある場合は、このメンバーの定義から `MustOverride` キーワードを削除するか、クラス定義から <xref:System.CLSCompliantAttribute> を削除するか、クラスを `<CLSCompliant(False)>` としてマークします。  
  
## 参照  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [\<PAVE OVER\> CLS 準拠コードの記述](http://msdn.microsoft.com/ja-jp/4c705105-69a2-4e5e-b24e-0633bc32c7f3)