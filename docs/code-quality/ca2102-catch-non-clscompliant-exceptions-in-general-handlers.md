---
title: "CA2102: 汎用ハンドラーの CLSCompliant でない例外をキャッチします | Microsoft Docs"
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
  - "CA2102"
  - "CatchNonClsCompliantExceptionsInGeneralHandlers"
helpviewer_keywords: 
  - "CA2102"
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2102: 汎用ハンドラーの CLSCompliant でない例外をキャッチします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|なし|  
  
## 原因  
 アセンブリ内の <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> でマークされていないメンバーまたは `RuntimeCompatibility(WrapNonExceptionThrows = false)` でマークされているメンバーには、<xref:System.Exception?displayProperty=fullName> を処理する catch ブロックがあり、その直後に汎用 catch ブロックはありません。  この規則は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] アセンブリを無視します。  
  
## 規則の説明  
 <xref:System.Exception> を処理する catch ブロックは、共通言語仕様 \(CLS: Common Language Specification\) に準拠した例外はすべてキャッチしますが、  CLS に準拠しない例外はキャッチしません。  CLS に準拠しない例外は、ネイティブ コードや Microsoft Intermediate Language \(MSIL\) アセンブラーで生成されたマネージ コードからスローされます。  ただし、C\# コンパイラおよび [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラでは CLS に準拠しない例外をスローできず、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] は CLS に準拠しない例外をキャッチしません。  catch ブロックによってすべての例外を処理する場合は、次の汎用 catch ブロック構文を使用します。  
  
-   C\#: `catch {}`  
  
-   C\+\+: `catch(...) {}` または `catch(Object^) {}`  
  
 以前に許可されたアクセス許可が catch ブロックから削除されると、CLS に準拠しない未処理の例外がセキュリティ問題に変わります。  CLS に準拠しない例外はキャッチされないため、CLS に準拠しない例外をスローする悪意のあるメソッドを昇格したアクセス許可で実行できることがあります。  
  
## 違反の修正方法  
 すべての例外のキャッチを目的とする場合に、この規則違反を修正するには、汎用 catch ブロックを代用または追加するか、アセンブリを `RuntimeCompatibility(WrapNonExceptionThrows = true)` とマークします。  catch ブロック内のアクセス許可が削除された場合は、汎用 catch ブロック内の機能を複製します。  すべての例外の処理を目的としない場合は、<xref:System.Exception> を処理する catch ブロックを削除し、代わりに特定の種類の例外を処理する catch ブロックを追加します。  
  
## 警告を抑制する状況  
 CLS に準拠しない例外を生成する可能性のあるステートメントが try ブロックに含まれていない場合は、この規則による警告を抑制しても安全です。  ネイティブ コードやマネージ コードは CLS に準拠しない例外をスローする可能性があるため、try ブロック内の各コード パスで実行されるコードをすべて把握している必要があります。  ただし、共通言語ランタイムは CLS に準拠しない例外をスローしません。  
  
## 使用例  
 次の例は、CLS に準拠しない例外をスローする MSIL クラスを示しています。  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## 使用例  
 次の例は、この規則に準拠する汎用 catch ブロックを含むメソッド示しています。  
  
 [!code-cs[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 上記のコード例を次のようにコンパイルします。  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## 関連規則  
 [CA1031: 一般的な例外の種類はキャッチしません](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)  
  
## 参照  
 [例外と例外処理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe \(IL アセンブラー\)](../Topic/Ilasm.exe%20\(IL%20Assembler\).md)   
 [Overriding Security Checks](http://msdn.microsoft.com/ja-jp/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)