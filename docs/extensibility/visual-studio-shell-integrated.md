---
redirect_url: shell/visual-studio-shell-integrated
title: "Visual Studio Shell (Integrated) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d92a6c7250e22972a2b352b74b974601ff6065c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (Integrated)
Visual Studio の統合シェルには、統合開発環境 (IDE)、デバッガー、およびソース管理の統合が含まれています。 プログラミング言語が含まれていない場合です。 ただし、integrated shell はプログラミング言語を追加するためのフレームワークを提供します。  
  
 Visual Studio の統合シェルは、実際には、Visual Studio 分離シェルと統合シェル固有のコンポーネントが含まれている追加のインストールの組み合わせです。  統合シェル アプリケーションは両方分離シェル再頒布可能パッケージを含める必要があります[Microsoft Visual Studio Shell (Isolated) 再頒布可能パッケージ](http://go.microsoft.com/fwlink/?LinkId=616022)だけでなく、統合シェルの再頒布可能パッケージ[Microsoft Visual Studio シェル (Integrated) 再頒布可能パッケージ](http://go.microsoft.com/fwlink/?LinkId=616021)です。  
  
> [!NOTE]
>  シェルの分離と統合された再頒布可能パッケージにアクセスできるように、簡単なアンケートに記入になります。  アンケートの記入、後に表示する再頒布可能パッケージのダウンロード リンクを Visual Studio の接続ページにします。  Visual Studio 接続サイトにアクセスする際にダウンロードのリンクを見つけることができます、**プログラム &#124;です。VISUAL STUDIO 2015 統合および ISOLATED SHELL**タブです。  
  
 完全バージョンの Visual Studio と同じコンピューターに、統合シェル アプリケーションをインストールする場合、アプリケーションのコンポーネントは、Visual Studio に直接統合されます。  
  
## <a name="features-in-the-integrated-shell"></a>Integrated Shell での機能  
  
|||  
|-|-|  
|機能分野|特性|  
|言語サポート|-なし|  
|IDE|<ul><li>設定<br /><br /> <ul><li>設定を作成します。</li><li>インポートとエクスポートの設定</li><li>設定のリセット</li></ul></li><li>**ツールボックス**統合</li><li>**タスク一覧**統合</li><li>ヘルプの統合</li><li>**オプション** ダイアログ ボックス</li><li>フォントおよび色の管理</li><li>**出力**ウィンドウ</li><li>**コマンド**ウィンドウ</li><li>ウィンドウの管理</li><li>コマンド、メニューのおよびショートカット キー</li><li>ドメイン固有言語 (DSL) ランタイム</li></ul>|  
|プロジェクト システムとプロジェクトの種類|ソリューションおよびソリューション フォルダー<br />ソリューション構成マネージャー<br />項目の管理<br />単一のプロジェクトおよびマルチ プロジェクト ソリューション<br />アプリケーション デザイナー (簡略化されたプロジェクトのプロパティ)<br />-Web 参照を追加します。<br />-サービス参照を追加します。<br />単一のプロジェクト<br />Web サイト プロジェクトの種類<br />Web アプリケーション プロジェクト|  
|ビルド|の IDE でカスタム ビルド ステップ<br />事前コンパイルの知的財産 (IP) の保護<br />コード署名<br />     MSBuild|  
|エディター|コードの参照ツール (統合検索、ソースの定義、継承)<br />コード ナビゲーション<br />IntelliSense<br />スマート タグ<br />リファクタリング<br />-見た目のよい一覧<br />IntelliSense のフィルター処理<br />-   **コード定義**ウィンドウ|  
|Designer|Windows Presentation Foundation デザイナー<br />Windows フォーム デザイナー<br />-Web デザイナーおよび HTML エディター|  
|データ|-   **サーバー エクスプ ローラー** (簡体字: データのみ)。 注 1 を参照してください。<br />-   **データ ソース**ウィンドウ<br />のデータ コントロール完全なセット<br />XML エディター<br />ローカル データ ソースにデータ バインド (です。MDF またはします。MDB)<br />のオブジェクトへのデータ バインド<br />Web サービスにデータ バインドします。<br />のローカル データベース サーバーへデータをバインドします。<br />、リモート データベース サーバーにデータ バインドします。<br />リモート データの DDL ツール<br />-   **サーバー エクスプ ローラー**機能拡張 ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]サンプル)|  
|デバッガー|-ローカル デバッグ。 注 2 を参照してください。<br />マネージ デバッグ<br />-ローカルのデバッグ<br />-ローカル プロセスにアタッチします。<br />-リモート プロセスにアタッチします。<br />匿名デリゲート<br />アプリケーション ドメイン<br />ASPX のデバッグ<br />属性<br />-Func eval の中に中断します。<br />-ブレークポイント<br />ブレークポイント制約<br />-呼び出し履歴<br />-   **コマンド**ウィンドウ<br />-スレッド間のデバッグ<br />データのヒント<br />データ ビジュアライザー<br />-マネージ デバッグ アシスタント (Mda) に対するデバッガーのサポート<br />-型フォワーダーに対するデバッガーのサポート<br />-OTB DTEEvents サポート<br />-JMC ステッパ<br />-デバッガー AppID テスト (DBGCLR)<br />デバッガーのプロファイル<br />-デバッガーのツールとオプション<br />反復子のデバッグ<br />デザイン時の式評価<br />-C# の式エバリュエーター<br />-逆アセンブル<br />-エディット コンティニュ<br />式エバリュエーター windows (ウォッチ、[ローカル]、[自動変数])<br />例外ヘルパー<br />-例外<br />-実行<br />- ジェネリック<br />-右のソースを取得します。<br />HPC/クラスター デバッガー<br />統合多言語のデバッグ<br />相互運用機能デバッグ<br />--Just-in-time デバッグ<br />-ローカルのデバッグ<br />マネージ デバッグ<br />-手動で制御 ([プロセス] ウィンドウ)<br />メモリ<br />のミニダンプ サポート<br />-モジュール<br />-マルチ プロセス デバッグ<br />ネイティブのデバッグ<br />-新しいデバッグ エンジンのサポート<br />-最適化されたコードのデバッグ<br />出力 windows フィルタ リング<br />プロセスでホストしているマネージ デバッグ<br />-プロセス<br />-[クイック ウォッチ]<br />-登録します。<br />スタックの登録<br />リモート デバッグ<br />戻り値<br />スクリプトのデバッグ<br />ソース サービスのサポート<br />セキュリティ<br />---並べて<br />-SQL<br />シンボル サーバー<br />トレース ポイント<br />スレッド<br />視覚エフェクト<br />-Extensible Stylesheet Language Transformations (XSLT) デバッガー|  
|64 ビット サポート|-64 ビットは、マネージとネイティブ コードの両方、すべての言語のデバッグ<br />-x64 のネイティブ サポート|  
|ソース コード管理 (SCC)|-基本的な SCC 統合します。 注 3 を参照してください。<br />ツールおよびオプションの確認|  
|機能拡張|-Vspackage および MEF コンポーネントを使用します。|  
  
