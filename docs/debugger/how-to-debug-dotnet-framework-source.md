---
title: "方法: .NET Framework ソースのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/23/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 75f3665afcf5d4937fae46e2a6871e0f7121b561
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-debug-net-framework-source"></a>方法 : .NET Framework ソースをデバッグする
.NET Framework のソースをデバッグするには、コードのデバッグ シンボルへのアクセスが必要です。 また、.NET Framework ソースへのステップ インを有効にする必要があります。  
  
 .NET Framework を有効にすることができますステップ実行とシンボルのダウンロード、**オプション** ダイアログ ボックス。 シンボルのダウンロードを有効にする場合は、シンボルを即時にダウンロードするのか、後でダウンロードするのかを選択できます。 シンボルを即時にダウンロードしない場合、次にアプリケーションのデバッグを開始するときにシンボルはダウンロードされます。 実行することもできますから手動でダウンロード、**モジュール**ウィンドウまたは**呼び出し履歴**ウィンドウです。  
  
### <a name="to-enable-net-framework-source-debugging"></a>.NET Framework ソースのデバッグを有効にするには  
  
1.  **ツール** メニューのをクリックして**オプション**s。  
  
2.  **オプション** ダイアログ ボックスをクリックして、**デバッグ**カテゴリ。  
  
3.  **全般**ボックスで、設定**を有効にする .NET Framework ソースのステップ インします。**  
  
    1.  [マイ コードのみ] が有効だった場合、[マイ コードのみ] が無効になったことを示す警告ダイアログ ボックスが表示されます。 **[OK]**をクリックします。  
  
    2.  シンボル キャッシュの場所が設定されていない場合は、既定のシンボル キャッシュの場所が設定されたことを示す別の警告ダイアログ ボックスが表示されます。 **[OK]**をクリックします。  
  
4.  下にある、**デバッグ**カテゴリで、をクリックして**シンボル**です。  
  
5.  シンボル キャッシュの場所を変更する場合は、場所を編集**このディレクトリにシンボルをキャッシュ** をクリックしてまたは**参照**場所を選択します。  
  
6.  シンボルを即時にダウンロードする場合は、クリックして**シンボルの読み込みは、上記の場所を使用して**です。  
  
     このボタンをクリックでは、デザイン モードでは使用できませんはデバッグ中に使用できます。  
  
     シンボルを即時にダウンロードしない場合、次にプログラムのデバッグを開始するときにシンボルは自動的にダウンロードされます。  
  
7.  **[OK]** をクリックして、**[オプション]** ダイアログ ボックスを閉じます。  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>[モジュール] ウィンドウを使用して Framework シンボルを読み込むには  
  
1.  **モジュール**ウィンドウ (デバッグ中に次のように選択します**デバッグ** > **Windows** > **モジュール**)、。シンボルが読み込まれていないモジュールを右クリックします。 あることがわかりますシンボルが読み込まれている場合、または参照ではなく、**シンボルの状態**列です。  
  
2.  をポイント**シンボル設定** をクリック**Microsoft シンボル サーバー** Microsoft パブリック シンボル サーバーからシンボルをダウンロードします。 または、モジュールを右クリックしを選択することができます**シンボルの読み込み**に位置するシンボルを格納したディレクトリから読み込みます。  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>[呼び出し履歴] ウィンドウを使用して Framework シンボルを読み込むには  
  
1.  **呼び出し履歴**ウィンドウで、シンボルが読み込まれていないフレームを右クリックします。 フレームが淡色表示されます。  
  
2.  をポイント**シンボル設定** をクリック**Microsoft シンボル サーバー**、またはモジュールを右クリックし、選択**シンボル パス**です。  
  
## <a name="see-also"></a>参照  
 [マネージ コードをデバッグする](../debugger/debugging-managed-code.md)   
 [シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)