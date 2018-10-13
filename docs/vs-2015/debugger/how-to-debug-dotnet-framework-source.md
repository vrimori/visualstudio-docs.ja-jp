---
title: '方法: .NET Framework のソースをデバッグ |Microsoft Docs'
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
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c717e1d9eccce48319d8a73dd52d7f13ce36296e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240618"
---
# <a name="how-to-debug-net-framework-source"></a>方法 : .NET Framework ソースをデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

最新バージョンの[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]向けの新機能を提供します。[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]デバッグします。 デバッグする[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]、ソース コードのデバッグ シンボルへのアクセスが必要です。 ステップ インを有効にする必要も[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]ソース。  
  
 有効にできます[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]ステップ実行とシンボルのダウンロード、**オプション** ダイアログ ボックス。 シンボルのダウンロードを有効にする場合は、シンボルを即時にダウンロードするのか、後でダウンロードするのかを選択できます。 シンボルを即時にダウンロードしない場合、次にアプリケーションのデバッグを開始するときにシンボルはダウンロードされます。 また、手動でダウンロードを行うことができます、**モジュール**ウィンドウまたは**呼び出し履歴**ウィンドウ。  
  
### <a name="to-enable-net-framework-source-debugging"></a>.NET Framework ソースのデバッグを有効にするには  
  
1.  **ツール** メニューのをクリックして**オプション**秒。  
  
2.  **オプション**ダイアログ ボックスで、をクリックして、**デバッグ**カテゴリ。  
  
3.  **全般**ボックスで、設定**を有効にする .NET Framework**ソースのステッピングします。  
  
    1.  [マイ コードのみ] が有効だった場合、[マイ コードのみ] が無効になったことを示す警告ダイアログ ボックスが表示されます。 **[OK]** をクリックします。  
  
    2.  シンボル キャッシュの場所が設定されていない場合は、既定のシンボル キャッシュの場所が設定されたことを示す別の警告ダイアログ ボックスが表示されます。 **[OK]** をクリックします。  
  
4.  下、**デバッグ**カテゴリで、をクリックして**シンボル**します。  
  
5.  シンボル キャッシュの場所を変更する場合:   
  
    1.  開く、**デバッグ**左側にあるボックス内のノード。  
  
    2.  下、**デバッグ**ノード、をクリックして**シンボル**します。  
  
    3.  内の場所を編集**このディレクトリにシンボル サーバーからシンボルをキャッシュ** をクリックしてまたは**参照**場所を選択します。  
  
6.  シンボルを即時にダウンロードする場合は、クリックして**シンボルの読み込みは、上記の場所を使用して**します。  
  
     このボタンはデザイン モードでは使用できません。  
  
     シンボルを即時にダウンロードしない場合、次にプログラムのデバッグを開始するときにシンボルは自動的にダウンロードされます。  
  
7.  **[OK]** をクリックして、**[オプション]** ダイアログ ボックスを閉じます。  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>[モジュール] ウィンドウを使用して Framework シンボルを読み込むには  
  
1.  **モジュール**ウィンドウで、シンボルが読み込まれていないモジュールを右クリックします。 シンボルが読み込まれている場合、またはしないを見てわかります、**シンボル ステータス**列。  
  
2.  をポイント**シンボルの読み込み元** をクリック**Microsoft シンボル サーバー** Microsoft パブリック シンボル サーバーからシンボルをダウンロードまたは**シンボル パス**ディレクトリから読み込む以前保存したシンボル。  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>[呼び出し履歴] ウィンドウを使用して Framework シンボルを読み込むには  
  
1.  **呼び出し履歴**ウィンドウで、シンボルが読み込まれていないフレームを右クリックします。 フレームが淡色表示されます。  
  
2.  をポイント**シンボルの読み込み元**クリック**Microsoft シンボル サーバー**または**シンボル パス**します。  
  
## <a name="see-also"></a>関連項目  
 [マネージド コードをデバッグする](../debugger/debugging-managed-code.md)   
 [シンボルとソース コードの管理](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)



