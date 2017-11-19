---
title: "方法: .NET Framework ソースのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9da2cd7b8a99d750692a69be406c9c8f82c461d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-net-framework-source"></a>方法 : .NET Framework ソースをデバッグする
最新バージョン[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]の新機能を提供[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]デバッグします。 デバッグする[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]、ソース コードのデバッグ シンボルへのアクセスが必要です。 ステップ インを有効にする必要も[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]ソース。  
  
 有効にすることができます[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]ステップ実行とシンボルのダウンロード、**オプション** ダイアログ ボックス。 シンボルのダウンロードを有効にする場合は、シンボルを即時にダウンロードするのか、後でダウンロードするのかを選択できます。 シンボルを即時にダウンロードしない場合、次にアプリケーションのデバッグを開始するときにシンボルはダウンロードされます。 実行することもできますから手動でダウンロード、**モジュール**ウィンドウまたは**呼び出し履歴**ウィンドウです。  
  
### <a name="to-enable-net-framework-source-debugging"></a>.NET Framework ソースのデバッグを有効にするには  
  
1.  **ツール** メニューのをクリックして**オプション**s。  
  
2.  **オプション** ダイアログ ボックスをクリックして、**デバッグ**カテゴリ。  
  
3.  **全般**ボックスで、設定**を有効にする .NET Framework**ソースのステッピングします。  
  
    1.  [マイ コードのみ] が有効だった場合、[マイ コードのみ] が無効になったことを示す警告ダイアログ ボックスが表示されます。 **[OK]** をクリックします。  
  
    2.  シンボル キャッシュの場所が設定されていない場合は、既定のシンボル キャッシュの場所が設定されたことを示す別の警告ダイアログ ボックスが表示されます。 **[OK]** をクリックします。  
  
4.  下にある、**デバッグ**カテゴリで、をクリックして**シンボル**です。  
  
5.  シンボル キャッシュの場所を変更する場合:   
  
    1.  開く、**デバッグ**左側のボックス内のノードです。  
  
    2.  下にある、**デバッグ**ノード、をクリックして**シンボル**です。  
  
    3.  内の場所を編集**このディレクトリにシンボル サーバーからシンボルをキャッシュ** をクリックしてまたは**参照**場所を選択します。  
  
6.  シンボルを即時にダウンロードする場合は、クリックして**シンボルの読み込みは、上記の場所を使用して**です。  
  
     このボタンはデザイン モードでは使用できません。  
  
     シンボルを即時にダウンロードしない場合、次にプログラムのデバッグを開始するときにシンボルは自動的にダウンロードされます。  
  
7.  をクリックして**OK**を閉じる、**オプション** ダイアログ ボックス。  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>[モジュール] ウィンドウを使用して Framework シンボルを読み込むには  
  
1.  **モジュール**ウィンドウで、シンボルが読み込まれていないモジュールを右クリックします。 あることがわかりますシンボルが読み込まれている場合、または参照ではなく、**シンボルの状態**列です。  
  
2.  をポイント**シンボルの読み込み元** をクリック**Microsoft シンボル サーバー** Microsoft パブリック シンボル サーバーからシンボルをダウンロードまたは**シンボル パス**をディレクトリから読み込みますここでシンボルを格納しました。  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>[呼び出し履歴] ウィンドウを使用して Framework シンボルを読み込むには  
  
1.  **呼び出し履歴**ウィンドウで、シンボルが読み込まれていないフレームを右クリックします。 フレームが淡色表示されます。  
  
2.  指す**シンボルの読み込み元** をクリック**Microsoft シンボル サーバー**または**シンボル パス**です。  
  
## <a name="see-also"></a>関連項目  
 [マネージ コードをデバッグする](../debugger/debugging-managed-code.md)   
 [シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)