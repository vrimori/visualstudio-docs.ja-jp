---
title: "カスタム データ型の表示 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.data.elements"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "autoexp.dat ファイル"
  - "カスタム データ型"
  - "データ型 [C#], カスタム"
  - "デバッガー, 拡張 (データ型の)"
  - "マネージ コード, カスタム データ型"
  - "mcee_cs.dat ファイル"
  - "mcee_mc.dat ファイル"
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# カスタム データ型の表示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio でデバッガーの変数ウィンドウにデータ型を表示する方法をカスタマイズできます。  
  
## 属性  
 C\# および Visual Basic では、<xref:System.Diagnostics.DebuggerTypeProxyAttribute>、<xref:System.Diagnostics.DebuggerDisplayAttribute>、および <xref:System.Diagnostics.DebuggerBrowsableAttribute> を使用して、カスタム データの展開を追加できます。  
  
 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] コードでは、Visual Basic は DebuggerBrowsable 属性をサポートしません。  この制限は、.NET Framework の新しいバージョンで解除されています。  
  
## ビジュアライザー  
 マネージ データ型を表示するには、ビジュアライザーを記述します。  詳細については、「[方法 : ビジュアライザーを記述する](../debugger/how-to-write-a-visualizer.md)」を参照してください。  
  
## ネイティブ コード  
 ネイティブ コードの場合、カスタム データ型の展開を autoexp.dat ファイルに追加します。autoexp.dat は、Program Files\\Microsoft Visual Studio 11.0\\Common7\\Packages\\Debugger ディレクトリにあります。  `autoexp` 規則の記述手順は、このファイルに含まれています。  
  
> [!CAUTION]
>  このファイルの構造と自動展開規則の構文は、Visual Studio のリリースごとに異なる可能性があります。  
  
 また、ネイティブ型の表示は、式エバリュエーター アドインを記述してカスタマイズできます。  詳細については、「[EEAddIn Sample: Debugging Expression Evaluator Add\-In](http://msdn.microsoft.com/ja-jp/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e)」を参照してください。  
  
## 参照  
 [DebuggerTypeProxy 属性の使用](../debugger/using-debuggertypeproxy-attribute.md)   
 [DebuggerDisplay 属性を使用します](../debugger/using-the-debuggerdisplay-attribute.md)   
 [ウォッチ ウィンドウと \[クイック ウォッチ\] ウィンドウ](../Topic/Watch%20and%20QuickWatch%20Windows.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)