---
title: Visual Studio 分離シェル |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e28a411ff5ef70cfd32e846edb0b70caa82c4764
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286066"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio 分離シェル
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 分離シェルでは、サイド バイ サイドで実行するスタンドアロン アプリケーションを作成できます。 Visual Studio の他のバージョン。 Visual Studio サービスを使用できますが、カスタマイズされた外観でもある特別なツールをホストするには、主に使用されるとブランド化をお勧めします。 Visual Studio の機能とメニュー コマンド グループ有効にできます簡単にオンとオフ。 アプリケーションのタイトル、アプリケーションのアイコンとスプラッシュ スクリーンは、完全にカスタマイズ可能です。 カスタマイズ可能な機能の一覧は、次を参照してください。[分離シェルのカスタマイズ](../extensibility/customizing-the-isolated-shell.md)します。  
  
 分離シェル プロジェクトを使用するには、Visual Studio SDK をインストールする必要があります。 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
 分離シェル アプリケーションを作成するには、Visual Studio 分離シェル プロジェクトを起動します。 このプロジェクトには、独自の分離シェル アプリケーション開発およびテストする必要のあるすべてのものが含まれます。 分離シェルの再頒布可能パッケージを取得する必要があります、アプリケーションをデプロイするセットアップ プログラムを記述する準備ができたら、 [Microsoft Visual Studio Shell (Isolated) 再頒布可能パッケージ](http://go.microsoft.com/fwlink/?LinkId=616022)します。  
  
> [!NOTE]
>  分離シェルの再頒布可能パッケージにアクセスする前にお客様の簡単なアンケートに記入してになります。  アンケートに記入した後は、するは再頒布可能パッケージのダウンロード リンクを含む Visual Studio の Connect ページに移動します。  Visual Studio の Connect サイトにアクセスする際に、ダウンロード リンクを見つけることができます、**プログラム&#124;VISUAL STUDIO 2015 統合と分離シェル**タブ。  
  
> [!NOTE]
>  分離シェルベースのアプリケーションをデプロイする方法の詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)します。  
  
## <a name="working-with-the-isolated-shell"></a>分離シェルの操作  
 Visual Studio 分離シェル アプリケーションは、Visual Studio services へのフル アクセスを備え、特別なカスタマイズとブランド化をサポートしています。 分離シェル アプリケーションをカスタマイズするいくつかの方法はあります。  
  
-   Vspackage と Managed Extensibility Framework (MEF) コンポーネント パーツを使用して、他の Visual Studio 拡張機能で使用する場合と同様に、分離シェル アプリケーションを拡張することができます。 詳細については、次を参照してください。[分離シェルの拡張](../extensibility/extending-the-isolated-shell.md)します。  
  
-   Visual Studio の機能とメニュー コマンドのグループを使用できないか使用できないように、アプリケーションのユーザー インターフェイス (UI) のプロジェクトで .vsct ファイルを更新します。  
  
-   削除する**オプション**ページや、アプリケーションからその他の Visual Studio シェル コンポーネントは、アプリケーションの .pkgundef ファイルを更新します。  
  
-   外観の他の側面またはシェルの動作を変更するには、アプリケーションの .pkgdef ファイルを更新します。  
  
-   シェルの一部の側面は、アプリケーションの起動時にも指定できます。 これを行うには、始点、appenvstub.dll の呼び出しでパラメーターを更新します。  
  
 カスタマイズ可能なさまざまな要素の詳細については、次を参照してください。[分離シェルの要素](../extensibility/elements-of-the-isolated-shell.md)します。  
  
## <a name="standard-features-of-the-isolated-shell"></a>分離シェルの標準機能  
 次の機能は、Visual Studio のすべてのエディションを standard です。  
  
|機能カテゴリ|機能|  
|----------------------|-------------|  
|IDE の機能|インポート/エクスポートの設定<br /><br /> ツールボックス コントロール インストーラー<br /><br /> エラー一覧 (&)、タスク一覧<br /><br /> [出力] ウィンドウ<br /><br /> スタート ページ<br /><br /> [プロパティ] ウィンドウ<br /><br /> ツールボックス<br /><br /> ソリューション エクスプローラー<br /><br /> ブックマーク ウィンドウ<br /><br /> クラス ビュー<br /><br /> オブジェクト ブラウザー<br /><br /> コマンド ウィンドウ<br /><br /> [ドキュメント アウトライン]<br /><br /> リソース ビュー<br /><br /> 外部ツール<br /><br /> Windows Communication Foundation (WCF) サービス参照を追加します。<br /><br /> 言語統合クエリ (LINQ) のサポート|  
|エディターとデザイナー|コード ツール (統合検索、ソースの定義の継承) を参照<br /><br /> IntelliSense<br /><br /> スマート タグ<br /><br /> コード スニペット マネージャー<br /><br /> コード スニペット<br /><br /> リファクタリング<br /><br /> かなりの一覧<br /><br /> IntelliSense のフィルター処理<br /><br /> コード定義ウィンドウ<br /><br /> アプリケーション デザイナー<br /><br /> Windows フォーム デザイナー<br /><br /> Windows Presentation Foundation (WPF) デザイナー|  
|デバッグ|C# 式エバリュエーター<br /><br /> ローカル デバッグ<br /><br /> マネージ デバッグ<br /><br /> エディット コンティニュ<br /><br /> スレッド間のデバッグ<br /><br /> 視覚エフェクト<br /><br /> [DataTips] ポップアップ<br /><br /> ネイティブ デバッグ<br /><br /> スクリプトのデバッグ<br /><br /> 相互運用機能デバッグ<br /><br /> イン タイム (JIT) デバッグ<br /><br /> マルチ プロセス デバッグ<br /><br /> XSLT のデバッグ<br /><br /> ローカルのプロセスにアタッチします。<br /><br /> トレース ポイント<br /><br /> ブレークポイント制約|  
|データ|サーバー エクスプ ローラー (簡体字のデータのみ)<br /><br /> ローカル データにデータをバインド (します。MDF またはします。MDB)<br /><br /> オブジェクトへのデータ バインド<br /><br /> Web サービスへのデータ バインド<br /><br /> データ コントロールの完全なセット<br /><br /> XML エディター<br /><br /> ローカル データベース サーバーへのデータ バインド<br /><br /> [データ ソース] ウィンドウ|  
|Web|HTML エディター<br /><br /> Web ブラウザー<br /><br /> Web フォーム デザイナー<br /><br /> Web サイト プロジェクト<br /><br /> Web アプリケーション プロジェクト|  
|機能拡張|Vspackage と MEF コンポーネントを使用します。|  
  
## <a name="see-also"></a>関連項目  
 [シェル (分離または統合)](../extensibility/shell-isolated-or-integrated.md)

