---
title: '方法: .NET Framework のソースをデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 02/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c06a2328987201198bc2d5d15a4788d2a821d7b6
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219121"
---
# <a name="how-to-debug-net-framework-source"></a>方法 : .NET Framework ソースをデバッグする
.NET Framework のソースをデバッグするには、コードのデバッグ シンボルへのアクセスが必要です。 また、.NET Framework のソースへのステップ インを有効にする必要があります。  
  
 .NET Framework を有効にすることがステップ実行とシンボルのダウンロード、**オプション** ダイアログ ボックス。 シンボルのダウンロードを有効にする場合は、シンボルを即時にダウンロードするのか、後でダウンロードするのかを選択できます。 シンボルを即時にダウンロードしない場合、次にアプリケーションのデバッグを開始するときにシンボルはダウンロードされます。 また、手動でダウンロードを行うことができます、**モジュール**ウィンドウまたは**呼び出し履歴**ウィンドウ。  
  
### <a name="to-enable-net-framework-source-debugging"></a>.NET Framework ソースのデバッグを有効にするには  
  
1.  **[ツール]** メニューの **[オプション]** をクリックします。  
  
2.  **オプション**ダイアログ ボックスで、をクリックして、**デバッグ**カテゴリ。  
  
3.  **全般**ボックスで、設定**を有効にする .NET Framework のソースのステップ インします。**  
  
    1.  [マイ コードのみ] が有効だった場合、[マイ コードのみ] が無効になったことを示す警告ダイアログ ボックスが表示されます。 **[OK]** をクリックします。  
  
    2.  シンボル キャッシュの場所が設定されていない場合は、既定のシンボル キャッシュの場所が設定されたことを示す別の警告ダイアログ ボックスが表示されます。 **[OK]** をクリックします。  
  
4.  下、**デバッグ**カテゴリで、をクリックして**シンボル**します。  
  
5.  シンボル キャッシュの場所を変更する場合は、場所を編集**このディレクトリにシンボルをキャッシュ** をクリックしてまたは**参照**場所を選択します。  
  
6.  シンボルを即時にダウンロードする場合は、クリックして**シンボルの読み込みは、上記の場所を使用して**します。  
  
     このボタンは、デザイン モードでは使用できませんはデバッグ中に使用できます。  
  
     シンボルを即時にダウンロードしない場合、次にプログラムのデバッグを開始するときにシンボルは自動的にダウンロードされます。  
  
7.  **[OK]** をクリックして、**[オプション]** ダイアログ ボックスを閉じます。  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>[モジュール] ウィンドウを使用して Framework シンボルを読み込むには  
  
1.  **モジュール**ウィンドウ (デバッグ中に、次のように選択します**デバッグ** > **Windows** > **モジュール**)、。シンボルが読み込まれていないモジュールを右クリックします。 シンボルが読み込まれている場合、またはしないを見てわかります、**シンボル ステータス**列。  
  
2.  をポイント**シンボル設定** をクリック**Microsoft シンボル サーバー** Microsoft パブリック シンボル サーバーからシンボルをダウンロードします。 あるいは、モジュールを右クリックして選択**シンボルの読み込み**シンボルを以前保存したディレクトリから読み込めません。  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>[呼び出し履歴] ウィンドウを使用して Framework シンボルを読み込むには  
  
1.  **呼び出し履歴**ウィンドウで、シンボルが読み込まれていないフレームを右クリックします。 フレームが淡色表示されます。  
  
2.  をポイント**シンボルの設定**クリック**Microsoft シンボル サーバー**、またはモジュールを右クリックし、選択**シンボル パス**。  
  
## <a name="see-also"></a>関連項目  
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)   
 [シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)