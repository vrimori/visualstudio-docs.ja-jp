---
title: "CA2118: SuppressUnmanagedCodeSecurityAttribute の使用法を再確認します | Microsoft Docs"
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
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
helpviewer_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2118: SuppressUnmanagedCodeSecurityAttribute の使用法を再確認します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 パブリック型、プロテクト型、パブリック メンバー、またはプロテクト メンバーに、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 属性があります。  
  
## 規則の説明  
 COM 相互運用機能またはプラットフォーム呼び出し機能を使用してアンマネージ コードを呼び出すメンバーの場合、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> によって、既定のセキュリティ システムの動作が変わります。  一般に、アンマネージ コード アクセス許可に[データとモデリング](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)が作成されます。  この要求は、実行時にメンバーを呼び出すと必ず発生し、コール スタックのすべての呼び出し元のアクセス許可がチェックされます。  属性が存在する場合、アクセス許可の[リンク確認要求](../Topic/Link%20Demands.md)が作成されます。直接の呼び出し元のアクセス許可は、呼び出し元が JIT でコンパイルされたときにチェックされます。  
  
 この属性は、主にパフォーマンスを向上するために使用されますが、パフォーマンスが向上するとセキュリティ上のリスクも高くなります。  ネイティブのメソッドを呼び出すパブリック メンバーにこの属性を指定すると、コール スタックの呼び出し元 \(直前の呼び出し元以外\) は、アンマネージ コードの実行にアンマネージ コード アクセス許可が必要でなくなります。  パブリック メンバーのアクションと入力処理によっては、信頼できない呼び出し元が、通常は信頼できるコードに制限されている機能にアクセスできることがあります。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] で現在のプロセスのアドレス空間に対する呼び出し元の直接アクセスを防ぐには、セキュリティ チェックが必要です。  この属性は通常のセキュリティを省略するため、コードでプロセスのメモリへの読み取りまたは書き込みに使用できる場合、セキュリティ上の問題は深刻になります。  このリスクは、プロセス メモリに意図的にアクセスできるメソッドに限定されない、ということに注意してください。悪意のあるコードが何らかの手段 \(予想できない入力、不適切な入力、または無効な入力を行うなど\) でアクセスできる場合もあります。  
  
 既定のセキュリティ ポリシーでは、アセンブリへのアンマネージ コード アクセス許可は認められていません。ただし、ローカル コンピューターから実行される場合と、次のグループのいずれかのメンバーである場合は例外です。  
  
-   My Computer Zone コード グループ  
  
-   Microsoft Strong Name コード グループ  
  
-   ECMA Strong Name コード グループ  
  
## 違反の修正方法  
 この属性が本当に必要かどうかについて、コードをよく確認します。  マネージ コードのセキュリティに精通していない場合、またはこの属性を使用した場合のセキュリティ実装について理解していない場合、コードからこの属性を削除します。  属性が必要な場合、悪意のある呼び出し元がコードを使用できないことを確認します。  このコードにアンマネージ コードを実行するアクセス許可がない場合、この属性は何も影響を及ぼさないため、削除します。  
  
## 警告を抑制する状況  
 この規則による警告を安全に抑制するには、破壊的な方法で使用できるネイティブの操作またはリソースに対するアクセス権を呼び出し元に付与しないようにします。  
  
## 使用例  
 この規則に違反する例を次に示します。  
  
 [!code-cs[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## 使用例  
 次の例では、`DoWork` メソッドで、プラットフォーム呼び出しメソッド `FormatHardDisk` に対してパブリックにアクセスできるコード パスを実現しています。  
  
 [!code-cs[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## 使用例  
 次の例では、パブリック メソッド `DoDangerousThing` で違反が発生します。  この違反を解決するには、`DoDangerousThing` をプライベートにし、セキュリティ要求によって保護されたパブリック メソッドを使用してアクセスします。`DoWork` メソッドはその例です。  
  
 [!CODE [FxCop.Security.TypeInvokeAndSuppress#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress#1)]  
  
## 参照  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines.md)   
 [Security Optimizations](http://msdn.microsoft.com/ja-jp/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [データとモデリング](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)   
 [リンク確認要求](../Topic/Link%20Demands.md)