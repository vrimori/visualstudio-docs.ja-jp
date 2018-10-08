---
title: '方法: ビジュアライザーを記述する |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, writing
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b48b4f6a3813942eb20f9daecbe27aa9abffd30
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548412"
---
# <a name="how-to-write-a-visualizer"></a>方法 : ビジュアライザーを記述する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: ビジュアライザーを記述する](https://docs.microsoft.com/visualstudio/debugger/how-to-write-a-visualizer)します。  
  
<xref:System.Object> および <xref:System.Array> を除く任意のマネージド クラスのオブジェクトのカスタム ビジュアライザーを記述できます。  
  
> [!NOTE]
>  **ストア**アプリ、標準のテキストのみ HTML、XML、および JSON ビジュアライザーがサポートされています。 カスタム (ユーザーが作成した) ビジュアライザーはサポートされていません。  
  
 デバッガー ビジュアライザーのアーキテクチャには、次の 2 つの部分があります。  
  
-   *デバッガー側*Visual Studio デバッガー内で実行します。 デバッガー側のコードは、ビジュアライザーのユーザー インターフェイスを作成し、表示します。  
  
-   *デバッグ対象側*Visual Studio がデバッグ プロセス内で実行 (、*デバッグ対象*)。  
  
 視覚化するデータ オブジェクト (String オブジェクトなど) は、デバッグ対象プロセスに存在します。 このためデバッグ対象側では、そのデータ オブジェクトをデバッガー側に送る必要があります。これによって、デバッガー側では、作成したユーザー インターフェイスを使ってデータ オブジェクトを表示できるようになります。  
  
 デバッガー側から視覚化対象である場合は、このデータ オブジェクトを受け取る、*オブジェクト プロバイダー*を実装する、<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>インターフェイス。 デバッグ対象側の送信を使用してデータ オブジェクト、*オブジェクト ソース*から派生<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>します。 オブジェクト プロバイダーは、オブジェクト ソースにデータを戻すこともできます。このため、データの表示だけでなく編集もできるビジュアライザーを記述できます。 オブジェクト プロバイダーは、式エバリュエーターと通信することでオブジェクト ソースと通信するようにオーバーライドできます。  
  
 デバッグ対象側とデバッガー側は、<xref:System.IO.Stream> を介して相互に通信します。 データ オブジェクトを <xref:System.IO.Stream> にシリアル化し、<xref:System.IO.Stream> をデータ オブジェクトに逆シリアル化するメソッドが用意されています。  
  
 デバッグ対象側のコードは、DebuggerVisualizer 属性 (<xref:System.Diagnostics.DebuggerVisualizerAttribute>) で指定します。  
  
 デバッガー側でビジュアライザー ユーザー インターフェイスを作成するには、<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> を継承するクラスを作成し、<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> メソッドをオーバーライドしてインターフェイスを表示する必要があります。  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> を使用すると、Windows フォーム、ダイアログ、およびコントロールをビジュアライザーによって表示できます。  
  
 ジェネリック型のサポートは制限されています。 ジェネリック型がオープン型の場合にのみ、そのジェネリック型のビジュアライザーを記述できます。 この制限は、`DebuggerTypeProxy` 属性を使用する場合の制限と同じです。 詳細については、次を参照してください。 [DebuggerTypeProxy 属性を使用して](../debugger/using-debuggertypeproxy-attribute.md)します。  
  
 カスタムのビジュアライザーでは、セキュリティについての配慮が必要な場合があります。 参照してください[ビジュアライザーのセキュリティに関する考慮事項](../debugger/visualizer-security-considerations.md)します。  
  
 以下の手順は、ビジュアライザーの作成に必要な作業の概要を示したものです。 詳細については、次を参照してください。[チュートリアル: c# でビジュアライザーを記述する](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)します。  
  
### <a name="to-create-the-debugger-side"></a>デバッガー側を作成するには  
  
1.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> メソッドを使用して、視覚化するオブジェクトをデバッガー側で取得します。  
  
2.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> を継承するクラスを作成します。  
  
3.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> メソッドをオーバーライドしてインターフェイスを表示します。 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> メソッドを使用して、Windows フォーム、ダイアログ、およびコントロールをインターフェイスの一部として表示します。  
  
4.  <xref:System.Diagnostics.DebuggerVisualizerAttribute> をビジュアライザー (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) に適用します。  
  
### <a name="to-create-the-debuggee-side"></a>デバッグ対象側を作成するには  
  
1.  <xref:System.Diagnostics.DebuggerVisualizerAttribute> をビジュアライザー (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) とオブジェクト ソース (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>) に適用します。 オブジェクト ソースを省略すると、既定のオブジェクト ソースが使用されます。  
  
2.  ビジュアライザーでデータ オブジェクトを表示するだけでなく、編集できるようにする場合は、`TransferData` の `CreateReplacementObject` メソッドまたは <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> メソッドをオーバーライドする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [カスタム ビジュアライザーを作成します。](../debugger/create-custom-visualizers-of-data.md)   
 [方法: ビジュアライザーをインストール](../debugger/how-to-install-a-visualizer.md)   
 [方法: テストし、デバッグのビジュアライザー](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [ビジュアライザーのセキュリティに関する考慮事項](../debugger/visualizer-security-considerations.md)



