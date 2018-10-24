---
title: '方法: Code Center Premium ソースをデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ac76a294c8f6b536da93f06afe6e423ca593b84
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824166"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>方法: Code Center Premium ソースをデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] デバッガーでは、Microsoft MSDN Code Center Premium のセキュリティ保護された共有ソースをデバッグできます。  
  
 このトピックでは、Visual Studio で Code Center Premium ソース コードを設定し、デバッグする方法について説明します。  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Code Center Premium を使用したデバッグを準備するには  
  
1. スマートカード リーダーを接続し、シェアード ソース イニシアティブから取得したカードを挿入します。  
  
2. Visual Studio を起動します。  
  
3. **[ツール]** メニューの **[オプション]** をクリックします。  
  
4. **オプション**ダイアログ ボックスで、**デバッグ**ノードをクリックします**全般**します。  
  
5. クリア、**を有効にする マイ コードのみ (マネージのみ)** チェック ボックスをオンします。  
  
6. 選択**ソース サーバー サポートを有効にする**します。  
  
7. クリア**元のバージョンと正確に一致するソース ファイルが必要です。** します。  
  
8. 下、**デバッグ**ノード、をクリックして**シンボル**します。  
  
9. **シンボル ファイル (.pdb) の場所**ボックスをオフ、 **Microsoft シンボル サーバー**チェック ボックスをオンし、次の場所を追加します。  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  末尾のスラッシュを必ず<strong>/</strong> パスの末尾。  
  
     これらの場所を一覧の最上部に移動して、これらのシンボルが最初に読み込まれるようにします。  
  
   > [!NOTE]
   >  これらの Code Center Premium の場所が最初に読み込まれる場所になるように、これらが一覧の最初に配置されている必要があります。 Visual Studio 2010 では、上記のすべてのサーバーを移動することはできません、 **Microsoft シンボル サーバー**エントリは、チェック ボックスをオフにする必要があります。  
   > 
   >  デバッグ セッション中に Microsoft シンボルからシンボルを読み込むには、次の手順に従います。  
   > 
   > 1. **デバッグ**] メニューの [選択**Windows**選び、**モジュール**します。  
   >    2.  シンボルの対象となるモジュールを選択し、ショートカット メニューを開きます。 選択**シンボルの読み込み元**選び、 **Microsoft シンボル サーバー**します。  
  
10. **このディレクトリにシンボル サーバーからシンボルをキャッシュ**などの場所の入力ボックスに、 `C:\symbols` Code Center Premium がシンボルをキャッシュできます。 シンボルをキャッシュすることにより、デバッグ中のパフォーマンスが大幅に向上します。  
  
     この手順を実行した後、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でのソース コードのデバッグに問題が発生する場合は、以前にキャッシュされて古くなったシンボル ファイルがキャッシュの場所にないかどうかを確認してください。 古いシンボル ファイルは削除してください。  
  
11. **[OK]** をクリックします。  
  
12. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] を再起動して、設定が保持されていることを確認します。  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>[プロセスにアタッチ] を使用してソース コードをデバッグするには  
  
1.  スマートカード リーダーを接続し、シェアード ソース イニシアティブから取得したカードを挿入します。  
  
2.  Visual Studio を起動します。  
  
3.  Visual Studio プロジェクトを開きます。  
  
4.  **ツール** メニューのをクリックして**プロセスにアタッチ**します。  
  
5.  **プロセスにアタッチ**ダイアログ ボックスで、をクリックして**選択**します。  
  
6.  **コードの種類の選択**ダイアログ ボックスで、**コードの種類を検出**を選択します**ネイティブ**、**マネージ**、および **(の管理v4.0)** します。  
  
7.  をクリックして**OK**を閉じる、**コードの種類の選択** ダイアログ ボックス。  
  
8.  **選択可能なプロセス**ボックスで、デバッグするプロセスを選択します。  
  
9. **[アタッチ]** をクリックします。  
  
10. 証明書を確認するメッセージが表示されたら、クリックして**OK**します。 暗証番号 (PIN) を入力します。 Code Center Premium の使用条件を承諾します (要求された場合)。  
  
     ネットワーク速度によっては、シンボルのダウンロードに時間がかかる場合があります。 すべてのシンボルが正常にダウンロードされると、ステータス バーにその旨が表示されます。  
  
11. ソリューションのすべてのマネージド プロジェクトに対して、アタッチ手順を繰り返します。  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>既存のソリューションのソース コードをデバッグするには  
  
1. **ソリューション エクスプ ローラー**ソリューションのショートカット メニューを開き、選択し、**プロパティ**します。  
  
2. [ソリューション プロパティ ページ] ダイアログ ボックスで、次のように選択します。**デバッグ ソース ファイル**で、**共通プロパティ**ノード。  
  
3. 次の場所を追加、**ソース ファイルを含むディレクトリ**一覧。  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  末尾のスラッシュを必ず<strong>/</strong> パスの末尾。  
  
4. ソリューション内のマネージド プロジェクトごとに、次の操作を行います。  
  
   1.  ソリューション エクスプ ローラーで プロジェクトのショートカット メニューを開き、**プロパティ**します。  
  
   2.  選択**デバッグ**選び、**アンマネージ コード デバッグを有効にする**します。  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Code Center Premium ソースを使用したソリューションをデバッグするには  
  
1.  `Package` クラスで、パッケージ コンストラクターにブレークポイントを設定します。  
  
2.  `Debug`  メニューのをクリックして**デバッグの開始**します。  
  
3.  パッケージ コンス トラクター内のブレークポイントにヒットしたらに移動、**呼び出し履歴**ウィンドウとをクリックし、シンボルからロードするアセンブリのスタック フレーム右**シンボルの読み込み**します。  
  
     ソースを読み込むには、呼び出しフレームをダブルクリックします。  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Code Center Premium のソース コードを参照するには  
  
1.  スマートカード リーダーを接続し、シェアード ソース イニシアティブから取得したカードを挿入します。  
  
2.  Internet Explorer を起動し、URL として「`https://codepremium.msdn.microsoft.com`」と入力します。  
  
3.  必要なソースを探します。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)   
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)



