---
title: "管理対象オブジェクトのカスタム ビューを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ae3149350bac7aca92ffbc8b308c75357c3edba4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="create-custom-views-of-managed-objects"></a>カスタム ビューの管理オブジェクトを作成します。
Visual Studio でデバッガーの変数ウィンドウにデータ型を表示する方法をカスタマイズできます。  
  
## <a name="attributes"></a>属性  
 C# および Visual Basic では、<xref:System.Diagnostics.DebuggerTypeProxyAttribute>、<xref:System.Diagnostics.DebuggerDisplayAttribute>、および <xref:System.Diagnostics.DebuggerBrowsableAttribute> を使用して、カスタム データの展開を追加できます。  
  
 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] コードでは、Visual Basic は DebuggerBrowsable 属性をサポートしません。 この制限は、.NET Framework の新しいバージョンで解除されています。  
  
## <a name="visualizers"></a>ビジュアライザー  
 マネージ データ型を表示するには、ビジュアライザーを記述します。 詳細については、次を参照してください。[する方法: ビジュアライザーを記述](../debugger/how-to-write-a-visualizer.md)です。  
  
## <a name="native-code"></a>ネイティブ コード  
 ネイティブ コードの場合、カスタム データ型の展開を autoexp.dat ファイルに追加します。autoexp.dat は、Program Files\Microsoft Visual Studio 11.0\Common7\Packages\Debugger ディレクトリにあります。 `autoexp` 規則の記述手順は、このファイルに含まれています。  
  
> [!CAUTION]
>  このファイルの構造と自動展開規則の構文は、Visual Studio のリリースごとに異なる可能性があります。  
  
 また、ネイティブ型の表示は、式エバリュエーター アドインを記述してカスタマイズできます。 詳細については、次を参照してください。 [EEAddIn サンプル: デバッグ式エバリュエーター アドイン](http://msdn.microsoft.com/en-us/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e)です。  
  
## <a name="see-also"></a>関連項目  
 [DebuggerTypeProxy 属性の使用](../debugger/using-debuggertypeproxy-attribute.md)   
 [DebuggerDisplay 属性の使用](../debugger/using-the-debuggerdisplay-attribute.md)   
 [ウォッチと [クイック ウォッチ] ウィンドウ](../debugger/watch-and-quickwatch-windows.md)   
 [デバッガー表示属性によるデバッグ機能の拡張](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)