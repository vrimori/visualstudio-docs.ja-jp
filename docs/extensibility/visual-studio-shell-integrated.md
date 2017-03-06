---
title: "Visual Studio Shell (統合) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
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
ms.sourcegitcommit: 4f2ddbc47f9a014acde2850dba5c72ef3a784847
ms.openlocfilehash: 8edd3a6fcca0c2ddd4d580f0874b737cfbbc40c9
ms.lasthandoff: 03/01/2017

---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (統合)
Visual Studio の統合シェルには、統合開発環境 (IDE)、デバッガー、およびソース管理の統合が含まれています。 プログラミング言語が含まれていません。 ただし、統合シェルはプログラミング言語を追加するためのフレームワークを提供します。  
  
 Visual Studio の統合シェルは、実際には、分離された Visual Studio シェルと統合シェルの特定のコンポーネントが含まれている追加のインストールの組み合わせです。  統合シェル アプリケーションは両方、分離シェル再頒布可能パッケージを含める必要があります[Microsoft Visual Studio Shell (Isolated) 再頒布可能パッケージ](http://go.microsoft.com/fwlink/?LinkId=616022)から統合シェルの再頒布可能パッケージだけでなく[Microsoft Visual Studio Shell (Integrated) 再頒布可能パッケージ](http://go.microsoft.com/fwlink/?LinkId=616021)します。  
  
> [!NOTE]
>  分離、統合シェルの再頒布可能パッケージにアクセスする前に、簡単なアンケートの記入を求められます。  アンケートの記入、後に表示する再頒布可能パッケージのダウンロード リンク付きの Visual Studio の Connect のページにします。  ダウンロード リンクを参照 [Visual Studio の Connect サイトにアクセスする際に、**プログラム |VISUAL STUDIO 2015 統合し、分離シェル**] タブをクリックします。  
  
 Visual Studio の完全なバージョンと同じコンピューターに、統合シェル アプリケーションをインストールする場合、アプリケーションのコンポーネントは、Visual Studio へ直接統合されます。  
  
## <a name="features-in-the-integrated-shell"></a>統合シェルの機能  
  
|||  
|-|-|  
|機能エリア|特性|  
|言語サポート|-なし|  
|IDE|<ul><li>設定<br /><br /> <ul><li>設定を作成します。</li><li>インポートとエクスポートの設定</li><li>設定のリセット</li></ul></li><li>**ツールボックス**統合</li><li>**タスク一覧**の統合</li><li>ヘルプの統合</li><li>**オプション** ダイアログ ボックス</li><li>フォントおよび色の管理</li><li>**出力**ウィンドウ</li><li>**コマンド**ウィンドウ</li><li>ウィンドウの管理</li><li>コマンド、メニューのおよびショートカット キー</li><li>ドメイン固有言語 (DSL) ランタイム</li></ul>|  
|プロジェクト システムとプロジェクトの種類|ソリューションおよびソリューション フォルダー<br />ソリューション構成マネージャー<br />-項目の管理<br />単一のプロジェクトおよびマルチ プロジェクト ソリューション<br />アプリケーション デザイナー (簡略化されたプロジェクトのプロパティ)<br />-Web 参照を追加します。<br />-サービス参照を追加します。<br />単一のプロジェクト<br />Web サイト プロジェクトの種類<br />-Web アプリケーション プロジェクト|  
|ビルド|の IDE でカスタム ビルド ステップ<br />-知的財産 (IP) 保護のプリコンパイル<br />コード署名<br />     MSBuild|  
|エディター|コードの参照ツール統合検索、ソースの定義 (継承)<br />コード ナビゲーション<br />IntelliSense<br />スマート タグ<br />リファクタリング<br />-再<br />-IntelliSense フィルター処理<br />-   **コード定義**ウィンドウ|  
|Designer|Windows Presentation Foundation デザイナー<br />Windows フォーム デザイナー<br />-Web デザイナーと HTML エディター|  
|データ|-   **サーバー エクスプ ローラー** (簡体字: データのみ)。 注 1 を参照してください。<br />-   **データ ソース**ウィンドウ<br />のデータ コントロール完全なセット<br />XML エディター<br />ローカル データ ソースにデータ バインド (します。MDF またはです。MDB)<br />オブジェクトへのデータ バインド<br />Web サービスにデータをバインドします。<br />ローカル データベース サーバーへのデータをバインドします。<br />リモート データベース サーバーへのデータをバインドします。<br />リモート データ DDL ツール<br />-   **サーバー エクスプ ローラー**機能拡張 ([!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]サンプル)|  
|デバッガー|-ローカル デバッグします。 注 2 を参照してください。<br />マネージ デバッグ<br />-ローカルのデバッグ<br />-ローカル プロセスにアタッチします。<br />-リモート プロセスにアタッチします。<br />匿名のデリゲート<br />アプリケーション ドメイン<br />ASPX のデバッグ<br />属性<br />-Func eval の中に中断します。<br />ブレークポイント<br />ブレークポイント制約<br />呼び出し履歴<br />-   **コマンド**ウィンドウ<br />-スレッド間のデバッグ<br />データ ヒント<br />-データ ビジュアライザー<br />-マネージ デバッグ アシスタント (Mda) に対するデバッガーのサポート<br />-型フォワーダーに対するデバッガーのサポート<br />-OTB DTEEvents サポート<br />-JMC ステッパ<br />デバッガーの AppID のテスト (DBGCLR)<br />デバッガーのプロファイル<br />-デバッガー ツールとオプション<br />反復子のデバッグ<br />-デザイン時の式の評価<br />-C# 式エバリュエーター<br />-[逆アセンブリ]<br />エディット コンティニュ<br />式エバリュエーター ウィンドウ ([ウォッチ]、[ローカル]、[自動変数])<br />例外ヘルパー<br />例外を許可<br />実行<br />ジェネリック型<br />-右のソースの概要<br />HPC/クラスター デバッガー<br />-統合多言語のデバッグ<br />-相互運用機能デバッグ<br />--Just-in-time デバッグ<br />-ローカルのデバッグ<br />マネージ デバッグ<br />-手動で制御 ([プロセス] ウィンドウ)<br />メモリ不足<br />のミニダンプ サポート<br />-モジュール<br />-マルチ プロセス デバッグ<br />ネイティブのデバッグ<br />新しいデバッグ エンジンのサポート<br />-最適化されたコードのデバッグ<br />出力 windows フィルタ リング<br />プロセスでホストしているマネージ デバッグ<br />-プロセス<br />-[クイック ウォッチ]<br />登録します。<br />スタックの登録<br />-リモート デバッグ<br />戻り値<br />スクリプトのデバッグ<br />ソース サービスのサポート<br />-セキュリティ<br />--Side-by-side<br />SQL<br />シンボル サーバー<br />トレース ポイント<br />スレッド<br />視覚エフェクト<br />-Extensible Stylesheet Language Transformations (XSLT) デバッガー|  
|64 ビット サポート|-64 ビットのマネージ コードとネイティブ コード、すべての言語のデバッグ<br />x64 ネイティブ サポート|  
|ソース コード管理 (SCC)|-基本的なソース コード管理の統合。 注 3 を参照してください。<br />ツールとオプションの確認|  
|機能拡張|-Vspackage および MEF コンポーネントを使用します。|  
  
## <a name="notes"></a>ノート  
  
#### <a name="1-data-tools"></a>1.データ ツール  
 Integrated shell には、データ拡張機能のサポートと、簡略化されたなどのデータベース開発ツールが含まれています。**ソリューション エクスプ ローラー**します。 ただし、SQL Server Express、SQL レポート、および Crystal Reports は、統合シェルには含まれません。  
  
#### <a name="2-debugging-support"></a>2.デバッグのサポート  
 Integrated shell には、Visual Studio の Community バージョンに含まれている同じデバッグ エンジンが含まれています。 デバッグ エンジンには、実行、アタッチ、ブレークポイントの設定、エディット コンティニュ、および他のユーザーなどの関連する機能とマネージ コードの一般的なデバッガーが含まれています。 ただし、デバッグ エンジンでは、SQL Server データベースのデバッグはできません。  
  
 サポート、基本的なデバッガー パッケージには、ネイティブのデバッグが含まれているの他の言語をサポートするようには拡張できません。  
  
#### <a name="3-source-code-control-integration"></a>3.ソース コード管理の統合  
 統合シェルは、ソース コード管理 (SCC) を実装するため、MSSCCI ベースの一般的なソース管理の統合コンポーネントを提供するために、Api を提供します。  
  
 SCC の統合が Pro エディションの Visual Studio の標準機能ではありませんが、ソース コード管理の統合は integrated shell で提供されます。  
  
#### <a name="4-build-support"></a>4.サポートを構築します。  
 統合シェルは、ビルドのサポートを提供します。 ビルドに関する情報を見つけることができます、 [MSBuild リファレンス](../msbuild/msbuild-reference.md)します。  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Integrated Shell で含まれていない機能  
 Integrated shell で含まれていない機能の一覧を次に示します。  
  
-   クラス デザイナー  
  
-   [Dotfuscator プリエンプティブの保護](../ide/dotfuscator/index.md)  
  
-   言語機能  
  
-   VSHost  
  
-   Integrated shell では、言語の Visual Studio や、関連付けられているプロジェクト テンプレートやプロジェクト項目テンプレートが含まれています。 その他の機能の言語固有の実装が含まれる、Visual Basic コード スニペットの例ではありません。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio の概要を拡張します。](../Topic/Extending%20Visual%20Studio%20Overview.md)
