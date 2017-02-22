---
title: "CA1901: P/Invoke 宣言はポータブルでなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
helpviewer_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1901: P/Invoke 宣言はポータブルでなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|分類|Microsoft.Portability|  
|互換性に影響する変更点|あり \- P\/Invoke がアセンブリの外部で参照できる場合  なし – P\/Invoke がアセンブリの外部で参照できない場合|  
  
## 原因  
 この規則では、P\/Invoke の各パラメーターのサイズと戻り値が評価され、32 ビット プラットフォームおよび 64 ビット プラットフォームのアンマネージ コードにマーシャリングされたときのサイズが正しいことが検証されます。  この規則の違反で最も一般的なものは、プラットフォームに依存するポインター サイズの変数が必要な場所に、固定サイズの整数を渡すことです。  
  
## 規則の説明  
 この規則に違反する次のいずれかのシナリオで発生します。  
  
-   戻り値またはパラメーターを `IntPtr` 型と指定しなければならないときに固定サイズの整数型と指定しています。  
  
-   戻り値またはパラメーターを固定サイズの整数型と指定しなければならないときに `IntPtr` 型と指定しています。  
  
## 違反の修正方法  
 この違反を修正するには、`Int32` や `UInt32` ではなく `IntPtr` または `UIntPtr` を使用してハンドルを表します。  
  
## 警告を抑制する状況  
 この警告は抑制しないでください。  
  
## 使用例  
 この規則に違反する場合を次の例に示します。  
  
```c#  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 この例では、32 ビット プラットフォームでは 4 バイト、64 ビット プラットフォームでは 8 バイトです `nIconIndex` パラメーターは  `IntPtr`として宣言されています。  その後のアンマネージ宣言では、`nIconIndex` がすべてのプラットフォームでは 4 バイトの符号なし整数として参照できます。  
  
```c#  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## 使用例  
 この規則違反を修正するには、宣言を次のように変更します。  
  
```c#  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## 参照  
 [移植性に関する警告](../code-quality/portability-warnings.md)