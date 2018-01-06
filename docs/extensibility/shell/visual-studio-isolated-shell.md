---
title: "Visual Studio 分離シェル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e80b947b2d4d20692e0abceae0ffa36e64f2b0df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio 分離シェル
Visual Studio 分離シェルでは、サイド バイ サイドで実行できるスタンドアロンのアプリケーションを作成できます。 Visual Studio の他のバージョンとします。 Visual Studio サービスを使用できますが、カスタマイズされた外観でもある特殊なツールをホストするには、主に使用されているとブランドをお勧めします。 Visual Studio の機能とメニュー コマンドのグループを容易にするオンとオフをします。 アプリケーションのタイトル、アプリケーションのアイコンとスプラッシュ スクリーンは、完全にカスタマイズできます。 カスタマイズ可能な機能の一覧は、次を参照してください。[分離シェルのカスタマイズ](customizing-the-isolated-shell.md)です。  
  
 分離シェル プロジェクトで作業するには、Visual Studio SDK をインストールする必要があります。 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../installing-the-visual-studio-sdk.md)です。  
  
 分離シェル アプリケーションを作成するには、でプロジェクトを Visual Studio 分離シェルを起動します。 このプロジェクトには、開発および分離シェル アプリケーションをテストする必要のあるすべてのものが含まれています。 分離シェルの再頒布可能パッケージを取得する必要があります、アプリケーションを展開するセットアップ プログラムを作成する準備ができたら、 [Microsoft Visual Studio Shell (Isolated) 再頒布可能パッケージ](http://go.microsoft.com/fwlink/?LinkId=616022)です。  
  
> [!NOTE]
>  分離シェルの再頒布可能パッケージにアクセスできるように、簡単なアンケートに記入するように求められます。  アンケートの記入、後に表示する再頒布可能パッケージのダウンロード リンクを Visual Studio の接続ページにします。  Visual Studio 接続サイトにアクセスする際にダウンロードのリンクを見つけることができます、**プログラム &#124;です。VISUAL STUDIO 2015 統合および ISOLATED SHELL**タブです。  
  
> [!NOTE]
>  分離シェルベースのアプリケーションを展開する方法の詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
## <a name="working-with-the-isolated-shell"></a>分離シェルの操作  
 Visual Studio 分離シェル アプリケーションは、Visual Studio のサービスへのフル アクセスを持ち、特別なカスタマイズおよびブランド化をサポートします。 いくつかの方法が分離シェル アプリケーションをカスタマイズできます。  
  
-   VSPackages および Managed Extensibility Framework (MEF) コンポーネント パーツを使用すると、その他の Visual Studio 拡張機能で使用すると同様に、分離シェル アプリケーションを拡張します。 詳細については、次を参照してください。[分離シェルを拡張する](extending-the-isolated-shell.md)です。  
  
-   Visual Studio の機能とメニュー コマンドのグループ使用可能または利用できない、アプリケーションのユーザー インターフェイス (UI) のプロジェクトで .vsct ファイルを更新します。  
  
-   削除する**オプション**ページまたはその他の Visual Studio シェル コンポーネント、アプリケーションからは、アプリケーションの .pkgundef ファイルを更新します。  
  
-   外観の他の側面またはシェルの動作を変更するには、アプリケーションの .pkgdef ファイルを更新します。  
  
-   シェルの一部の機能は、アプリケーションの起動時にも指定することができます。 これを行うには、始点、appenvstub.dll をへの呼び出しでパラメーターを更新します。  
  
 カスタマイズできるさまざまな要素の詳細については、次を参照してください。 [Isolated Shell の要素](elements-of-the-isolated-shell.md)です。  
  
## <a name="standard-features-of-the-isolated-shell"></a>Isolated Shell の標準的な機能  
 次の機能は、Visual Studio のすべてのエディションを standard です。  
  
|機能カテゴリ|機能|  
|----------------------|-------------|  
|IDE の機能|インポート/エクスポートの設定<br /><br /> ツールボックス コントロール インストーラー<br /><br /> エラー一覧 (&)、タスク一覧<br /><br /> [出力] ウィンドウ<br /><br /> スタート ページ<br /><br /> [プロパティ] ウィンドウ<br /><br /> ツールボックス<br /><br /> ソリューション エクスプローラー<br /><br /> ブックマーク ウィンドウ<br /><br /> クラス ビュー<br /><br /> オブジェクト ブラウザー<br /><br /> コマンド ウィンドウ<br /><br /> [ドキュメント アウトライン]<br /><br /> リソース ビュー<br /><br /> 外部ツール<br /><br /> Windows Communication Foundation (WCF) サービス参照を追加します。<br /><br /> 言語統合クエリ (LINQ) のサポート|  
|デザイナー/エディター|コード参照ツール (統合検索、ソースの定義、継承)<br /><br /> IntelliSense<br /><br /> スマート タグ<br /><br /> コード スニペット マネージャー<br /><br /> コード スニペット<br /><br /> リファクタリング<br /><br /> 見た目のよい一覧<br /><br /> IntelliSense フィルター処理<br /><br /> コード定義ウィンドウ<br /><br /> アプリケーション デザイナー<br /><br /> Windows フォーム デザイナー<br /><br /> Windows Presentation Foundation (WPF) デザイナー|  
|デバッグ|C# の式エバリュエーター<br /><br /> ローカル デバッグ<br /><br /> マネージ デバッグ<br /><br /> エディット コンティニュ<br /><br /> スレッド間のデバッグ<br /><br /> 視覚エフェクト<br /><br /> [DataTips] ポップアップ<br /><br /> ネイティブ デバッグ<br /><br /> スクリプトのデバッグ<br /><br /> 相互運用機能デバッグ<br /><br /> ジャスト イン タイム (JIT) デバッグ<br /><br /> マルチ プロセス デバッグ<br /><br /> XSLT のデバッグ<br /><br /> ローカル プロセスにアタッチします。<br /><br /> トレース ポイント<br /><br /> ブレークポイント制約|  
|データ|サーバー エクスプ ローラー (簡体字のデータのみ)<br /><br /> ローカル データにデータ バインド (です。MDF またはします。MDB)<br /><br /> オブジェクトへのデータ バインド<br /><br /> Web サービスへのデータ バインド<br /><br /> データ コントロールの完全なセット<br /><br /> XML エディター<br /><br /> ローカル データベース サーバーへのデータ バインド<br /><br /> [データ ソース] ウィンドウ|  
|Web|HTML エディター<br /><br /> Web ブラウザー<br /><br /> Web フォーム デザイナー<br /><br /> Web サイト プロジェクト<br /><br /> Web アプリケーション プロジェクト|  
|機能拡張|Vspackage と MEF コンポーネントを使用します。|  
  
## <a name="see-also"></a>参照  
 [シェル (分離または統合)](shell-isolated-or-integrated.md)