## <a name="notes"></a>メモ  
  
#### <a name="1-data-tools"></a>1.データ ツール  
 Integrated shell には、データ拡張機能のサポートと、簡略化されたなどのデータベース開発ツールが含まれています。**ソリューション エクスプ ローラー**です。 ただし、SQL Server Express、SQL レポート、および Crystal Reports は、integrated shell には含まれません。  
  
#### <a name="2-debugging-support"></a>2.デバッグのサポート  
 Integrated shell には、Visual Studio のコミュニティ バージョンに含まれている同じデバッグ エンジンが含まれています。 デバッグ エンジンには、実行、アタッチ、ブレークポイントの設定、エディット コンティニュ、および他のユーザーなどの関連する機能と、マネージ コードの一般的なデバッガーが含まれています。 ただし、デバッグ エンジンでは、SQL Server データベースのデバッグはできません。  
  
 サポート ネイティブ デバッグは、デバッガーの基本的なパッケージに含まれての他の言語をサポートするようには拡張できません。  
  
#### <a name="3-source-code-control-integration"></a>3.ソース コード管理の統合  
 Integrated shell は、ソース コード管理 (SCC) を実装するため、一般的なソースの MSSCCI に基づいた管理の統合コンポーネントを提供するために、Api を提供します。  
  
 SCC 統合ではありませんが、正規 Pro 版の Visual Studio の機能は、SCC 統合が integrated shell で提供されます。  
  
#### <a name="4-build-support"></a>4.ビルドのサポート  
 Integrated shell では、ビルドのサポートを提供します。 ビルドに関する情報を見つけることができます、 [MSBuild リファレンス](../msbuild/msbuild-reference.md)です。  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Integrated Shell に含まれていない機能  
 Integrated shell に含まれていない機能の一覧を次に示します。  
  
-   クラス デザイナー  
  
-   [プリエンプティブの保護 - Dotfuscator](../ide/dotfuscator/index.md)  
  
-   言語機能  
  
-   VSHost  
  
-   Integrated shell では、なしの Visual Studio の言語や、関連付けられているプロジェクト テンプレートやプロジェクト項目テンプレートが含まれています。 その他の機能の言語固有の実装が含まれる、Visual Basic コード スニペットの例ではありません。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)