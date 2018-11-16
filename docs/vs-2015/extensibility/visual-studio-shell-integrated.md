---
title: Visual Studio Shell (Integrated) |Microsoft Docs
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
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3eb0c8dd0588e1af9b3aad500c8bc9f899b44513
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765274"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell (Integrated)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio の統合シェルには、統合開発環境 (IDE)、デバッガー、およびソース管理の統合が含まれています。 プログラミング言語が含まれていません。 ただし、統合シェルはプログラミング言語を追加することを可能にするフレームワークを提供します。  
  
 Visual Studio の統合シェルとは、実際には、Visual Studio 分離シェルと統合シェルの特定のコンポーネントを含む追加のインストールの組み合わせです。  統合シェル アプリケーションは、両方の分離シェル再頒布可能パッケージを含める必要があります[Microsoft Visual Studio Shell (Isolated) 再頒布可能パッケージ](http://go.microsoft.com/fwlink/?LinkId=616022)と統合シェルの再頒布可能パッケージ[Microsoft Visual Studio Shell (Integrated) 再頒布可能パッケージ](http://go.microsoft.com/fwlink/?LinkId=616021)します。  
  
> [!NOTE]
>  分離と統合シェルの再頒布可能パッケージにアクセスする前にお客様の簡単なアンケートに記入してになります。  アンケートに記入した後は、するは再頒布可能パッケージのダウンロード リンクを含む Visual Studio の Connect ページに移動します。  Visual Studio の Connect サイトにアクセスする際に、ダウンロード リンクを見つけることができます、**プログラム&#124;VISUAL STUDIO 2015 統合と分離シェル**タブ。  
  
 完全なバージョンの Visual Studio と同じコンピューターに、統合シェル アプリケーションをインストールする場合、アプリケーションのコンポーネントを直接 Visual Studio に統合されます。  
  
## <a name="features-in-the-integrated-shell"></a>統合シェルの機能  
  
|||  
|-|-|  
|機能分野|機能|  
|言語サポート|-None|  
|IDE|<ul><li>設定<br /><br /> <ul><li>設定を作成します。</li><li>インポートおよびエクスポート設定</li><li>リセット設定</li></ul></li><li>**ツールボックス**統合</li><li>**タスク一覧**統合</li><li>ヘルプの統合</li><li>**オプション** ダイアログ ボックス</li><li>フォントおよび色の管理</li><li>**出力**ウィンドウ</li><li>**コマンド**ウィンドウ</li><li>ウィンドウの管理</li><li>コマンド、メニューのおよびキー バインド</li><li>ドメイン固有言語 (DSL) ランタイム</li></ul>|  
|プロジェクト システムとプロジェクトの種類|-ソリューションとソリューション フォルダー<br />ソリューション構成マネージャー<br />-項目の管理<br />単一のプロジェクトおよびマルチ プロジェクト ソリューション<br />アプリケーション デザイナー (簡略化されたプロジェクトのプロパティ)<br />-Web 参照を追加します。<br />-サービス参照を追加します。<br />単一のプロジェクト<br />Web サイト プロジェクトの種類<br />-Web アプリケーション プロジェクト|  
|ビルド|の IDE でカスタム ビルド ステップ<br />-知的財産 (IP) 保護のプリコンパイル<br />コード署名<br />     MSBuild|  
|エディター|コードの参照ツール (統合検索、ソースの定義、継承)<br />コード ナビゲーション<br />IntelliSense<br />スマート タグ<br />リファクタリング<br />-再フォーマットの一覧<br />IntelliSense のフィルター処理<br />-   **コード定義**ウィンドウ|  
|Designer|-Windows Presentation Foundation デザイナー<br />-Windows フォーム デザイナー<br />-Web デザイナーと HTML エディター|  
|データ|-   **サーバー エクスプ ローラー** (簡体字: データのみ)。 注 1 を参照してください。<br />-   **データ ソース**ウィンドウ<br />データ コントロールの完全なセット<br />XML エディター<br />データがローカル データ ソースにバインド (します。MDF またはします。MDB)<br />オブジェクトへのデータ バインド<br />Web サービスにデータをバインドします。<br />-データをバインドするローカル データベース サーバー<br />リモート データベース サーバーにデータ バインドします。<br />リモート データの DDL ツール<br />-   **サーバー エクスプ ローラー**機能拡張 ([!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]サンプル)|  
|デバッガー|-ローカル デバッグします。 注 2 を参照してください。<br />マネージ デバッグ<br />-ローカル デバッグ<br />-ローカルのプロセスにアタッチします。<br />-リモート プロセスにアタッチします。<br />匿名デリゲート<br />アプリケーション ドメイン<br />ASPX のデバッグ<br />-属性<br />-Func eval の中に中断します。<br />-ブレークポイント<br />ブレークポイント制約<br />-呼び出し履歴<br />-   **コマンド**ウィンドウ<br />-クロス スレッドのデバッグ<br />-データのヒント<br />データ ビジュアライザー<br />マネージ デバッグ アシスタント (Mda) のデバッガー サポート<br />型フォワーダーのデバッガー サポート<br />-DTEEvents OTB のサポート<br />-JMC ステッパ<br />-デバッガー AppID テスト (DBGCLR)<br />デバッガーのプロファイル<br />-デバッガー ツールとオプション<br />反復子のデバッグ<br />デザイン時の式の評価<br />-C# の式エバリュエーター<br />-逆アセンブリ<br />エディット コンティニュ<br />式エバリュエーター windows (ウォッチ、[ローカル]、[自動変数])<br />-例外ヘルパー<br />-例外<br />-実行<br />- ジェネリック<br />-適切なソースを取得します。<br />HPC/クラスター デバッガー<br />-複数言語のデバッグを統合します。<br />-相互運用機能デバッグ<br />--Just-in-time デバッグ<br />-ローカル デバッグ<br />マネージ デバッグ<br />-手動で制御 ([プロセス] ウィンドウ)<br />メモリ<br />のミニダンプ サポート<br />-モジュール<br />-マルチ プロセス デバッグ<br />ネイティブのデバッグ<br />新しいデバッグ エンジンのサポート<br />-最適化されたコードのデバッグ<br />-出力 windows フィルタ リング<br />-プロセスをホストしているマネージ デバッグのため<br />-プロセス<br />-[クイック ウォッチ]<br />登録<br />Stack の登録<br />-リモート デバッグ<br />戻り値<br />スクリプトのデバッグ<br />ソース サービスのサポート<br />-セキュリティ<br />--サイド<br />-SQL<br />シンボル サーバー<br />トレース ポイント<br />-スレッド<br />-視覚エフェクト<br />-Extensible Stylesheet Language Transformations (XSLT) デバッガー|  
|64 ビット サポート|-64 ビットのマネージ コードとネイティブ コード、すべての言語のデバッグ<br />-x64 のネイティブ サポート|  
|ソース コード管理 (SCC)|-基本的な SCC 統合です。 注 3 を参照してください。<br />ツールとオプションの確認|  
|機能拡張|-Vspackage と MEF コンポーネントを使用します。|  
  
## <a name="notes"></a>メモ  
  
#### <a name="1-data-tools"></a>1.データ ツール  
 統合シェルには、データ拡張機能のサポートと、簡略化などのデータベース開発ツールが含まれています。**ソリューション エクスプ ローラー**します。 ただし、SQL Server Express、SQL Reporting、および Crystal Reports は、統合シェルには含まれません。  
  
#### <a name="2-debugging-support"></a>2.デバッグのサポート  
 統合シェルには、Visual Studio の Community バージョンに含まれている同じデバッグ エンジンが含まれています。 デバッグ エンジンには、実行、アタッチ、ブレークポイントの設定、編集と続行、および他のユーザーなどの関連機能とマネージ コードは、一般的なデバッガーが含まれています。 ただし、デバッグ エンジンでは、SQL Server データベースのデバッグはできません。  
  
 サポート、デバッガーの基本的なパッケージでは、ネイティブ デバッグが含まれているの他の言語をサポートするようには拡張できません。  
  
#### <a name="3-source-code-control-integration"></a>3.ソース コード管理の統合  
 統合シェルは、ソース コード管理 (SCC) を実装するため、MSSCCI ベースの一般的なソース管理の統合コンポーネントを提供するための Api を提供します。  
  
 SCC 統合は、Pro エディションの Visual Studio の標準機能ではありませんが、統合シェルの SCC 統合が提供されます。  
  
#### <a name="4-build-support"></a>4.ビルドのサポート  
 統合シェルは、ビルドのサポートを提供します。 ビルドに関する情報を見つけることができます、 [MSBuild リファレンス](../msbuild/msbuild-reference.md)します。  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Integrated Shell に含まれていない機能  
 統合シェルに含まれていない機能の一覧を次には。  
  
-   クラス デザイナー  
  
-   プリエンプティブな DotFuscator  
  
-   言語機能  
  
-   VSHost  
  
-   言語の Visual Studio、または、関連付けられているプロジェクト テンプレートまたはプロジェクト項目テンプレートは、統合シェルに含まれます。 その他の機能の言語固有の実装が含まれる、Visual Basic コード スニペットの例ではありません。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio の拡張の概要](http://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)