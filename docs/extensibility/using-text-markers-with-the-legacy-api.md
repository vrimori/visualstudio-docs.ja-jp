---
title: "レガシ API でテキストのマーカーの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシー - テキスト マーカー"
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# レガシ API でテキストのマーカーの使用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テキスト マーカーはテキスト領域の表示と動作に影響を与える可能性のあるバッファー内のテキストの浮動範囲です。  マーカーはブレークポイントブックマーク波線では読み取り専用領域を含んでいます。  テキスト マーカーは構文の色指定と基本的には異なります。  構文の色指定にはテキスト領域に関連付けられている言語構文を含む簡単です。  構文の色指定は速度が重要な場合はWindows が画面を再描画する場合に要求されます。  構文の色指定はテキストの色を変更します。  テキスト マーカーは他の多くのテキスト プロパティを変更できます。  テキスト マーカーは 「」を指定でき特別な動作と色指定を適用します。  
  
 テキスト マーカーに関連するパフォーマンス オーバーヘッドのテキスト バッファーの多くのマーカーを作成しないでください。  ユーザーがバッファーの内容を編集する各マーカーはたびに更新されます。  
  
> [!NOTE]
>  ユーザーは形状とスタイル参照できるマーカーの色を変更できません。  詳細については、「[\[フォントおよび色\] \(\[オプション\] ダイアログ ボックス \- \[環境\]\)](../Topic/Fonts%20and%20Colors,%20Environment,%20Options%20Dialog%20Box.md)」を参照してください。  
  
## 関連トピック  
  
|Title|Description|  
|-----------|-----------------|  
|[方法: 標準のテキストのマーカーを追加](../extensibility/how-to-add-standard-text-markers.md)|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコア エディターによって提供されるテキスト ビューではテキスト マーカーの種類を追加する方法について説明します。|  
|[方法: エラー マーカーを実装します。](../extensibility/how-to-implement-error-markers.md)|エラーを示すために赤い波線で使用される [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] マーカーのインスタンスを実装する方法について説明します。|  
|[方法: カスタム テキスト マーカーを作成](../extensibility/how-to-create-custom-text-markers.md)|テキスト ビューにカスタム テキスト マーカーの型を作成して追加する方法について説明します。|  
|[方法: テキストのマーカーを使用します。](../extensibility/how-to-use-text-markers.md)|テキスト マーカーを追加する方法について説明します。|  
|[コア エディターの内部](../extensibility/inside-the-core-editor.md)|コア エディターの機能とコア エディターをカスタマイズする方法について詳しく説明します。|  
|[Editor Features](http://msdn.microsoft.com/ja-jp/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のコア エディターで使用できる機能について説明します。|  
  
## Reference  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 エディターによって定義されたかVSPackage に登録されるかに関係なく特定のテキスト マーカーの型に関する情報を取得するための統一された機能が用意されています。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 へのアクセスを提供し次元の座標を使用してテキスト バッファーのテキスト マーカーの位置を調整します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 テキスト マーカーを管理するためのメソッドを提供します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 テキスト マーカーを調整するために使用される [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE および他のプロセスからコールバックを提供します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 追加のコールバックを使用して<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> のインターフェイスを通じて使用できる機能を拡張します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 追加のコールバックを使用して<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> のインターフェイスを通じて使用できる機能を拡張します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 マーカーの型が他のマーカーの型が色のセットを共有するかどうかを判断します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 コア エディターのテキスト マーカーのコンテキストを提供します。  コア エディターではテキスト マーカーの場合<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> の別のオブジェクトを作成します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 グリフがドラッグ アンド ドロップ編集をサポートするマーカーに使用されるハンドラー。  グリフはマーカーの位置を示すアイコンです。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 他の VSPackages にテキスト マーカーを提供するサービスから <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> のインターフェイスを返します。  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 へのアクセスを提供し1 次元座標を使用してテキスト バッファーのテキスト マーカーの位置を調整します。  可能であればこのインターフェイスを使用しないでください。