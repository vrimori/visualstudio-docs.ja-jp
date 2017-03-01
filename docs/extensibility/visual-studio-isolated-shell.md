---
title: "Visual Studio シェルの分離 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: d6925bbb3fa432c098f62d223b1c1a7478ecca23
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-isolated-shell"></a>Visual Studio シェルの分離
分離された Visual Studio シェルでは、サイド バイ サイドで実行できるスタンドアロンのアプリケーションを作成できます。 Visual Studio の他のバージョンとします。 Visual Studio のサービスを使用できますが、カスタマイズされた外観も場合は、特殊なツールをホストするには、主に使用した、またはブランド化をお勧めします。 Visual Studio 機能とコマンドのメニュー グループできますを容易にするオン/オフします。 アプリケーションのタイトル、アプリケーションのアイコンとスプラッシュ スクリーンは、完全にカスタマイズできます。 カスタマイズ可能な機能の一覧は、次を参照してください。[分離シェルをカスタマイズする](../extensibility/customizing-the-isolated-shell.md)です。  
  
 分離シェル プロジェクトを操作するには、Visual Studio SDK をインストールする必要があります。 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
 分離シェル アプリケーションを作成するには、Visual Studio 分離シェル プロジェクト始めます。 このプロジェクトには、開発および分離シェル アプリケーションをテストする必要があるすべてのものが含まれています。 分離シェルの再頒布可能パッケージを取得する必要があります、アプリケーションを展開するセットアップ プログラムを作成する準備ができたら、 [Microsoft Visual Studio Shell (Isolated) 再頒布可能パッケージ](http://go.microsoft.com/fwlink/?LinkId=616022)します。  
  
> [!NOTE]
>  分離 shell 再頒布可能パッケージにアクセスするには、簡単なアンケートの記入が求められます。  アンケートの記入、後に表示する再頒布可能パッケージのダウンロード リンク付きの Visual Studio の Connect のページにします。  ダウンロード リンクを参照 [Visual Studio の Connect サイトにアクセスする際に、**プログラム |VISUAL STUDIO 2015 統合し、分離シェル**] タブをクリックします。  
  
> [!NOTE]
>  分離のシェル ベースのアプリケーションを展開する方法の詳細については、次を参照してください。[チュートリアル: 基本的な分離シェル アプリケーションを作成する](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)です。  
  
## <a name="working-with-the-isolated-shell"></a>分離シェルの操作  
 Visual Studio の分離シェル アプリケーションは、Visual Studio のサービスへのフル アクセスを持ち、特別なカスタマイズとブランド化をサポートしています。 分離シェル アプリケーションをカスタマイズするいくつかの方法があります。  
  
-   Vspackage と Managed Extensibility Framework (MEF) コンポーネント パーツを使用すると、その他の Visual Studio 拡張機能で使用すると同様に、分離シェル アプリケーションを拡張します。 詳細については、次を参照してください。[分離シェルの拡張](../extensibility/extending-the-isolated-shell.md)します。  
  
-   使用可能に Visual Studio の機能とメニュー コマンドのグループを作成するには、アプリケーションのユーザー インターフェイス (UI) のプロジェクトで .vsct ファイルを更新します。  
  
-   削除する**オプション**ページや、アプリケーションからその他の Visual Studio シェル コンポーネントは、アプリケーションの .pkgundef ファイルを更新します。  
  
-   外観の他の側面またはシェルの動作を変更するには、アプリケーションの .pkgdef ファイルを更新します。  
  
-   シェルの一部の機能は、アプリケーションを開始したときにも指定することができます。 これを行うには、始点、appenvstub.dll への呼び出しでパラメーターを更新できます。  
  
 カスタマイズ可能なさまざまな要素の詳細については、次を参照してください。[分離シェルの要素](../extensibility/elements-of-the-isolated-shell.md)します。  
  
## <a name="standard-features-of-the-isolated-shell"></a>分離シェルの標準的な機能  
 次の機能は、Visual Studio のすべてのエディションに標準的です。  
  
|機能カテゴリ|特性|  
|----------------------|-------------|  
|IDE の機能|インポート/エクスポートの設定<br /><br /> ツールボックス コントロール インストーラー<br /><br /> タスク一覧 >/documents/report1.rdl」のエラー一覧<br /><br /> [出力] ウィンドウ<br /><br /> スタート ページ<br /><br /> プロパティ ウィンドウ<br /><br /> ツールボックス<br /><br /> ソリューション エクスプローラー<br /><br /> ブックマーク ウィンドウ<br /><br /> クラス ビュー<br /><br /> オブジェクト ブラウザー<br /><br /> コマンド ウィンドウ<br /><br /> [ドキュメント アウトライン]<br /><br /> リソース ビュー<br /><br /> 外部ツール<br /><br /> Windows Communication Foundation (WCF) サービス参照を追加します。<br /><br /> 言語統合クエリ (LINQ) のサポート|  
|エディターとデザイナー|コード参照ツール統合検索、ソースの定義 (継承)<br /><br /> IntelliSense<br /><br /> スマート タグ<br /><br /> コード スニペット マネージャー<br /><br /> コード スニペット<br /><br /> リファクタリング<br /><br /> 見た目のよい一覧<br /><br /> IntelliSense フィルター処理<br /><br /> コード定義ウィンドウ<br /><br /> アプリケーション デザイナー<br /><br /> Windows フォーム デザイナー<br /><br /> Windows Presentation Foundation (WPF) デザイナー|  
|デバッグ|C# 式エバリュエーター<br /><br /> ローカルのデバッグ<br /><br /> マネージ デバッグ<br /><br /> エディット コンティニュ<br /><br /> スレッド間のデバッグ<br /><br /> 視覚エフェクト<br /><br /> [DataTips] ポップアップ<br /><br /> ネイティブ デバッグ<br /><br /> スクリプトのデバッグ<br /><br /> 相互運用機能デバッグ<br /><br /> ジャスト イン タイム (JIT) デバッグ<br /><br /> マルチ プロセス デバッグ<br /><br /> XSLT のデバッグ<br /><br /> ローカル プロセスにアタッチします。<br /><br /> トレース ポイント<br /><br /> ブレークポイント制約|  
|データ|サーバー エクスプ ローラー (簡体字のデータのみ)<br /><br /> ローカル データに対してデータ バインド (します。MDF またはです。MDB)<br /><br /> オブジェクトへのデータ バインド<br /><br /> Web サービスへのデータ バインド<br /><br /> データ コントロールの完全なセット<br /><br /> XML エディター<br /><br /> ローカル データベース サーバーへのデータ バインド<br /><br /> [データ ソース] ウィンドウ|  
|Web|HTML エディター<br /><br /> Web ブラウザー<br /><br /> Web フォーム デザイナー<br /><br /> Web サイト プロジェクト<br /><br /> Web アプリケーション プロジェクト|  
|機能拡張|Vspackage および MEF コンポーネントを使用します。|  
  
## <a name="see-also"></a>関連項目  
 [Shell (分離プロセスまたは統合)](../extensibility/shell-isolated-or-integrated.md)
