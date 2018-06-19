---
title: DebuggerTypeProxy 属性の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af0f2521b2276d28b07a4712009c4c4ae85a4d2d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477889"
---
# <a name="using-debuggertypeproxy-attribute"></a>DebuggerTypeProxy 属性の使用
<xref:System.Diagnostics.DebuggerTypeProxyAttribute> では、ある型のプロキシ (代理) を指定し、その型をデバッガー ウィンドウで表示する方法を変更します。 プロキシを持つ変数を表示したときに、プロキシが元の型の**表示**です。 デバッガーの変数ウィンドウには、プロキシ型のパブリック メンバーのみが表示されます。 プライベート メンバーは表示されません。  
  
 この属性は次の対象に適用できます。  
  
-   構造体  
  
-   クラス  
  
-   アセンブリ  
  
 型プロキシ クラスには、プロキシで置換される型の引数を使用するコンストラクターが必要です。 デバッガーでは、対象となる型の変数を表示するときに、毎回、新しい型プロキシ クラスのインスタンスが作成されます。 その結果、パフォーマンスが低下する可能性があります。 そのため、コンストラクターでの作業は必要最小限に抑えます。  
  
 パフォーマンスの低下を最小限にするために、式エバリュエーターでは、型の表示プロキシに関する属性はチェックされません。ただし、デバッガー ウィンドウで + 記号をクリックして型を展開したときや、<xref:System.Diagnostics.DebuggerBrowsableAttribute> を使用するときはチェックされます。 そのため、表示型に属性を指定するのは避けます。 属性は、表示型の本体で使用できるようにします。  
  
 型プロキシは、属性の対象となるクラスに入れ子にした、プライベート クラスにすることをお勧めします。 こうすることで、内部のメンバーに簡単にアクセスできます。  
  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> をアセンブリ レベルで使用する場合は、プロキシに置換される型を `Target` パラメーターで指定します。  
  
 と共にこの属性を使用する方法の例については<xref:System.Diagnostics.DebuggerDisplayAttribute>と<xref:System.Diagnostics.DebuggerTypeProxyAttribute>を参照してください[DebuggerDisplay 属性を使用して](../debugger/using-the-debuggerdisplay-attribute.md)です。  
  
## <a name="using-generics-with-debuggertypeproxy"></a>ジェネリックと DebuggerTypeProxy の使用  
 ジェネリックのサポートは限定的です。 C# では、`DebuggerTypeProxy` はオープン型のみをサポートします。 オープン型 (構築されていない型とも呼ばれます) とは、その型パラメーターの引数によってインスタンス化されていないジェネリック型のことです。 クローズ型 (構築された型とも呼ばれます) は、サポートされていません。  
  
 オープン型の構文は次のようになります。  
  
 `Namespace.TypeName<,>`  
  
 `DebuggerTypeProxy` 内でジェネリック型を対象として使用する場合は、この構文を使用する必要があります。 `DebuggerTypeProxy` の機構は、型パラメーターを推論します。  
  
 C# でのオープンおよびクローズされた種類の詳細を参照してください、 [c# 言語仕様](/dotnet/csharp/language-reference/language-specification)、セクション 20.5.2 を開くとクローズ型です。  
  
 Visual Basic にはクローズ型の構文はないため、Visual Basic で同じ処理はできません。 代わりに、オープン型の名前の文字列形式を使用する必要があります。  
  
 `"Namespace.TypeName'2"`  
  
## <a name="see-also"></a>関連項目  
 [DebuggerDisplay 属性の使用](../debugger/using-the-debuggerdisplay-attribute.md)   
 [カスタム ビュー .managed オブジェクトを作成します。](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [デバッガー表示属性によるデバッグ機能の拡張](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)