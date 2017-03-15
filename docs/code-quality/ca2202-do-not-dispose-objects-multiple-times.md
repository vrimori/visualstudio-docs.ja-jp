---
title: "CA2202: オブジェクトを複数回破棄しません | Microsoft Docs"
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
  - "CA2202"
  - "Do not dispose objects multiple times"
  - "DoNotDisposeObjectsMultipleTimes"
helpviewer_keywords: 
  - "CA2202"
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2202: オブジェクトを複数回破棄しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 メソッドの実装に、同じオブジェクトに対して <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> または Dispose と同等の操作 \(たとえば、一部の型に対する Close\(\) メソッドなど\) を複数回呼び出すコード パスが含まれています。  
  
## 規則の説明  
 正しく実装された <xref:System.IDisposable.Dispose%2A> メソッドは、複数回呼び出しても例外はスローされません。  しかし、これは保証されているわけではありません。<xref:System.ObjectDisposedException?displayProperty=fullName> が生成されないようにするには、同じオブジェクトに対して <xref:System.IDisposable.Dispose%2A> を複数回呼び出さないようにします。  
  
## 関連規則  
 [CA2000: スコープが失われる前にオブジェクトを破棄します](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## 違反の修正方法  
 この規則違反を修正するには、コード パスに関係なく、<xref:System.IDisposable.Dispose%2A> がオブジェクトに対して 1 回のみ呼び出されるように実装を変更します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  オブジェクトに対して <xref:System.IDisposable.Dispose%2A> を複数回呼び出しても安全なことが判明している場合でも、実装が将来変更される可能性があります。  
  
## 使用例  
 入れ子になった `using` ステートメント \(Visual Basic では `Using`\) は、CA2202 警告の違反の原因になる可能性があります。  入れ子の内側の `using` ステートメントの IDisposable リソースに、外側の `using` ステートメントのリソースが格納されている場合、入れ子のリソースの `Dispose` メソッドにより格納されているリソースが解放されます。  この状況が生じると、外側の `using` ステートメントの `Dispose` メソッドはそのリソースをもう一度破棄しようとします。  
  
 次の例では、ステートメントを使用して外側で作成された <xref:System.IO.Stream> オブジェクトは、`stream` オブジェクトを格納する <xref:System.IO.StreamWriter> オブジェクトの Dispose メソッドでステートメントを使用して内側の末尾で解放されます。  外側の `using` ステートメントの末尾で、`stream` オブジェクトがもう一度解放されます。  2 回目の解放は、CA2202 違反です。  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## 使用例  
 この問題を解決するには、外側の `using` ステートメントの代わりに `try`\/`finally` ブロックを使用します。  `finally` ブロックで、`stream` リソースが null でないことを確認します。  
  
```  
Stream stream = null;  
try  
{  
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        stream = null;  
        // Use the writer object...  
    }  
}  
finally  
{  
    if(stream != null)  
        stream.Dispose();  
}  
  
```  
  
## 参照  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose パターン](../Topic/Dispose%20Pattern.md)