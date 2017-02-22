---
title: "フォントおよび色を使用します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フォント、IDE で制御します。"
  - "IDE のテキストの色とフォントを制御します。"
  - "フォントおよび色] プロパティ ページ"
  - "フォントと色のコントロール [Visual Studio SDK]"
  - "IDE のテキスト"
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# フォントおよび色を使用します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] はフォントの使用をサポートし表示する色はショートサーキット メッセージを送信します。  
  
## このセクションの内容  
 [フォントと色の概要](../extensibility/font-and-color-overview.md)  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の統合開発環境でテキストのフォントおよび色の設定について説明します \(IDE\)。  またカテゴリおよび表示項目の概念や VSPackage とコア エディターでテキスト属性を使用する方法について説明します。  
  
 [フォントとテキストの色づけの色の情報を取得します。](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 **テキスト エディター**  以外  **カテゴリ**  を管理する VSPackage のテキストの色づけを実行するためのガイドラインを示します。  
  
 [ストアドのフォントと色の設定にアクセスします。](../extensibility/accessing-stored-font-and-color-settings.md)  
 現在のフォントおよび色の設定を格納および取得され適用する方法について説明します。  
  
 [カスタム カテゴリと \[表示項目を実装します。](../extensibility/implementing-custom-categories-and-display-items.md)  
 ウィンドウを作成しテキスト表示に  **表示項目**  サポートと  **カテゴリ**  独自のを使用する基本的な手順について説明します。  
  
 この方法はVSPackage が <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>インターフェイスおよび関連のインターフェイスを実装する必要があります。  
  
 [方法: ビルトインのフォントおよび画面の配色にアクセス](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 組み込みのフォントおよび色を使用してカテゴリを定義して登録する方法について説明します。使用するシステムで指定されたフォントと色を開始します。  
  
## 関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 `IVsFontAndColorDefaults` または \[ENT2ENT\] ダイアログ ボックスの \[ENT1ENT ページの ENT0ENT \[入力\] ボックスの一覧で特定の項目に対応する <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> インターフェイスのインスタンスを提供します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 VSPackage をウィンドウや UI 要素の既定のフォントと色を定義して\[ENT0ENT ページの IDE をサポートすることができます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 VSPackage を提供するフォントおよび色のサポートの表示項目グループ複数のカテゴリの共用体を表す場合カテゴリに指定できる機能を提供します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 VSPackage のフォントを取得しデータが変化するようにしたりレジストリに保存します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 VSPackage が通知を使用してフォントフォントの変更に関する情報と色色を設定します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **\*\*\* Font and Color \*\*\*** 機能のメソッドで使用される入出力データを扱うためのツールです。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 フォントと色でのキャッシュを制御します。  
  
## 関連項目  
 [言語サービスを開発します。](../extensibility/internals/developing-a-legacy-language-service.md)  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] エディターをカスタマイズするにはVSPackage で言語サービスを使用する方法について説明します。  
  
 [構文のカスタム エディターの色指定](../extensibility/syntax-coloring-in-custom-editors.md)  
 構文の色指定を実行するために [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] エディターで言語サービスを使用する方法を検索します。  
  
 [Visual Studio の他の部分を拡張します。](../extensibility/extending-other-parts-of-visual-studio.md)  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] サービスを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の他に一致する UI 要素を作成する方法について説明します。