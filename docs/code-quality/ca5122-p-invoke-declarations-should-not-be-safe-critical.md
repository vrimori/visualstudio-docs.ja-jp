---
title: "CA5122 P/Invoke 宣言をセーフ クリティカルにしないでください | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 4
---
# CA5122 P/Invoke 宣言をセーフ クリティカルにしないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|  
|CheckId|CA5122|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 P\/Invoke 宣言が <xref:System.Security.SecuritySafeCriticalAttribute> でマークされました。  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
// ...  
public class C  
{  
    [SecuritySafeCritical]  
    [DllImport("kernel32.dll")]  
    public static extern bool Beep(int frequency, int duration); // CA5122 – safe critical p/invoke  
   }  
  
```  
  
 この例では、`C.Beep(...)` がセキュリティ セーフ クリティカルなメソッドとしてマークされています。  
  
## 規則の説明  
 メソッドは、セキュリティに対する配慮が必要な操作を行うときは SecuritySafeCritical としてマークされますが、透過的なコードによって使用される場合も安全です。  セキュリティ透過性モデルの基本的な規則の 1 つは、透過的なコードが P\/Invoke を通じてネイティブ コードを直接呼び出してはいけないということです。  そのため、P\/Invoke をセキュリティ セーフ クリティカルとしてマークしても、透過的なコードはそれを呼び出すことができず、セキュリティ分析の際に紛らわしくなります。  
  
## 違反の修正方法  
 透過的なコードで P\/Invoke を使用できるようにするには、そのコードのためのセキュリティ セーフ クリティカルなラッパー メソッドを公開します。  
  
```c#  
[assembly: AllowPartiallyTrustedCallers  
  
class C  
{  
   [SecurityCritical]  
   [DllImport(“kernel32.dll”, EntryPoint=”Beep”)]  
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke  
  
   [SecuritySafeCritical]  
   public static bool Beep(int frequency, int duration)  
   {  
      return BeepPInvoke(frequency, duration);  
   }  
}  
  
```  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。