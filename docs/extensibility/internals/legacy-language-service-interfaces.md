---
title: "従来の言語サービス インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IVsLanguageInfo インターフェイス"
  - "言語サービス、オブジェクト"
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# 従来の言語サービス インターフェイス
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

特定のプログラミング言語では言語サービスの一度に 1 個のインスタンスは一つだけです。  ただし一つの言語サービスは複数のエディターを提供できます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] は特定のエディターと言語サービスに関連付けない。  したがって言語サービスの操作を要求するとパラメーターとして適切なエディターを指定する必要があります。  
  
## 言語サービスに関連付けられた共通インターフェイス  
 エディターによって適切な VSPackage の <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> を呼び出して言語サービスを取得します。  この呼び出しに渡されるサービス ID \(SID\) が要求される言語サービスを識別します。  
  
 別のクラスの複数のコア言語サービスのインターフェイスを実装できます。  ただし一般的な方法は単一のクラスのインターフェイスを実装することです :  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> \(省略可能\)  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> のインターフェイスはすべての言語サービスで実行する必要があります。  これは言語にローカライズされた名前などの言語サービスについて言語サービスに関連付けられているファイル名の拡張子 colorizer を取得する方法を提供します。  
  
## 言語サービス インターフェイスの追加  
 他のインターフェイスは言語サービスを提供できます。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] はテキスト バッファーのインスタンスごとにこれらのインターフェイスのインスタンスを要求します。  したがって独自のオブジェクトはこれらのインターフェイスを実装する必要があります。  次の表にテキスト バッファーのインスタンスごとに 1 回のインスタンスが必要なインターフェイスを示しています。  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|ドロップダウン バーのようなコード ウィンドウの表示要素を管理します。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> のメソッドを使用してこのインターフェイスを取得できます。  コード ウィンドウに対して 1 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> があります。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colorizes 言語のキーワードと区切り記号。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> のメソッドを使用してこのインターフェイスを取得できます。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> は描画時に呼び出されます。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> のローカライズ作業中の計算方法とパフォーマンスが低下を回避できます。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|IntelliSense のパラメーターのヒントを紹介します。  言語サービスが認識すると言語サービスの \[パラメーター ヒントのツールヒントを表示する準備ができたらメソッドのデータは左かっこなどの表示になることを示す文字はテキスト ビューに通知するために <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> のメソッドを呼び出します。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> のメソッドのツールヒントを表示するために必要な情報を取得するために使用した言語サービスにはテキスト ビューのを呼び出してインターフェイスします。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|IntelliSense のステートメント入力候補機能を提供します。  言語サービスはコンプリート リストを表示する準備ができたらテキスト ビューの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> のメソッドを呼び出します。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> のメソッドを使用して言語サービスにはテキスト ビューのを呼び出してオブジェクト。|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|コマンド ハンドラーを使用してテキスト ビューの変更を作成できます。  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> のインターフェイスを実装するクラスは<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> のインターフェイスを実装する必要があります。  テキスト ビューは <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> のメソッドに渡される <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> のオブジェクトを照会して<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> のオブジェクトを取得します。  次に各ビューの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> の 1 種類のオブジェクトである必要があります。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|コード ウィンドウにユーザーがそのコマンドを受け取ります。  カスタムの完了および詳細ビューの変更を提供するために <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> の実装からの出力を監視します。<br /><br /> テキスト ビューを <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> のオブジェクトを渡すには<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> を呼び出します。|  
  
## 参照  
 [言語サービスを開発します。](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [チェックリスト: 従来の言語サービスを作成します。](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)